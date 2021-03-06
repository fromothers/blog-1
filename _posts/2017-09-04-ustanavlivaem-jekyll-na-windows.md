---
title: "Устанавливаем Jekyll на Windows"
category: "Веб"
tags:
- Гайд
- Jekyll
---

<p main>По мере настройки и доведения блога до ума я столкнулась с необходимостью установки тех или иных плагинов на <a href="http://jekyllrb.com/">Jekyll</a>, а значит ограничиваться <a href="https://pages.github.com/">GitHub Pages</a> стало нельзя. А потому, я решила собирать сайт локально и отправлять на GitHub Pages уже готовое. Минусы - Сайт привязан к компьютеру, если Windows слетит настраивать придется заново. Плюсы - Можно использовать любые плагины, редактировать сайт локально прежде чем выпустить в свет. В целом, за сохранность блога можно не беспокоится, исходные файлы хранится в <mark>master</mark> ветке репозитория, а собранный сайт в ветке <mark>gh-pages</mark>, до кучи мой сайт хранятся еще и в Dropbox, таким образом его можно синхронизировать между компьютерами, но на каждый из них придется ставить Ruby и прочие дистрибутивы.  В общем, для себя и для вас написала этот гайд по установке Jekyll на Windows.</p>

<p aside>Использованы материалы: <a href="https://msdn.microsoft.com/en-us/commandline/wsl/install_guide#for-anniversary-update-and-creators-update-install-using-lxrun">Инструкция с сайта Microsoft</a> и <a href="https://jekyllrb.com/docs/windows/">Официальная документация Jekyll</a></p>

<hr>

Для установки Jekyll на Windows у вас должна быть 64-разрядная Windows 10 старше версии 1607 Anniversary Update. Чтобы узнать версию своей операционной системы откройте **Параметры** - **Система** - **О системе**. Если все в порядке, запустите <mark>PowerShell</mark> от администратора и введите:

{% highlight shell %}
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
{% endhighlight %}

Компьютер перезагрузится. Далее, чтобы установить среду Ubuntu в Windows понадобится включить режим разработчика, откройте **Параметры** - **Обновление и безопасность** - **Для разработчиков** и включите «Режим разработчика». Откройте <mark>cmd</mark> от администратора и введите: 

{% highlight shell %}
bash
{% endhighlight %}

<p left>Начиная с обновления 1709 (Fall Creators Update) среду Ubuntu можно установить напрямую из <a href="https://www.microsoft.com/store/productId/9NBLGGH4MSV6">Windows маркета</a> пропустив предыдущие шаги.</p>

Примите лицензионное соглашение и дождитесь окончания установки. После её завершения будет предложено ввести имя пользователя и пароль которые могут пригодиться в будущем.

Приступим к установке Jekyll. Но для начала обновим пакеты:

{% highlight shell %}
sudo apt-get update -y && sudo apt-get upgrade -y
{% endhighlight %}

Теперь можно установить Ruby на котором работает Jekyll. Для этого используем репозиторий [BrightBox](https://www.brightbox.com/docs/ruby/ubuntu/) оптимизированный для Ubuntu. Вводим команды:

{% highlight shell %}
sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.4 ruby2.4-dev build-essential
{% endhighlight %}

Обновляем RubyGems.

{% highlight shell %}
sudo gem update
{% endhighlight %}

Теперь осталось установить сам Jekyll.

{% highlight shell %}
sudo gem install jekyll bundler
{% endhighlight %}

Проверить правильность установки можно командой:

{% highlight shell %}
jekyll -v
{% endhighlight %}

Jekyll установлен. Теперь создайте свой блог.

{% highlight shell %}
jekyll new my_blog
{% endhighlight %}

По умолчанию файлы блога  будут находиться по адресу <mark>C:/Пользователи/Имя_пользователя/my_blog</mark>, но его можно размещать и в любой другой папке, на любом диске. Чтобы ничего не потерялось и можно было синхронизироваться между компьютерами я размещаю и использую блог прямо из папки Dropbox'a. Далее переходим в папку с блогом:

{% highlight shell %}
cd my_blog
{% endhighlight %}

Теперь можно запустить Jekyll.

{% highlight shell %}
bundle exec jekyll serve
{% endhighlight %}

Блог станет доступен по локальному адресу [localhost:4000](http://localhost:4000).