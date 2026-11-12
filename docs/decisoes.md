# Registro de decisões

Decisões tomadas durante a implementação, com data, responsável e onde estão registradas em detalhe. O registro completo fica no repositório de código [CultivaProjetoFase1](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1); esta página reúne tudo num lugar só.

!!! info "Como ler a classificação"
    - **Decisão da equipe:** aprovada pelo grupo, com registro da aprovação.
    - **Proposta técnica:** escolha implementada e revisada num PR, mas ainda sem validação ampla da equipe ou sem evidência suficiente. Pode mudar com novos testes.
    - Uma decisão não comprova eficácia: os resultados medidos e as limitações estão nos documentos de cada linha.

## Corpus de Nutrição

| Data | Decisão | Classificação | Responsável | Registro |
|---|---|---|---|---|
| 06/11/2026 | **Licenças:** o repositório mantém PDFs, Markdown e Trechos de todas as fontes, inclusive com licença ausente ou ambígua, e a equipe assume o risco para uso acadêmico sem fins lucrativos. Reavaliar antes de qualquer uso comercial ou da vitrine paga (RN12). | Decisão da equipe | Felipe de Jesus Rodrigues, a pedido do grupo | [corpus/README.md, "Decisão sobre licenças"](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/corpus/README.md) |
| 06/11/2026 | **Aprovação de fontes:** status único `approval_status` (`pendente` ou `aprovado`) no manifesto; checklist mínima (origem verificável, vigente, sem conflito de interesse evidente, escopo adequado) e conferência de amostra de páginas. A licença não entra no gate. | Decisão da equipe | Grupo | [corpus/README.md, "Aprovação das fontes"](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/corpus/README.md) |
| 06/11/2026 | **Catálogo único:** o `corpus/manifest.yaml` substitui o `sources.yaml` previsto na arquitetura. | Decisão da equipe | Grupo | [corpus/README.md](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/corpus/README.md) |
| 08/11/2026 | **21 de 22 fontes aprovadas.** A SBAN (Água, Hidratação e Saúde) fica `pendente` por conflito de interesse evidente (material com marca da Nestlé, RN16). SVB e CFN aprovados com ressalva. | Decisão da equipe | Grupo | [PR #31](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/31), [revisão](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/corpus/nutricao/relatorios/revisao-aprovacao-corpus.md) |
| 10/11/2026 | **Trechos acompanham o manifesto:** ao mudar o manifesto (inclusive o `approval_status`), o `prepare_rag.py` ou o `rag.yaml`, os Trechos são regenerados no mesmo PR; o CI falha se ficarem para trás. | Proposta técnica | feliperodri0 | [PR #37](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/37) |

## Busca e avaliação

| Data | Decisão | Classificação | Responsável | Registro |
|---|---|---|---|---|
| 07/11/2026 | **Contrato entre corpus e retriever:** formato do Trecho validado por JSON Schema e conversão para o chunk do RAG. | Proposta técnica (ADR com status "Proposto") | Equipe | [ADR 0002](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/docs/adrs/0002-contrato-corpus-retriever.md) |
| 08/11/2026 | **HNSW mantido no ChromaDB**, com `ef_construction` e `ef_search` em 200, para a busca densa ficar determinística sem trocar por força bruta. | Decisão da equipe | feliperodri0 | [PR #33](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/33) |
| 10/11/2026 | **Ranking padrão: RRF puro sobre BM25 + ChromaDB.** O reranker por sobreposição de termos pesava cerca de 11 vezes a fusão e decidia o ranking sozinho; ele e a mistura com TF-IDF/LSA ficam desligados por padrão (configuráveis). MRR do benchmark v1: 0,750 → 0,778. O ganho é pequeno e foi medido em conjuntos pequenos: hipótese a confirmar. | Proposta técnica | MatheusSales2773; revisão de feliperodri0 | [PR #42](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/42), [ablação](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/eval/runs/ablacao_mrr_issue35.md) |
| 10/11/2026 | **Fascículo 1 não é equivalente ao Guia no benchmark v1.** A equivalência por conteúdo já é tratada no benchmark v2, que deve substituir o v1 como gate. | Decisão da equipe (grupo, sem objeções) | Proposta de MatheusSales2773 | [PR #44](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/44), [data/benchmark/README.md](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/data/benchmark/README.md) |
| 10/11/2026 | **Benchmark v2:** golden set com Trecho e página esperados, relevância julgada por pooling, `dev` para ajustar e `test` como holdout. O gate do CI continua no v1 até a troca ser feita. | Proposta técnica | feliperodri0 | [PR #40](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/40), [README do v2](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/eval/golden/v2/README.md) |

## Como acrescentar uma decisão

1. Registre a decisão primeiro no repositório de código, no documento do assunto (por exemplo, `corpus/README.md` ou um ADR em `docs/adrs/`), com data, responsável e motivo.
2. Acrescente uma linha na tabela certa desta página, com o link para esse registro.
3. Marque como **decisão da equipe** só o que teve aprovação do grupo registrada; o resto entra como **proposta técnica**.
