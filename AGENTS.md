# Contrato de manutenção do portfólio

## Propósito e escopo

Este repositório contém o portfólio profissional estático de Rodrigo Trombeta, com foco declarado em QA, SDET, automação de testes e arquitetura. A fonte primária para descrever o comportamento atual é o código deste repositório. As informações profissionais são declarações publicadas e não devem ser ampliadas por inferência.

## Arquitetura e localização

- Páginas Jekyll na raiz: `index.html`, `sobre.html`, `experiencia.html`, `habilidades.html`, `projetos.html`, `arquitetura.html`, `contato.html`, `movvia.html` e `imobilis.html`.
- Layout comum: `_layouts/default.html`.
- Seções compartilhadas: `_includes/sections/`.
- Estilos: `assets/css/style.css`.
- Imagens: `assets/img/`.
- Configuração e dependências: `_config.yml`, `Gemfile`, `Gemfile.lock`.
- Documentação: `README.md`, `docs/` e este arquivo.

O Jekyll compõe páginas estáticas a partir do front matter, layout e includes. Ver [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) e [docs/FUNCTIONAL_INVENTORY.md](docs/FUNCTIONAL_INVENTORY.md).

`AGENTS.md` e `docs/` são documentação versionada para manutenção do repositório e estão excluídos do site gerado pelo Jekyll em `_config.yml`.

## Regras de preservação e segurança

- Não alterar arquivos de implementação, imagens, configuração ou conteúdo publicado ao executar uma tarefa limitada à documentação.
- Não instalar dependências, acessar dados de produção, alterar configuração remota, publicar ou fazer commit sem autorização explícita.
- Preservar alterações preexistentes do usuário. Antes de editar, verificar `git status --short`; não sobrescrever conteúdo existente sem leitura e integração cuidadosa.
- Não incluir segredos, dados pessoais adicionais ou informações não destinadas à publicação.
- Não mudar texto profissional, datas, empresas, certificações, resultados ou métricas sem confirmação explícita do proprietário.

## Convenções existentes

As páginas usam HTML com front matter YAML/Liquid, includes Jekyll e classes Tailwind. O layout define `lang="pt-BR"`, título e descrição. Os links internos observados usam caminhos absolutos desde a raiz. Não presumir convenções adicionais além das presentes no código.

## Alterações e validação

Antes de qualquer alteração, identificar escopo autorizado e arquivos afetados. Para mudanças documentais, conferir links relativos, consistência com o código e diff. Para mudanças de implementação, selecionar validação proporcional e segura somente se autorizada; não afirmar que build, testes, links externos ou produção foram validados sem execução real. Não executar comandos que instalem dependências ou criem artefatos quando a tarefa proibir isso.

## Conteúdo profissional

Tratar textos e links profissionais como conteúdo declarado. Classificar evidências como `DECLARED`, `CODE_VERIFIED`, `EXTERNALLY_VERIFIED` ou `NEEDS_OWNER_CONFIRMATION`, conforme [docs/PROFESSIONAL_CONTENT.md](docs/PROFESSIONAL_CONTENT.md). Só usar `EXTERNALLY_VERIFIED` após consulta real a fonte externa. Não inventar nem completar lacunas por plausibilidade.

## Manutenção documental contínua

Toda mudança futura deve avaliar impacto na documentação e registrar explicitamente:

`DOCS_IMPACT=UPDATED | NOT_REQUIRED | PENDING_AUTHORIZATION`

- `UPDATED`: documentos impactados atualizados na mesma atividade.
- `NOT_REQUIRED`: impacto avaliado e considerado inexistente, com justificativa.
- `PENDING_AUTHORIZATION`: a atualização depende de autorização ou informação do proprietário; não apresentá-la como concluída.

Manter `README.md` conciso. Atualizar arquitetura, inventário funcional, conteúdo profissional e backlog quando mudanças afetarem esses temas. Separar fatos, inferências e itens não verificados. Não implementar itens do backlog sem escopo autorizado.

## Limites para arquitetura e agentes de IA

Mudanças em stack, dependências, estrutura de páginas, integração externa ou publicação exigem escopo explícito e avaliação de impacto antes de execução. Agentes devem ler este contrato e os documentos relevantes, inspecionar o estado atual antes de agir, respeitar o escopo solicitado e relatar evidências, validações reais, limitações e `DOCS_IMPACT`. Em caso de conflito entre documentação antiga e o código atual, investigar e documentar divergência; não tratar a documentação como prova de comportamento.
