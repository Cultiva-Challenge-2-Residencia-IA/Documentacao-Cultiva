# Histórico de mudanças

O que mudou no repositório de código [CultivaProjetoFase1](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1) depois de cada entrega, do mais recente para o mais antigo. Cada linha aponta para o PR com os detalhes, os testes e as limitações.

## Depois da semana 2

### Em andamento

| PR | Assunto | Situação em 12/11/2026 |
|---|---|---|
| [#41](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/41) | Detector de risco com acolhimento fixo (CVV 188), defesa contra prompt injection e máscara de dados pessoais (issue #9, RF-IA03, RNF04, RNF05) | Mudanças solicitadas na revisão: num lote de frases escrito sem olhar as regras, o detector acionou em 20 de 30 casos de risco (recall 0,667, abaixo do mínimo de 0,95) |
| [#45](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/45) | Ollama local como provedor padrão de geração, com a Groq desativada por padrão (ADR 0003) | Aberto |

### Mesclados

| Data | PR | O que mudou |
|---|---|---|
| 12/11/2026 | [#43](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/43) | Corpus: o campo `secao` dos Trechos é normalizado, e títulos inválidos vindos da extração (cedilhas separadas, referências entre colchetes, frases promovidas a título) são descartados. |
| 10/11/2026 | [#44](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/44) | Avaliação: registra a decisão de não tratar o Fascículo 1 como equivalente ao Guia no benchmark v1. Fecha a issue #35. |
| 10/11/2026 | [#42](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/42) | Busca: ranking padrão passa a ser RRF puro sobre BM25 + ChromaDB, com ablação de 9 variantes nos benchmarks v1 e v2. MRR do v1 de 0,750 para 0,778; MRR por Trecho do v2 de 0,740 para 0,814. Resultados desfavoráveis registrados (casos que pioram e queda de 2 p.p. na cobertura de termos do v2). |
| 10/11/2026 | [#40](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/40) | Avaliação: benchmark v2 com 42 casos (`dev` e `test`), Trecho e página esperados, guardrail com recall de prescrição separado, grafo, TACO e abstenção. Ainda não é o gate do CI. |
| 10/11/2026 | [#38](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/38) | Corpus: itálico e negrito colados às palavras não juntam mais palavras nos Trechos ("Alimentosin naturaou" vira "Alimentos in natura ou"); nomes de arquivo e URLs mantêm o `_`. Fecha a issue #36. |
| 10/11/2026 | [#37](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/37) | Corpus: o CI passa a conferir os Trechos contra o manifesto e a origem (`geracao.json`); um `approval_status` alterado sem regenerar os Trechos faz o CI falhar. Fecha a issue #22. |
| 08/11/2026 | [#33](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/33) | Busca: volta ao HNSW do ChromaDB com `ef` em 200, e o CI constrói o índice antes de medir o determinismo do benchmark. |

## Semana 2 (09/11/2026)

RAG de Nutrição com corpus curado, embeddings locais, ChromaDB, busca híbrida, guardrails e citações. Veja [Entregas > Semana 2](entregas/semana-2.md).

## Como manter esta página

Quando um PR for mesclado no CultivaProjetoFase1, acrescente uma linha no topo de "Mesclados" com a data, o link e uma frase sobre o que mudou para quem usa ou avalia o sistema. Se o PR trouxer uma decisão, registre-a também em [Registro de decisões](decisoes.md). Se mudar um número citado na documentação (métricas, quantidade de fontes ou Trechos), atualize a página que o cita.
