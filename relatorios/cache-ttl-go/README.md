---
tipo: relatorio
criado_em: 2026-10-27
atualizado_em: 2026-10-27
tags: [go, cache, aprendizado, agentes]
---

# Do caso real ao conceito reutilizável

Captura de projeto em 2026-10-27, fuso America/Sao_Paulo. [Abrir versão HTML](index.html).

## Resumo

Você transformou um caso da empresa em um serviço pequeno e genérico para estudar e verificar se um agente conseguiria aplicar o conceito em outra codebase. O exemplo mostra um catálogo de metadados com cache TTL e filtros SQL guiados por essas definições. A transferência efetiva para a empresa ainda não foi demonstrada nesta captura.

## Como lembrar

O catálogo é uma ficha de consulta na mesa. Dentro do prazo, a API reutiliza a ficha. Quando o prazo vence, a próxima chamada tenta buscar outra. Se o banco falhar, continua com a anterior, quando existe.

- **Conteúdo do cache:** definições de campos e fatores, não os resultados das buscas.
- **Carga:** lê `attribute_definitions` e `risk_factors` e cria um snapshot com listas e mapas por chave.
- **TTL:** um minuto desde a carga bem-sucedida; a atualização é sob demanda.
- **Invalidação:** marca a versão como vencida; a próxima chamada tenta recarregar.
- **Filtros:** o catálogo valida campos e operadores; os valores seguem separados do SQL. Uma lista permitida controla os nomes de coluna.

## A experiência e o projeto

**Relato do usuário, em 2026-10-27:** o caso nasceu de um problema da empresa, está sendo implementado e foi generalizado para publicação e aprendizado. O experimento procura avaliar a transferência do conceito por um agente.

- **Repositório:** [j-ordep/go-in-memory-ttl-cache-example](https://github.com/j-ordep/go-in-memory-ttl-cache-example).
- **Revisão consultada:** `dca8e1e9cfd892dc0239e24f42a2113a6b8bb592`, na branch `main` no momento da captura.
- **Associação confirmada:** link e propósito fornecidos pelo usuário nesta conversa.
- **Contexto em aberto:** problema empresarial específico, prompt de transferência, resultado da implementação, tarefa Jira e PR da empresa.
- **Caminho local original e codebase de destino:** não informados. A cópia temporária dos testes não representa o checkout do usuário.

## Para levar à codebase

**Interpretação do agente:** um exemplo pequeno pode servir como uma especificação concreta de comportamento. É útil explicar quando recarregar, como responder a falhas e quem pode alterar o snapshot. A organização dos arquivos e a infraestrutura podem mudar no projeto de destino.

- **Dados antigos:** o fallback não tem limite próprio de idade; decidir se isso atende ao caso real.
- **Concorrência:** o mutex permanece adquirido durante a carga. Outros consumidores que chamam `Get` aguardam a recarga.
- **Compartilhamento:** o snapshot precisa ser tratado como somente leitura; essa imutabilidade é uma convenção. Cada processo mantém seu próprio cache e sua invalidação.

O benefício esperado é facilitar estudo e transferência. Não há ganho de desempenho medido nem confirmação de sucesso na empresa nesta captura.

## Detalhes da verificação

- **Implementação:** README, catálogo, campos, filtros, repository, HTTP e inicialização foram consultados na revisão fixa.
- **Testes de filtros:** existem cenários de compilação, rejeição e parametrização; foram lidos.
- **Tentativa de execução:** `go test -mod=mod ./... -skip '^TestIntegration' -v`, em cópia temporária, parou na preparação por bloqueio de rede ao baixar `pgx/v5`. Os cenários não tiveram execução concluída; isso não é aprovação ou reprovação dos testes.
- **PostgreSQL:** integração não executada; o repositório não inclui migrations ou dados de preparação.
- **Cache em execução:** análise estática. Não foram encontrados testes unitários específicos de TTL/recarga na revisão consultada.
- **Empresa e impacto:** implementação de destino e resultados ainda sem evidência consultada.

## Revisão rápida

**Passou um minuto sem requisições. O cache foi atualizado?** Não. O TTL vence, mas a recarga só ocorre quando uma chamada pede o catálogo.

**Invalidar consulta o banco imediatamente?** Não. `Invalidate` zera o instante da carga. O próximo `Get` tenta recarregar e ainda pode usar a versão anterior se a consulta falhar.

## Próximo passo

Escolher uma alteração concreta na codebase de destino. Definir o comportamento esperado e conferir primeira carga, leitura dentro do TTL, expiração, invalidação, falha com e sem versão anterior e duas chamadas simultâneas durante uma recarga.

Perguntas para completar o caso:

- Qual era o problema concreto da empresa?
- Qual parte o agente já aplicou? O que acertou e o que precisou de correção?
- Se o banco falhar por horas, usar o catálogo antigo é aceitável?
- Que comportamento precisa ser preservado e que parte é específica do laboratório?

## Fontes e aprofundamento

- [README do exemplo](https://github.com/j-ordep/go-in-memory-ttl-cache-example/blob/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592/README.md) e [código na revisão consultada](https://github.com/j-ordep/go-in-memory-ttl-cache-example/tree/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592).
- [Catálogo com cache TTL em Go](../../conhecimento/cache-ttl-go.md).
- [Filtros dinâmicos com parâmetros](../../conhecimento/filtros-sql-parametrizados.md).
