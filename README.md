# Documentação do portfólio — Do Código à Decisão

Este repositório reúne a documentação do portfólio desenvolvida com **MkDocs** e o tema **Material for MkDocs**.

## Conteúdo

A navegação configurada em `mkdocs.yml` contém:
- **Home:** `docs/index.md`;
- **Arquitetura:** `docs/arquitetura.md`.

## Executar localmente

**Pré-requisitos:** Python 3 e pip.

No terminal, na raiz do projeto:

```bash
python -m venv .venv
```

Ative o ambiente virtual:

- **Windows (PowerShell):** `.venv\Scripts\Activate.ps1`
- **Linux/macOS:** `source .venv/bin/activate`

Instale as dependências declaradas no projeto:

```bash
python -m pip install -r requirements.txt
```

Inicie o servidor local:

```bash
mkdocs serve
```

Abra o endereço informado pelo MkDocs no terminal para conferir a documentação.

## Publicação

O MkDocs possui suporte à publicação no GitHub Pages:

```bash
mkdocs gh-deploy
```

> **Atenção:** esse comando publica conteúdo. Verifique a configuração de GitHub Pages, a URL de produção e a branch de publicação antes de executá-lo. A edição deste README não executa a publicação.

## Arquivos importantes

- `mkdocs.yml`: tema, endereço e navegação da documentação;
- `docs/`: páginas em Markdown;
- `requirements.txt`: dependências do ambiente Python.

## Portfólio profissional

O projeto integra a documentação técnica do portfólio **Do Código à Decisão**, que reúne trabalhos em engenharia de software, arquitetura e dados.

Para conhecer outros projetos, consulte o [perfil no GitHub](https://github.com/Gabriel-S-Inacio).
