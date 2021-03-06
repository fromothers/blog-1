---
title: "Уютный Jekyll"
category: "Заметки"
tags:
  - Jekyll
  - CMS
---

Внезапно, но блог сменил движок с [Эгеи]({{ site.baseurl }}/blog/egeya/) на Jekyll и тому было несколько причин. Во-первых, в блог я пишу не так часто, иногда и вовсе раз в несколько месяцев, поэтому нет смысла содержать полноценный хостинг. Во-вторых, Jekyll представляет собой статический сайт без какого-либо php и mysql, соответственно страницы загружаются если не моментально, то явно гораздо быстрее, в отличие от сайта на хостинге который, ко всему прочему, был не очень то быстр. В-третьих, Jekyll базируется на GitHub Pages, следовательно, не придется беспокоится об оплате хостинга, а сайт всегда будет доступен из репозитория.

![Уютный Jekyll](https://i.imgur.com/yfBC1VR.png)

Что же касается удобства пользования, Jekyll довольно прост в обращении. Установить его можно просто создав аккаунт на GitHub и сделав форк репозитория [Jekyll now](https://github.com/barryclark/jekyll-now). Для написания заметки в блог, достаточно создать файл с markdown разметкой, написать и оформить саму заметку, отправить ее на github. Админ-панели у Jekyll нет, но всегда можно воспользоваться [prose.io](http://prose.io) или брутально написать пост прямо в notepad++. Если чукча дизайнер, а не программист и нет желания возиться с консолью и командами, то взаимодействовать с файлами блога можно через приложение [GitHub Desktop](https://desktop.github.com/). К слову, верстать шаблон для Jekyll гораздо легче чем для Эгеи, при том, что Jekyll дает куда большую свободу для оформления поста и самого сайта.