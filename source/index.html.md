---
title: API de Integração de Estoque

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - auth.html
  - campuses.html
  - errors.html

search: true
---

# Introdução

O grupo Kroton Educacional é um dos principais parceiros do Quero Bolsa, trazendo para nossa plataforma diversas bolsas de estudo que permitem o ingresso de muitos alunos ao ensino superior. Como mais um passo a facilitar esse processo de gerenciamento do estoque de bolsas, garantindo a validade do benefício, acordamos a implementação de serviços automatizados para integração dos estoques de cursos. O contexto em questão refere-se a uma sincronização das ofertas ilimitadas de cursos à distância da universidade, assim como os campuses associados aos cursos.

O objetivo desse serviço é garantir a consistência entre as bases de dados, sinalizando quais cursos estão divergentes na base do Quero Bolsa em relação a base do grupo Kroton. Uma vez que esse serviço retorne os resultados, realizaremos as devidas operações de atualização de cursos com valores divergentes, criação de cursos para os cursos faltantes e o processo de desabilitar os cursos para os cursos excedentes. O mesmo processo deve ser aplicado aos campi.

Para otimizar esse processo de sincronização de cursos disponíveis, gostaríamos de propor a implementação de uma Interface de Aplicações (API) REST para atender esses devidos fins, composta por três serviços interdependentes.
