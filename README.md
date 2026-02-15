# Git - Шпаргалка команд

## Инициализация и настройка

### Создание репозитория
```bash
git init                    # Создать новый репозиторий в текущей папке
git clone <url>             # Клонировать существующий репозиторий
```

### Настройка пользователя
```bash
git config --global user.name "Ваше Имя"
git config --global user.email "your.email@example.com"
git config --list           # Просмотр всех настроек
```

---

## Основные команды

### Проверка статуса
```bash
git status                  # Показать статус изменений
git status -s               # Краткий формат
```

### Добавление файлов
```bash
git add filename.txt        # Добавить конкретный файл
git add .                   # Добавить все изменения
git add *.swift             # Добавить все файлы с расширением .swift
git add folder/             # Добавить все файлы из папки
```

### Создание коммита
```bash
git commit -m "Описание изменений"
git commit -am "Описание"   # add + commit (только для отслеживаемых файлов)
git commit --amend          # Изменить последний коммит
```

### Просмотр истории
```bash
git log                     # Полная история коммитов
git log --oneline           # Краткая история (по одной строке)
git log --graph             # С визуализацией веток
git log --all --graph       # Все ветки с графом
git log -n 5                # Последние 5 коммитов
git log --author="Name"     # Коммиты конкретного автора
```

---

## Работа с ветками

### Создание и переключение
```bash
git branch                  # Список всех веток
git branch new-feature      # Создать новую ветку
git checkout new-feature    # Переключиться на ветку
git checkout -b new-branch  # Создать ветку и сразу переключиться
git switch main             # Переключиться на ветку (новый синтаксис)
git switch -c new-branch    # Создать и переключиться (новый синтаксис)
```

### Слияние и удаление
```bash
git merge feature-branch    # Слить ветку в текущую
git branch -d branch-name   # Удалить ветку (безопасно)
git branch -D branch-name   # Принудительно удалить ветку
```

---

## Работа с удаленным репозиторием

### Добавление удаленного репозитория
```bash
git remote add origin <url>              # Добавить удаленный репозиторий
git remote -v                            # Посмотреть список удаленных репозиториев
git remote remove origin                 # Удалить удаленный репозиторий
git remote set-url origin <new-url>      # Изменить URL репозитория
```

### Отправка изменений
```bash
git push origin main                     # Отправить изменения в ветку main
git push -u origin main                  # Первый push с установкой upstream
git push origin feature-branch           # Отправить конкретную ветку
git push --all                           # Отправить все ветки
git push origin --delete branch-name     # Удалить ветку на удаленном репозитории
```

### Получение изменений
```bash
git pull origin main        # Скачать и слить изменения из main
git fetch                   # Скачать изменения без слияния
git fetch origin            # Скачать изменения с конкретного remote
```

---

## Отмена изменений

### Отмена в рабочей директории
```bash
git restore filename.txt    # Отменить изменения в файле
git restore .               # Отменить все изменения
git checkout -- filename    # Отменить изменения (старый синтаксис)
```

### Отмена в staging area
```bash
git restore --staged file   # Убрать файл из staging area
git reset HEAD file         # Убрать файл из staging (старый синтаксис)
```

### Отмена коммитов
```bash
git reset --soft HEAD~1     # Отменить последний коммит, изменения в staging
git reset --mixed HEAD~1    # Отменить коммит, изменения в working directory
git reset --hard HEAD~1     # Полностью удалить последний коммит (ОПАСНО!)
git revert <commit-hash>    # Создать новый коммит, отменяющий указанный
```

---

## Просмотр изменений

### Различия
```bash
git diff                    # Изменения в рабочей директории
git diff --staged           # Изменения в staging area
git diff HEAD               # Все изменения (staged + unstaged)
git diff branch1 branch2    # Различия между ветками
git diff commit1 commit2    # Различия между коммитами
```

### Просмотр файлов
```bash
git show <commit-hash>      # Показать изменения в коммите
git show HEAD               # Показать последний коммит
git show <commit>:file.txt  # Показать файл из конкретного коммита
```

---

## Полезные команды

### Временное сохранение изменений
```bash
git stash                   # Сохранить изменения в stash
git stash save "message"    # Сохранить с описанием
git stash list              # Список всех stash
git stash apply             # Применить последний stash
git stash apply stash@{0}   # Применить конкретный stash
git stash pop               # Применить и удалить stash
git stash drop              # Удалить последний stash
git stash clear             # Удалить все stash
```

### Очистка
```bash
git clean -n                # Показать, что будет удалено
git clean -f                # Удалить неотслеживаемые файлы
git clean -fd               # Удалить файлы и папки
```

### Игнорирование файлов
Создать файл `.gitignore`:
```
# Комментарий
*.log                       # Игнорировать все .log файлы
node_modules/               # Игнорировать папку
.DS_Store                   # Игнорировать системные файлы
!important.log              # НЕ игнорировать этот файл
build/                      # Игнорировать build директорию
```

### Теги
```bash
git tag                     # Список всех тегов
git tag v1.0.0              # Создать легковесный тег
git tag -a v1.0.0 -m "msg"  # Создать аннотированный тег
git push origin v1.0.0      # Отправить тег на remote
git push origin --tags      # Отправить все теги
git tag -d v1.0.0           # Удалить локальный тег
```
