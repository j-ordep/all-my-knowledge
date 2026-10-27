# All My Knowledge

Uma base pessoal para transformar estudos, tarefas e problemas resolvidos em conhecimento que eu consiga encontrar, lembrar e aplicar novamente.

Este projeto reúne as instruções para cuidar da base, as skills que executam os fluxos e, conforme o uso, minhas notas, exemplos e relatórios. Markdown é o formato principal, para leitura no Obsidian, no GitHub e em editores de texto. Relatórios HTML apresentam visões desse mesmo conteúdo.

## Estudos registrados

| Estudo | Leitura rápida | Aprofundamento |
| --- | --- | --- |
| Caso genérico de cache TTL em Go | [Relatório](relatorios/2026-10-27-cache-ttl-go.md) · [HTML](relatorios/2026-10-27-cache-ttl-go.html) | [Cache TTL](conhecimento/go/catalogo-com-cache-ttl.md) · [Filtros SQL](conhecimento/banco-de-dados/filtros-dinamicos-parametrizados.md) · [Experiência](experiencias/2026-10-27-case-generico-cache-go.md) |

As fontes relacionadas estão no [mapa de projetos](perfil/projetos.md).

## Comece por aqui

Abra esta pasta no seu agente e peça uma ação concreta. O [AGENTS.md](AGENTS.md) explica as convenções e indica qual skill ler.

Exemplo de primeiro uso:

> Leia `skills/capturar-aprendizado/SKILL.md` e registre o que aprendi ao resolver este problema. Vou fornecer o contexto e indicar o projeto relacionado.

Para usar a inspiração da revisão semanal:

> Leia `skills/revisar-semana/SKILL.md` e revise meu trabalho dos últimos sete dias. Consulte as fontes disponíveis do Jira e GitHub, relacione com o código local e pergunte quando a associação estiver incerta. Registre o resumo e os aprendizados relevantes.

O agente usa os acessos disponíveis na sessão. As skills descrevem o procedimento; não fornecem credenciais nem estabelecem conexões por conta própria.

## Skills

| Skill | Quando usar | Resultado |
| --- | --- | --- |
| [Capturar aprendizado](skills/capturar-aprendizado/SKILL.md) | Depois de estudar, descobrir algo ou resolver um problema | Nota de conceito ou experiência, resumo, exemplos e perguntas |
| [Revisar semana](skills/revisar-semana/SKILL.md) | Para revisar entregas e aprendizados de um período | Retrospectiva com fontes, contribuição, impacto e links para conhecimento |
| [Planejar aprendizado](skills/planejar-aprendizado/SKILL.md) | Para decidir o que estudar e por quê | Prioridades relacionadas a objetivos, interesses e lacunas |
| [Revisar conhecimento](skills/revisar-conhecimento/SKILL.md) | Para praticar o que está na base | Perguntas, exercícios e registro do que foi demonstrado |
| [Gerar relatório](skills/gerar-relatorio/SKILL.md) | Para analisar a base visualmente | HTML local com resumo, evidências e próximos passos |

As skills podem ser usadas individualmente. Uma revisão semanal pode alimentar notas de conhecimento; essas notas podem orientar estudos e relatórios.

## Estrutura

```text
all-my-knowledge/
├── AGENTS.md
├── README.md
├── conhecimento/
│   ├── go/
│   └── banco-de-dados/
├── experiencias/
├── perfil/
├── relatorios/
└── skills/
    ├── capturar-aprendizado/SKILL.md
    ├── revisar-semana/SKILL.md
    ├── planejar-aprendizado/SKILL.md
    ├── revisar-conhecimento/SKILL.md
    └── gerar-relatorio/SKILL.md
```

As pastas de conteúdo crescem conforme houver material para registrar:

| Pasta | Conteúdo |
| --- | --- |
| `conhecimento/` | Conceitos, explicações e relações entre assuntos |
| `experiencias/` | Contexto, investigação e solução de casos reais |
| `perfil/` | Objetivos, interesses confirmados, projetos relacionados e planos de estudo |
| `relatorios/` | Retrospectivas, registros de revisão e relatórios HTML |
| `exemplos/` | Exemplos de código que precisem de arquivos próprios |

## Como o conhecimento será registrado

Uma nota começa com um resumo curto. Conforme o assunto, aprofunda o contexto, a explicação, o raciocínio da solução, o código e suas limitações. As fontes permitem voltar à tarefa, ao commit, ao documento ou ao relato que deu origem ao aprendizado.

Perguntas de revisão ajudam a praticar três coisas: recordar o conceito, explicar uma decisão e aplicar o aprendizado em uma situação diferente. Notas existentes são atualizadas para evitar várias versões da mesma explicação.

Na análise de direção dos estudos, serão consideradas separadamente:

- **Interesse:** o que eu declaro gostar ou querer explorar.
- **Necessidade:** o que preciso aprender para um objetivo concreto.
- **Domínio observado:** o que consegui explicar ou aplicar em uma revisão.
- **Dificuldade:** onde encontrei obstáculos e qual foi o contexto.

Uma hipótese do agente permanece identificada como hipótese até ser confirmada. Impacto medido exige evidência; expectativa de melhoria é registrada como expectativa.

## Obsidian, GitHub e HTML

No Obsidian, abra esta pasta como um vault. A navegação principal usa links Markdown relativos, e os exemplos de código ficam legíveis no próprio arquivo.

Quando o projeto for versionado e enviado ao GitHub, suas notas poderão ser consultadas por lá. Nenhuma publicação é necessária para usar a base localmente.

Relatórios HTML serão gerados sob demanda a partir das notas e abertos no navegador. A visualização de um arquivo HTML no repositório do GitHub normalmente mostra seu código; hospedá-lo como página é uma configuração adicional.

Os relatórios terão texto claro, direto e pouco formal, com analogias curtas quando ajudarem a entender. O padrão é ser conciso, com aprofundamento quando eu pedir ou quando for necessário para compreender a conclusão.

## Uso das skills no agente

A pasta `skills/` é o catálogo deste projeto. O `AGENTS.md` encaminha os pedidos aos arquivos correspondentes, e também é possível pedir explicitamente a leitura de um `SKILL.md`, como nos exemplos acima.

A descoberta nativa de skills locais pelo Codex usa diretórios como `.agents/skills/`. Este projeto mantém o catálogo em `skills/`; ele ainda não foi instalado nesses diretórios. Essa distinção evita depender de um nome no seletor que pode não estar disponível. Veja a [documentação oficial de skills](https://learn.chatgpt.com/docs/build-skills) e de [AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md).

## Estado e próximo passo

As diretrizes e as cinco skills estão escritas. A primeira captura usa o repositório público de cache TTL em Go e inclui conceitos, experiência, mapeamento do projeto e relatório Markdown/HTML. A tentativa de testes Go ficou bloqueada no download de dependências; as conclusões técnicas se baseiam na leitura do código.

O próximo passo desse estudo é completar o contexto do problema e avaliar a transferência para a codebase de destino. A consulta ao Jira, a associação com checkouts originais e a rotina agendada de sexta-feira ainda não foram exercitadas.

## Inspiração

A ideia começou com o [vídeo indicado pelo usuário, no trecho de 01:05](https://www.youtube.com/watch?v=2E5P_l3UXD4&t=65s), descrito como uma rotina semanal que consulta Jira e GitHub e registra impacto. O escopo foi ampliado na conversa para incluir aprendizado técnico, revisão e direção dos estudos. A transcrição completa do vídeo não foi verificada.
