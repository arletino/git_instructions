
**Создание конфликта**

Но что если изменения в ветке master конфликтуют с изменениями в style?
Создание конфликтующих изменений в ветке master.

Вернитесь в master и создайте конфликт

Вернитесь в ветку master и внесите следующие изменения:

`git checkout master`

Файл: *lib/hello.html*

        <!-- Author: Alexander Shvets (alex@githowto.com) -->
        <html>
        <head>
        <!-- no style -->
        </head>  
        <body> 
        <h1>Hello, World! Life is great!</h1>  
        </body> 
        </html> 

**Выполните:**

`git add lib/hello.html`  
`git commit -m 'Life is great!'`  

**Внимание: используйте для этого коммита одинарные кавычки, дабы избежать проблем с символом !. В bash он считается служебным.**
**Просмотр веток**  
**Выполните:**

`git hist --all`

**Результат:**

    $ git hist --all
    * 454ec68 2011-03-09 | Life is great! (HEAD, master) [Alexander Shvets]
    | * 5813a3f 2011-03-09 | Merge branch 'master' into style (style) [Alexander Shvets]
    | |\  
    | |/  
    |/| 
    * | 6c0f848 2011-03-09 | Added README [Alexander Shvets]
    | * 07a2a46 2011-03-09 | Updated index.html [Alexander Shvets]
    | * 649d26c 2011-03-09 | Hello uses style.css [Alexander Shvets]
    | * 1f3cbd2 2011-03-09 | Added css stylesheet [Alexander Shvets]
    |/  
    * 8029c07 2011-03-09 | Added index.html. [Alexander Shvets]
    * 567948a 2011-03-09 | Moved hello.html to lib [Alexander Shvets]
    * 6a78635 2011-03-09 | Add an author/email comment [Alexander Shvets]
    * fa3c141 2011-03-09 | Added HTML header (v1) [Alexander Shvets]
    * 8c32287 2011-03-09 | Added standard HTML page tags (v1-beta) [Alexander Shvets]
    * 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
    * 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

После коммита *«Added README»* ветка **master** была объединена с веткой *style*, но в настоящее время в **master** есть дополнительный коммит, который не был слит с *style*.

Последнее изменение в **master** конфликтует с некоторыми изменениями в *style*.  
  
На следующем шаге мы решим этот конфликт.  

Научиться разрешать конфликты во время слияния

Слияние master с веткой *style*

Теперь вернемся к ветке *style* и попытаемся объединить ее с новой веткой **master**.
**Выполните:**

`git checkout style`
`git merge master`

**Результат:**

    $ git checkout style
    Switched to branch 'style'
    $ git merge master
    Auto-merging lib/hello.html
    CONFLICT (content): Merge conflict in lib/hello.html
    Automatic merge failed; fix conflicts and then commit the result.

Если вы откроете *lib/hello.html,* вы увидите:
Файл: *lib/hello.html*

    <!-- Author: Alexander Shvets (alex@githowto.com) -->
    <html>
    <head>
    <<<<<<< HEAD
        <link type="text/css" rel="stylesheet" media="all" href="style.css" />
    =======
        <!-- no style -->
    >>>>>>> master
    </head>
    <body>
        <h1>Hello,World! Life is great!</h1>
    </body>
    </html>

Первый раздел - версия во главе текущей ветки *(style)*. Второй раздел - версия ветки **master**.

**Решение конфликта**

Вам необходимо вручную разрешить конфликт. Внесите изменения в *lib/hello.htm*l для достижения следующего результата.
Файл: *lib/hello.html*

    <!-- Author: Alexander Shvets (alex@githowto.com) -->
    <html>
    <head>
        <link type="text/css" rel="stylesheet" media="all" href="style.css" />
    </head>
    <body>
        <h1>Hello, World! Life is great!</h1>
    </body>
    </html>


Сделайте коммит решения конфликта
**Выполните:**

`git add lib/hello.html`
`git commit -m "Merged master fixed conflict."`

**Результат:**

    $ git add lib/hello.html
    $ git commit -m "Merged master fixed conflict."
    Recorded resolution for 'lib/hello.html'.
    [style 645c4e6] Merged master fixed conflict.