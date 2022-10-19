
# Git?

**Содержание:**
1. [Установка Git](##1.-Установка-Git)
2. [Настройка Git](##2.-Настройка-Git)
3. [Создание репозитория](##3.-Создание-репозитория)
4. [Добавить файлы или новые файлы в репозиторий](##4.-Добавить-файлы-или-новые-файлы-в-репозиторий)
5. [Проверка текущего состояния репозитория](##5.-Проверка-текущего-состояния-репозитория)  

**Git**  — мощная и сложная распределенная система контроля версий. Понимание всех возможностей git открывает для разработчика новые горизонты в управлении исходным кодом. Самый верный способ обучиться владению Git — испытать его своими руками.

## 1. Установка Git

Основой интерфейс для работы с **Git**-ом является консоль/терминал.

Установка **Git**:

### - Windows 

Переходим по этой [***ссылке***](https://git-scm.com/download/win), выбираем под вашу ОС (32 или 64 битную), скачиваем и устанавливаем.

### - MacOS
![MaxOs install](/MacOS_install.png)

### - Linux (**Ubuntu, ArchLinx**)
**Debian или Ubuntu**  

`sudo apt install git`

### **ArchLinux**  

`sudo pacman -S git`
	
## 2. Настройка Git 

Вы установили себе Git и можете им пользоваться. Давайте теперь его настроим, чтобы когда вы создавали commit, указывался автор, кто его создал. Выполните следующие команды, чтобы git узнал ваше имя и электронную почту. Если git уже установлен, можете переходить к разделу окончания строк.

**Выполнить:**  
`git config --global user.name "Your Name"`  
и  
`git config --global user.email "your_email@whatever.com"`

### Параметры установки окончания строк
**Для пользователей** ***Unix/Mac***

**Выполнить:**  
`git config --global core.autocrlf input`  
и  
`git config --global core.safecrlf warn`
	
**Для пользователей** ***Windows***

**Выполнить:**

`git config --global core.autocrlf input`       
и  
`git config --global core.safecrlf warn`

## 3. Создание репозитория

Чтобы создать git репозиторий из каталога, выполните команду *git init* в этом каталоге.

**Выполните:**

`git init`	
	
## 4. Добавить файлы или новые файлы в репозиторий

Теперь давайте добавим в репозиторий страницу «Hello, World» - hello.html.

**Выполните:**

 `git add hello.html`  
 и  
 `git commit -m "First Commit"`
	
где "First commit" - Коммит - Название(Комментарий к) точки сохранения).

## 5. Проверка текущего состояния репозитория

Используйте команду *git status*, чтобы проверить текущее состояние репозитория.

**Выполните:**

`git status`	
	
Команда проверки состояния сообщит, что коммитить нечего. Это означает, что в репозитории хранится текущее состояние рабочего каталога, и нет никаких изменений, ожидающих записи.

Команда *git status*, необходима, чтобы продолжать отслеживать состояние репозитория и рабочего каталога.

## 6. Добавление изменений

Если вы изменили файлы или добавили новые файлы, то набрав команду *git status* вы можете увидить следующий результат:  

      git status  
      On branch master  
      Changes not staged for commit:  
      (use "git add <file>..." to update what will be committed)  
      (use "git checkout -- <file>..." to discard changes in working directory)  
      
      modified:   hello.html  
      
      no changes added to commit (use "git add" and/or "git commit -a")"

Первое, что нужно заметить, это то, что **git** знает, что файл *hello.html* был изменен, но при этом эти изменения еще не зафиксированы в репозитории.

Также обратите внимание на то, что сообщение о состоянии дает вам подсказку о том, что нужно делать дальше. Если вы хотите добавить эти изменения в репозиторий, используйте команду *"git add"*. В противном случае используйте команду *"git сheckout"* для отмены изменений.

**Добавим изменения**

Дадим команду **git** проиндексировать изменения.

***Выполнить:***

`git add hello.html`

Изменения файла *hello.html* были проиндексированы. Это означает, что **git** теперь знает об изменении, но изменение пока не перманентно (читай, навсегда) записано в репозиторий. Следующий коммит будет включать в себя проиндексированные изменения.

***Если вы решили, что не хотите коммитить изменения, команда состояния напомнит вам о том, что с помощью команды **"git reset"** можно снять индексацию этих изменений.***

Отдельный шаг индексации в **git** позволяет вам продолжать вносить изменения в рабочий каталог, а затем, в момент, когда вы захотите взаимодействовать с версионным контролем, **git** позволит записать изменения в малых коммитах, которые фиксируют то, что вы сделали.

Предположим, что вы отредактировали три файла *(a.html, b.html, и c.html)*. Теперь вы хотите закоммитить все изменения, при этом чтобы изменения в *"a.html"* и *"b.html"* были одним коммитом, в то время как изменения в *"c.html"* логически не связаны с первыми двумя файлами и должны идти отдельным коммитом.

В теории, вы можете сделать следующее:

`git add a.html`  
Затем  
`git add b.html`

Затем

`git commit -m "Changes for a and b"`

Затем  
`git add c.html` 
	
И наконец  

`git commit -m "Unrelated change to c"`
	
Разделяя индексацию и коммит, вы имеете возможность с легкостью настроить, что идет в какой коммит.



Давайте обозначим категории файлов, которые вообще можно добавлять. Будем использовать те же обозначения, что и в выводе команды git status -s:

M - (modified) отслеживаемые, изменились с прошлого коммита, еще не добавлены
D - (deleted) отслеживаемые, удалены после прошлого коммита, еще не добавлены
? - (untracked) неотслеживаемые, не запрещены к добавлению
! - (ignored) неотслеживаемые, запрещены к добавлению (например, в .gitignore)
Параметры и аргументы

Первое различие  — в том, что . — это путь (аргумент), а всё остальное — параметры. Те и другие не исключают друг друга и возможны их сочетания.
Использование абсолютных :/ и относительных . путей с командой add

Путь . обозначает текущую директорию, т.е. ту, в которой была запущена команда.

    Начиная с Git версии 2.0, поведение команды add приведено в соответствие с поведением commit и других комманд. Теперь . обозначает не всю рабочую область (working tree), а текущий путь в этой области.

Таким образом, если вы выполняете команду add не в корневой директории проекта (той, где лежит .git/), то будет обработано содержимое только текущей директории.

Чтобы явным образом дать указание Git работать со всей рабочей областью, используйте :/:

# работает одинаково из любой директории, добавляет всю рабочую область
git add :/

# путь относительно корневой директории
git add :/path/to/files/

# работает только в текущей директории
cd test
git add .
# эквивалентно этому:
git add :/test

# путь относительно текущей директории
cd test
git add ./path
# эквивалентно этому:
git add :/test/path

Если не указан никакой путь к добавляемым файлам, то большинство команд работает во всей рабочей области, а git add и git add --no-all просто не работают.
Сводная таблица

сводная таблица
О функционале команд подробно

git add .
git add '*'

Git версии 2.0+ просматривает текущую папку и добавляет файлы M, D, ?.
Git версии 1.х просматривает всю рабочую область и добавляет файлы M, D.

Если '*' дается в кавычках, то обрабатывать его будет Git и это эквивалентно git add .. Исключение: из-под cmd.exe git add '*' не сработает, используйте git add . или git add *.

git add --no-all :/
git add --ignore-removal :/

Эта команда в Git v. 2.0+ работает как git add . в Git v. 1.x, то есть добавляет измененные и новые файлы M, ? во всей рабочей области. Для этой команды обязательно указывать путь.

git add --no-all . #добавляет измененные и новые файлы в *текущей директории*
git add --no-all path1/ path2/ # добавляет измененные и новые файлы в путях *относительно текущей директории*

git add -u
git add -update

Git обновляет (update) статус уже отслеживаемых файлов т.е. M, D.

git add -A
git add --all
git add --no-ignore-removal

Эти варианты эквивалентны и добавляют M, D, ?.

Без точки — из всей рабочей области:

git add -A = git add -A :/ = git add :/ + git add -u

С точкой — только текущий путь:

git add -A . = git add . + git add -u .

 git add *

    Этот синтаксис лучше не использовать, и вот почему:

При этой команде shell (или bash или другая командная оболочка) просматривает рабочую область и отдает Git список файлов на добавление. Система сработает таким образом, что будут найдены абсолютно все не-скрытые файлы, находящиеся в заданном корне. Вы можете посмотреть на этот список, выполнив echo *. ( Исключение: из-под cmd.exe git add * работает так же как git add '*' на shell/bash. )

Произойдет следующее (здесь мы видим сразу несколько причин не использовать add *):

    Добавятся не изменившиеся с прошлого коммита файлы. Git спокойно и молча "прожует" этот запрос, не влияющий на индекс.
    Будут добавлены в индекс файлы в не-скрытых папках M,?.
    Не будут добавлены файлы в скрытых папках. .M, .?
    Не будут добавлены удаленные файлы D.
    Если будут захвачены игнорируемые файлы !, то будет попытка их добавить. Git отменит всю операцию и покажет сообщение об ошибке.

Зачем столько способов

Разнообразие параметров (-u, -A, --no-all) нужно для того, чтобы можно было добавлять разные группы файлов. Конкретно --no-all . было добавлено для того, чтобы реализовывать старое поведение add . в версиях 1.х.

Похоже, что несмотря на это, Git не позволяет добавлять конкретные группы файлов одной командой (см. сводную таблицу в начале).

Тонкости в использовании . и :/ нужны для того, чтобы каждую команду можно было выполнять как на всю рабочую область, так и на конкретную подпапку.


## 7. История
**Git** позволяет просматривать историю проекта.

Получение списка произведенных изменений — функция команды **"git log"**.
Выполните:

`git log`

Вы увидите…  
**Результат:**

      $ git log
      commit fa3c1411aa09441695a9e645d4371e8d749da1dc
      Author: Alexander Shvets <alex@githowto.com>
      Date:   Wed Mar 9 10:27:54 2011 -0500

      Added HTML header

      commit 8c3228730ed03116815a5cc682e8105e7d981928
      Author: Alexander Shvets <alex@githowto.com>
      Date:   Wed Mar 9 10:27:54 2011 -0500

      Added standard HTML page tags

      commit 43628f779cb333dd30d78186499f93638107f70b
      Author: Alexander Shvets <alex@githowto.com>
      Date:   Wed Mar 9 10:27:54 2011 -0500

            Added h1 tag

      commit 911e8c91caeab8d30ad16d56746cbd6eef72dc4c
      Author: Alexander Shvets <alex@githowto.com>
      Date:   Wed Mar 9 10:27:54 2011 -0500

         First Commit

Вот список всех четырех коммитов в репозиторий, которые мы успели совершить.
### Однострочная история

Вы полностью контролируете то, что отображает ***log***,  например, нравится однострочный формат:
Выполните:

`git log --pretty=oneline`

Вы увидите…
### Результат:

      $ git log --pretty=oneline
      fa3c1411aa09441695a9e645d4371e8d749da1dc  Added HTML header
      8c3228730ed03116815a5cc682e8105e7d981928  Added standard HTML page tags
      43628f779cb333dd30d78186499f93638107f70b  Added h1 tag
      911e8c91caeab8d30ad16d56746cbd6eef72dc4c First Commit

### **Контроль отображения записей**

Есть много вариантов выбора, какие элементы отображаются в логе. Поиграйте со следующими параметрами:

`git log --pretty=oneline --max-count=2`  
`git log --pretty=oneline --since='5 minutes ago`  
`git log --pretty=oneline --until='5 minutes ago`  
`git log --pretty=oneline --author=<your name>`  
`git log --pretty=oneline --all`  

В unix-системах доступна справочная страница `man git log`.

Для просмотра изменений, сделанных за последнюю неделю, от автора "alex" `--author=alex`

`git log --all --pretty=format:"%h %cd %s (%an)" --since='7 days ago'`

Еще удобный вывод 
### **Выполните:**

`git log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short`

Результат:

      $ git log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short
      * fa3c141 2011-03-09 |  Added HTML header (HEAD, master) [Alexander Shvets]
      * 8c32287 2011-03-09 |  Added standard HTML page tags [Alexander Shvets]
      * 43628f7 2011-03-09 |  Added h1 tag [Alexander Shvets]
      * 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

Давайте рассмотрим его в деталях:

    --pretty="..." — определяет формат вывода.
    %h — укороченный хэш коммита
    %d — дополнения коммита («головы» веток или теги)
    %ad — дата коммита
    %s — комментарий
    %an — имя автора
    --graph — отображает дерево коммитов в виде ASCII-графика
    --date=short — сохраняет формат даты коротким и симпатичным

Таким образом, каждый раз, когда вы захотите посмотреть лог, вам придется много печатать. К счастью, мы узнаем о **git** ***алиасах*** далее.
## **8. Алиасы**
Как настраивать алиасы и шорткаты для команд **git**

### Общие алиасы

Для пользователей **Windows**  
**Выполнить:**

`git config --global alias.co checkout`  
`git config --global alias.ci commit`  
`git config --global alias.st status`  
`git config --global alias.br branch`   
`git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short`  
`git config --global alias.type 'cat-file -t`  
`git config --global alias.dump 'cat-file -p`    

Также, для пользователей **Unix/Mac**:

*git status*, *git add*, *git commit*, *git checkout* — общие команды, для которых полезно иметь сокращения.

Добавьте следующее в файл *.gitconfig* в вашем *$HOME* каталоге.
Файл: *.gitconfig*

      [alias]
      co = checkout
      ci = commit
      st = status
      br = branch
      hist = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
      type = cat-file -t
      dump = cat-file -p

## 9. Получение старых версий
Как возвращать рабочий каталог к любому предыдущему состоянию.

Возвращаться назад в историю очень просто. Команда ***checkout*** скопирует любой снимок из репозитория в рабочий каталог.

Получите хэши предыдущих версий

      * fa3c141 2011-03-09 | Added HTML header (HEAD, master) [Alexander Shvets]
      * 8c32287 2011-03-09 | Added standard HTML page tags [Alexander Shvets]
      * 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
      * 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

Изучите данные лога и найдите хэш для первого коммита. Он должен быть в последней строке данных. Используйте этот хэш-код (достаточно первых 7 знаков) в команде ниже. Затем проверьте содержимое файла *hello.html*.  
**Выполните:**

`git checkout <hash>`  
`cat hello.html`

Примечание: Многие команды зависят от хэшевых значений в репозитории. Поскольку ваши хеш-значения будут отличаться от представленных в примере, когда вы видите что-то вроде <hash> или <treehash> в команде, подставьте необходимое значение хэш для вашего репозитория.

**Результат:**

`git checkout 911e8c9`  

      Note: checking out '911e8c9'.

      You are in 'detached HEAD' state. You can look around, make experimental
      changes and commit them, and you can discard any commits you make in this
      state without impacting any branches by performing another checkout.

      If you want to create a new branch to retain commits you create, you may
      do so (now or later) by using -b with the checkout command again. Example:

`git checkout -b new_branch_name`

      HEAD is now at 911e8c9... First Commit
`cat hello.html`  

      Hello, World

Выходные данные команды **checkout** очень хорошо объясняют ситуацию. Старые версии **git** будут ругаться, что не расположены в локальной ветке. В любом случае, сейчас об этом не беспокойтесь.

Обратите внимание на то, что содержимое файла *hello.html* является значением по умолчанию.

Вернитесь к последней версии в ветке master
**Выполните:**

`git checkout master`  
`cat hello.html`

Результат:

$ git checkout master
Previous HEAD position was 911e8c9... First Commit
Switched to branch 'master'
$ cat hello.html
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

«master» — имя ветки по умолчанию. Переключая имена веток, вы попадаете на последнюю версию выбранной ветки.

13. Создание тегов версий
ads via Carbon
Limited time offer: Get 10 free Adobe Stock images.
ads via Carbon
Цели

    Узнать, как создавать теги для коммитов для использования в будущем

Давайте назовем текущую версию страницы hello первой (v1).
01
Создайте тег первой версии
Выполните:

git tag v1

Теперь текущая версия страницы называется v1.
02
Теги для предыдущих версий

Давайте создадим тег для версии, которая идет перед текущей версией и назовем его v1-beta. В первую очередь нам надо переключиться на предыдущую версию. Вместо поиска по хэшу, мы будем использовать ^, обозначающее «родитель v1».

Если обозначение v1^ вызывает у вас какие-то проблемы, попробуйте также v1~1, указывающее на ту же версию. Это обозначение можно определить как «первую версию предшествующую v1».
Выполните:

git checkout v1^
cat hello.html

Результат:

$ git checkout v1^
Note: checking out 'v1^'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at 8c32287... Added standard HTML page tags
$ cat hello.html
<html>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

Это версия c тегами <html> и <body>, но еще пока без <head>. Давайте сделаем ее версией v1-beta.
Выполните:

git tag v1-beta

03
Переключение по имени тега

Теперь попробуйте попереключаться между двумя отмеченными версиями.
Выполните:

git checkout v1
git checkout v1-beta

Результат:

$ git checkout v1
Previous HEAD position was 8c32287... Added standard HTML page tags
HEAD is now at fa3c141... Added HTML header
$ git checkout v1-beta
Previous HEAD position was fa3c141... Added HTML header
HEAD is now at 8c32287... Added standard HTML page tags

04
Просмотр тегов с помощью команды tag

Вы можете увидеть, какие теги доступны, используя команду git tag.
Выполните:

git tag

Результат:

$ git tag
v1
v1-beta

05
Просмотр Тегов в логах

Вы также можете посмотреть теги в логе.
Выполните:

git hist master --all

Результат:

$ git hist master --all
* fa3c141 2011-03-09 | Added HTML header (v1, master) [Alexander Shvets]
* 8c32287 2011-03-09 | Added standard HTML page tags (HEAD, v1-beta) [Alexander Shvets]
* 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
* 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

Вы можете видеть теги (v1 и v1-beta) в логе вместе с именем ветки (master). Кроме того HEAD показывает коммит, на который вы переключились (на данный момент это v1-beta).

14. Отмена локальных изменений (до индексации)
ads via Carbon
Limited time offer: Get 10 free Adobe Stock images.
ads via Carbon
Цели

    Научиться отменять изменения в рабочем каталоге

01
Переключитесь на ветку Master

Убедитесь, что вы находитесь на последнем коммите ветки master, прежде чем продолжить работу.
Выполните:

git checkout master

02
Измените hello.html

Иногда случается, что вы изменили файл в рабочем каталоге, и хотите отменить последние коммиты. С этим справится команда checkout.

Внесите изменение в файл hello.html в виде нежелательного комментария.
Файл: hello.html

<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
    <!-- This is a bad comment.  We want to revert it. -->
  </body>
</html>

03
Проверьте состояние

Сначала проверьте состояние рабочего каталога.
Выполните:

git status

Результат:

$ git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#   modified:   hello.html
#
no changes added to commit (use "git add" and/or "git commit -a")

Мы видим, что файл hello.html был изменен, но еще не проиндексирован.
04
Отмена изменений в рабочем каталоге

Используйте команду checkout для переключения в версию файла hello.html в репозитории.
Выполните:

git checkout hello.html
git status
cat hello.html

Результат:

$ git checkout hello.html
$ git status
# On branch master
nothing to commit (working directory clean)
$ cat hello.html
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

Команда status показывает нам, что не было произведено никаких изменений, не зафиксированных в рабочем каталоге. И «нежелательный комментарий» больше не является частью содержимого файла.

15. Отмена проиндексированных изменений (перед коммитом)
ads via Carbon
Limited time offer: Get 10 free Adobe Stock images.
ads via Carbon
Цели

    Научиться отменять изменения, которые были проиндексированы

01
Измените файл и проиндексируйте изменения

Внесите изменение в файл hello.html в виде нежелательного комментария
Файл: hello.html

<html>
  <head>
    <!-- This is an unwanted but staged comment -->
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

Проиндексируйте это изменение.
Выполните:

git add hello.html

02
Проверьте состояние

Проверьте состояние нежелательного изменения.
Выполните:

git status

Результат:

$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#   modified:   hello.html
#

Состояние показывает, что изменение было проиндексировано и готово к коммиту.
03
Выполните сброс буферной зоны

К счастью, вывод состояния показывает нам именно то, что мы должны сделать для отмены индексации изменения.
Выполните:

git reset HEAD hello.html

Результат:

$ git reset HEAD hello.html
Unstaged changes after reset:
M   hello.html

Команда reset сбрасывает буферную зону к HEAD. Это очищает буферную зону от изменений, которые мы только что проиндексировали.

Команда reset (по умолчанию) не изменяет рабочий каталог. Поэтому рабочий каталог все еще содержит нежелательный комментарий. Мы можем использовать команду checkout из предыдущего урока, чтобы удалить нежелательные изменения в рабочем каталоге.
04
Переключитесь на версию коммита
Выполните:

git checkout hello.html
git status

Результат:

$ git status
# On branch master
nothing to commit (working directory clean)

Наш рабочий каталог опять чист.

16. Отмена коммитов
ads via Carbon
Adobe Creative Cloud for Teams starting at $33.99 per month.
ads via Carbon
Цели

    Научиться отменять коммиты в локальный репозиторий.

01
Отмена коммитов

Иногда вы понимаете, что новые коммиты являются неверными, и хотите их отменить. Есть несколько способов решения этого вопроса, здесь мы будем использовать самый безопасный.

Мы отменим коммит путем создания нового коммита, отменяющего нежелательные изменения.
02
Измените файл и сделайте коммит

Измените файл hello.html на следующий.
Файл: hello.html

<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
    <!-- This is an unwanted but committed change -->
  </body>
</html>

Выполните:

git add hello.html
git commit -m "Oops, we didn't want this commit"

03
Сделайте коммит с новыми изменениями, отменяющими предыдущие

Чтобы отменить коммит, нам необходимо сделать коммит, который удаляет изменения, сохраненные нежелательным коммитом.
Выполните:

git revert HEAD

Перейдите в редактор, где вы можете отредактировать коммит-сообщение по умолчанию или оставить все как есть. Сохраните и закройте файл. Вы увидите…
Результат:

$ git revert HEAD --no-edit
[master 45fa96b] Revert "Oops, we didn't want this commit"
 1 files changed, 1 insertions(+), 1 deletions(-)

Так как мы отменили самый последний произведенный коммит, мы смогли использовать HEAD в качестве аргумента для отмены. Мы можем отменить любой произвольной коммит в истории, указав его хэш-значение.

Примечание: Команду --no-edit можно проигнорировать. Она была необходима для генерации выходных данных без открытия редактора.
04
Проверьте лог

Проверка лога показывает нежелательные и отмененные коммиты в наш репозиторий.
Выполните:

git hist

Результат:

$ git hist
* 45fa96b 2011-03-09 | Revert "Oops, we didn't want this commit" (HEAD, master) [Alexander Shvets]
* 846b90c 2011-03-09 | Oops, we didn't want this commit [Alexander Shvets]
* fa3c141 2011-03-09 | Added HTML header (v1) [Alexander Shvets]
* 8c32287 2011-03-09 | Added standard HTML page tags (v1-beta) [Alexander Shvets]
* 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
* 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

Эта техника будет работать с любым коммитом (хотя, возможно, возникнут конфликты). Она безопасна в использовании даже в публичных ветках удаленных репозиториев.
05
Далее

Далее давайте посмотрим на технику, которая может быть использована для удаления последних коммитов из истории репозитория.

17. Удаление коммитов из ветки
ads via Carbon
Adobe Creative Cloud for Teams starting at $33.99 per month.
ads via Carbon
Цели

    Научиться удалять самые последние коммиты из ветки

Revert из предыдущего раздела является мощной командой, которая позволяет отменить любые коммиты в репозиторий. Однако, и оригинальный и «отмененный» коммиты видны в истории ветки (при использовании команды git log).

Часто мы делаем коммит, и сразу понимаем, что это была ошибка. Было бы неплохо иметь команду «возврата», которая позволила бы нам сделать вид, что неправильного коммита никогда и не было. Команда «возврата» даже предотвратила бы появление нежелательного коммита в истории git log.
01
Команда reset

Мы уже видели команду reset и использовали ее для согласования буферной зоны и выбранного коммита (мы использовали коммит HEAD в нашем предыдущем уроке).

При получении ссылки на коммит (т.е. хэш, ветка или имя тега), команда reset…

    Перепишет текущую ветку, чтобы она указывала на нужный коммит
    Опционально сбросит буферную зону для соответствия с указанным коммитом
    Опционально сбросит рабочий каталог для соответствия с указанным коммитом

02
Проверьте нашу историю

Давайте сделаем быструю проверку нашей истории коммитов.
Выполните:

git hist

Результат:

$ git hist
* 45fa96b 2011-03-09 | Revert "Oops, we didn't want this commit" (HEAD, master) [Alexander Shvets]
* 846b90c 2011-03-09 | Oops, we didn't want this commit [Alexander Shvets]
* fa3c141 2011-03-09 | Added HTML header (v1) [Alexander Shvets]
* 8c32287 2011-03-09 | Added standard HTML page tags (v1-beta) [Alexander Shvets]
* 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
* 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

Мы видим, что два последних коммита в этой ветке - «Oops» и «Revert Oops». Давайте удалим их с помощью сброса.
03
Для начала отметьте эту ветку

Но прежде чем удалить коммиты, давайте отметим последний коммит тегом, чтобы потом можно было его найти.
Выполните:

git tag oops

04
Сброс коммитов к предшествующим коммиту Oops

Глядя на историю лога (см. выше), мы видим, что коммит с тегом «v1» является коммитом, предшествующим ошибочному коммиту. Давайте сбросим ветку до этой точки. Поскольку ветка имеет тег, мы можем использовать имя тега в команде сброса (если она не имеет тега, мы можем использовать хэш-значение).
Выполните:

git reset --hard v1
git hist

Результат:

$ git reset --hard v1
HEAD is now at fa3c141 Added HTML header
$ git hist
* fa3c141 2011-03-09 | Added HTML header (HEAD, v1, master) [Alexander Shvets]
* 8c32287 2011-03-09 | Added standard HTML page tags (v1-beta) [Alexander Shvets]
* 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
* 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

Наша ветка master теперь указывает на коммит v1, а коммитов Oops и Revert Oops в ветке уже нет. Параметр --hard указывает, что рабочий каталог должен быть обновлен в соответствии с новым head ветки.
05
Ничего никогда не теряется

Что же случается с ошибочными коммитами? Оказывается, что коммиты все еще находятся в репозитории. На самом деле, мы все еще можем на них ссылаться. Помните, в начале этого урока мы создали для отмененного коммита тег «oops». Давайте посмотрим на все коммиты.
Выполните:

git hist --all

Результат:

$ git hist --all
* 45fa96b 2011-03-09 | Revert "Oops, we didn't want this commit" (oops) [Alexander Shvets]
* 846b90c 2011-03-09 | Oops, we didn't want this commit [Alexander Shvets]
* fa3c141 2011-03-09 | Added HTML header (HEAD, v1, master) [Alexander Shvets]
* 8c32287 2011-03-09 | Added standard HTML page tags (v1-beta) [Alexander Shvets]
* 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
* 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

Мы видим, что ошибочные коммиты не исчезли. Они все еще находятся в репозитории. Просто они отсутствуют в ветке master. Если бы мы не отметили их тегами, они по-прежнему находились бы в репозитории, но не было бы никакой возможности ссылаться на них, кроме как при помощи их хэш имен. Коммиты, на которые нет ссылок, остаются в репозитории до тех пор, пока не будет запущен сборщик мусора.
06
Опасность сброса

Сброс в локальных ветках, как правило, безопасен. Последствия любой «аварии» как правило, можно восстановить простым сбросом с помощью нужного коммита.

Однако, если ветка «расшарена» на удаленных репозиториях, сброс может сбить с толку других пользователей ветки.
18. Удаление тега oops
ads via Carbon
Limited time offer: Get 10 free Adobe Stock images.
ads via Carbon
Цели

    Удаление тега oops (уборка)

01
Удаление тега oops

Тег oops свою функцию выполнил. Давайте удалим его и коммиты, на которые он ссылался, сборщиком мусора.
Выполните:

git tag -d oops
git hist --all

Результат:

$ git tag -d oops
Deleted tag 'oops' (was 45fa96b)
$ git hist --all
* fa3c141 2011-03-09 | Added HTML header (HEAD, v1, master) [Alexander Shvets]
* 8c32287 2011-03-09 | Added standard HTML page tags (v1-beta) [Alexander Shvets]
* 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
* 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

Тег «oops» больше не будет отображаться в репозитории.
19. Внесение изменений в коммиты
ads via Carbon
Limited time offer: Get 10 free Adobe Stock images.
ads via Carbon
Цели

    Научиться изменять существующие коммиты

01
Измените страницу, а затем сделайте коммит

Добавьте в страницу комментарий автора.
Файл: hello.html

<!-- Author: Alexander Shvets -->
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

Выполните:

git add hello.html
git commit -m "Add an author comment"

02
Ой... необходим email

После совершения коммита вы понимаете, что любой хороший комментарий должен включать электронную почту автора. Обновите страницу hello, включив в нее email.
Файл: hello.html

<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

03
Измените предыдущий коммит

Мы действительно не хотим создавать отдельный коммит только ради электронной почты. Давайте изменим предыдущий коммит, включив в него адрес электронной почты.
Выполните:

git add hello.html
git commit --amend -m "Add an author/email comment"

Результат:

$ git add hello.html
$ git commit --amend -m "Add an author/email comment"
[master 6a78635] Add an author/email comment
 1 files changed, 2 insertions(+), 1 deletions(-)

04
Просмотр истории
Выполните:

git hist

Результат:

$ git hist
* 6a78635 2011-03-09 | Add an author/email comment (HEAD, master) [Alexander Shvets]
* fa3c141 2011-03-09 | Added HTML header (v1) [Alexander Shvets]
* 8c32287 2011-03-09 | Added standard HTML page tags (v1-beta) [Alexander Shvets]
* 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
* 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

Мы можем увидеть, что оригинальный коммит «автор» заменен коммитом «автор/email». Этого же эффекта можно достичь путем сброса последнего коммита в ветке, и повторного коммита новых изменений.
24. Создание ветки
ads via Carbon
Students and Teachers, save up to 60% on Adobe Creative Cloud.
ads via Carbon
Цели

    Научиться создавать локальную ветку в репозитории

Пора сделать наш hello world более выразительным. Так как это может занять некоторое время, лучше переместить эти изменения в отдельную ветку, чтобы изолировать их от изменений в ветке master.
01
Создайте ветку

Давайте назовем нашу новую ветку «style».
Выполните:

git checkout -b style
git status

Примечание: git checkout -b <имяветки> является шорткатом для git branch <имяветки> за которым идет git checkout <имяветки>.

Обратите внимание, что команда git status сообщает о том, что вы находитесь в ветке «style».
02
Добавьте файл стилей style.css
Выполните:

touch lib/style.css

Файл: lib/style.css

h1 {
  color: red;
}

Выполните:

git add lib/style.css
git commit -m "Added css stylesheet"

03
Измените основную страницу

Обновите файл hello.html, чтобы использовать стили style.css.
Файл: lib/hello.html

<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
    <link type="text/css" rel="stylesheet" media="all" href="style.css" />
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

Выполните:

git add lib/hello.html
git commit -m "Hello uses style.css"

04
Измените index.html

Обновите файл index.html, чтобы он тоже использовал style.css
Файл: index.html

<html>
  <head>
    <link type="text/css" rel="stylesheet" media="all" href="lib/style.css" />
  </head>
  <body>
    <iframe src="lib/hello.html" width="200" height="200" />
  </body>
</html>

Выполните:

git add index.html
git commit -m "Updated index.html"

05
Далее

Теперь у нас есть новая ветка под названием style с 3 новыми коммитами. Далее мы узнаем, как осуществлять навигацию и переключаться между ветками.
25. Навигация по веткам
ads via Carbon
Limited time offer: Get 10 free Adobe Stock images.
ads via Carbon
Цели

    Научиться перемещаться между ветками репозитория

Теперь в вашем проекте есть две ветки:
Выполните:

git hist --all

Результат:

$ git hist --all
* 07a2a46 2011-03-09 | Updated index.html (HEAD, style) [Alexander Shvets]
* 649d26c 2011-03-09 | Hello uses style.css [Alexander Shvets]
* 1f3cbd2 2011-03-09 | Added css stylesheet [Alexander Shvets]
* 8029c07 2011-03-09 | Added index.html. (master) [Alexander Shvets]
* 567948a 2011-03-09 | Moved hello.html to lib [Alexander Shvets]
* 6a78635 2011-03-09 | Add an author/email comment [Alexander Shvets]
* fa3c141 2011-03-09 | Added HTML header (v1) [Alexander Shvets]
* 8c32287 2011-03-09 | Added standard HTML page tags (v1-beta) [Alexander Shvets]
* 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
* 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

01
Переключение на ветку Master

Просто используйте команду git checkout для переключения между ветками.
Выполните:

git checkout master
cat lib/hello.html

Результат:

$ git checkout master
Switched to branch 'master'
$ cat lib/hello.html
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

Сейчас мы находимся на ветке Master. Это заметно по тому, что файл hello.html не использует стили style.css.
02
Вернемся к ветке «style».
Выполните:

git checkout style
cat lib/hello.html

Результат:

$ git checkout style
Switched to branch 'style'
$ cat lib/hello.html
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
    <link type="text/css" rel="stylesheet" media="all" href="style.css" />
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

Содержимое lib/hello.html подтверждает, что мы вернулись в ветку style.
	
