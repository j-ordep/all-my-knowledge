---
name: planejar-aprendizado
description: Orienta próximos estudos a partir de objetivos, interesses declarados e lacunas observadas na base. Use quando o usuário quiser decidir o que aprender, avaliar prioridades ou analisar a direção de seu desenvolvimento.
---

# Planejar aprendizado

Ajude o usuário a escolher próximos estudos com motivos claros e uma forma concreta de verificar avanço. Siga o [AGENTS.md da base](../../AGENTS.md).

## Entender a direção

Leia o objetivo informado e os relatórios pertinentes, incluindo retrospectivas e seções de revisão de conhecimento. Se o objetivo estiver indefinido e impedir a priorização, pergunte qual resultado o usuário deseja alcançar.

Considere tempo disponível, prazo e contexto de aplicação quando informados. Sem esses dados, proponha uma sequência de estudos, sem inventar disponibilidade ou compromissos de calendário.

## Avaliar os assuntos

Mantenha estas dimensões distintas:

| Dimensão | Evidência adequada |
| --- | --- |
| Interesse | Declaração do usuário, com data e contexto |
| Necessidade | Dependência ou requisito ligado a um objetivo concreto |
| Domínio observado | Explicação, exercício ou aplicação realizada pelo usuário |
| Dificuldade | Obstáculo relatado ou observado, com o contexto em que ocorreu |

Ausência de avaliação significa **não avaliado**. Código gerado pelo agente, notas lidas ou tarefas frequentes não demonstram, por si sós, domínio ou preferência.

Apresente padrões possíveis como hipóteses e faça perguntas para confirmá-los. Dificuldade não implica desinteresse. Uma declaração de desinteresse também não elimina uma necessidade ligada ao objetivo.

## Priorizar e planejar

1. Relacione as lacunas ao objetivo e aos pré-requisitos. Explique por que um assunto é necessário, útil ou opcional.
2. Selecione poucas prioridades, normalmente de uma a três, ajustando ao tempo conhecido.
3. Para cada prioridade, defina o resultado esperado, a atividade prática, o conhecimento prévio e um critério observável de conclusão.
4. Quando um tema for necessário e pouco interessante para o usuário, proponha o domínio mínimo útil e um exercício ligado a um problema real.
5. Use referências existentes quando adequadas. Se recomendar material externo específico, verifique a fonte e sua pertinência ao objetivo.

Evite percentuais de domínio ou pontuações calculadas sem método e dados. Prefira evidências concretas, como conseguir explicar um comportamento e resolver uma variação sem consultar a solução.

## Registro

Quando o pedido incluir criar ou atualizar o planejamento, use uma seção no `relatorios/<tema>/README.md` existente. Para um planejamento independente, crie `relatorios/<objetivo>/README.md`, com `tipo: plano` e os metadados comuns. Inclua objetivo, evidências utilizadas, prioridades, atividades, critérios de conclusão e questões em aberto.

Registre interesses e objetivos confirmados no próprio relatório, preservando a data e o contexto. Não transforme sugestões de carreira ou hipóteses em preferências permanentes. Atualize o índice principal quando criar um relatório e sincronize seu `index.html` caso exista, usando [Gerar relatório](../gerar-relatorio/SKILL.md). Se o usuário pedir apenas sugestões, apresente-as no chat.

## Exemplo de pedido

> Tenho estudado muito banco de dados. Veja se devo seguir nessa direção ou focar em testes.

Investigue o objetivo, as revisões e as dificuldades registradas. A frequência de estudos de banco de dados não confirma preferência. Compare como cada assunto contribui para o resultado desejado e proponha uma experiência de estudo quando ainda faltar evidência para escolher.

## Entrega

Explique o próximo passo e a razão da prioridade. Aponte o plano salvo quando houver, as informações confirmadas e as hipóteses que ainda dependem do usuário.
