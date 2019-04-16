---
title: API de Integração de Estoque

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - auth.html
  - pagination.html
  - campuses.html
  - courses.html
  - offers.html
  - stock_operations.html
  - errors.html

search: true
---

# Introdução

A Quero Educação deu mais um passo no gerenciamento do estoque de bolsas de estudo por seus parceiros e agora esse processo passou por uma grande melhoria. Tudo isso para estreitar ainda mais os laços e reafirmar seu compromisso como Marketplace.

A partir de agora abrimos nosso modelo de estoque para ser acessado programaticamente via conjunto de APIs. O serviço permitirá que o parceiro consulte, crie, altere ou delete seu portfólio de bolsas como desejar.

O objetivo dessa melhoria é garantir a consistência entre as bases de dados da Quero Educação e da instituição de ensino superior, além de dar uma maior liberdade e autonomia para que se opere as bolsas.

Em poucas palavras, por meio das APIs o parceiro poderá integrar suas aplicações (sistemas de uso interno) diretamente no nosso modelo e, assim, fazer a gestão de suas bolsas de estudo do modo que preferir.

Para otimizar esse processo, implementamos uma Interface de Aplicações (API) REST. Ela é composta por três serviços interdependentes (“Campi”, “Cursos” e “Ofertas”), os quais possuem seus respectivos métodos, conforme especificado abaixo.
