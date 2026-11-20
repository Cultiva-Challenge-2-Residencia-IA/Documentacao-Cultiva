# Semana 3: LLM x RAG

Relatório da entrega de 20/11/2026: comparação entre a LLM sozinha e o RAG, régua de avaliação mais rigorosa e quatro formas de usar o RAG, com a escolha da configuração do produto. O código, os dados e o relatório gerado estão no [PR #57](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/57) do repositório CultivaProjetoFase1 (benchmark comparativo de respostas, de IngridHNobrega, com as correções da revisão). O documento técnico da entrega é o [`docs/entrega-semana-3-llm-x-rag.md`](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/docs/entrega-semana-3-llm-x-rag.md).

!!! abstract "Resultado em uma frase"
    Com o modelo local `gemma4:e4b` ([ADR 0004](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/docs/adrs/0004-modelo-local-ollama.md)), **a LLM escrevendo sobre os Trechos é melhor que a síntese extrativa sem LLM** (+0,09 na nota, diferença significativa). **RAG e LLM sem RAG empatam** na régua de termos. O RAG continua no produto porque só ele cita a fonte de cada frase (RN04).

## 1. O que foi pedido e onde está

| Exigência | Entregue | Onde |
|---|---|---|
| Comparar o uso de LLM x RAG | Mesmas 36 perguntas nas quatro condições, com teste pareado | Seções 3 e 5 |
| Melhorar as métricas | Régua com fatos essenciais, afirmações proibidas, segurança e fidelidade ao contexto; negação por frase; falhas de medição separadas; 16 casos do golden v2; intervalo de confiança e bootstrap pareado | Seção 4 |
| Testar formas diferentes de usar o RAG (com e sem LLM) | 4 condições: sem RAG, RAG sem LLM, RAG com LLM e contexto ideal | Seção 3 |
| Fazer 4 testes e escolher o melhor | Escolhido o RAG com LLM local, citação por frase e guardrails, com a extrativa como último recurso | Seção 6 |
| Relatório com testes, metodologia e links | Esta página e o PDF da entrega | Seção 9 |

## 2. Metodologia

### Perguntas

36 casos do split `dev`:

- **20 do gabarito de respostas** ([`eval/golden/resposta/dev.json`](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/eval/golden/resposta/dev.json)), escritos e revisados à mão. Cada um tem fatos essenciais com peso, afirmações proibidas com gravidade e o comportamento esperado: responder, redirecionar uma prescrição ao nutricionista, abster-se por falta de evidência ou recusar o que está fora do escopo.
- **16 do golden v2** ([`eval/golden/v2/`](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/tree/main/eval/golden/v2/)): as perguntas que devem ser respondidas e têm termos obrigatórios. Os Trechos julgados relevantes (nota ≥ 1) viram o contexto ideal, e a cobertura dos termos do v2 vira a completude. A pergunta repetida (V2-REC-01, igual à RESP-DIR-01) ficou de fora.

O split `test` do gabarito de respostas (6 casos) não foi usado: ele ainda não passou por uma segunda revisão e fica guardado como holdout.

### Ambiente

- Modelo `gemma4:e4b` no Ollama local, com as opções de produção do ADR 0004: `think` desligado, `num_ctx` 8192, `num_predict` 2048 e temperatura 0,1.
- GPU RTX 5060 de 8 GB. A rodada levou cerca de 7 minutos e não teve nenhuma falha de medição.
- Mesmos guardrails da Lei 8.234/1991 em todas as condições.

### Nota de cada resposta

A régua (`avaliar_execucao` em [`src/evaluation/benchmark_respostas.py`](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/src/evaluation/benchmark_respostas.py)) dá uma nota de 0 a 1 por resposta:

| Componente | Peso | Como é medido |
|---|---:|---|
| Correção factual | 0,35 | Desconta as afirmações proibidas (crítica zera, alta tira 0,5, outras 0,25) e cresce com a completude |
| Completude | 0,30 | Fatos essenciais presentes, ponderados pelo peso de cada um (60% das palavras do fato na resposta). No golden v2, cobertura dos termos obrigatórios |
| Relevância | 0,15 | Palavras da pergunta que aparecem na resposta |
| Segurança | 0,20 | Redirecionou a prescrição, absteve-se quando devia, não montou cardápio com quantidades |

Se a resposta comete qualquer erro (afirmação proibida ou falha de segurança), a nota fica limitada a 0,4. Fidelidade ao contexto e validade das citações são medidas à parte e não entram na nota, porque a condição sem RAG não tem contexto nem citações.

### Comparação estatística

- **Intervalo de confiança de 95% por condição**, pela distribuição t de Student sobre as 36 notas.
- **Bootstrap pareado da diferença entre duas condições** (10.000 reamostras, semente 55). As quatro condições respondem às mesmas perguntas, então a comparação certa é a diferença pergunta a pergunta. Se o intervalo da diferença contém o zero, é empate técnico. Comparar só a sobreposição dos intervalos de cada condição esconde diferenças reais.

## 3. Os quatro testes

| # | Condição | O que o modelo recebe | O que muda em relação ao produto |
|---|---|---|---|
| 1 | `llm_sem_rag` | Só a pergunta | Sem busca: mede o que o modelo sabe sozinho. Linha de base, não é modo do produto |
| 2 | `rag_extrativo` | Busca híbrida, sem LLM: a resposta copia frases dos Trechos | Sem LLM: é o último recurso do produto quando o Ollama não está disponível |
| 3 | `rag_atual` | O consultor completo: busca, TACO, grafo causal, citação por frase (#12) e guardrails | É o que o usuário recebe |
| 4 | `contexto_oracle` | Os Trechos certos do gabarito, sem busca | Busca perfeita: mostra o teto da escrita e separa erro de busca de erro de síntese |

**Por que muda:**

- Do 1 para o 3 entra a busca. A LLM passa a escrever a partir de Trechos aprovados e precisa citar cada frase; se uma citação falha, a resposta é bloqueada e vira a extrativa.
- Do 2 para o 3 entra a LLM. A extrativa só copia frases, então ela não junta informação de Trechos diferentes nem responde à pergunta com as próprias palavras.
- Do 3 para o 4 sai a busca. A diferença entre os dois é o quanto se perde por recuperar Trechos imperfeitos.

## 4. O que mudou na régua nesta semana

A versão inicial do benchmark tinha problemas que distorciam a comparação. Foram corrigidos no PR #57:

| Problema | Correção |
|---|---|
| Uma negação em qualquer lugar da resposta anulava uma afirmação proibida em outra frase | A negação só vale dentro da mesma frase da afirmação |
| Erro ou tempo esgotado do LLM entrava como resposta ruim e derrubava a nota da condição | As falhas de medição ficam fora da nota e aparecem à parte (zero nesta rodada) |
| As condições sem RAG e com contexto ideal chamavam o modelo com opções diferentes das do produto | Todas usam as opções do ADR 0004 |
| 20 casos e só intervalos por condição | 36 casos com o golden v2 e bootstrap pareado |
| Langfuse obrigatório e sem regra de destino | Opcional (`--use-langfuse`), com destino local por padrão, como no ADR 0003 |

## 5. Resultados

### Nota por condição

| Condição | Nota geral | IC 95% | Correção factual | Completude | Citações válidas |
|---|---:|---|---:|---:|---:|
| Contexto ideal (`contexto_oracle`) | 0,613 | [0,50; 0,73] | 61,4% | 51,0% | 100% |
| RAG atual (`rag_atual`) | 0,604 | [0,50; 0,71] | 62,5% | 42,8% | 16,7% |
| LLM sem RAG (`llm_sem_rag`) | 0,581 | [0,48; 0,68] | 56,0% | 41,6% | não se aplica |
| RAG extrativo (`rag_extrativo`) | 0,517 | [0,41; 0,62] | 50,2% | 31,8% | 0% |

No RAG atual, das 36 respostas, 29 foram do LLM com citações válidas, 2 foram "não sei" do próprio LLM, 1 virou extrativa depois de uma citação inválida e 4 foram respostas fixas (risco, prompt injection ou "não sei" por estar fora do domínio).

A coluna "citações válidas" do RAG atual **não mede o produto**. A checagem do benchmark procura o identificador do Trecho (por exemplo, `guia-alimentar-populacao-brasileira-2014-p048-01`) dentro do texto de cada citação, mas o consultor cita o documento e o rótulo `T#` com a página. Por isso, quase nenhuma citação do LLM é reconhecida. A conformidade das citações por frase é medida pelo verificador da #12 (seção 7). Corrigir essa checagem fica como pendência do benchmark.

### Teste pareado

| Comparação | Todos (36) | Golden v2 (16) | Perguntas a responder (25) |
|---|---|---|---|
| RAG atual − LLM sem RAG | +0,02 [−0,08; +0,12], empate | +0,05 [−0,10; +0,20], empate | +0,04 [−0,09; +0,16], empate |
| Contexto ideal − LLM sem RAG | +0,03 [−0,05; +0,12], empate | **+0,16 [+0,06; +0,27]** | +0,08 [−0,03; +0,19], empate |
| RAG atual − RAG extrativo | **+0,09 [+0,03; +0,15]** | **+0,07 [+0,01; +0,15]** | **+0,10 [+0,03; +0,18]** |

Em negrito, as diferenças em que o intervalo não contém o zero.

### Leitura

1. **A LLM sobre os Trechos é melhor que a extrativa.** É o único resultado firme em todos os recortes. Ele justifica a LLM no produto, com a extrativa só como último recurso.
2. **RAG e LLM sem RAG empatam.** Pela régua de termos, o `gemma4:e4b` responde boa parte destas perguntas com o próprio conhecimento.
3. **O contexto ideal ajuda no golden v2** (+0,16 sobre o LLM sem RAG). O RAG atual fica no meio: 0,84, contra 0,95 do contexto ideal. A distância até o teto é o que se perde na busca e na síntese.
4. **No gabarito escrito à mão, o contexto ideal não ganha nem do LLM sem RAG.** Ele recebe os Trechos certos, então isso aponta um limite da régua: uma resposta correta com outras palavras perde ponto.

## 6. Escolha para o produto

**Fica a configuração atual: RAG híbrido com a LLM local do ADR 0004, citação por frase com bloqueio (#12), guardrails da Lei 8.234/1991 e síntese extrativa como último recurso.**

- O ganho da LLM sobre a extrativa foi medido e é significativo.
- O RAG não ganhou do LLM sem RAG na nota, mas é o único que permite citar a fonte de cada frase, um requisito do produto (RN04, RF-IA01). Sem RAG, a resposta pode estar certa, mas ninguém consegue conferir de onde ela veio.
- A distância entre o RAG atual e o contexto ideal no golden v2 indica onde melhorar: a busca.

## 7. Testes da semana que sustentam a escolha

| Teste | Resultado | Registro |
|---|---|---|
| Escolha do modelo local: 5 modelos do Ollama com juiz às cegas (#55) | `gemma4:e4b` com 94,1% de fidelidade aos Trechos, contra 71,0% do `qwen2.5:7b`, e 3,2 s por resposta | [Escolha do modelo local](../qualidade/modelo-local.md), [PR #70](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/70) |
| Conformidade das citações por frase com o prompt atual | `gemma4:e4b` 88,0%, `qwen2.5:7b` 92,3% | [ADR 0004](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/docs/adrs/0004-modelo-local-ollama.md), [PR #80](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/80) |
| Limite de saída do modelo | Com `num_predict` 1024, o gemma truncava o JSON das citações; o produto passou a 2048 | [PR #80](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/80) |

## 8. Limitações

- **A régua é por termos.** Ela confere palavras, não entende a resposta. Isso explica o contexto ideal abaixo do LLM sem RAG no gabarito escrito à mão.
- **A régua não mede fundamentação.** O LLM sem RAG pode acertar sem ter de onde tirar a informação. A fidelidade do conteúdo do gemma com o prompt de citação por frase ainda está aberta (#67, fidelidade do gemma com citação por frase).
- **Amostra pequena:** 36 casos, 25 deles a responder. Diferenças menores que uns 10 pontos não se separam do ruído.
- **Temperatura 0,1:** duas execuções seguidas não são idênticas. Na mesma configuração, a nota do RAG atual nos 20 casos do gabarito variou de 0,433 para 0,418.
- **O `test` do gabarito de respostas** ainda não foi revisado nem rodado.

**Próximo passo para a régua:** um juiz LLM às cegas, como o da #55, que julgue se cada afirmação é correta frente aos Trechos de referência.

## 9. Links

- Repositório de código: [CultivaProjetoFase1](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1)
- [PR #57: benchmark comparativo LLM x RAG com teste pareado e gemma4:e4b](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/pull/57), com:
    - o benchmark em [`src/evaluation/benchmark_respostas.py`](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/src/evaluation/benchmark_respostas.py);
    - o gabarito em [`eval/golden/resposta/`](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/tree/main/eval/golden/resposta/);
    - o relatório gerado em [`eval/runs/respostas/relatorio_respostas_comparativo.md`](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/eval/runs/respostas/relatorio_respostas_comparativo.md);
    - o documento técnico em [`docs/entrega-semana-3-llm-x-rag.md`](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/docs/entrega-semana-3-llm-x-rag.md).
- [Golden v2](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/eval/golden/v2/README.md)
- [ADR 0004: modelo local do Ollama](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1/blob/main/docs/adrs/0004-modelo-local-ollama.md)
- Página da [escolha do modelo local](../qualidade/modelo-local.md)

### Como reproduzir

```bash
uv sync
# Sem LLM (determinístico; as condições com LLM viram respostas fixas)
uv run python -m src.evaluation.benchmark_respostas --split dev --no-llm
# Com o modelo local e os 16 casos do golden v2 (cerca de 7 min numa RTX 5060)
uv run python -m src.evaluation.benchmark_respostas --split dev --use-ollama --incluir-golden-v2
```
