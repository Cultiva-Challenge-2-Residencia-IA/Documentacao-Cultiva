# Histórico de mudanças

O que mudou no repositório de código [CultivaProjetoFase1](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1) depois de cada entrega, do mais recente para o mais antigo. Cada linha aponta para o PR com os detalhes, os testes e as limitações.

## Depois da semana 2

### Em andamento

| PR | Assunto | Situação em 12/11/2026 |
|---|---|---|
| [#51](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/51) | Resposta "não sei" quando o corpus não tem evidência (issue #6, RF-IA01) | Mudanças solicitadas: recusa perguntas que o corpus responde, como "Jejum intermitente funciona?" (exemplo da persona Rafael), porque o sinal olha só o cosseno do ChromaDB |

### Mesclados

| Data | PR | O que mudou |
|---|---|---|
| 12/11/2026 | [#45](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/45) | LLM: Ollama local passa a ser o provedor padrão; a Groq só é usada com `LLM_PROVIDER=groq`, `ALLOW_EXTERNAL_LLM=true` e chave (ADR 0003). Só a pergunta do usuário é mascarada antes de ir ao modelo; Trechos, TACO e grafo seguem intactos. |
| 12/11/2026 | [#49](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/49) | Avaliação: um lote de frases de risco escrito às cegas vira o holdout do detector. Recall de **0,133** (4 de 30), sem falsos positivos: o RF-IA03 não está cumprido. O gate do holdout aparece como falha conhecida (aviso com o número real) e volta a falhar se cair abaixo de 0,1333. |
| 12/11/2026 | [#41](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/41) | Segurança: portão de risco por léxico com mensagem fixa de acolhimento (CVV 188, SAMU 192), defesa contra prompt injection e máscara de dados pessoais (issue #9). O léxico acerta as frases que orientaram as regras, mas generaliza pouco para frases novas (ver #49); a camada semântica é a issue #48. |
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
