# Создаем блог используя Jekyll и GitHub Pages

Я недавно перенес блог с WordPress на Jekyll, генератор
сайтов, разработанный для создания минималистичных блогов
хостящихся в GitHub Pages. Процесс написания статей и
создание тем для Jekyll фантастически просты, однако
настройка сайта заняла значительно дольше, чем ожидалось.

В этой статье мы рассмотрим следующее:

* самый быстрый способ запустить блог на основе Jekyll;
* как избежать основных проблем с Jekyll;
* как перенести материалы из WordPress, использовать свое
  доменное имя и писать статьи в любимом редакторе;
* как создавать темы для Jekyll, на пример Liquid;
* несколько новых функций Jekyll 2.0, включая поддержку Sass
   и CoffeeScript и коллекций.


## Назначение Jekyll

Том Престон-Вернер (Tom Preston-Werner) создал Jekyll, что бы вести блог, используя простой, статический HTML, со всеми материалами размещенными на GitHub, который ещё и осуществляет контроль их версий. Целью было избавится от сложности других платформ создав рабочий процесс, который позволял бы вести блог, как [настоящему хакеру][1].

![Октокот, который является маскотом Jekyll][3]

_Октокот, который является маскотом Jekyll. (Изображение
 принадлежит: [GitHub][4])_

Jekyll берет контент написанный в маркдаун, применяет к нему
 шаблоны и выдает на выходе статический сайт, готовый для
того, что бы отдать клиенту. GitHub Pages отдает сайт прямо
из GitHub-репозитория, так что вам не приходится решать
вопросы хостинга.

Вот примеры сайтов, созданных с использованием Jekyll:

* [Блог Барри Кларка (Barry Clark)][01] (это мой)
* [Блог Зака Холмана (Zach Holman)][02]
* [CSS Wizardry][03]
* [Jekyll][04]
* Лендинг и внутренние страницы [HealthCare.gov][05]
* [Development Seed][06]


## Преимущества статики

* **Простота**  
  Jekyll сводит все к абсолютному минимуму, устраняя
  сложности:

  * **Никаких баз данных**
    В отличии от WordPress и других систем управления
    материалами (CMS), Jekyll не использует базы данных
    (БД). Все странцы перед публикацией преобразуются в
    статический HTML. Это прекрасно с точки зрения
    скорости загрузки, так как не происходит никаких
    запросов к БД во время загрузки страницы.

  * **Никаких CMS**
    Просто пишите в Markdown и Jekyll применит к материалам шаблоны и сгенерирует статический сайт.  GitHub может исполнять роль CMS, если нужно, ведь он позволяет редактировать материалы, верно?

  * **Быстрый**
    Jekyll быстрый, потому, что обладает ограниченными
    возможностями и не использует базы данных, просто
    собирает статические странички. Мой основной шаблон
    [Jekyll Now][6] создает всего три HTTP-запроса — 
    включая картинки и иконки социальных сетей!

  * **Минималистичный**
    Большинство сайтов на Jekyll не содержат никаких
    неиспользуемых функций.

* **Контроль представления**
  Проводите меньше времени борясь со сложными шаблонами,
  написанными другими людьми, и больше — создавая
  собственный или адаптируя простостой, базовый шаблон.

* **Безопастность**
  Большенство уязвимостей, которые есть у таких платформ,
  как WordPress отсутствуют в Jekyll, так как отсутствуют
  CMS, базы данных или PHP. Так что не приходится тратить
  массу времени устанавливая обновления, закрывающие
  уязвимости безопастности.

* **Удобный хостинг**
  Это удобно, если вы используете GitHub, вот и все.
  GitHub Pages соберут и захостят использующий Jekyll сайт
  бесплатно и одновременно реализуют для него контроль
  версий.


## Давайте попробуем

Есть несколько способов разобраться с Jekyll, у каждого свои
 особенности. Вот несколько вариантов:

* Установите Jekyll локально используя консоль и создайте
  новый бойлерплейт, используя комманда `jekyll new`,
  соберите его коммандой `jekyll build` и выложите.
  ([Вебсайт Jekyll][4] показывает процес.)

