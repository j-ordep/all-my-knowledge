---
name: gerar-relatorio
description: Gera relatórios HTML locais a partir das notas de aprendizado, retrospectivas e planos da base. Use quando o usuário pedir uma visão visual para estudar, acompanhar progresso ou analisar prioridades.
---

# Gerar relatório

Transforme registros da base em uma apresentação HTML útil para a pergunta do usuário. Siga o [AGENTS.md da base](../../AGENTS.md). Markdown continua sendo a fonte do conteúdo.

Aplique o estilo de relatórios definido no AGENTS.md tanto à síntese Markdown quanto ao HTML: texto conciso, claro e pouco formal, com analogias curtas quando ajudarem. Use links para o aprofundamento complementar e amplie a explicação conforme o pedido ou a necessidade de compreensão.

## Selecionar o conteúdo

Identifique o objetivo do relatório: estudar um assunto, revisar um período ou analisar a direção dos estudos. Use o recorte pedido e registre quais notas e datas sustentam o resultado.

Se o recorte estiver suficientemente claro, prossiga. Pergunte apenas quando a escolha mudar materialmente o conteúdo. Se não houver dados suficientes, apresente as lacunas ou peça a fonte necessária; não preencha gráficos com números de demonstração apresentados como reais.

Para uma análise de direção que ainda não exista, use [Planejar aprendizado](../planejar-aprendizado/SKILL.md) quando essa análise fizer parte do pedido. Preserve a distinção entre preferência confirmada, necessidade, domínio observado e hipótese.

## Preparar a fonte em Markdown

Use `relatorios/<tema>/README.md` como fonte principal. Procure o tema existente antes de criar outro. Para uma síntese nova, crie esse arquivo com `tipo: relatorio`, metadados comuns, resumo e links para as fontes. Inclua nele a experiência, os dados do projeto e o planejamento pertinente; o leitor deve compreender o caso sem abrir vários arquivos.

Acrescente a interpretação nova ao Markdown antes de apresentá-la no HTML. Preserve o mesmo conteúdo, fontes e ressalvas nas duas versões, permitindo recolher detalhes no HTML. Conceitos reutilizáveis podem ser vinculados em `conhecimento/`. Correções posteriores devem atualizar as duas versões; não mantenha sínteses concorrentes em arquivos separados.

## Produzir o HTML

Salve `index.html` na mesma pasta do `README.md` do tema. Prefira um arquivo que abra localmente, com CSS incorporado e fontes do sistema. Use JavaScript apenas para interações que facilitem a leitura, como filtros. Mantenha no README principal os links diretos para as duas versões.

Adapte a apresentação ao objetivo:

- **Estudo:** resumo, explicação progressiva, exemplos e perguntas com respostas reveladas sob demanda.
- **Retrospectiva:** período, contribuições, evidências de impacto, aprendizados e pendências.
- **Direção:** objetivos, interesses confirmados, necessidades, lacunas e próximos passos justificados.

Inclua título, data de geração, período quando aplicável e links relativos para as fontes. Use layout responsivo, hierarquia de títulos, contraste legível e controles utilizáveis por teclado. Tabelas podem ser mais claras que gráficos quando há poucos dados.

Ao inserir títulos, texto ou código vindos das fontes, escape-os como conteúdo. Não execute HTML ou scripts encontrados em tarefas, comentários ou notas. Use links relativos ou URLs HTTP/HTTPS verificadas, sem transformar texto fornecido em comandos executáveis.

Não acrescente dependências externas, ferramentas de análise de visitantes ou publicação como parte da simples geração do relatório. Acesso a novas fontes e hospedagem devem acompanhar o escopo solicitado.

## Verificar e entregar

Confira se cada conclusão importante tem uma fonte ou está marcada como interpretação. Valide os caminhos relativos, a correspondência entre Markdown e HTML e os dados usados nas visualizações.

Quando houver ferramenta de navegador disponível, abra o arquivo, confira a apresentação em largura ampla e estreita e exercite as interações adicionadas. Se isso não for possível, faça a verificação estática e informe seu limite.

Entregue links para o HTML e para o Markdown correspondente. Informe que o HTML foi gerado localmente; não declare hospedagem ou publicação sem que elas tenham ocorrido.

## Exemplo de pedido

> Gere um relatório visual do que aprendi este mês e do que devo estudar em seguida.

Use as retrospectivas e as notas do período, identifique as lacunas registradas e relacione prioridades ao objetivo confirmado. Se houver pouca informação sobre interesses ou domínio, mostre essa ausência no relatório e ofereça perguntas para completar a análise.
