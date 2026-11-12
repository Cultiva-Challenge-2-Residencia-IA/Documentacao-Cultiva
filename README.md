# CULTIVA: Documentação

> Empoderando pessoas com IA para compreender melhor, decidir melhor e viver melhor.

Documentação do projeto **CULTIVA** (Grupo 12), publicada com [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) no GitHub Pages.

**Site:** https://cultiva-challenge-2-residencia-ia.github.io/Documentacao-Cultiva/

## Sobre o projeto

O CULTIVA é um aplicativo que reúne Nutrição, Saúde Física e Estudos em um núcleo comum de registros, metas e resumos. Agentes de IA especializados por área esclarecem dúvidas sempre com fontes e apoiam o planejamento da rotina.

A IA oferece apoio educativo e organizacional. Não diagnostica, não prescreve e não substitui profissionais.

## Conteúdo

- **Projeto:** visão geral, problema e evidências, stakeholders, personas e premissas
- **Regras de negócio:** RN01 a RN18
- **Requisitos:** funcionais, aplicados à IA, não funcionais e backlog
- **Qualidade:** riscos e métricas de sucesso
- **Decisões:** guiding questions e pendências
- **Equipe**

## Rodando localmente

Requer Python 3.10 ou superior.

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve
```

O site fica disponível em http://127.0.0.1:8000. Para gerar a versão estática na pasta `site/`:

```bash
mkdocs build
```

## Estrutura

```
.
├── mkdocs.yml                 # configuração do site e da navegação
├── requirements.txt           # dependências Python
├── docs/
│   ├── index.md               # página inicial
│   ├── projeto/               # visão geral, problema, stakeholders, personas, premissas
│   ├── requisitos/            # funcionais, IA, não funcionais, backlog
│   ├── regras-de-negocio.md
│   ├── riscos.md
│   ├── metricas.md
│   ├── guiding-questions.md
│   ├── pendencias.md
│   ├── equipe.md
│   └── stylesheets/extra.css  # paleta e estilos
└── .github/workflows/docs.yml # deploy automático
```

## Publicação

A cada push na branch `main`, o workflow `.github/workflows/docs.yml` executa `mkdocs gh-deploy` e atualiza a branch `gh-pages`. Em **Settings → Pages**, a fonte deve estar configurada como a branch `gh-pages`.

## Como contribuir

1. Edite os arquivos Markdown em `docs/`.
2. Confira o resultado com `mkdocs serve`.
3. Use [Conventional Commits](https://www.conventionalcommits.org/pt-br/) nas mensagens (`docs:`, `feat:`, `fix:`, `chore:`).
4. Abra um pull request ou faça push na `main`, conforme o combinado com a equipe.
5. Antes de abrir o PR, rode `mkdocs build --strict`: ele falha se houver link ou âncora quebrados.

### Mantendo a documentação em dia com o código

O código fica no [CultivaProjetoFase1](https://github.com/Cultiva-Challenge-2-Residencia-IA/CultivaProjetoFase1). Quando um PR for mesclado lá:

- acrescente uma linha em `docs/historico.md`, com data, link do PR e o que mudou;
- se houver decisão (com data e responsável), acrescente-a em `docs/decisoes.md`, marcando se é decisão da equipe ou proposta técnica;
- se mudar algo que aparece aqui (métricas, número de fontes ou Trechos, componentes implementados), atualize `docs/arquitetura.md` e `docs/pendencias.md`.

As páginas de entrega (`docs/entregas/`) são o retrato de cada entrega e não são reescritas depois.

## Equipe (Grupo 12)

- Davi Vasconcelos de Araújo
- Felipe de Jesus Rodrigues
- Ingrid Hanna Nóbrega
- Matheus Sales Carvalho
- Ranni Heler Lopes

## Licença

Veja o arquivo [LICENSE](LICENSE).
