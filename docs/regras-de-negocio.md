# Regras de negócio

O que o sistema deve respeitar em **qualquer** funcionalidade.

## 1. Limites de atuação da IA (safety e guardrails)

| ID | Regra |
|---|---|
| **RN01** | **Bloqueio de prescrição.** A IA é proibida de prescrever dietas fechadas (quantidades exatas e horários imutáveis), fichas de treino prescritivas ou realizar diagnósticos de saúde (física ou mental) |
| **RN02** | **Alerta de orientação profissional.** Toda resposta que envolva sugestões de saúde, nutrição ou mudança drástica de rotina traz aviso padrão orientando consulta a profissional qualificado |
| **RN03** | **Redirecionamento para a vitrine.** Pergunta que exige avaliação individualizada (ex.: "Sinto dor no joelho ao correr, o que fazer?") recebe explicação de que a IA não diagnostica e sugestão de buscar um profissional |

## 2. Qualidade da informação e transparência

| ID | Regra |
|---|---|
| **RN04** | **Citação de fontes.** Os agentes devem citar a fonte (artigo, diretriz, livro ou portal reconhecido) da informação usada |
| **RN05** | **Tratamento de fake news.** Dietas da moda extremas ou informações sem validade científica são desmistificadas com base em consenso, em tom educativo e não punitivo |

## 3. Registros e organização da rotina (core)

| ID | Regra |
|---|---|
| **RN06** | **Núcleo de dados integrado.** Os registros alimentam uma base única. Ex.: o Agente de Estudos acessa o cansaço reportado em Saúde para ajustar o planejamento |
| **RN07** | **Resumo periódico.** Resumo automático (semanal ou quinzenal) correlacionando os três pilares |
| **RN08** | **Simplificação de input.** O registro diário não pode exigir mais de **X** cliques, ou deve aceitar linguagem natural (áudio ou texto via chat) |

## 4. Vitrine e gestão de profissionais

| ID | Regra |
|---|---|
| **RN09** | **Perfis de acesso.** Ao menos dois perfis: Usuário Final e Profissional (nutricionistas, educadores físicos, professores e mentores) |
| **RN10** | **Visibilidade na vitrine.** O profissional precisa ter dados mínimos preenchidos e validados (critérios a definir) |

## 5. Modelo de negócio e assinaturas

| ID | Regra |
|---|---|
| **RN11** | **Gratuidade para o usuário final.** Registro, acompanhamento e interação com os agentes são 100% gratuitos |
| **RN12** | **Vitrine paga (B2B).** O profissional precisa de assinatura ativa para aparecer. Se expirar, o perfil é ocultado automaticamente das buscas e sugestões |
| **RN13** | **Limite de uso de IA.** Máximo de **X** interações diárias com os agentes, ou sistema de créditos diários, para controlar custo até que os profissionais pagantes sustentem a operação |

## 6. Validação e segurança de profissionais

| ID | Regra |
|---|---|
| **RN14** | **Triagem obrigatória.** Ninguém fica visível logo após o cadastro. O perfil fica "Em Análise" até validar o registro profissional ativo (CRN, CREF etc.) |
| **RN15** | **Transparência de credenciais.** O perfil na vitrine exibe obrigatoriamente o número de registro de classe |

## 7. Curadoria e base de conhecimento da IA

| ID | Regra |
|---|---|
| **RN16** | **Restrição de fontes (whitelist).** Sem buscas livres na web. Respostas técnicas só a partir de bases pré-aprovadas (SciELO, PubMed, portais do Ministério da Saúde) |
| **RN17** | **Assinatura da fonte.** Toda informação técnica de saúde ou estudos gera na interface um link ou referência clicável para a fonte usada |

## 8. Mecanismo de indicação (matchmaking)

| ID | Regra |
|---|---|
| **RN18** | **Recomendação contextual.** Ao identificar demanda crônica no resumo periódico (RN07) ou no chat (ex.: insônia constante, estagnação no treino), a IA aciona um "Card de Indicação" com **3 profissionais** da vitrine da especialidade |

!!! note "Divergência entre documentos"
    Na RN03, o documento principal cita a vitrine do aplicativo, enquanto o arquivo de regras fala apenas em buscar um profissional. A equipe precisa uniformizar o texto.
