# Rodrigo Trombeta Portfolio

Este repositório hospeda o código do portfólio profissional de Rodrigo Trombeta. A fonte primária para o comportamento atual é o código do repositório; as informações profissionais são declarações publicadas e não foram verificadas independentemente por esta documentação.

Portfolio online: https://rftrombeta.github.io/

---

## Rodar localmente (Jekyll)

1) Instale Ruby e Bundler
2) Na raiz do projeto, rode:

```bash
bundle install
bundle exec jekyll serve
```

3) Abra no navegador:

```
http://localhost:4000
```

---

## Publicacao no GitHub Pages

Arquivos usados pelo Jekyll (como [_layouts/], [_includes/] e [index.html](index.html))
precisam estar no repositorio para o Pages montar o site.

Arquivos locais nao precisam ser versionados (ex: [_site/], [.jekyll-cache/] e [vendor/bundle/]).

## Documentação e manutenção

Os documentos de manutenção abaixo são versionados no repositório e excluídos do site gerado pelo Jekyll.

- [Contrato de manutenção para agentes e colaboradores](AGENTS.md)
- [Arquitetura AS-IS](docs/ARCHITECTURE.md)
- [Inventário funcional](docs/FUNCTIONAL_INVENTORY.md)
- [Conteúdo profissional publicado e estados de evidência](docs/PROFESSIONAL_CONTENT.md)
- [Backlog de melhorias](docs/IMPROVEMENT_BACKLOG.md)

As instruções locais acima são as existentes no repositório; não foram executadas nesta atividade. A árvore local não contém testes ou workflow de CI identificado. Consulte [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) para limites de verificação. Ao alterar o projeto, registre `DOCS_IMPACT=UPDATED | NOT_REQUIRED | PENDING_AUTHORIZATION` conforme [AGENTS.md](AGENTS.md). Não trate documentação pendente como concluída.