* Клонируйте


*   Clone a starting point to your local machine, install Jekyll locally via
    the command line, make updates to your website, build it locally, and then serve
    it.

*   Fork a starting point, make changes, and then serve it.

We’ll get started with the quickest and easiest option: forking a starting
point. This will get us up and running in a few minutes, and we won’t have to
install any dependancies. Here’s what we’re going to do directly on GitHub.com
in the browser:

1.  Create our Jekyll powered website.
2.  Host it for free on GitHub Pages.
3.  Customize it to include our name, avatar and social links.
4.  Publish our first blog post!


### 1. Fork A Starting Point

We’ll start by forking a repository that has followed best practices and the
workflows that we’ll be covering in this article. This will get us on the right
track and save a lot of time.

I have prepared a repository for us already. Head to [Jekyll Now][12][11][13],
and hit the “Fork” button in the top-right corner of the repository to fork a
copy of the blog theme to your GitHub account.<figure>

![step1][14][12][15]<figcaption>Walkthrough of steps 1 and 2. (
[View large version][16][13][17])</figcaption></figure>
Starting with a fork is great because it will give you a feel for what Jekyll
is like before you have to set up a local development environment, install
dependencies and figure out Jekyll’s build process.

**Common problem #1**: Creating a Jekyll website through the local command line
can be frustrating and time-consuming because you have to**install and
configure dependencies** like Ruby and RubyGems. Let GitHub Pages build the
website for you, until you have a real need to build it locally.

### 2. Host On Your GitHub Account

As a GitHub user, you’re entitled to one free “user” website (as opposed
to a “project” website), which will live at`http://yourusername.github.io`.
This space is ideal for hosting a Jekyll blog!

The best part is that you can simply place your unbuilt Jekyll blog on the
master branch of your user repository, and GitHub Pages will build the static
website and serve it for you. You don’t have to worry about the build process at
all — it’s all taken care of.

Click the “Settings” button in your new forked repository (in the menu on
the right), and change the repository’s name to`yourusername.github.io`,
replacing`yourusername` with your GitHub user name.

Your website will probably go live immediately. You can check by going to
`http://yourusername.github.io`. Don’t worry if it isn’t live yet: Step 3
will force it to be built.<figure>

![The base theme of your blog will look like this after being forked.][18]
[14][19]<figcaption>The base theme of your blog will look like this after being
forked. (Image:[Jekyll Now][6][51][7][25][8][15][9][9][10]) (
[View large version][20][16][21])</figcaption></figure>
Whew! We’re moving fast here. We already have a Jekyll website up and running
! Let’s step back for a second and look at some of the most common issues to be
aware of when hosting a Jekyll website on GitHub Pages.

**Common problem #2**: Be aware of the difference between
[user websites and project websites][22][17][23] on GitHub. With a user website
(which we’re setting up), you don’t need to do any branching. The`master`
branch is already configured to run anything placed on it through Jekyll. You
don’t need to set up a`gh-pages` branch.

**Common problem #3**: Using a project website for your Jekyll website
[introduces some complexity][24][18][25] because your website will be published
to a subdirectory. The URL will look like
`http://yourname.github.io/repository-name`, which will cause problems in
Jekyll templates, such as breaking references to images and not letting you
preview the website locally.

**Common problem #4**: Jekyll has a [lot of plugins][26][19][27], but GitHub
Pages supports only a[few of them][28][20][29]. If you try to include a plugin
that isn’t supported, then Jekyll will fail while building your website. So,
stick to the supported list. Luckily, my favorite plugin is on the list:
[Jemoji][30][21][31] lets you include emoji in blog posts, just like you would
on GitHub and Basecamp.

### 3. Customize Your Website

You can now change your website’s name, description, avatar and other options
by editing the`_config.yml` file. These custom variables have been set up for
convenience and are pulled into your theme when your website gets built.

Making a change to `_config.yml` (or any file in your repository) will force
GitHub Pages to rebuild your website with Jekyll. The rebuilt website will be
viewable a few seconds later at`http://yourusername.github.io`. If your website
wasn’t live immediately after step 2, it will be after this step.

