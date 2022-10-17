
# Git?

**Git**  — мощная и сложная распределенная система контроля версий. Понимание всех возможностей git открывает для разработчика новые горизонты в управлении исходным кодом. Самый верный способ обучиться владению Git — испытать его своими руками.

## Установка Git

Основой интерфейс для работы с **Git**-ом является консоль/терминал.

Установка **Git**:

### - Windows 

Переходим по этой [***ссылке***](https://git-scm.com/download/win), выбираем под вашу ОС (32 или 64 битную), скачиваем и устанавливаем.

### - MacOS
![MaxOs install](/MacOS_install.png)

### - Linux (**Ubuntu, ArchLinx**)
**Debian или Ubuntu**  

	sudo apt install git

**ArchLinux**  

	sudo pacman -S git
	
## Настройка Git 

Вы установили себе Git и можете им пользоваться. Давайте теперь его настроим, чтобы когда вы создавали commit, указывался автор, кто его создал. Выполните следующие команды, чтобы git узнал ваше имя и электронную почту. Если git уже установлен, можете переходить к разделу окончания строк.

**Выполнить:**
	git config --global user.name "Your Name"
	git config --global user.email "your_email@whatever.com"

## Параметры установки окончания строк
**Для пользователей** ***Unix/Mac***

**Выполнить:**  

	git config --global core.autocrlf input  

	git config --global core.safecrlf warn
	
**Для пользователей** ***Windows***

**Выполнить:**

	git config --global core.autocrlf input       
  

	git config --global core.safecrlf warn
	
	
