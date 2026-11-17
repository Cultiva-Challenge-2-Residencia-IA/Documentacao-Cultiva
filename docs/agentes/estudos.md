# Agente de Estudos

!!! warning "Rascunho em construção"
    Página em definição pela equipe (iniciada em 17/11/2026). As seções trazem **propostas** de 17/11, ainda a confirmar com o grupo; as decisões em aberto estão na seção 12. Classificação das afirmações, como em todo o projeto: **requisito documentado** (está nos requisitos ou nas regras de negócio, com aprovação ainda não confirmada), **decisão da equipe** (com data), **proposta** (sugestão ainda não decidida) e **hipótese** (benefício a testar).

Os requisitos ficam na lista única do projeto ([Requisitos](../requisitos/index.md) e [Regras de Negócio](../regras-de-negocio.md)). Esta página não cria requisitos: só aponta para eles e registra as decisões de escopo do agente. Uma regra nova necessária para Estudos entra na lista única, com número próprio.

## 1. Definições

| | |
|---|---|
| **Objetivo** | Apoiar o estudante no **planejamento, na realização e na revisão** da rotina de estudos, oferecendo próximos passos claros, técnicas de estudo com fonte e sugestões de foco e de lembretes (RF-A14), e ajustando o plano à disponibilidade, ao progresso informado e à rotina registrada nas outras abas, como cansaço, refeições e treinos (RN06). |
| **ODS** | 4 (Educação de Qualidade), pela aba Estudos ([Visão geral](../projeto/index.md)) |
| **Limite** | Como todo o CULTIVA, apoio educativo e organizacional, sem diagnóstico nem substituição de profissionais. Não faz o trabalho acadêmico pelo aluno, não ensina o conteúdo das matérias e não indica remédio (seção 4). |

**Requisitos documentados que se aplicam:**

- **RF-IA06:** agente por área, que responde só na sua área, redireciona perguntas de outras e gera planos editáveis.
- **RF-A05 e RF-A07:** metas por aba e registro manual de hábitos de estudo.
- **RN06:** o Agente de Estudos acessa o cansaço registrado em Saúde para ajustar o planejamento.
- **RN17:** toda informação técnica de estudos traz fonte clicável.
- **RF-IA07 e RF-IA08:** no máximo 3 sugestões por resumo; padrões descritos como associação, sem afirmar causalidade.
- **RF-IA10:** tom acolhedor e não culpabilizador.
- **RF-A14:** lembretes por aba, com horário e dias configuráveis, desativáveis e sem tom culpabilizador.
- **RF-IA03:** o portão de risco vale em todas as abas, inclusive Estudos.

## 2. Persona e anti-persona

**Persona principal: Larissa, 20 anos** ([Personas](../projeto/personas.md)). 3º semestre de Engenharia, mora em república, faz estágio de meio período e dorme pouco em época de prova. Quer organizar os estudos e manter a rotina até o fim do semestre. Abas principais: Estudos e Nutrição. O CULTIVA ajuda mostrando padrões (alimentação irregular e sessões de estudo menos produtivas) e preparando um plano de estudos simples para levar à tutoria.

**Anti-persona: Bruno, 22 anos** (proposta de 17/11/2026, a confirmar com a equipe).

| | |
|---|---|
| **Comportamento** | Pede ao app para escrever o TCC e resolver as listas de exercício. Na semana de provas, pede o nome e a dose de um remédio para "virar a noite estudando". |
| **Por que importa** | Define as duas recusas do agente: não fazer o trabalho acadêmico pelo aluno e não indicar remédio nem diagnosticar (seção 4). |
| **Resposta esperada** | Recusar sem julgamento e explicar o motivo. No trabalho, oferecer ajuda para planejar como fazer (etapas e prazos). No remédio, encaminhar a médico ou psicólogo. |

## 3. O que o agente faz

**Proposta de 17/11/2026 (MatheusSales2773), a confirmar com a equipe.**

O agente tem três papéis:

