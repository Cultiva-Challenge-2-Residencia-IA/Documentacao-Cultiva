# Premissas

Cada premissa descreve um problema que o CULTIVA quer resolver, como resolver e como medir. Consideram o escopo atual: área do usuário com as abas Nutrição, Saúde Física e Estudos.

## 1. Informação dispersa em vários apps

- **Problema:** alimentação, atividade física e estudos ficam em apps separados, sem visão integrada.
- **Solução:** núcleo comum com a tela "Meu dia" e resumo semanal da IA mostrando relações entre as áreas.
- **Exemplo:** "Nas semanas em que você pulou o almoço, suas sessões de estudo foram 40% mais curtas."
- **Medição:** usuários ativos semanais e avaliação de utilidade do resumo.

## 2. Conteúdo sem fonte confiável

- **Problema:** excesso de informação contraditória nas redes dificulta decidir com segurança.
- **Solução:** a IA responde só com fontes aprovadas (Guia Alimentar do Ministério da Saúde, OMS), com resumo curto e "ver fonte". Sem fonte confiável, diz que não sabe.
- **Exemplo:** Rafael pergunta se jejum intermitente funciona e recebe resposta equilibrada, com a fonte.
- **Medição:** % de respostas com fonte e respostas sinalizadas como incorretas.

## 3. Decisões difíceis no dia a dia

- **Problema:** a pessoa decide mal em momentos de cansaço, fome ou falta de tempo.
- **Solução:** a IA prepara a decisão com 2 ou 3 opções simples e explicadas, sem decidir pela pessoa. Metas pequenas e progressivas.
- **Exemplo:** "Você tem 20 minutos hoje. Opções: caminhada de 20 minutos, treino em casa sem equipamento ou descanso ativo."
- **Medição:** decisões preparadas com apoio da IA; metas definidas e cumpridas.

## 4. Pedido de diagnóstico ou prescrição

- **Problema:** risco de a IA parecer diagnosticar ou prescrever.
- **Solução:** regras no prompt e filtros que bloqueiam dose, medicamento, dieta fechada e diagnóstico. A IA explica por que não pode e sugere o tipo de profissional.
- **Exemplo:** Eduardo pede protocolo para perder 10 kg em um mês e recebe recusa, explicação e encaminhamento.
- **Medição:** casos encaminhados e zero respostas prescritivas nos testes.

## 5. Sinal de risco fora da aba de Saúde Mental

- **Problema:** sinais de sofrimento aparecem em qualquer aba, mesmo com Saúde Mental no backlog.
- **Solução:** detecção nos registros e nas conversas. O fluxo normal é interrompido e o app mostra acolhimento e orientação de ajuda (CVV 188), sem aconselhamento clínico.
- **Exemplo:** Larissa escreve que não dorme há dias e "não aguenta mais".
- **Medição:** todos os cenários de teste de segurança tratados corretamente.

## 6. Medo de expor dados de saúde

- **Problema:** dados sensíveis expostos e falta de confiança no app.
- **Solução:** coleta mínima, consentimento claro e revogável, opções para ver e apagar os próprios dados. Nada é compartilhado sem autorização explícita.
- **Medição:** zero incidentes de privacidade e confiança declarada pelos usuários.
