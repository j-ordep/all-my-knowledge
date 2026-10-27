---
name: revisar-conhecimento
description: Conduz uma revisão interativa das notas com perguntas e pequenos exercícios. Use quando o usuário quiser praticar recordação, explicar conceitos ou verificar se consegue aplicar o que estudou.
---

# Revisar conhecimento

Use o conteúdo da base para praticar recordação, explicação e aplicação. Siga o [AGENTS.md da base](../../AGENTS.md).

## Preparar

Leia as notas do assunto solicitado e seus registros anteriores de revisão, quando existirem. Se o tema for amplo, proponha um recorte pequeno relacionado ao objetivo conhecido. Identifique inconsistências nas notas antes de usá-las como gabarito.

Escolha perguntas que ajudem a observar raciocínio. Uma combinação útil é recordar a ideia central, explicar uma decisão e resolver uma situação diferente. Ajuste quantidade e profundidade ao pedido.

## Conduzir a sessão

1. Faça uma pergunta por vez e aguarde a resposta. Se o usuário pedir uma lista de questões, entregue a lista no formato solicitado.
2. Não mostre o gabarito antes da tentativa, salvo pedido do usuário. Ofereça uma pista quando ela ajudar a pessoa a continuar pensando.
3. Compare a resposta com o conceito e com a justificativa esperada. Explique o que está correto, o que falta e por que isso muda o resultado.
4. Proponha uma variação para verificar transferência quando fizer sentido. Em exercícios de código, diferencie o que foi executado do que foi inspecionado.
5. Se o usuário preferir interromper ou estudar a explicação, respeite a escolha. Não registre uma tentativa inexistente como resposta errada.

Use perguntas como “o que aconteceria se esta condição mudasse?” ou “qual evidência descartaria sua hipótese?”. Evite depender apenas de memorização de termos.

## Registrar o que foi observado

Ao concluir uma sessão solicitada para esta base, salve uma síntese em `relatorios/revisoes/YYYY-MM-DD-<assunto>.md`, com `tipo: revisao` e os metadados comuns. Se já houver uma sessão nesse arquivo, acrescente um registro identificado pelo horário sem apagar o anterior.

Inclua notas consultadas, perguntas efetivamente respondidas, síntese fiel das respostas do usuário, ajuda oferecida, acertos, lacunas e uma sugestão de prática. Preserve a distinção entre resposta independente, resposta com pista e explicação dada pelo agente.

Para uma lista avulsa de questões ou um pedido de explicação, responda no chat; isso não constitui avaliação do usuário. Se a sessão terminar antes de haver respostas, registre apenas a interrupção quando houver necessidade de salvar o estado.

Uma revisão indica o desempenho naquele contexto. Não converta poucas respostas em um diagnóstico amplo de competência, preferência ou carreira.

## Exemplo de pedido

> Quero revisar a nota sobre transações. Faça perguntas e veja onde estou com dificuldade.

Leia a nota e comece com uma pergunta sobre o problema que uma transação resolve. Depois da resposta, ajuste a dificuldade e use um caso com falha entre duas operações. Mostre a explicação comentada depois da tentativa.

## Entrega

Resuma o que o usuário demonstrou, a principal lacuna e o próximo exercício. Vincule o registro salvo e as notas para consulta. Sugira uma próxima revisão quando útil, sem criar um agendamento automaticamente.
