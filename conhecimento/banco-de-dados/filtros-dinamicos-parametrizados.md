---
tipo: conceito
criado_em: 2026-10-27
atualizado_em: 2026-10-27
tags: [sql, go, filtros, metadados]
---

# Filtros dinâmicos com catálogo e parâmetros

## Resumo

O cliente descreve um filtro em JSON; o servidor usa um catálogo para conferir campo, tipo e operador, e então produz SQL com parâmetros. O catálogo funciona como um cardápio de opções permitidas: o cliente escolhe entre elas, e o backend controla como cada escolha vira SQL.

## Caminho no exemplo

1. O handler lê o JSON em `FilterNode`, que representa uma condição ou um grupo `and`/`or`.
2. O compilador consulta o snapshot para verificar se o campo existe e é filtrável.
3. A tabela `operatorsByType` determina quais operadores o tipo aceita.
4. `fieldExpr` seleciona uma coluna permitida ou monta uma expressão para acessar JSONB.
5. `args.add` acumula os valores e devolve marcadores `$1`, `$2` etc. O repository passa SQL e argumentos separadamente ao `pgx`.

## Exemplo pequeno

Adaptação didática de uma condição existente nos testes; não executada nesta captura:

```json
{"field":"department","operator":"eq","value":"Comercial"}
```

Compilada isoladamente, a condição corresponde a:

```sql
em.department = $1::text
-- argumento: "Comercial"
```

Na busca completa, o escopo já adiciona parâmetros de mês e visibilidade, então a numeração muda.

## A diferença que importa

Valores podem ser parâmetros. Nomes de coluna exigem uma escolha controlada pelo servidor: o exemplo usa `viewColumns` como lista permitida. Para JSONB, a chave é um valor da expressão de acesso e também entra como parâmetro.

O compilador ainda limita profundidade e quantidade de condições. Isso restringe a estrutura aceita, sem demonstrar sozinho que toda consulta terá bom desempenho.

O cache guarda as regras usadas nessa compilação. Reutilizá-lo não elimina as consultas dos dados finais. Também é importante distinguir a validação de uma data enviada no filtro da validade dos dados já armazenados: verificar o formato de uma string não garante que a data exista no calendário.

## Perguntas para revisar

1. Por que o nome de uma coluna não deve ser aceito como SQL livre enviado pelo cliente?
2. Qual é o papel do catálogo e qual é o papel da lista permitida de colunas?
3. O que muda se uma definição de campo for alterada enquanto o snapshot ainda estiver no TTL?

## Fontes e relações

Análise estática em 2026-10-27, revisão `dca8e1e9cfd892dc0239e24f42a2113a6b8bb592`:

- [Expressões e argumentos SQL](https://github.com/j-ordep/go-in-memory-ttl-cache-example/blob/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592/internal/analytics/fields.go).
- [Compilação e validação de filtros](https://github.com/j-ordep/go-in-memory-ttl-cache-example/blob/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592/internal/analytics/filter.go).
- [Construção do escopo e consultas](https://github.com/j-ordep/go-in-memory-ttl-cache-example/blob/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592/internal/analytics/repository.go).
- [Testes existentes de filtros](https://github.com/j-ordep/go-in-memory-ttl-cache-example/blob/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592/internal/analytics/filter_test.go), lidos, sem execução concluída nesta captura.
- [Catálogo com cache TTL](../go/catalogo-com-cache-ttl.md).