1. **Organizar a rotina de estudos.** Planeja a semana (sessões, pausas, prazos de prova), considerando o que o usuário registrou de estudo e, com consentimento, o cansaço e a alimentação das outras abas (RN06). O plano é uma sugestão editável (RF-IA06).
2. **Explicar técnicas de estudo, com fonte.** Por exemplo, revisão espaçada, autoavaliação (testar-se em vez de só reler), intercalar conteúdos e técnicas de foco e pausa. Toda explicação traz fonte clicável (RN17, RF-IA01); sem fonte aprovada, a resposta é "não sei".

3. **Criar flashcards e resumos a partir do material do próprio usuário.** O estudante cola um texto ou envia um PDF, e o agente gera flashcards (autoteste, uma das técnicas com mais evidência) e resumos **só com o que está nesse material**, sem acrescentar conteúdo de fora. Base: RF-IA14 (ler PDF enviado para montar resumo, com pelo menos 80% das saídas fiéis ao material). **Exceção ao RF-IA01** (proposta de 17/11/2026, a registrar no documento principal): aqui a fonte é o próprio material do estudante, citado por trecho, e não a lista de fontes aprovadas. O RF-IA01 continua valendo para as explicações de técnicas de estudo.

Inclui **procrastinação e gestão do tempo**, com estratégias organizacionais (quebrar tarefas, metas pequenas e progressivas, blocos de tempo), sempre sem tom de culpa (RF-IA10). Quando a procrastinação vem com sofrimento intenso, o agente não faz terapia: encaminha (seção 4).

**Fora do escopo:** ensinar o conteúdo das disciplinas (cálculo, anatomia etc.). O agente ajuda a organizar o estudo da matéria e transforma o material que o estudante já tem, mas não explica a matéria nem gera conteúdo novo sobre ela.

**Tarefas que a entrega de 20/11 vai demonstrar:**

| Tarefa | Exemplo | Requisitos |
|---|---|---|
| **Plano da semana** | A partir de uma semana de registros (sintéticos) da Larissa, com estudo, sono e cansaço e alimentação, propõe um plano simples para a semana seguinte, com até 3 sugestões, para ela levar à tutoria | RF-IA06, RF-IA07, RF-IA08, RN06 |
| **Dúvida no chat** | "Como revisar para a prova de cálculo em 5 dias?" Responde com técnicas de estudo e fonte, sem ensinar cálculo | RF-IA01, RN17 |

**Hipótese a testar:** planos simples, ligados à rotina real (cansaço, alimentação), ajudam a manter o estudo melhor que um planejador isolado. A existência da tarefa não demonstra esse benefício.

## 4. O que o agente não faz

**Proposta de 17/11/2026 (MatheusSales2773), a confirmar com a equipe.**

| Pedido | Resposta do agente | Base |
|---|---|---|
| **Fazer o trabalho ou a prova pelo aluno** ("escreve minha redação", "resolve essa lista") | Recusa sem julgamento, explica o motivo e oferece ajuda para **organizar** como fazer: dividir em etapas, prazos, blocos de estudo | **Regra nova necessária** (integridade acadêmica): não há regra equivalente na lista única. Proposta: incluir uma RN própria em [Regras de Negócio](../regras-de-negocio.md) |
| **Diagnóstico** ("acho que tenho TDAH", dislexia, ansiedade) | Não diagnostica. Explica por quê e sugere procurar psicólogo ou médico | RN01 (proíbe diagnóstico de saúde física ou mental), RF-IA02 |
| **Remédio para estudar** ("qual remédio tomar para focar?", dose de estimulante) | Nunca indica remédio nem dose. Explica por quê e sugere procurar médico | RF-IA02 (recusa prescrição de medicamentos); passa pelo guardrail de prescrição |
| **Ensinar o conteúdo da matéria** ("não entendi derivada") | Não explica a matéria; sugere levar a dúvida ao professor, à monitoria ou à tutoria e oferece organizar o estudo dela | Escopo (seção 3) |
| **Flashcards ou resumo sem material** ("faz flashcards de fotossíntese") | Pede o material do estudante (texto, anotações ou PDF); não gera o conteúdo a partir do próprio modelo | Escopo (seção 3) e RF-IA01: sem material nem fonte aprovada, o conteúdo não teria base |
| **Acrescentar ou corrigir o material** | Não acrescenta informação que não está no material e não "corrige" o conteúdo com conhecimento próprio; se algo parecer inconsistente, sugere conferir com o professor | RF-IA14 (fidelidade ao material) |
| **Resumo para entregar como trabalho** ("faz o resumo do capítulo pra eu entregar") | Trata como pedido de trabalho acadêmico: recusa e oferece ajuda para organizar como fazer | Integridade acadêmica (regra nova necessária) |
| **Sinal de risco** (sofrimento intenso, ideação suicida, autolesão) | O portão de risco interrompe o fluxo com a mensagem fixa de acolhimento e o CVV 188, antes de o agente responder | RF-IA03 |

