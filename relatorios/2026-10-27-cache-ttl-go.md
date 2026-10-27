---
tipo: relatorio
criado_em: 2026-10-27
atualizado_em: 2026-10-27
tags: [go, cache, aprendizado]
---

# Do caso real ao conceito reutilizável

Gerado em 2026-10-27, fuso America/Sao_Paulo. Captura de um projeto, sem recorte de produtividade semanal.

## O aprendizado central

Você transformou um caso da empresa em um exemplo genérico para estudar e orientar um agente, conforme seu relato. O projeto mostra como reutilizar um catálogo de metadados com cache TTL e como empregar essas definições na montagem de filtros SQL.

## Como lembrar

O catálogo é uma ficha de consulta na mesa. Dentro do prazo, a API reutiliza a ficha. Quando o prazo vence, a próxima chamada tenta buscar outra. Se o banco falhar, continua com a anterior, quando existe.

- **O que fica em cache:** definições de campos e fatores, não resultados das buscas.
- **TTL:** um minuto desde a carga bem-sucedida; a atualização é sob demanda.
- **Invalidação:** marca a versão como vencida; a próxima chamada recarrega.
- **Filtros:** o catálogo valida campos e operadores; os valores seguem separados do SQL.

## Para levar à codebase

**Interpretação:** o valor do exemplo está em explicitar o comportamento que o agente deve preservar. Antes de aplicar, decidir se dados antigos são aceitáveis, como lidar com chamadas simultâneas e como invalidar o cache quando houver várias instâncias. A imutabilidade do snapshot precisa ser respeitada pelos consumidores.

## O que foi verificado

README, implementação e testes existentes foram lidos na revisão `dca8e1e9`. A tentativa de testes Go parou no download de uma dependência por bloqueio de rede; não houve execução concluída dos cenários. PostgreSQL e a implementação da empresa não foram validados. O impacto esperado é facilitar estudo e transferência; não há ganho de desempenho medido nesta captura.

## Três perguntas para o próximo passo

1. Qual era o problema original da empresa?
2. Qual parte o agente já conseguiu aplicar e como isso foi conferido?
3. Se o banco falhar por horas, a aplicação pode continuar usando o catálogo antigo?

## Aprofundar

- [Catálogo com cache TTL em Go](../conhecimento/go/catalogo-com-cache-ttl.md).
- [Filtros dinâmicos com parâmetros](../conhecimento/banco-de-dados/filtros-dinamicos-parametrizados.md).
- [Experiência e limites da verificação](../experiencias/2026-10-27-case-generico-cache-go.md).
- [Código-fonte consultado](https://github.com/j-ordep/go-in-memory-ttl-cache-example/tree/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592).
- [Abrir apresentação HTML](2026-10-27-cache-ttl-go.html).
