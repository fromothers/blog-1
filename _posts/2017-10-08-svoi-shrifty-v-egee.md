---
title: "Свои шрифты в Эгее"
category: "Веб"
tags:
- Эгея
- Гайд
---

Меня тут спрашивают «Как прикрутить свои шрифты к Эгее, но не от Google Fonts?», а потому, расскажу на примере стандартного шаблона <mark>plain</mark> и движка стабильной версии <mark>3118</mark>.

Для начала нам понадобятся сами шрифты. Для примера изменим стандартный шрифт заголовков на Gilroy Extra Bold, бесплатную версию которого можно [скачать у автора][1], а бесплатную <mark>webfont</mark> версию, которую я использую в примере, можно скачать [отсюда][2]. После, откроем каталог шаблона:

{% highlight shell %}
../themes/plain/styles/
{% endhighlight %}

И создадим в нем папки <mark>../fonts/gilroy</mark>, куда положим скачанные файлы шрифта в форматах <mark>eot</mark>, <mark>ttf</mark>, <mark>woff</mark> и <mark>woff2</mark>. В папке <mark>styles</mark> шаблона создадим файл <mark>fonts.css</mark> где подключаем шрифт:

{% highlight css %}
@font-face {
	font-family: 'Gilroy-ExtraBold';
	src: url('fonts/gilroy/34D194_0_0.eot');
	src: url('fonts/gilroy/34D194_0_0.eot?#iefix') format('embedded-opentype'),
	     url('fonts/gilroy/34D194_0_0.woff2') format('woff2'),
	     url('fonts/gilroy/34D194_0_0.woff') format('woff'),
	     url('fonts/gilroy/34D194_0_0.ttf') format('truetype');
	font-style: normal;
	font-weight: normal;
}
{% endhighlight %}

К слову, подробнее о @font-face можно почитать [здесь][3]. Чтобы подключить <mark>fonts.css</mark> с вашими шрифтами к шаблону, внесем изменения в <mark>main.tmpl.php</mark>, для этого скопируем его из:

{% highlight shell %}
../system/theme/templates/
{% endhighlight %}

И вставим в:

{% highlight shell %}
../themes/plain/templates/
{% endhighlight %}

Помните, что вносить изменения в файлы стандартного шаблона можно только скопировав их в папку своего шаблона, иначе при обновлении движка все ваши измнениея пропадут. Откроем скопированный <mark>main.tmpl.php</mark> и после 41 строки добавим:

{% highlight php %}
<?php _CSS ('fonts') ?>
{% endhighlight %}

Всё, css с вашими шрифтами подключен к шаблону. Тепепь внесем изменения в основной файл стилей <mark>main.css</mark>, найдем класс <mark>.e2-note h1</mark> и заменим на:

{% highlight css %}
.e2-note h1 {
	color: #000;
	font-size: 40px;
	line-height: 1.4;
	max-width: 720px;
	margin-bottom: 8px;
	padding-right: 25px;
	font-family: 'Gilroy-ExtraBold', sans-serif;
}
{% endhighlight %}

<p left>Смотрите ещё: <a href="{{ site.baseurl }}/blog/kat-v-egee">Кат в Эгее</a> и <a href="{{ site.baseurl }}/blog/pishem-svoy-shablon-dlya-egei/">Пишем свой шаблон для Эгеи</a>.</p>

Чтобы разминимизировать <mark>main.css</mark>, для более удобного внесения правок, стоит воспользоваться полезным <a href="http://unminify.com/">сервисом</a>. Таким несложным образом можно добавлять любые нестандартные шрифты в свой шаблон Эгеи.

[1]:	https://www.tinkov.info/gilroy.html
[2]:	https://www.myfonts.com/fonts/radomir-tinkov/gilroy/extra-bold/
[3]:	http://htmlbook.ru/css/font-face