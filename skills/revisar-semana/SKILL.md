---
name: revisar-semana
description: Revisa trabalho de um período usando Jira, GitHub e Git local para registrar contribuições, impacto e aprendizados. Use para retrospectivas pessoais e registros semanais com evidências.
---

# Revisar semana

Produza uma retrospectiva pessoal que conecte trabalho realizado e aprendizado reutilizável. Siga o [AGENTS.md da base](../../AGENTS.md).

## Definir o recorte

Use o período e os projetos pedidos. Sem período explícito, considere os sete dias corridos encerrados no momento da consulta; registre os limites exatos e o fuso `America/Sao_Paulo`. Respeite outro recorte informado pelo usuário.

Identifique a conta do usuário pelos conectores e pelo contexto disponível. Se houver ambiguidade, pergunte. Um responsável atual no Jira ou o autor configurado no Git não bastam, isoladamente, para atribuir toda a execução de uma tarefa à pessoa.

## Reunir evidências

1. Consulte o mapeamento `perfil/projetos.md`, caso exista, e as referências fornecidas. Use os conectores disponíveis para Jira e GitHub; use Git local para os repositórios relacionados.
2. No Jira, examine tarefas e alterações relevantes no período, contexto e conclusão. Consulte comentários ou histórico quando necessários para entender a contribuição. Diferencie o estado atual do que aconteceu no período.
3. No GitHub, examine PRs, commits e revisões pertinentes. Registre se a mudança está aberta, integrada ou tem implantação comprovada; um merge não comprova implantação.
4. Respeite a paginação das ferramentas. Se o acesso ou o volume limitar a consulta, registre fontes consultadas, período coberto e o que ficou incompleto. Não apresente uma amostra como inventário completo.

Se um conector estiver indisponível, continue com arquivos, links acessíveis, Git local ou relato fornecido. Não interprete falta de acesso ou de resultados como ausência de trabalho.

## Relacionar tarefa e código

Procure primeiro links de desenvolvimento da tarefa, referências explícitas à chave no PR ou commit e o repositório remoto correspondente. Valide o conteúdo da alteração antes de afirmar que ela resolve a tarefa. Relacione o remoto ao caminho local conhecido e leia apenas os arquivos pertinentes.

Nomes parecidos, branches sem contexto e datas próximas geram candidatos. Se a associação continuar incerta, pergunte qual repositório, caminho, PR ou contexto corresponde à tarefa. Prossiga nas demais tarefas enquanto essa informação estiver pendente.

Quando o usuário confirmar a relação, registre em `perfil/projetos.md` a identificação do projeto, o repositório remoto, o caminho local quando disponível e a data/origem da confirmação. Um projeto Jira pode envolver vários repositórios. Caminhos variam entre máquinas; use remoto, arquivo relativo e commit como referência durável.

## Produzir a retrospectiva

Grave em `relatorios/semanais/YYYY-MM-DD-a-YYYY-MM-DD.md`, usando as datas do intervalo consultado. Antes de escrever, procure uma retrospectiva com o mesmo recorte. Atualize-a sem duplicar itens; se os escopos forem diferentes, identifique o projeto no nome.

Use `tipo: retrospectiva`, os metadados comuns e o período exato no corpo. Inclua:

- **Resumo:** principais entregas, aprendizados e pendências.
- **Contribuições:** tarefa/PR, participação identificada, mudança, estado e links de evidência. Não atribua ao usuário trabalho de outras pessoas.
- **Impacto:** resultados medidos com fonte ou benefícios esperados identificados como expectativa. Quantidade de commits não mede valor entregue.
- **Aprendizados:** conceitos, investigação e decisões que merecem ser reutilizados.
- **Lacunas:** associações incertas, fontes indisponíveis e perguntas pendentes.
- **Próximos passos:** poucas ações justificadas pelas evidências.

Para aprendizados que mereçam uma nota própria, use [Capturar aprendizado](../capturar-aprendizado/SKILL.md) e vincule o resultado. Não transforme toda tarefa em uma nota: priorize descobertas, decisões e padrões úteis.

## Exemplo de pedido

> Revise minha semana. A tarefa EXEMPLO-123 pode estar no projeto de pagamentos, mas não tenho certeza.

Trate a relação como candidata. Procure a chave e os links nos projetos indicados; se não houver evidência suficiente, peça o projeto ou PR correto e registre a lacuna. Não use a suspeita para declarar a tarefa entregue pelo usuário.

## Entrega

Informe o período, o caminho da retrospectiva, as notas relacionadas e os limites da coleta. Esta execução registra a revisão local; frequência semanal é uma rotina de uso, não um agendamento criado pela skill.