**Encaminhamento:** dúvidas sobre a matéria vão para **professor, monitoria ou tutoria** da universidade, e o agente oferece organizar a dúvida e montar flashcards se o estudante enviar o material. Diagnóstico, remédio e sofrimento intenso vão para **psicólogo ou médico**. Sinais de risco seguem para o CVV pelo portão de risco, como em todas as abas.

## 5. Entradas

**Proposta de 17/11/2026 (MatheusSales2773), a confirmar com a equipe.**

**Registro na aba Estudos** (RF-A07), pensado para caber em 30 segundos (RNF01):

| Campo | Exemplo | Para que serve |
|---|---|---|
| **Tempo e matéria** | 50 min de Cálculo I | Base do plano e dos padrões |
| **Foco ou rendimento** | 3 de 5 | Padrões como "semanas sem almoço, foco menor" (RF-IA08) |
| **Provas e prazos** | Prova de Cálculo I em 25/11; entrega de relatório em 28/11 | O plano prioriza o que vence primeiro |

**Material de estudo do usuário** (para flashcards e resumos): **texto colado ou PDF** (proposta de 17/11/2026). Foto de caderno fica de fora por ora: exigiria reconhecimento de texto e é mais sujeita a erro. É **dado do usuário, não fonte do corpus**: não entra no corpus científico, no manifesto nem nos índices (separação entre corpus e dados pessoais), segue o consentimento (RF-A16), passa pela defesa contra prompt injection (RNF04) e vai ao modelo pelo provedor do ADR 0003 (Ollama local).

**Disponibilidade:** vem do **calendário geral do app** (seção 11), com aulas, estágio, treinos, provas e prazos. O agente usa os horários livres para montar o plano.

**O que o agente vê das outras abas** (RN06), só com consentimento do usuário (RF-A16) e só o necessário, pelo projetor de contexto da [arquitetura](../arquitetura.md):

| Dado | De qual aba | Para que serve | O que **não** vê |
|---|---|---|---|
| **Cansaço e sono** | Saúde | Não marcar sessão longa em dia de cansaço | Outros dados de saúde |
| **Se fez as refeições** | Nutrição | Padrão da Premissa 1 ("nas semanas em que você pulou o almoço, suas sessões de estudo foram mais curtas") | O que a pessoa comeu |
| **Horários de treino** | Saúde Física | Não marcar estudo em cima do treino | Tipo e carga do treino |

**Demonstração de 20/11:** uma semana fictícia da Larissa com esses campos, marcada como **dado sintético** e guardada fora do corpus científico, como pede a separação entre corpus e dados pessoais.

## 6. Saídas

**Proposta de 17/11/2026 (MatheusSales2773), a confirmar com a equipe.**

**Plano da semana:**

- **Grade por dia:** matéria, duração e pausa, priorizando as provas e entregas mais próximas e evitando os dias e horários de cansaço ou treino.
- **Até 3 sugestões** explicadas (RF-IA07), cada uma podendo ser aceita, ajustada ou ignorada.
- **Editável** pelo usuário (RF-IA06).
- **Fato x estimativa** (RF-IA05): cada informação marcada como "Registrado por você" (ex.: "você estudou 3 h de Cálculo") ou "Estimativa da IA" (ex.: "o foco pode estar associado aos dias sem almoço").
- **Linguagem de associação**, nunca de causa (RF-IA08), e tom sem culpa (RF-IA10).
- **Pronto para levar à tutoria**, como na persona; o relatório em PDF é o RF-A15.

