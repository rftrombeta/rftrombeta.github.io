# Arquitetura AS-IS

## Escopo e evidência

Documento baseado em inspeção estática dos arquivos locais. Histórico: um build Jekyll foi executado em uma etapa anterior com destino temporário externo. Na PORTFOLIO-RELEASE-01A-FIX-01, `bundle check`, build Jekyll com destino externo, inspeção de HTML, verificação de links internos/âncoras/assets e `git diff --check` foram executados. Não foram executados testes automatizados da aplicação, validação atual de links externos, inspeção do site publicado nem consulta de configuração remota do GitHub. O repositório é a fonte primária para o estado descrito.

## Stack comprovada

- Jekyll por meio da dependência `github-pages` declarada em `Gemfile`; `Gemfile.lock` registra Jekyll 3.10.0 e `github-pages` 232.
- HTML com front matter YAML, templates Liquid e includes Jekyll.
- CSS local em `assets/css/style.css`; classes Tailwind aparecem no HTML e Tailwind é carregado por CDN no layout.
- JavaScript embutido em includes para ampliar certificado e imagens de projetos.
- Mermaid 10 importado por ES Module via jsDelivr e inicializado pelo layout.
- Ruby/Bundler são indicados pelo Gemfile e instruções locais do README. Versões locais de Ruby e Bundler não foram verificadas.

## Estrutura

```text
_includes/sections/   conteúdo reutilizável por página
_layouts/default.html layout HTML compartilhado
assets/css/           CSS local
assets/img/           certificado, thumbnails e imagens
docs/                 documentação do projeto
*.html                nove páginas Jekyll na raiz
Gemfile               dependências Ruby
Gemfile.lock          versões resolvidas registradas
_config.yml           configuração Jekyll
```

## Geração e composição

Cada página HTML possui front matter com `layout`, `title` e `description`, e inclui as seções necessárias. `_layouts/default.html` fornece `doctype`, idioma `pt-BR`, viewport, título, descrição, Tailwind CDN, CSS local, `{{ content }}` e inicialização de Mermaid. O conteúdo é estático no repositório: textos, listas e cards são mantidos em HTML; não há CMS, API ou persistência identificados.

As páginas são `index.html`, `sobre.html`, `experiencia.html`, `habilidades.html`, `projetos.html`, `arquitetura.html`, `contato.html`, `movvia.html` e `imobilis.html`. A página inicial inclui navegação, início, cards de acesso e rodapé; as demais incluem navegação, conteúdo correspondente e rodapé. `projetos.html` compõe `_includes/sections/produtos.html` antes de `_includes/sections/projetos.html`, mantendo Produtos próprios separados dos sete projetos SDET. `movvia.html` e `imobilis.html` são páginas internas de estudo de caso compostas diretamente em HTML com front matter, layout padrão e includes compartilhados de navegação e rodapé; não introduzem dependências ou integração externa.

`AGENTS.md` e `docs/` contêm documentação interna versionada, excluída do artefato Jekyll por `_config.yml`; permanece disponível no repositório Git.

## Navegação, conteúdo e comportamento

`_includes/sections/navegacao.html` define links para as sete páginas, com caminhos iniciados por `/`, um skip link para `#conteudo` e um botão nativo para expandir/recolher os links em viewport mobile. Todas as nove páginas públicas têm um `<main id="conteudo" tabindex="-1">`, com navegação global e rodapé fora desse landmark, e exatamente um `h1`. A estrutura e o comportamento receberam homologação manual 5/5 informada pelo proprietário: aparência das nove páginas, skip link e navegação por teclado, navegação sticky e âncoras, dialogs e responsividade desktop/mobile. Essa homologação não constitui auditoria WCAG completa nem teste com leitor de tela. O cabeçalho usa `position: sticky`, permanece no fluxo do documento e acompanha a altura responsiva do menu. O CSS preserva o espaçamento superior do primeiro conteúdo e aplica margem de rolagem a alvos de âncora. O script inline sincroniza `aria-expanded`, trata Escape, fecha ao selecionar um link sem transferir o foco ao botão e ajusta o estado ao cruzar o breakpoint de 768 px. Sem JavaScript, os links permanecem visíveis como fallback. As homologações funcionais anteriores (12/12 verificações iniciais e 6/6 finais) também foram informadas pelo proprietário. `index.html` fornece cards para as páginas. Os includes em `_includes/sections/` concentram o conteúdo. Não foi identificado roteador client-side.

