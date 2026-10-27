---
tipo: experiencia
criado_em: 2026-10-27
atualizado_em: 2026-10-27
tags: [go, aprendizado, agentes, transferencia-de-conhecimento]
---

# Extrair um caso genérico para orientar um agente

## Resumo

O usuário relatou ter transformado um caso da empresa em um serviço pequeno e genérico, publicado no GitHub. O objetivo era verificar se um agente conseguiria entender o conceito e aplicá-lo na codebase de destino. O repositório público permite estudar catálogo com cache TTL e filtros dinâmicos; a transferência efetiva para a empresa ainda não foi demonstrada nesta captura.

## Contexto relatado

Fonte: relato do usuário nesta conversa, em 2026-10-27.

- O caso nasceu de um problema da empresa e está sendo implementado.
- O exemplo foi generalizado para publicação e aprendizado.
- O experimento procura avaliar a capacidade do agente de transferir um conceito entre projetos.

O problema empresarial específico, o prompt usado na transferência e o resultado da implementação não foram detalhados. Não foram fornecidos uma tarefa Jira, um PR da empresa ou o caminho da codebase de destino.

## O que o exemplo permite estudar

O catálogo carrega metadados de duas tabelas, monta um snapshot e o compartilha em memória. A aplicação configura TTL de um minuto, recarga sob demanda, invalidação explícita e fallback para o último snapshot disponível. Os filtros usam essas definições para validar entradas e construir SQL parametrizado.

Os detalhes estão nas notas de [cache e TTL](../conhecimento/go/catalogo-com-cache-ttl.md) e [filtros dinâmicos](../conhecimento/banco-de-dados/filtros-dinamicos-parametrizados.md).

## Aprendizado extraído

**Interpretação do agente:** um exemplo pequeno pode servir como uma especificação concreta de comportamento. Ao transferi-lo, vale explicar quais contratos precisam continuar verdadeiros: quando recarregar, o que fazer em falhas e quem pode alterar o snapshot. A codebase de destino pode exigir outra organização de arquivos ou outra infraestrutura.

Isso é uma proposta de uso do exemplo, não uma confirmação de que o agente já fez a transferência corretamente.

## Estado da verificação

| Item | Evidência desta captura |
| --- | --- |
| Repositório público e implementação | README e arquivos Go consultados em revisão fixa |
| Testes de filtros | Existem cenários de compilação, rejeição e parametrização; foram lidos |
| Tentativa de execução | `go test -mod=mod ./... -skip '^TestIntegration' -v` em cópia temporária falhou na preparação: acesso ao proxy de módulos bloqueado ao baixar `pgx/v5` |
| Integração PostgreSQL | Não executada; o repositório não inclui migrations ou dados de preparação |
| Comportamento do cache em execução | Analisado estaticamente; não foram encontrados testes unitários específicos de TTL/recarga na revisão consultada |
| Aplicação na empresa e impacto | Ainda sem evidência consultada |

O bloqueio da preparação dos testes não é um resultado de aprovação ou reprovação dos cenários.

## Próxima validação sugerida

Escolher uma alteração concreta na codebase de destino e comparar: primeira carga, leitura dentro do TTL, expiração, invalidação e falha com/sem versão anterior. Observar também duas chamadas simultâneas durante uma recarga. Registrar o comportamento esperado antes de avaliar o que o agente produziu.

## Perguntas que completam a experiência

1. Qual era o problema concreto que motivou a extração do serviço?
2. O agente já aplicou o conceito na empresa? O que acertou ou precisou de correção?
3. Que comportamento precisa ser preservado e que parte é específica do laboratório?

## Fontes e relações

- [README do exemplo](https://github.com/j-ordep/go-in-memory-ttl-cache-example/blob/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592/README.md).
- Revisão analisada: `dca8e1e9cfd892dc0239e24f42a2113a6b8bb592`, consultada em 2026-10-27.
- [Projeto na base](../perfil/projetos.md).
- [Relatório curto](../relatorios/2026-10-27-cache-ttl-go.md) e [versão HTML](../relatorios/2026-10-27-cache-ttl-go.html).