**Flashcards e resumos:** cada flashcard e cada item do resumo indica de que parte do material veio (página do PDF ou trecho), para o estudante conferir. Ficam editáveis e só são salvos com confirmação (RF-A10).

**Dúvida no chat:** resposta curta com a técnica de estudo, um exemplo de como aplicar e a fonte clicável (RN17). Sem fonte aprovada, "não sei" (RF-IA01).

## 7. Fontes

**Proposta de 17/11/2026 (MatheusSales2773), a confirmar com a equipe. Responsável pelo corpus de Estudos: MatheusSales2773.**

- **Mesmo processo do corpus de Nutrição:** fonte catalogada no manifesto, com origem verificável, licença conferida no próprio documento, conversão rastreável, revisão e `approval_status`. Só fonte aprovada responde (RN16, RF-IA01).
- **Português e inglês**, como decidido para Nutrição; a resposta ao usuário continua em português (RNF23).
- **Começo pequeno:** 2 a 4 fontes abertas sobre técnicas de estudo, gestão do tempo e procrastinação.

**Candidatas** (a conferir; nenhuma está aprovada):

| Fonte | Tema | Situação |
|---|---|---|
| Weinstein, Madan e Sumeracki (2018), "Teaching the science of learning", *Cognitive Research: Principles and Implications* | As seis técnicas com mais evidência: revisão espaçada, autoteste, intercalar, elaborar, exemplos concretos e combinar palavra e imagem | Acesso aberto (CC BY 4.0 informado pela revista); licença a conferir no PDF |
| Alves, Soares e Jardim (2024) | Autoeficácia, gestão do tempo e procrastinação em 800 universitários brasileiros (citado no [Problema](../projeto/problema.md)) | Localizar, conferir acesso e licença |
| Artigos do SciELO sobre estratégias de aprendizagem e autorregulação no ensino superior | Evidência em português, com público brasileiro | Buscar |

*Pendente:* critérios de busca e seleção para Estudos. O protocolo da issue #47 foi escrito para Nutrição.

## 8. Colaboração com os outros agentes

**Proposta de 17/11/2026 (MatheusSales2773), a confirmar com a equipe.** Segue a [arquitetura proposta](../arquitetura.md): no **chat**, cada agente responde só na sua área e redireciona as outras (RF-IA06); a **integração entre áreas** acontece no **agente sincronizador**, nos resumos e planos (RF-IA09), e cada agente recebe só o contexto necessário.