Go ahead and customize your website by updating the variables in your
`_config.yml` file and then committing the changes.

You can change your blog’s files from here on in one of three ways. Pick
whichever suits you best:

*   Edit files in your new `username.github.io` repository directly in the
    browser at GitHub.com (as shown below
    ).
*   Use a third-party GitHub content editor, such as [Prose][32][22][33] by
    Development Seed. It’s optimized for Jekyll, which makes it easy to edit
    Markdown, write drafts and upload images.

*   Clone your repository and make updates locally, and then push them to your
    GitHub repository
    ([Atlassian has a guide][34][23][35] on this).<figure>

![Editing your website’s _config.yml on GitHub.com ][36][24][37]<figcaption>
Editing your website’s`_config.yml` on GitHub.com. (Image credit:
[Jekyll Now][6][51][7][25][8][15][9][9][10]) ([View large version][38][26][39]
**Common problem #5**: Don’t assume that you need to `jekyll build` the website
locally in order to customize and theme a Jekyll website. GitHub Pages does that
for you. You just need to place the files that you want to be built in the
master branch of your user repository or in the`gh-pages` branch of any other
repository, and then GitHub Pages will process it with Jekyll.

### 4. Publish Your First Blog Post

Your website is now customized, live and looking good. You just have to publish
your first blog post:

1.  Edit `/_posts/2014-3-3-Hello-World.md`, deleting the placeholder content
    and entering your own. If you need a quick primer on writing in Markdown, check
    out
   [Adam Pritchard’s cheat sheet][40][27][41].
2.  Change the file name to include today’s date and the title of your post.
    Jekyll requires posts to be named
   `year-month-day-title.md`.
3.  Update the title at the top of the Markdown file. Those variables at the
    top of the blog post are called front matter, which we’ll dig into a little
    later. In this case, they specify which layout to use and the title of the blog
    post.
   [Additional front-matter variables][42][28][43] exist, such as `permalink`
   `tags` and `category`.

If you’d like to create new blog posts in the browser on GitHub.com, simply
hit the “+” icon in`/_posts/`. Just remember to format the file name correctly
and to include the front-matter block so that the file gets processed by Jekyll.

![Creating a new post on GitHub.com][44][29][45]<figcaption>Creating a new post
on GitHub.com.
([View large version][46][30][47])</figcaption></figure>
**Common problem #6**: One concern I had about using Jekyll for my blog was
that it has no CMS, so I wouldn’t have the convenience of being able to make
quick edits by logging into a CMS interface when I’m away from my laptop. It
turns out that your Jekyll blog will have a CMS if you use GitHub Pages, because
GitHub itself serves as the CMS. You can edit posts in the browser, even on your
phone if you wish. It might not be as convenient as other CMS’, but you won’t be
stuck when you’re away from your computer and need to make a change.

### Optional Steps

#### Use Your Own Domain

Configuring your domain name to point to GitHub Pages is a simple two-step
process:

1.  Go to the root of your blog’s repository, and edit the CNAME file to
    include your domain name (for example,
   `www.yourdomainname.com`).
2.  Go to your domain name registrar, and add a CNAME DNS record pointing your
    domain to GitHub Pages:

    *   type: `CNAME`
    *   host: `www.yourdomainname.com`
    *   answer: `yourusername.github.io`
    *   TTL: `300`

Then, refresh [What’s My DNS][48][31][49] like crazy until you’ve propagated
. If you run into any problems, refer to
“[Setting Up a Custom Domain With GitHub Pages][50][32][51].”

#### Import Your Blog Posts From WordPress

Before importing, you’ll need to export your data from WordPress, possibly
massaging the data a little (for example, by updating the image references), and
then import it into your new Jekyll website. Fortunately, a few great tools can
help.

To **export from WordPress**, I’d highly recommend Ben Balter’s one-click
[WordPress to Jekyll Exporter][52][33][53] plugin. It exports all of your
WordPress content as a ZIP file, including posts, images and meta data,
converting it to Jekyll’s format where needed. Good on you, Ben.

The other option is to export all content in the “Tools” menu of the
WordPress dashboard, and then importing it with[Jekyll’s importer][54][34][55]

Next, we need to **update our image references**. Ben Balter’s plugin will
export all of your images into a folder. Then, you’ll need to copy them to
wherever you’re hosting your images on your Jekyll blog. This could be in an
`/images` folder or on a content delivery network.

Then, you have the fun task of updating all of the links to these images across
your WordPress content. Because I was only updating five or six posts, a quick
find-and-replace worked well, but if you have a lot of content, then it might be
worth writing a script or checking out scripts that others have written, such as
[Paul Stamatiou’s][56][35][57].

Finally, we have to **import comments**. Being a platform for static websites,
Jekyll doesn’t support comments. However, a hosted solution like Disqus works
really well! I’d recommend[importing your WordPress comments to Disqus][58]
[36][59]. Then, if you’re using Jekyll Now, you can enter your Disqus user
name in`_config.yml` and you’re set.

#### Blog Locally in Your Favorite Editor {#bloglocallyinyourfavoriteeditor}

If you prefer to write in Sublime, Vim, Atom or another editor, all you need to
do is clone to your repository, create new Markdown blog posts in the`_posts`
folder, and then push the changes to GitHub. GitHub Pages will automatically
rebuild your website as soon as your Markdown file hits the repository, and your
new blog post will be live as soon as the build is complete.

1.  First, `git clone git@github.com:yourusername/yourusername.github.io.git`,
    or clone your repository using
   [GitHub Mac][60][37][61].
2.  Create a new post in the `_posts` folder. Remember to name it in the format
   `year-month-day-title.md`, and include the front matter at the top of the
    post.

3.  Commit the post’s Markdown file, and push to your GitHub repository. (
    [Atlassian’s guide to Git’s basics][34][38][62] might come in handy.)
4.  That’s it! Just wait for GitHub Pages to rebuild your website. This
    typically takes under 10 seconds, assuming you don’t have a huge amount of
    content.


**Common problem #7**: Again, you don’t need to build your Jekyll website
locally in order to write a blog post locally and publish it to your website.
You can write the Markdown post locally and push it with any images you’ve used,
and then GitHub Pages will rebuild the website for you on the server.

### Создание темы для Jekyll

Хотите адаптировать тему? Вот кое что из того, что, следует иметь ввиду:


#### Сборка сайта локально

Если тема, которую вы хотите создать, чуть сложнее, чем тривиальная, то разумно проводить её разработку и тестирование локально. Это необязательно, можно просто пушить изменения в репозиторий и GitHub Pages всё соберут. Однако видеть изменения в процессе работы может быть полезно.

Сначала нужно установить Jekyll и его зависимости. Запустите `gem install jekyll`, затем `gem install jemoji jekyll-sitemap`. Должны быть установлены [Ruby][63], [RubyGems][65] и [Kramdown][67]. Полный [список зависимостей Jekyll][69].

Вот шаги для создания и просмотра сайта на базе Jekyll локально:

1. Cначала войдите (`cd`) в директорий, в котором находится сайт.
2. Запустите `jekyll serve --watch`. (у Jekyll [масса встроенных настроек][71].)
3. Откройте свой сайт по адресу `http://0.0.0.0:4000`.
4. Когда закончите, закомитьте изменения и пушните все в ветку `master` репозитория. GitHub Pages пересоберут сайт.


**Проблема №8**: Имейте в виду, что `jekyll build` сотрет
все из `/_sites/`. Первый шаг `jekyll build` — удаление
всего, что есть в `/_sites/` и сборка всего с нуля. Так что
не стоит там хранить файлы, если вы не хотите, что бы они
исчезли при следующей же сборке. В `/_sites/` должно быть
только то, что генерируется Jekyll.


### Структура директориев

Вот срез структуры директориев сайта на базе Jekyll:

    /Users/barryclark/Code/jekyll-now
    ├─ CNAME # Содержит доменное имя (опционально)
    ├─ _config.yml # Файл конфигурации Jekyll
    ├─ _includes # Сниппеты кода, которые можно использовать в шаблонах
    │  ├─ analytics.html
    │  └─ disqus.html
    ├─ _layouts
    │  ├─ default.html # Основной шаблон. Включает <head>, <navigation>, <footer>, и т.д.
    │  ├─ page.html # Лаяут для статических страниц
    │  └─ post.html # Лаяут для постов в блоге
    ├─ _posts # Все посты — тут!
    │  └─ 2014-3-3-Hello-World.md
    ├─ _site # После сборки сайта Jekyll генерирует HTML в этот директорий. Это то, что отдается браузеру!
    │  ├─ CNAME
    │  ├─ LICENSE
    │  ├─ about.html
    │  ├─ feed.xml
    │  ├─ index.html
    │  ├─ sitemap.xml
    │  └─ style.css
    ├─ about.md # Статическая страничка "О проекте", которую я создал.
    ├─ feed.xml # XML для работы RSS
    ├─ images # Содержит все картинки
    │  ├── first-post.jpg
    ├─ index.html # Лендинг
    ├─ scss # Sass со стилями сайта
    │  ├─ _highlights.scss
    │  ├─ _reset.scss
    │  ├─ _variables.scss
    │  └─ style.scss
    └── sitemap.xml # Карта сайта


#### Liquid Templating

Jekyll uses the Liquid templating language to process templates. There are two
important things to know about using Liquid.

First, a **YAML front-matter** block is at the beginning of every content file
. It specifies the layout of the page and other variables, like`title`, `date`
and`tags`. It may include custom page variables that you’ve created, too.

**Liquid template tags** are used to execute loops and conditional statements
and to output content.

For example, each blog post uses the following layout from
`/_layouts/post.html`:

    ---
    layout: default
    ---

    <article class="post">

      <h1>{{ page.title }}</h1>

      <div class="entry">
        {{ content }}
      </div>

      <div class="date">
        Written on {{ page.date | date: "%B %e, %Y" }}
      </div>

      <div class="comments">
        {% include disqus.html disqus_identifier=page.disqus_identifier %}
      </div>
    </article>


At the top of the file, YAML front matter is surrounded by triple hyphens. Here
, we’re specifying that this file should be processed as the content for the
`default.html` layout, which contains the website’s header and footer.

Liquid markup uses double curly braces to output content. The first Liquid
template tags that do this in the example above are`{{ page.title }}` and
`{{ content }}`, which output the title and content of the blog post. A number
of[Jekyll variables][73][44][74] are made available for outputting in templates
.

Single curly braces and modules are used for conditionals and loops and for
displaying includes. Here, I’m including a Disqus commenting partial at the
bottom of the blog post, which will display the markup from
`/_includes/disqus.html`.

#### _config.yml

This is Jekyll’s configuration file, containing all of the
[settings for your Jekyll website][75][45][76]. The great thing about
`_config.yml` is that you can also specify all of your own variables here to be
pulled in via template files across the website.

For example, I use custom variables in Jekyll Now’s `_config.yml` to allow SVG
icons to be easily included in the footer:

Here is `_config.yml`:

    # Includes an icon in the footer for each user name you enter
    footer-links:
      github: barryclark
      twitter: baznyc


And here is `/_layouts/default.html`:

    <footer class="footer">
      {% if site.footer-links.github %}<a href="http://github.com/{{ site.footer-links.github }}">{% include svg-icons/github.html %}</a>{% endif %}
      {% if site.footer-links.twitter %}<a href="http://twitter.com/{{ site.footer-links.twitter }}">{% include svg-icons/twitter.html %}</a>{% endif %}
    </footer>
    <figure>

![Example of SVG footer icons][77]<figcaption>Example of SVG footer icons</
figcaption
></figure>
The variable is outputted to the Twitter URL like this:
`http://twitter.com/{{ site.footer-links.twitter }}`, so that the footer icon
links to your Twitter profile. One other thing I really like about variables is
that you can use them to optionally add pieces of UI. So, a footer icon wouldn’t
be displayed if you don’t enter anything in the variable.

**Common problem #9**: Note that `_config.yml` changes are loaded at compile
time, not runtime. This means that if you’re running`jekyll serve` locally and
you edit`_config.yml`, then changes to it won’t be detected. You’ll need to
kill and rerun`jekyll serve`.


### Лаяут и статические страницы

Большинство простых блогов требуют только двух лаяутов: один для постов (`post.html`) и один для статики (`page.html`). И единственная разница между ними в Jekyll Now в том, что `post.html` включает блок комментариев Disqus и дату, а `page.html` — нет.

Если вы создаете файл с расширением `.html` или `.md` в корневом директорие сайта, он будет рассматриваться как статическая страничка. Например `about.md` будет доступна по адресу `www.mysite.com/about`. Просто и замечательно!

### Изображения

Я храню изображения в директорие репозитория `/images/` и не испытываю на данный момент никаких проблем с производительностью. Если сайт размещен на GitHub Pages, то изображения будут доставляться супер-быстро c CDN GitHub'а. Пока я не вижупричин хранить их в другом месте, но если уж мигрировать куда то, вроде CloudFront, то изменить ссылки — не проблема.

Мне нравится простота хранения изображений в директорие `/images/`. Маркдаун для добавления изображения прост:

    ![Image description](/images/my-image.jpg)


### Поддержка препроцессоров

Jekyll на данный момент поддерживает Sass и CoffeeScript без необходимости использовать плагины или Grunt. Можно просто добавить файлы с расширениями `.sass`, `.scss` и `.coffee` в рабочий директорий и Jekyll их обработает, сгенерировав в том же директорие `.css` и `.js`

![It's Sass time!][78]

_Время Sass'ить! (Источник: [Sass][79])_

Что бы убелится, что `.sass`, `.scss` и `.coffee` обрабатываются, добавьте в начало файла две строки с тройным дефисом:

    ---
    ---
    $color-coffee: #644C37;

Если используете `@imports` для разбиения Sass на модули, то надо сообщить об этом Jekyll, добавив в `_config.yml` следующее:

    sass:
      sass_dir: _scss

Кроме того, можно задать то, как будет проходить сборка:

    sass:
      sass_dir: _scss
      style: :compressed


## Более углубленно о функциональных возможностях Jekyll

В Jekyll есть несколько мощных, более продвинутых фич,
которые могут помочь, если надо построить что то более
сложное, чем простой блог.


### Файлы данных

Есть два способа интегрировать внешние данные в Jekyll.
Первый, используя сторонние сервисы и API. Например Disqus
позволяет добавлять динамику на страницы и является примером
сервиса.

Второй способ — использование файлов данных. Jekyll может читать [файлы][81] в формате YAML и JSON из директория `/_data/`, и позволяет использовать их в шаблонах, как обычные переменные. Это весьма полезно для хранения повторяющихся данных или настроек, которые вы не хотите помещать в `_config.yml`, что бы он не разростался сверх меры.

Кроме того, файлы данных дают возможность добавлять на сайт большие выборки данных. Можно написать скрипт, который будет разбивать их на несколько JSON файлов, разместить их в директорие `/_data/`. Ярким йпримером такого подхода является [доставка данных Google Analytics Jekyll][83], для ранжирования постов по популярности.


### Колекции

Два стандартных типа документов Jekyll это посты (блога) и
страницы (просто статика). Релиз Jekyll 2.0 добавил
[коллекции][85], которые позволяют добавлять собственные
типы документов. Например, можно использовать коллекции для
определения фотоальбома, книги или портфолио.


## Заключение

Jekyll подходит не для каждого проекта. Основным недостатком
генератора статики является сложность внедрения динамических
функций на стороне сервера. Количество сервисов, которые
можно интегрировать в проект, таких как Disqus, ростет, но
не все из них предоставляют возможность гибких настроек и
контроля. Jekyll не подходит для создания сайтов со своей
базой пользователей, так как в нем нет ни баз данных, ни
логики на стороне сервера для обработки регистрации или
аутентификации.

Достоинства Jekyll — его простота и минимализм, которые
обеспечивают вас, всем чем нужно, что бы создать
контентно-ориентированный сайт, который не подразумевает
значимой интерактивности — и не более того. Что делает
Jekyll идеальным для блога и портфолио и дает возможность
рассматривать его для реализации простых сайтов для
клиентов.

Не дайте репутации Jekyll, как платформы для создания
блогов, ориентированной на хакеров, отпугнуть вас. Создание
красивых, быстрых, минималистичных сайтов с его помощью не
требует элитных хакерских навыков или умения работать с
командной строкой. Как я уже показал в пошаговом руководстве
выше, его можно настроить за считанные минуты, и посвятить
свое время работе над материалами и дизайном.

## Ресурсы для дальнейшего изучения

* [Jekyll][87]
  Официальный сайт это лучший рисурс для изучения Jekyll и
  создания сайта. Значительная часть информации для статьи
  была почерпнута оттуда.

* [Jekyll Now][6]
  Этот ресурс упрощает создание блога на основе Jekyll устраняя необходимость в множестве начальных настроек.

* [Исходный код Jekyll][89]
  Репозиторий содержит исходный код и дискуссии не тему
  Jekyll


[01]: http://www.barryclark.co/
[02]: http://zachholman.com/
[03]: http://csswizardry.com/about/#colophon
[04]: http://jekyllrb.com/
[05]: http://www.healthcare.gov/
[06]: http://developmentseed.org/blog/2013/10/24/its-called-jekyll/

 [1]: http://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html

 [3]: img/octojekyll-opt.jpg
 [4]: http://jekyllrb.com/

 [6]: http://github.com/barryclark/jekyll-now

 [12]: http://www.github.com/barryclark/jekyll-now

 [14]: img/step1.gif

 [16]: http://www.smashingmagazine.com/wp-content/uploads/2014/07/step1.gif

 [18]: img/jekyll-now-theme-500-opt.png

 [20]: http://www.smashingmagazine.com/wp-content/uploads/2014/07/jekyll-now-theme-large-opt.jpg

 [22]: https://help.github.com/articles/user-organization-and-project-pages

 [24]: http://jekyllrb.com/docs/github-pages/#project_page_url_structure

 [26]: http://jekyllrb.com/docs/plugins/

 [28]: https://help.github.com/articles/using-jekyll-plugins-with-github-pages

 [30]: https://github.com/jekyll/jemoji

 [32]: http://prose.io

 [33]: http://www.smashingmagazine.com/2014/08/01/build-blog-jekyll-github-pages/#22
 [34]: https://www.atlassian.com/git/tutorial/git-basics

 [36]: img/config-500-opt.png

 [38]: http://www.smashingmagazine.com/wp-content/uploads/2014/07/config-large-opt.png

 [40]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

 [42]: http://jekyllrb.com/docs/frontmatter/

 [44]: img/newpost-500-opt.png

 [46]: http://www.smashingmagazine.com/wp-content/uploads/2014/07/newpost-large-opt.png

 [48]: https://www.whatsmydns.net/

 [50]: https://help.github.com/articles/setting-up-a-custom-domain-with-pages

 [52]: https://github.com/benbalter/wordpress-to-jekyll-exporter

 [54]: http://import.jekyllrb.com/docs/wordpress/

 [56]: https://gist.github.com/stammy/790971

 [58]: http://help.disqus.com/customer/portal/articles/466255-importing-comments-from-wordpress

 [60]: https://mac.github.com/

 [63]: http://www.ruby-lang.org/

 [65]: http://rubygems.org/

 [67]: https://github.com/gettalong/kramdown

 [69]: https://github.com/jekyll/jekyll

 [71]: http://jekyllrb.com/docs/usage/

 [73]: http://jekyllrb.com/docs/variables/

 [75]: http://jekyllrb.com/docs/configuration/

 [77]: img/footer-icons-opt.png
 [78]: img/sass.svg "It's Sass time!"
 [79]: http://sass-lang.com/

 [81]: http://jekyllrb.com/docs/datafiles/

 [83]: http://developmentseed.org/blog/google-analytics-jekyll-plugin/

 [85]: http://jekyllrb.com/docs/collections/

 [87]: http://jekyllrb.com

 [89]: http://github.com/jekyll/jekyll
