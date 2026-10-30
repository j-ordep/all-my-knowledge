# All My Knowledge

Uma base pessoal para transformar estudos, tarefas e problemas resolvidos em conhecimento que eu consiga encontrar, lembrar e aplicar novamente.

Este projeto reúne as instruções para cuidar da base, as skills que executam os fluxos e, conforme o uso, minhas notas, exemplos e relatórios. Markdown é o formato principal, para leitura no Obsidian, no GitHub e em editores de texto. Relatórios HTML apresentam visões desse mesmo conteúdo.

## Estudos registrados

| Estudo | Ler Markdown | Abrir HTML |
| --- | --- | --- |
| Caso genérico de cache TTL em Go | [Relatório completo](relatorios/cache-ttl-go/README.md) | [Versão visual](relatorios/cache-ttl-go/index.html) |

A experiência, os dados do projeto e os próximos passos ficam no próprio relatório. Para aprofundar conceitos, consulte [Cache TTL](conhecimento/cache-ttl-go.md) e [Filtros SQL](conhecimento/filtros-sql-parametrizados.md).

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
| [Capturar aprendizado](skills/capturar-aprendizado/SKILL.md) | Depois de estudar, descobrir algo ou resolver um problema | Relatório do tema com experiência, resumo e perguntas; nota de conceito quando útil |
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
├── relatorios/
│   └── cache-ttl-go/
│       ├── README.md
│       └── index.html
├── conhecimento/
│   ├── cache-ttl-go.md
│   └── filtros-sql-parametrizados.md
└── skills/
    ├── capturar-aprendizado/SKILL.md
    ├── revisar-semana/SKILL.md
    ├── planejar-aprendizado/SKILL.md
    ├── revisar-conhecimento/SKILL.md
    └── gerar-relatorio/SKILL.md
```

Há duas áreas de conteúdo:

| Pasta | Conteúdo |
| --- | --- |
| `relatorios/<tema>/` | Um relatório em Markdown e sua apresentação HTML; inclui experiência, fontes, objetivos e próximos passos pertinentes |
| `conhecimento/` | Referências de conceitos reutilizáveis, sem subpastas por assunto |

Comece pelo relatório: ele deve permitir entender o caso sem navegar por vários arquivos. Só crie notas separadas de conhecimento quando trouxerem benefício de reutilização. Planos e sessões de revisão ficam em seções do tema, com data; uma revisão semanal independente recebe sua própria pasta de relatório. Exemplos com arquivos próprios ficam junto ao tema.

## Como o conhecimento será registrado

O relatório começa com um resumo curto e reúne o contexto, a experiência, a explicação, o raciocínio da solução, o código e suas limitações, conforme forem úteis. As fontes permitem voltar à tarefa, ao commit, ao documento ou ao relato que deu origem ao aprendizado.

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

Cada pasta de tema usa `README.md` como fonte principal e `index.html` como apresentação do mesmo conteúdo. Quando o Markdown mudar, o HTML existente deve ser sincronizado. A versão visual pode recolher detalhes para manter a leitura leve.

Os relatórios terão texto claro, direto e pouco formal, com analogias curtas quando ajudarem a entender. O padrão é ser conciso, com aprofundamento quando eu pedir ou quando for necessário para compreender a conclusão.

## Uso das skills no agente

A pasta `skills/` é o catálogo deste projeto. O `AGENTS.md` encaminha os pedidos aos arquivos correspondentes, e também é possível pedir explicitamente a leitura de um `SKILL.md`, como nos exemplos acima.

A descoberta nativa de skills locais pelo Codex usa diretórios como `.agents/skills/`. Este projeto mantém o catálogo em `skills/`; ele ainda não foi instalado nesses diretórios. Essa distinção evita depender de um nome no seletor que pode não estar disponível. Veja a [documentação oficial de skills](https://learn.chatgpt.com/docs/build-skills) e de [AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md).

## Estado e próximo passo

As diretrizes e as cinco skills seguem esta organização. A primeira captura usa o repositório público de cache TTL em Go e reúne experiência, dados do projeto e verificação no mesmo relatório, com duas notas de conceitos reutilizáveis. A tentativa de testes Go ficou bloqueada no download de dependências; as conclusões técnicas se baseiam na leitura do código.

O próximo passo desse estudo é completar o contexto do problema e avaliar a transferência para a codebase de destino. A consulta ao Jira, a associação com checkouts originais e a rotina agendada de sexta-feira ainda não foram exercitadas.

## Inspiração

A ideia começou com o [vídeo indicado pelo usuário, no trecho de 01:05](https://www.youtube.com/watch?v=2E5P_l3UXD4&t=65s), descrito como uma rotina semanal que consulta Jira e GitHub e registra impacto. O escopo foi ampliado na conversa para incluir aprendizado técnico, revisão e direção dos estudos. A transcrição completa do vídeo não foi verificada.