**Onde roda a demonstração de 20/11** (proposta de 17/11/2026, MatheusSales2773, a confirmar com a equipe): no repositório **CultivaProjetoFase1**, em Python, onde já estão o RAG com fontes aprovadas, o portão de risco, a máscara de dados pessoais e o Ollama local (ADR 0003). A Agenda da demonstração é **sintética**, no mesmo formato das tarefas do [App](https://github.com/Cultiva-Challenge-2-Residencia-IA/App) (`LocalTask`: título, data, horário, categoria e concluída), para que a ligação futura com o App não exija conversão. Ligar o App a esses agentes, por API, fica para depois.

**Tarefa "plano da semana":**

```mermaid
sequenceDiagram
    actor U as Larissa
    participant R as Portão de risco
    participant S as Agente sincronizador
    participant A as Agenda
    participant N as Agente de Nutrição
    participant E as Agente de Estudos
    U->>R: Pede o plano da próxima semana
    R->>S: Sem sinal de risco
    S->>A: Lê só os horários ocupados, provas e prazos
    S->>N: Refeições da semana (só se fez ou pulou)
    N-->>S: Padrão observado, com fonte do corpus de Nutrição
    S->>E: Horários livres, provas, estudo, foco, cansaço e o padrão de Nutrição
    E-->>S: Blocos de estudo e sugestões, com fonte do corpus de Estudos
    S->>S: Concilia: no máximo 3 sugestões, fato x estimativa, sem causalidade
    S-->>U: Plano com blocos sugeridos
    U->>A: Aceita, ajusta ou ignora cada bloco; só os aceitos entram na Agenda
```

| Agente | Recebe | Entrega |
|---|---|---|
| **Portão de risco** (já existe) | A mensagem | Interrompe com acolhimento e CVV 188, se houver risco (RF-IA03) |
| **Agente sincronizador** (novo) | O pedido, os horários ocupados, provas e prazos da Agenda e as saídas dos dois agentes | Plano final com blocos sugeridos e até 3 sugestões (RF-IA07), fato x estimativa (RF-IA05), sem afirmar causalidade (RF-IA08) |
| **Agente de Nutrição** (já existe) | Só se as refeições foram feitas ou puladas | Padrão observado na semana, com fonte |
| **Agente de Estudos** (novo) | Horários livres, provas e prazos, registros de estudo, foco, cansaço e o padrão de Nutrição | Blocos de estudo (inclusive revisão com os flashcards do material do estudante, se houver) e sugestões, com fonte |

**A Agenda só muda com confirmação:** os blocos chegam como sugestões; cada um pode ser aceito, ajustado ou ignorado, e só os aceitos viram tarefas da Agenda (RF-IA07, seção 11).

**Dúvida no chat da aba Estudos:** portão de risco → Agente de Estudos (busca no corpus de Estudos e responde com fonte, ou "não sei"). Pergunta de outra área recebe a sugestão da aba certa.

**Flashcards e resumos:** portão de risco → Agente de Estudos, que gera a partir do material enviado e indica o trecho de origem; nada é salvo sem confirmação.

**Orquestração:** **LangGraph** (proposta de 17/11/2026, a confirmar com a equipe), que já aparece no diagrama da [arquitetura](../arquitetura.md), gera o grafo dos agentes automaticamente e se integra ao Langfuse (issue #46). *Pendente:* registrar a decisão num ADR no CultivaProjetoFase1.

## 9. Riscos

**Proposta de 17/11/2026 (MatheusSales2773), a confirmar com a equipe.** Complementa os [Riscos](../riscos.md) do projeto.

| Risco | Impacto | Mitigação |
|---|---|---|
| **Pressão e culpa com o plano:** plano apertado ou cobrança por não cumprir gera culpa e ansiedade, sobretudo em época de prova | Médio | Metas pequenas e progressivas, plano editável, tom sem culpa (RF-IA10), lembretes desativáveis (RF-A14) |
| **Ajudar a "colar":** o usuário contorna a recusa e o agente faz o trabalho acadêmico | Médio | Regra de integridade acadêmica e casos adversariais na avaliação |
| **Padrão falso entre áreas:** afirmar que pular o almoço "causa" foco menor com poucos dados | Alto | Só associação, volume mínimo de dados e grau de certeza (RF-IA08) |
| **Flashcard ou resumo infiel ao material:** o modelo inventa, distorce ou acrescenta conteúdo, e o estudante decora algo errado | Alto | Gerar só a partir do material, indicar o trecho de origem, permitir edição e medir a fidelidade (RF-IA14, mínimo de 80%) |
| **Instrução escondida no material:** um PDF ou texto colado traz instruções para o modelo | Médio | Tratar o material como dado, não como instrução (RNF04), como já é feito com os Trechos do corpus |
| **Privacidade entre abas:** o agente vê mais do que precisa das outras abas | Alto | Projetor de contexto, consentimento por dado (RF-A16) e logs que mostram o que cada agente recebeu (RF-IA09) |

## 10. Avaliação

**Proposta de 17/11/2026 (MatheusSales2773), a confirmar com a equipe.**

**Conjunto inicial para 20/11 (cerca de 15 casos):**

| Tipo | Casos | O que se confere |
|---|---:|---|
| Dúvida de técnica de estudo | 6 | Resposta com fonte aprovada, ou "não sei" sem fonte (RF-IA01, RN17) |
| Plano da semana | 3 | Até 3 sugestões, fato x estimativa, sem causalidade, respeita cansaço, treino e provas |
| Recusa | 3 | Trabalho acadêmico, diagnóstico e remédio recusados, com explicação e encaminhamento |
| Fora da área | 3 | Pergunta de Nutrição ou Saúde Física recebe a sugestão da aba certa (RF-IA06) |
| Flashcards e resumo de material | 3 | Todo flashcard e item do resumo está no material; nada acrescentado (RF-IA14); pedido sem material recebe pedido do material |

**Depois:** chegar aos 30 casos do RNF28, com casos escritos por quem não escreveu o agente, como no detector de risco.

## 11. Tela

A documentação não tem requisitos específicos da tela de Estudos: valem os requisitos gerais das telas de IA, todos **requisitos documentados, com aprovação ainda não confirmada**. Esta seção só aponta para eles.

**Registro de estudo:** registro manual com data e hora, visível em "Meu dia" (RF-A07); em até 30 s (RNF01) e com poucos cliques ou linguagem natural (RN08); por áudio, só salva depois da confirmação do usuário (RF-A09, RF-A10, RF-IA13); edição e exclusão com confirmação (RF-A11); metas de Estudos editáveis (RF-A05).

**Chat com o agente:** fonte clicável em toda resposta explicativa, ou "não sei" (RF-IA01, RN17); a IA se identifica e mostra o grau de certeza (RNF02); botão "resposta incorreta" (RF-IA15); pergunta de outra área recebe a sugestão da aba certa (RF-IA06); tom sem culpa (RF-IA10); aviso de profissional quando a sugestão muda muito a rotina (RN02); resposta em até 8 s no p95 (RNF06).

**Plano da semana e resumo:** até 3 sugestões, cada uma com aceitar, ajustar ou ignorar (RF-IA07); rótulos "Registrado por você" e "Estimativa da IA" (RF-IA05); plano editável (RF-IA06); resumo diário e semanal (RF-A13); relatório em PDF para levar à tutoria (RF-A15).

**Em toda tela:** aviso de limites (RF-A04); lembretes da aba, desativáveis e sem culpa (RF-A14); aba em "Meu dia" e desativável (RF-A12, RF-A06); consentimento por dado das outras abas (RF-A16); limite diário de interações (RN13); WCAG 2.1 AA e pt-BR (RNF11, RNF23).

### Calendário geral do app

**Já implementado no [repositório App](https://github.com/Cultiva-Challenge-2-Residencia-IA/App)** como a página **Agenda** (verificado em 17/11/2026): visão de semana e de dia, tarefas com data, horário e categoria (inclusive "Estudos") e marcação de concluída, com os dados guardados só no navegador (IndexedDB). **Ainda não está nos requisitos**: precisa entrar na lista única com número próprio. **Os agentes do App ainda não leem a Agenda**: hoje recebem só o check-in do dia.

O uso proposto (17/11/2026, MatheusSales2773, a confirmar com a equipe) é um calendário **único para todas as abas**, com aulas, estágio, provas e prazos de entrega, treinos e outros compromissos, por onde os agentes coordenam a rotina sem trocar mais dados do que o necessário:

| Uso | Exemplo |
|---|---|
| **Disponibilidade** | O Agente de Estudos usa os horários livres para montar a grade da semana |
| **Prazos** | Provas e entregas definem a prioridade do plano |
| **Interação entre agentes** | O plano de estudos não marca sessão em cima do treino; o agente sincronizador vê a semana inteira para conciliar as áreas (RF-IA09) |

**Regras propostas:**

- **Nada entra no calendário sem confirmação do usuário.** Os agentes **sugerem** blocos (por exemplo, "Cálculo, 50 min, quarta às 19 h"), e a pessoa aceita, ajusta ou ignora, como nas sugestões do RF-IA07 e nas confirmações do RF-A10.
- **Cada agente vê só o necessário.** O Agente de Estudos vê os horários ocupados e os eventos de estudo, não o conteúdo dos eventos de saúde (RF-IA09, RF-A16).
- **Eventos editáveis e apagáveis pelo usuário**, como os registros (RF-A11).

### O que falta para a tela

| Ponto | Situação |
|---|---|
| **Provas e prazos, grade da semana e nota de foco** | Só estão neste documento; não há requisito |
| **Temporizador de foco** (pomodoro) | Funcionalidade nova, não prevista (seção 12) |
| **Exemplos de meta de Estudos** | O RF-A05 só dá exemplos de Nutrição e Saúde Física |
| **Protótipo ou wireframe** | Não há tela desenhada de nenhuma aba |
| **Quando o aviso de profissional (RN02) aparece em Estudos** | A regra foi escrita pensando em saúde |

## 12. Perguntas em aberto

| Pergunta | Por que importa |
|---|---|
| **Regra de integridade acadêmica** precisa entrar na lista única de regras de negócio, com número próprio | Sem ela, a recusa não tem base documental |
| **ADR da orquestração com LangGraph** no CultivaProjetoFase1 | A escolha é proposta; a arquitetura ainda é provisória |
| **Critérios de busca e seleção de fontes de Estudos** | O protocolo da #47 cobre só Nutrição |
| **Calendário geral do app** precisa entrar nos [Requisitos](../requisitos/funcionais.md), com número próprio (seção 11) | A Agenda já existe no App, mas nenhum requisito a prevê; o plano e a disponibilidade dependem dela |
| **Os agentes do App passam a ler a Agenda?** | Hoje recebem só o check-in. Na demonstração de 20/11, os agentes rodam no CultivaProjetoFase1 com uma Agenda sintética no formato do App (seção 8); ligar o App a eles, por API, é o passo seguinte |
| **O que cada agente vê e pode escrever no calendário** | Ver só o necessário (RF-IA09) e nada entrar no calendário sem confirmação do usuário |
| **Ferramentas de foco** (por exemplo, um temporizador de pomodoro) não estão em nenhum requisito | O agente pode sugerir a técnica e o momento de usar; um temporizador no app seria funcionalidade nova, a registrar nos Requisitos |
| **Registrar no documento principal a exceção ao RF-IA01** para flashcards e resumos do material do usuário (seção 3) | Sem o registro, a função parece violar a regra de só responder com fontes aprovadas |
| **Por quanto tempo o material do estudante fica guardado** (RNF26) | Define o consentimento e o descarte; os formatos já estão definidos (texto colado e PDF) |
| **Validação das propostas desta página pela equipe** | Todas as seções estão como proposta de 17/11 |

**Divergências entre o App e a documentação** (verificadas em 17/11/2026 no [repositório App](https://github.com/Cultiva-Challenge-2-Residencia-IA/App), `src/lib/agentApi.ts` e `src/App.tsx`), para o grupo decidir qual desenho vale:

| No App | Na documentação e nesta página |
|---|---|
| O agente de estudos "ajuda a entender conteúdos" e gera flashcards de conteúdo a partir do modelo (ex.: "revisar fotossíntese"), sem material do usuário | O agente não ensina a matéria; gera flashcards e resumos só a partir do material enviado pelo estudante (seção 3) |
| Existe um agente de Saúde mental | Saúde mental está no backlog (RF-B01), fora do escopo atual |
| Os agentes enviam o check-in inteiro (humor, estresse, alimentação, nota livre) à Groq | ADR 0003 do CultivaProjetoFase1: Ollama local por padrão e nenhum dado real na Groq; RF-IA09: cada agente recebe só o necessário; RNF05: envio mínimo ao provedor |
| Os agentes respondem só com instruções ao modelo, sem corpus nem fontes | RF-IA01 e RN17: toda resposta explicativa traz fonte aprovada; o RAG com fontes está no repositório CultivaProjetoFase1 e ainda não está ligado ao App |
| **Profissionais de Estudos na vitrine** (RN09): professores e mentores não têm conselho de classe, mas a validação pede registro (RN14, RN15) | Sem critério, não há como validar esse cadastro |
