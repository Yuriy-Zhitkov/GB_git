# GIT - основные команды

GIT - представляет собой распределённую систему управления версиями.
[Официальное руководство пользователя](https://git-scm.com/book/ru)

## Содержание
- SETUP - основные команды
- SETUP & INIT - основные команды
- STAGE & SNAPSHOT - основные команды
- BRANCH & MERGE - основные команды

## 1. SETUP - основные команды
Настройка информации пользователя, используемой во всех локальных репозиториях:  
- установите имя, которое можно будет идентифицировать при просмотре истории версий
```sh
git config --global user.name “[firstname lastname]”
```
  
- установите адрес электронной почты, который будет связан с каждым маркером истории
```sh
git config --global user.email “[valid-email]”
```
  
- установить автоматическую раскраску командной строки для Git для удобства просмотра
```sh
git config --global color.ui auto
```

## 2. SETUP & INIT - основные команды
Настройка информации о пользователе, инициализация и клонирование репозиториев:
- инициализировать существующий каталог как репоиторий Git
```sh
git init
```
  
- получить весь репозиторий из размещенного места через URL-адрес
```sh
git clone [url]
```

## 3. STAGE & SNAPSHOT - основные команды
Работа со снапшотами и репозиторием Git.
- показывать измененные файлы в рабочем каталоге, подготовленные для вашего следующего коммита
```sh
git status
```
  
- добавьте файл, как он выглядит сейчас, в ваш следующий коммит (этап)
```sh
git add [file]
```
  
- удалить файл, сохранив изменения в рабочем каталоге
```sh
git reset [file]
```
  
- разница того, что изменено, но не поставлено в репозиторий
```sh
git diff
```
  
- разница между тем, что поставлено в репозиторий, но еще не находится в коммите
```sh
git diff --staged
```
  
- зафиксируйте подготовленные файлы как новый коммит
```sh
git commit -m “[descriptive message]”
```

## 4. BRANCH & MERGE - основные команды
Изолирование работы в ветках, изменение контекста и интеграция изменений
- перечислите свои филиалы. * появится рядом с текущей активной веткой
```sh
git branch
```
  
- создать новую ветку в текущем коммите
```sh
git branch [branch-name]
```
  
- переименовать текущую ветку
```sh
git branch -M [new_name]
```

- переключитесь на другую ветку и проверьте ее в своем рабочем каталоге
```sh
git checkout
```
  
- объединить историю указанной ветки с текущей
```sh
git merge [branch]
```
  
- показать все коммиты в истории текущей ветки
```sh
git log
```

- показать все коммиты в виде строк
```sh
git log --oneline
```

- показать все коммиты в графическом представлении
```sh
git log --graph
```

## 5 REMOTE - удаленный репозиторий


- установить удаленный репозиторий по умолчанию
```sh
git remote add origin https://github.com/Yuriy-Zhitkov/GB_git.git
```

- сведения о ссылках на удаленном репозитории
```sh
git remote -v
```

- сведения о удаленном репозитории
```sh
git remote show [remote_repo_name]
```

- полный список удаленных ссылок
```sh
git ls-remote [remote_repo_name]
```

- загрузить файлы на удаленный репозиторий в ветку
```sh
git push -u origin main 
```

- скачать с удаленного репозитория
```sh
git pull
```

- клонировать удаленный репозиторий
```sh
git clone [remote_repo_url_or_ssh]
```

- удаление ветки в удаленном репозитории
```sh
git push origin --delete [branch_name]
```

## Разрешаем конфликт c удаленным репозиторием.
На удаленном и локальном репозитории существует конфликт.
При вводе команды `git push` и попытке загрузить файлы на удаленный репозиторий, появляется ошибка `! [rejected]        main -> main (fetch first)`.

Для разрешения конфликта необходимо загрузить файлы с удаленного репозитория с опцией `--rebase`
```sh
git pull --rebase
```

 После загрузки файлов разрешаем конфликт, выбирая нужные изменеия в файле, например, инструментами VSCode.

 Добавляем измененный файл в индекс и делаем коммит
 ```sh
git add [file_name]
git commit -m "Комментарий к коммиту"
 ```

Далее неоюбходимо завершить разрешение конфликта и отправить файлы в удаленный репозиторий
```sh
git rebase --continue
git push
```