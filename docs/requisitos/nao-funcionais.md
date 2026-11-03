# Requisitos não funcionais

| ID | Categoria | Requisito | Prioridade | Métrica |
|---|---|---|---|---|
| RNF01 | Usabilidade | Registro rápido | Essencial | Até 30 s por registro |
| RNF02 | Transparência | A IA se identifica como IA e mostra fonte e grau de certeza | Essencial | 100% das respostas explicativas |
| RNF03 | Justiça | Desempenho equivalente entre perfis (vegetariano, restrição alimentar, baixa renda, treino sem equipamento, estudante que trabalha) | Essencial | Diferença ≤ 5 p.p. na rubrica |
| RNF04 | Segurança do LLM | Resistir a prompt injection (inclusive em PDFs e fotos); não vazar o prompt nem dados de outros usuários | Essencial | Zero vazamentos no conjunto adversarial |
| RNF05 | Privacidade | Enviar ao provedor só o mínimo, sem nome nem contato, com contrato que proíba treino; logs sem dados de saúde em texto claro | Essencial | Conferido nos logs e no contrato |
| RNF06 | Desempenho | Tempo de resposta da IA | Importante | p95 ≤ 8 s |
| RNF07 | Custo | Custo da IA por usuário ativo | Importante | ≤ R$ X/mês (definir antes do piloto) |
| RNF08 | Rastreabilidade | Registrar versão do prompt, do modelo e das fontes em cada resposta | Essencial | 100% das respostas |
| RNF09 | Estabilidade | Versão do modelo fixada; troca só após rodar o golden set sem piora | Importante | Nenhuma regressão acima de 5 p.p. |
| RNF10 | Monitoramento | Acompanhar respostas sinalizadas como incorretas | Importante | Revisão semanal; alta acima de 5 p.p. dispara revisão |
| RNF11 | Acessibilidade | Contraste, tamanho de fonte e leitor de tela | Importante | WCAG 2.1 nível AA |
| RNF12 | Conformidade | LGPD: consentimento específico para dados sensíveis, RIPD e encarregado (DPO) | Essencial | Base legal, finalidade, RIPD e DPO documentados |
| RNF13 | Justiça | Reconhecer pratos brasileiros e regionais | Importante | Diferença ≤ 5 p.p. entre regionais e comuns |
| RNF14 | Justiça | Entender regionalismos e sotaques no áudio | Importante | WER ≤ 15% em todos os sotaques do conjunto de teste |
| RNF15 | Privacidade | Remover metadados das fotos antes do envio | Essencial | 100% das imagens sem metadados |
| RNF16 | Privacidade | Desfocar ou recusar rostos e documentos nas fotos | Essencial | Zero rostos ou documentos legíveis enviados |
| RNF17 | Desempenho | Tempo de processamento de foto | Importante | p95 ≤ 10 s |
| RNF18 | Robustez | Funcionar com fotos escuras, tremidas ou de celular simples | Importante | Queda ≤ 10 p.p. vs. boa qualidade |
| RNF19 | Custo | Custo de imagem por usuário ativo | Importante | Somado ao limite do RNF07 |
| RNF20 | Segurança | Dados protegidos em trânsito e em repouso; senhas com hash seguro | Essencial | TLS 1.2+; criptografia em repouso; OWASP sem falhas críticas ou altas |
| RNF21 | Segurança | Isolar dados entre usuários com controle de acesso | Essencial | Zero falhas nos testes de autorização |
| RNF22 | Disponibilidade | Serviço disponível e com backup | Importante | ≥ 99% mensal e backup diário (propostas) |
| RNF23 | Localização | Interface e respostas da IA em pt-BR | Essencial | 100% dos textos em pt-BR |
| RNF24 | Compatibilidade | Plataformas-alvo a definir (Android, iOS ou web responsiva) | Essencial (pendente) | Funciona nas 2 versões mais recentes de cada plataforma |
| RNF25 | Conformidade | Registrar cada consentimento com data, hora e versão do termo | Essencial | 100% auditáveis |
| RNF26 | Privacidade | Descartar foto e áudio originais após o processamento, salvo escolha do usuário | Importante | Descarte em até 24 h (proposta) |
| RNF27 | Segurança do LLM | Fundamentar respostas nas fontes citadas | Essencial | ≥ 95% das afirmações sustentadas, em amostra humana |
| RNF28 | Qualidade | Golden set versionado cobrindo abas, perfis do RNF03 e regionalismos | Importante | Mínimo de 30 casos por aba (proposta) |
| RNF29 | Desempenho | Resposta rápida do fluxo de risco | Essencial | p95 ≤ 3 s |
| RNF30 | Usabilidade | Onboarding simples | Importante | Primeiro registro em até 2 min, sem ajuda (proposta) |