`inicio.html` contém apresentação, link de validação do CTFL e uma prévia acionada por botão independente, implementada como diálogo nativo com zoom. A UX-01C recebeu homologação funcional manual informada (14/14 PASS) em 320 px, 375 px, 768 px e desktop; isso não certifica conformidade WCAG nem inclui teste de leitor de tela ou medição formal de contraste. `projetos.html` lista sete projetos, mantém links nativos para repositórios e oferece botões separados para abrir thumbnails em diálogo modal nativo. Em mobile, as thumbnails usam largura total e altura natural, e os botões overlay acompanham sua proporção original; o layout horizontal atual permanece a partir de `sm`. O responsável pelo projeto informou aprovação funcional manual dos cards e lightbox e aprovação visual responsiva após FIX-02, com imagens sem cortes. Não foi informada quantidade de testes nem se afirma repetição integral dos cenários funcionais após FIX-02. UX-01D-VAL não encontrou bloqueantes estáticos e registrou possível redundância no gerenciamento de foco como observação não bloqueante. Não há evidência de testes com leitor de tela ou auditoria automatizada, e essa homologação não certifica conformidade WCAG 2.2 AA. Os detalhes funcionais estão em [FUNCTIONAL_INVENTORY.md](FUNCTIONAL_INVENTORY.md).

## Estilos, scripts e assets

O CSS local importa Inter do Google Fonts e contém regras CSS gerais, de impressão e específicas para links, além de estilos Mermaid. Também mantém `hidden` efetivo para o menu recolhido e fornece `:focus-visible` para links de projetos, arquitetura e contato e para o botão mobile. A maior parte do estilo visual observado no HTML é expressa por classes Tailwind.

Os scripts inline implementam abertura/fechamento do diálogo e zoom do certificado, além do lightbox de projetos. O layout importa e inicializa Mermaid com `securityLevel: "loose"`; nenhum bloco Mermaid foi identificado no conteúdo inspecionado. `assets/img/` contém `cert-ctfl.jpg`, thumbnails de projetos, `architecture-diagram.png` e `og-image.png`; os dois últimos arquivos não foram localizados como referências HTML/CSS durante a inspeção.

## Dependências e integrações externas

- `Gemfile`: `github-pages` no grupo `:jekyll_plugins` e `webrick` `~> 1.8`.
- Tailwind: `https://cdn.tailwindcss.com`.
- Mermaid: `https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs`.
- Inter: Google Fonts importado em `assets/css/style.css`.
- Links para GitHub, LinkedIn, BSTQB e email estão no conteúdo. Disponibilidade e destino atual dos links não foram verificados.

## Execução local e publicação conhecida

`README.md` instrui instalar Ruby e Bundler, executar `bundle install` e `bundle exec jekyll serve`, e acessar `http://localhost:4000`. Essas instruções foram documentadas, não executadas nesta atividade.

O README descreve publicação pelo GitHub Pages e explica que os arquivos Jekyll devem estar no repositório. Não há workflow GitHub Actions ou configuração de deploy na árvore inspecionada. A forma atual de publicação, configuração do repositório remoto, domínio ativo e estado do site publicado não foram verificados; não inferir detalhes operacionais além do README.

## Limitações e itens não verificados

- Sem evidência local de testes automatizados ou CI. As homologações funcionais manuais de navegação e certificado estão registradas no backlog e no inventário; não incluem testes de leitor de tela nem medição formal de contraste.
- Menu é ocultado abaixo do breakpoint `md` pelas classes atuais; não foi encontrado menu alternativo no include.
- A inicialização de dependências externas ocorre no cliente e depende da disponibilidade dos CDNs.
- Metadados presentes no layout incluem título e descrição; não foram identificadas tags Open Graph, canonical ou dados estruturados.
- O build Jekyll e as verificações estáticas listadas no escopo foram executados na PORTFOLIO-RELEASE-01A-FIX-01. Não foram executados testes automatizados da aplicação, análise de performance, auditoria WCAG, teste com leitor de tela, validação atual de links externos ou inspeção de produção.
- A ausência de workflow refere-se à árvore local inspecionada; não comprova a configuração remota do GitHub Pages.
