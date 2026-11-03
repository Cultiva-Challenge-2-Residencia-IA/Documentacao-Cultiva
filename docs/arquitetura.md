# Arquitetura de IA

!!! warning "Versão provisória"
    Esta arquitetura é uma **proposta inicial**, ainda não validada pela equipe. Ela reúne as decisões discutidas até agora (RAG, multiagentes, multimodal, guardrails, LLMOps e observabilidade) e deve mudar conforme os testes, o golden set e as escolhas de plataforma e provedor. Itens marcados como "a definir" nas [Pendências](pendencias.md) continuam em aberto.

## Fluxo de uma mensagem

O diagrama mostra o caminho de uma mensagem do usuário, da entrada até a resposta com fontes, e as camadas transversais de conhecimento (RAG), dados e observabilidade.

[![Arquitetura de IA do CULTIVA: fluxo de uma mensagem](assets/arquitetura/arquitetura-fluxo.png)](assets/arquitetura/arquitetura-fluxo.png){ target=_blank }

[Abrir a imagem em tamanho original](assets/arquitetura/arquitetura-fluxo.png){ target=_blank }

### Principais decisões desta proposta

- **Chat por aba, grafo único.** O usuário conversa dentro de Nutrição, Saúde Física ou Estudos. Uma pergunta de outra área recebe uma mensagem padrão que sugere a aba certa, sem repassar o conteúdo a outro agente (RF-IA06).
- **Risco antes de tudo.** O detector de risco roda em paralelo ao pré-processamento e tem prioridade sobre qualquer outro fluxo. O acolhimento com CVV 188 é uma mensagem fixa, não gerada por IA (RF-IA03, RNF29).
- **Confirmação obrigatória.** Foto, áudio e PDF viram uma proposta de registro e só entram no histórico após confirmação do usuário (RF-A10).
- **Contexto mínimo entre agentes.** Um projetor de contexto entrega a cada agente apenas o que ele precisa. O agente sincronizador só atua nos resumos (RF-IA09).
- **RAG fechado.** Respostas técnicas vêm só de fontes da whitelist, com citação por trecho. Sem evidência, a resposta é "não sei" (RN16, RN17, RF-IA01).
- **Guardrails de saída.** Schema com fato x estimativa, bloqueio de prescrição e diagnóstico, checagem de fundamentação e aviso de profissional inserido por código (RN01, RN02, RF-IA05).
- **Rastreabilidade.** Cada resposta registra versão do prompt, do modelo, das fontes e do corpus (RNF08).

## Qualidade contínua (LLMOps)

O segundo diagrama descreve o ciclo de avaliação: pull request, execução do golden set no CI, gates de qualidade e realimentação com casos vindos da produção.

[![Qualidade contínua do CULTIVA: golden dataset, CI/CD e observabilidade](assets/arquitetura/qualidade-llmops.png)](assets/arquitetura/qualidade-llmops.png){ target=_blank }

[Abrir a imagem em tamanho original](assets/arquitetura/qualidade-llmops.png){ target=_blank }

### Principais decisões desta proposta

- **Avaliação determinística.** A comparação com o golden set usa métricas fixas (como ROUGE e checagens de regra), sem juiz LLM.
- **Gates no CI.** O merge é bloqueado se o recall de risco ficar abaixo de 0,95, se houver resposta prescritiva, se faltar fonte nas respostas explicativas, se houver regressão acima de 5 p.p. ou se a latência sair do p95 (RNF06, RNF09, RNF29).
- **Golden dataset versionado no Git.** Cobre as abas (mínimo de 30 casos por aba), perfis e regionalismos, risco por modalidade, casos adversariais e pedidos fora de escopo (RNF28).
- **Observabilidade com Langfuse.** Traces por nó, scores, alertas e revisão humana semanal. Casos revisados voltam ao golden set.

!!! note "Limitações conhecidas"
    - ROUGE mede sobreposição de palavras com uma resposta de referência. Ele não detecta, sozinho, afirmação sem sustentação na fonte nem prescrição disfarçada. Esses pontos dependem das checagens de regra descritas nos gates.
    - Na produção não há resposta de referência, então ali valem regras fixas e a revisão humana.
    - A avaliação de tom (RF-IA10) segue dependendo de rubrica com revisores.

## Pendências desta arquitetura

- Escolha dos provedores de modelo e de embeddings, respeitando o RNF05 (sem uso dos dados para treino).
- Definição do esquema do `sources.yaml`, dos critérios de confiabilidade das fontes e da rotina de reindexação.
- Decisão sobre usar ou não grafo de conhecimento e análise causal (hoje fora do MVP).
- Valores de limite diário de interações (RN13) e de custo por usuário (RNF07).
- Plataformas-alvo (RNF24) e canal dos lembretes.
