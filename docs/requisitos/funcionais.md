# Requisitos funcionais: software convencional

| ID | Requisito | Prioridade | Critério de aceite |
|---|---|---|---|
| RF-A01 | Cadastrar conta com e-mail e senha, declarando ter 18 anos ou mais | Essencial | Conta criada só com e-mail válido e senha dentro da política; e-mail de verificação enviado; cadastro bloqueado sem a declaração de idade |
| RF-A02 | Entrar com e-mail e senha (ou login social) | Essencial (social: Desejável) | Login válido abre a sessão; erro mostra mensagem genérica; bloqueio temporário após 5 tentativas falhas (proposta) |
| RF-A03 | Recuperar senha por e-mail | Essencial | Link expira em até 60 min (proposta) e só pode ser usado uma vez |
| RF-A04 | Exibir aviso de limites e termos de uso | Essencial | Aceite obrigatório no onboarding; aviso visível nas telas de IA, relatórios e vitrine |
| RF-A05 | Definir perfil e metas iniciais por aba (vegetariano, restrição alimentar, treino sem equipamento etc.) | Essencial | Ao menos uma meta por aba ativa; metas e preferências editáveis depois |
| RF-A06 | Ativar e desativar abas | Importante | Aba desativada não aparece em "Meu dia" nem é usada pelos agentes |
| RF-A07 | Registrar hábitos manualmente em Nutrição, Saúde Física e Estudos | Essencial | Registro salvo com data e hora e visível em "Meu dia" |
| RF-A08 | Registrar por foto (câmera ou galeria) | Importante | A foto gera uma interpretação que vai para a confirmação (RF-A10), sem salvar direto |
| RF-A09 | Registrar por áudio | Importante (confirmar escopo) | Áudio é transcrito e o texto vai para a confirmação (RF-A10) |
| RF-A10 | Mostrar o que a IA entendeu (foto, áudio ou PDF) antes de salvar, com opção de corrigir ou descartar | Essencial | **Nenhum registro vindo de foto, áudio ou PDF é salvo sem confirmação explícita** |
| RF-A11 | Editar e apagar registros | Essencial | Alteração aparece em "Meu dia", resumos e relatórios; exclusão pede confirmação |
| RF-A12 | Tela "Meu dia" com as três abas e o progresso das metas | Essencial | Registros do dia juntos, por aba; estado vazio quando não há registros |
| RF-A13 | Resumo diário e semanal unificado (registrar, resumir, recomendar) | Essencial | Gerado sob demanda ou automaticamente toda semana; segue RF-IA05 |
| RF-A14 | Configurar lembretes por aba (horário, dias, ativar e desativar) | Importante | Notificação no horário, tolerância de 1 min (proposta); mensagens sem tom culpabilizador |
| RF-A15 | Gerar relatório por período em PDF | Importante | Usuário escolhe período e abas; PDF traz registros, metas e resumos, identifica estimativas da IA e inclui o aviso de limites |
| RF-A16 | Dar e revogar consentimento de forma granular (dados de saúde, uso de IA, fotos e áudios) | Essencial | Cada consentimento é independente; revogar interrompe o tratamento em até 24 h (proposta) |
| RF-A17 | Apagar conta e todos os dados pessoais | Essencial | Após confirmação, dados removidos do sistema e dos provedores em até 15 dias (proposta) |
| RF-A18 | Exportar os próprios dados em formato aberto | Importante | CSV ou JSON com todos os registros em até 15 dias (proposta) |
| RF-A19 | Cadastrar profissional na vitrine | Desejável | Exige registro profissional (CRN, CREF) e validação manual antes da publicação; critérios de apresentação a definir |
| RF-A20 | Consultar a vitrine de profissionais | Desejável | Lista filtrável por área; aviso de que o CULTIVA não avalia nem indica clinicamente; ordenação documentada, **sem posicionamento pago** |
