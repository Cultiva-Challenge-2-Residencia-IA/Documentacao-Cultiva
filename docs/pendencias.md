# Pendências e decisões em aberto

- [ ] Definir **X cliques** máximos por registro (RN08)
- [ ] Definir o **limite diário de interações** ou créditos com os agentes (RN13)
- [ ] Definir o **custo máximo por usuário ativo** antes do piloto (RNF07, RNF19)
- [ ] Escolher as **plataformas-alvo**: Android, iOS ou web responsiva (RNF24)
- [ ] Definir o **canal dos lembretes** (RF-A14)
- [ ] Definir **critérios de apresentação, ordenação e indicação** da vitrine
- [ ] Definir o **modelo de assinatura** dos profissionais (RN12)
- [ ] Confirmar o **escopo do registro por áudio** (RF-A09)
- [ ] **Calibrar** os valores marcados como "proposta" nos requisitos
- [ ] Registrar as **decisões das perguntas P1** das [Guiding Questions](guiding-questions.md)
- [ ] Confirmar que os **requisitos refatorados substituem** a lista original
- [ ] Uniformizar o texto da **RN03** entre os documentos

## RAG de Nutrição

Itens levantados na [entrega da semana 2](entregas/semana-2.md), atualizados em 12/11/2026. O que mudou desde então está no [Histórico](historico.md), e as decisões, no [Registro de decisões](decisoes.md).

- [x] Definir o **esquema do catálogo de fontes**: resolvido pelo `corpus/manifest.yaml` do CultivaProjetoFase1, que substitui o `sources.yaml` previsto
- [x] Escolher os **embeddings** iniciais: `paraphrase-multilingual-MiniLM-L12-v2`, local, sem envio de texto a terceiros (RNF05)
- [x] **Filtrar o índice por fonte aprovada**: só `approval_status: aprovado` entra por padrão (issue #7)
- [x] **Comparar modelos de embeddings** em português no golden set (issue #15): `multilingual-e5-large` escolhido ([PR #103](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/103), ADR 0006)
- [ ] Decidir o **banco vetorial definitivo**: ChromaDB na implementação, pgvector na proposta
- [x] **Aprovar as fontes**: 21 de 22 aprovadas no PR #31 (issue #8)
- [ ] Decidir sobre a **SBAN**, pendente por possível conflito de interesse (material com marca da Nestlé)
- [x] **Recuperar o MRR**: o reranker por sobreposição de termos decidia o ranking sozinho; com RRF puro, o MRR do v1 foi de 0,750 para 0,778 ([PR #42](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/42), issue #35). O ganho é pequeno e precisa ser confirmado num conjunto novo
- [ ] **Incluir os resumos do PubMed** (issue #28). O reranker que favorecia textos em português foi desligado no [PR #42](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/42), então resta decidir se entram no manifesto
- [ ] Decidir se as **sínteses de `seed_guidelines`** voltam ao índice: hoje ficam fora por não terem origem verificável
- [ ] **Detector de risco** com CVV 188 (issue #9, RF-IA03): o portão por léxico entrou no [PR #41](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/41), mas o recall em frases novas é 0,133 ([PR #49](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/49)), longe do mínimo de 0,95. A camada semântica é a [issue #48](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/issues/48). Até lá, nenhum material do grupo deve afirmar que o CULTIVA detecta risco de forma confiável
- [x] **Benchmark v2** com Trecho e página esperados e `dev`/`test` separados ([PR #40](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/40), issue #13)
- [ ] Trocar o **gate do CI do benchmark v1 para o v2**
- [ ] Aprovar a decisão do **provedor de LLM** (issue #16): Ollama local virou o padrão no [PR #45](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/45) (ADR 0003, proposta técnica); antes de usar a Groq com dados reais, falta confirmar contrato de não treinamento, retenção zero e transferência internacional
- [x] Aplicar a **escolha do modelo local** (issue #55): `gemma4:e4b` com `qwen2.5:7b` de reserva, no [PR #80](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/80) (ADR 0004, proposta técnica)
- [ ] Medir a **fidelidade do `gemma4:e4b` com o prompt atual** de citação por frase ([issue #67](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/issues/67)); até lá, só a forma das citações foi conferida ([detalhes](qualidade/modelo-local.md#conferencia-com-o-prompt-atual))
- [x] Responder **"não sei"** sem recusar perguntas que o corpus responde (issue #6, [PR #51](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/51))
- [ ] Definir os **critérios de busca e seleção de novas fontes** para o corpus (issue #47)
- [ ] Revisar os **22 julgamentos de Trecho** acrescentados ao golden set v2 no [PR #42](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/42), ainda sem revisão humana

## Sistema multiagentes e contexto

- [ ] Aprovar em grupo o **ADR 0005** (arquitetura multiagentes), revisado em 25/11 com o projetor de contexto ([PR #113](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/113))
- [ ] Implementar o **projetor de contexto e os Fatos do Usuário** ([issue #112](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/issues/112)), com critérios de avaliação escritos antes de medir
- [ ] Revisar com a pessoa encarregada de proteção de dados a seção do **RIPD** sobre os Fatos do Usuário, que inclui condição de saúde (dado sensível), antes de qualquer uso com pessoas reais
- [ ] Calibrar os valores marcados como proposta: **expiração dos fatos** (90 dias) e **orçamento do Histórico** (2.500 tokens, até 20 mensagens)

## Entrega multimodal (30/11/2026)

Itens levantados na [entrega multimodal](entregas/multimodal.md) ([PR #101](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/101), [PR #102](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/102) e [PR #122](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/122)).

- [x] **Saída da foto de prato do escopo atual e passagem para o [Backlog](requisitos/backlog.md)** (`RF-B04`, decisão confirmada em 27/11/2026 a partir da proposta de 24/11/2026): **RF-A08** (no que se refere a foto de refeição), **RF-IA12** (parte de refeição; foto de atividade segue fora desta entrega) e **RNF13** ficam fora do escopo atual, mantendo-se no escopo apenas foto de rótulo nutricional e foto de documento impresso (registrado em [Registro de decisões](decisoes.md))
- [ ] Definir escopo e prazo para o **áudio** (**RF-IA13** e **RNF14**, além do **RF-A09** listado acima): **não coberto** na entrega multimodal de 30/11/2026 por falta de tempo para registrar critérios e medir WER por sotaque antes do prazo
- [ ] Confirmar em grupo a regra proposta no PDF (#95) de **atribuir a orientação do profissional sem reescrevê-la**
- [ ] Reavaliar **fidelidade e cobertura** após as correções de revisão dos PRs #101 e #102 (checagem de unidade junto com o número e portões na pergunta sobre PDF/foto): zero número alterado continua valendo, mas fidelidade e cobertura podem ter mudado e não foram medidas de novo
- [ ] Medir **fotos reais de embalagens** (além das sintéticas) e melhorar a **fidelidade da explicação do rótulo com o corpus**, que ficou em 78,6% (11/14 frases), abaixo da meta de 80%
