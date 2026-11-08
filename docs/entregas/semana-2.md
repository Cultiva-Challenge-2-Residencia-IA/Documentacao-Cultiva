# Semana 2: RAG de Nutrição

Entrega de 09/11/2026. Código no [PR #30](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/30) e aprovação das fontes no [PR #31](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/31), do repositório CultivaProjetoFase1. O documento completo da entrega, com a tabela das 22 fontes e o log da demonstração, está em [`docs/entrega-rag-nutricao.md`](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/docs/entrega-rag-nutricao.md).

!!! info "Classificação"
    O que está aqui é **implementação** da aba Nutrição. As escolhas técnicas (ChromaDB, modelo de embeddings, pesos do reranker) são **propostas técnicas** ainda não validadas pela equipe nem calibradas no golden set. A visão geral está em [Arquitetura](../arquitetura.md).

## O que foi pedido e onde está

| Exigência | Entregue | Onde |
|---|---|---|
| Base curada com pelo menos 20 fontes | 21 fontes aprovadas no índice (de 22 catalogadas), 1818 Trechos | `corpus/manifest.yaml`, `corpus/nutricao/rag/` |
| Estratégia de chunking | Trechos de cerca de 1.000 caracteres (máximo 1.400), cortados em fronteira de frase, sem atravessar página nem seção, com cabeçalho contextual | `corpus/scripts/prepare_rag.py`, `src/rag/contrato.py` |
| Estratégia de embeddings | `paraphrase-multilingual-MiniLM-L12-v2`, 384 dimensões, local via `fastembed` (RNF05) | `src/retrieval/vector_store.py` |
| Banco vetorial | ChromaDB persistente, HNSW por cosseno, coleção versionada pela impressão digital do corpus e do modelo | `src/retrieval/vector_store.py` |
| Demonstração com fontes | 3 consultas com Trechos, página do PDF, resposta e citações | `src/demo_entrega.py`, `entrega_semanal/` |
| Diagramas de arquitetura e de ingestão | Diagramas em [Arquitetura](../arquitetura.md#o-que-ja-esta-implementado-nutricao-semana-2) | `docs/assets/arquitetura/` |

## Base de conhecimento

- **22 fontes**: 7 diretrizes e normas (Guia Alimentar, Fascículo 1 de protocolos, ABESO, SBAN, SBME, SVB e o Código de Ética do CFN), 4 revisões e 11 estudos publicados em periódicos brasileiros.
- **Aprovação**: 21 fontes estão `aprovado` (PR #31). A SBAN segue `pendente` por possível conflito de interesse e fica fora do índice. SVB e CFN foram aprovados com ressalva. Demonstração e benchmark usam só as fontes aprovadas.
- **Fora do índice nesta entrega**: as sínteses de `seed_guidelines.json` (sem origem verificável), a cópia do Guia em `data/raw` (o Guia entra pelo corpus, com página e hash) e os 31 resumos do PubMed, em inglês (issue #28).
- **Licenças**: não são critério de aprovação, pelo aceite de risco para projeto acadêmico sem fins lucrativos.

## Avaliação

Benchmark offline (`run_benchmark.py`), sem LLM, nas 16 perguntas atuais e só com as fontes aprovadas (medido em 08/11/2026):

| Métrica | Valor |
|---|---|
| Recall@4 por fonte | 91,7% (12 das 16 perguntas entram na média) |
| MRR | 0,750 |
| Cobertura de termos esperados | 88,1% |
| Acurácia do guardrail legal | 100% |

- O recall passou a ser medido por fonte, não por capítulo. Os números **não são comparáveis** aos da versão anterior (93,8% de recall com 47 fontes).
- No PR #30, o gate de regressão (RNF09, tolerância de 5 p.p.) apontou queda do MRR: 0,750 contra 0,9688 do baseline antigo. Com o merge, 0,750 virou o baseline do `main`. A queda indica que o reranker coloca a fonte certa abaixo de outras.
- O conjunto tem só 3 armadilhas de prescrição, então 100% no guardrail não demonstra robustez. O benchmark v2 é a issue #13.

## Issues

| Issue | Situação |
|---|---|
| #4 Integrar os JSONL do corpus | Fechada pelo PR #30 |
| #7 Filtrar por fonte aprovada | Fechada pelo PR #30 |
| #15 Embeddings e banco vetorial | Parcial: falta comparar modelos em português |
| #11 Rastreabilidade | Parcial: citações completas; falta registrar `corpus_version` em cada resposta (RNF08) |
| #13 Benchmark v2 | Parcial: ids mapeados para as fontes do corpus; o conjunto continua o mesmo |
| #28 PubMed e TACO no corpus | PubMed fora nesta entrega; o pipeline já aceita resumos |

## Limitações conhecidas

- O detector de risco com CVV 188 ainda não existe (issue #9).
- O reranker favorece Trechos em português e rebaixa a fonte certa em parte das perguntas (queda do MRR).
- A SBAN aguarda decisão sobre conflito de interesse (issue #8).
- O Código de Ética do CFN de 2018 pode ter sido substituído por resolução mais recente, ainda sem texto oficial localizado.
- Há defeitos de extração conhecidos em duas fontes (issues #26 e #27).
