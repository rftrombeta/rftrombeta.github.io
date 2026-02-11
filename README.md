# Rodrigo Trombeta Portfolio

Este repositorio hospeda o codigo da pagina do portfolio.

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
