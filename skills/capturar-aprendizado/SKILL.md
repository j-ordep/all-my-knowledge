---
name: capturar-aprendizado
description: Registra estudos, conceitos e problemas resolvidos na base pessoal em Markdown. Use quando o usuário pedir para guardar um aprendizado, explicar uma solução ou conectar uma experiência ao conhecimento existente.
---

# Capturar aprendizado

Transforme o material fornecido em uma nota que ajude o usuário a recordar e reutilizar o aprendizado. Siga o [AGENTS.md da base](../../AGENTS.md). Esta distribuição usa a base que contém esse arquivo; se o destino estiver ambíguo, confirme antes de gravar.

## Entrada e escolha da nota

Use a conversa, os arquivos, as fontes ou a tarefa indicados pelo usuário. Identifique o aprendizado central e procure notas relacionadas antes de criar uma nova.

- Um conceito reutilizável pertence a `conhecimento/<assunto>/<conceito>.md`.
- Um problema com contexto e investigação próprios pertence a `experiencias/YYYY-MM-DD-<caso>.md`.
- Quando ambos forem úteis, registre o caso e vincule o conceito; mantenha a explicação geral em um único lugar.

Os caminhos acima são padrões de destino, não arquivos prontos. Use uma estrutura existente quando ela já atender ao assunto.

Se o usuário mencionar código ou uma tarefa sem indicar sua localização, procure nas referências e nos projetos conhecidos da base. Pergunte pelo projeto, arquivo ou contexto que faltar. Nunca transforme uma associação incerta em fato.

## Construção

1. Leia as fontes necessárias e identifique o que elas realmente demonstram. Peça detalhes sobre decisões pessoais quando o código ou o relato não explicarem o motivo.
2. Selecione o que vale preservar. Uma captura pequena pode resultar em uma nota curta; não crie uma aula extensa por padrão.
3. Escreva o resumo e a explicação. Inclua os mecanismos que tornam a solução compreensível, suas condições de uso e limitações relevantes.
4. Acrescente um exemplo de código quando ele ajudar. Diferencie trecho real de adaptação didática e execução comprovada de análise estática.
5. Conecte a nota a conhecimentos existentes e às fontes. Ao atualizar uma nota, preserve conteúdo válido e explique mudanças de entendimento relevantes.

## Formato orientador

Use os metadados comuns definidos no AGENTS.md, com `tipo: conceito` ou `tipo: experiencia`. Adapte as seções à utilidade para o caso:

- **Resumo:** duas a cinco frases com a ideia central e quando usá-la.
- **Contexto:** problema, objetivo e restrições relevantes.
- **Explicação ou resolução:** mecanismo, investigação, decisões e motivos conhecidos. Registre tentativas anteriores somente se houver evidência ou relato.
- **Exemplo:** código mínimo, resultado esperado e estado de verificação, quando aplicável.
- **Quando usar e limites:** condições que mudam a escolha ou exigem cuidado técnico.
- **Perguntas para revisão:** recordar o conceito, justificar uma decisão e transferir para outro cenário. Deixe as respostas comentadas em uma seção posterior, quando úteis.
- **Fontes e relações:** notas, documentos, tarefa, repositório e revisão de código, conforme disponíveis.

Para conhecimento baseado apenas na conversa, identifique a fonte como relato do usuário e registre a data. Não invente um link de conversa. Explicações adicionais do agente devem ser diferenciadas do histórico real.

## Exemplo de pedido

> Registre o que aprendi ao corrigir esta consulta e relacione com minha nota sobre índices.

Leia a consulta e a nota existente. Acrescente a explicação reutilizável à nota de índices. Crie uma experiência separada apenas se houver uma investigação ou contexto que mereça ser preservado. Ganhos de desempenho precisam de medições; sem elas, registre a justificativa técnica e a verificação pendente.

## Entrega

Confira os links e se o resumo representa a explicação. Informe os arquivos criados ou atualizados e as lacunas relevantes. Se a solicitação for apenas uma explicação ou proposta, entregue no chat sem registrar como experiência confirmada.
