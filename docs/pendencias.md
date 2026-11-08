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

Itens levantados na [entrega da semana 2](entregas/semana-2.md).

- [x] Definir o **esquema do catálogo de fontes**: resolvido pelo `corpus/manifest.yaml` do CultivaProjetoFase1, que substitui o `sources.yaml` previsto
- [x] Escolher os **embeddings** iniciais: `paraphrase-multilingual-MiniLM-L12-v2`, local, sem envio de texto a terceiros (RNF05)
- [x] **Filtrar o índice por fonte aprovada**: só `approval_status: aprovado` entra por padrão (issue #7)
- [ ] **Comparar modelos de embeddings** em português no golden set (issue #15)
- [ ] Decidir o **banco vetorial definitivo**: ChromaDB na implementação, pgvector na proposta
- [x] **Aprovar as fontes**: 21 de 22 aprovadas no PR #31 (issue #8)
- [ ] Decidir sobre a **SBAN**, pendente por possível conflito de interesse (material com marca da Nestlé)
- [ ] **Recuperar o MRR**: caiu de 0,9688 para 0,750 com o corpus curado; calibrar o reranker (issue #13)
- [ ] **Incluir os resumos do PubMed** sem que o reranker penalize textos em inglês (issue #28)
- [ ] Decidir se as **sínteses de `seed_guidelines`** voltam ao índice: hoje ficam fora por não terem origem verificável
- [ ] Implementar o **detector de risco** com CVV 188 (issue #9, RF-IA03)
