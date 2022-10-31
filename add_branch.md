

Создание ветки

Цель
Научиться создавать локальную ветку в репозитории

При внесении изменений, лучше переместить эти изменения в отдельную ветку, чтобы изолировать их от изменений в ветке master.

Создайте ветку

Давайте назовем нашу новую ветку «style».
Выполните:

git checkout -b style
git status

Примечание: git checkout -b <имяветки> является шорткатом для git branch <имяветки> за которым идет git checkout <имяветки>.

Обратите внимание, что команда git status сообщает о том, что вы находитесь в ветке «style».

Добавьте файл стилей style.css

Выполните:

touch lib/style.css

Выполните:

git add lib/style.css
git commit -m "Added css stylesheet"


Измените основную страницу и выполните

Выполните:

git add lib/hello.html
git commit -m "Hello uses style.css"