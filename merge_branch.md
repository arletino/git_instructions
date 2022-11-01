Слияние

**Цели:**  
Научиться сливать две отличающиеся ветки для переноса изменений обратно в одну ветку.  
**Слияние веток**  
Слияние переносит изменения из двух веток в одну. Давайте вернемся к ветке *style* и сольем **master** с *style*.  
**Выполните:**  
`git checkout style`  
`git merge master`  
`git hist --all`  
**Результат:**  

    $ git checkout style  
        Switched to branch 'style'  
    $ git merge master  
        Merge made by recursive.  
        README |    1 +  
        1 files changed, 1 insertions(+), 0 deletions(-)  
        create mode 100644 README  
    $ git hist --all
        *   5813a3f 2011-03-09 | Merge branch 'master' into style (HEAD, style) [Alexander Shvets]
        |\  
        | * 6c0f848 2011-03-09 | Added README (master) [Alexander Shvets]
        * | 07a2a46 2011-03-09 | Updated index.html [Alexander Shvets]
        * | 649d26c 2011-03-09 | Hello uses style.css [Alexander Shvets]
        * | 1f3cbd2 2011-03-09 | Added css stylesheet [Alexander Shvets]
        |/  
        * 8029c07 2011-03-09 | Added index.html. [Alexander Shvets]
        * 567948a 2011-03-09 | Moved hello.html to lib [Alexander Shvets]
        * 6a78635 2011-03-09 | Add an author/email comment [Alexander Shvets]
        * fa3c141 2011-03-09 | Added HTML header (v1) [Alexander Shvets]
        * 8c32287 2011-03-09 | Added standard HTML page tags (v1-beta) [Alexander Shvets]
        * 43628f7 2011-03-09 | Added h1 tag [Alexander Shvets]
        * 911e8c9 2011-03-09 | First Commit [Alexander Shvets]

Путем периодического слияния ветки master с веткой *style* вы можете переносить из master любые изменения и поддерживать совместимость изменений *style* с изменениями в основной ветке.  
Однако, это делает графики коммитов действительно уродливыми. Позже мы рассмотрим возможность перебазирования, как альтернативы слиянию.