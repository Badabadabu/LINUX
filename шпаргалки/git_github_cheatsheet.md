# Git и GitHub - Шпаргалка

## 🚀 Основные команды Git

### Инициализация и настройка
```bash
git init                          # Инициализация репозитория
git config --global user.name "Имя"
git config --global user.email "email@example.com"
git config --list                 # Просмотр конфигурации
```

### Работа с файлами
```bash
git add .                         # Добавить все файлы в staging area
git add filename.txt              # Добавить конкретный файл
git commit -m "Описание изменений"  # Создать коммит
git commit -am "Сообщение"        # Добавить и закоммитить измененные файлы
```

### Просмотр статуса и истории
```bash
git status                        # Статус рабочей директории
git log                          # История коммитов
git log --oneline                # Краткая история
git log --graph                  # История с графиком
git diff                         # Изменения в файлах
git diff --staged                # Изменения в staging area
```

### Работа с ветками
```bash
git branch                       # Список веток
git branch branch-name           # Создать новую ветку
git checkout branch-name         # Переключиться на ветку
git checkout -b branch-name      # Создать и переключиться на ветку
git merge branch-name            # Слить ветку в текущую
git branch -d branch-name        # Удалить ветку
git branch -D branch-name        # Принудительно удалить ветку
```

### Удаленные репозитории
```bash
git remote add origin URL        # Добавить удаленный репозиторий
git remote -v                    # Просмотр удаленных репозиториев
git push origin branch-name      # Отправить изменения
git push -u origin main          # Первый push с установкой upstream
git pull origin branch-name      # Получить изменения
git fetch                        # Загрузить изменения без слияния
git clone URL                    # Клонировать репозиторий
```

## 📝 Работа с GitHub

### Создание репозитория
1. Зайти на GitHub.com
2. Кликнуть "New repository"
3. Заполнить название и описание
4. Выбрать публичный/приватный
5. Добавить README, .gitignore, лицензию (по желанию)

### Связывание локального репозитория с GitHub
```bash
git remote add origin https://github.com/username/repository.git
git branch -M main
git push -u origin main
```

### Pull Requests (PR)
1. Создать новую ветку для функции
2. Внести изменения и закоммитить
3. Запушить ветку на GitHub
4. Создать Pull Request через веб-интерфейс
5. Добавить описание изменений
6. Дождаться ревью и одобрения

### Fork и работа с чужими репозиториями
```bash
# 1. Сделать Fork через веб-интерфейс GitHub
# 2. Клонировать свой fork
git clone https://github.com/your-username/forked-repo.git

# 3. Добавить оригинальный репозиторий как upstream
git remote add upstream https://github.com/original-owner/repo.git

# 4. Синхронизация с оригинальным репозиторием
git fetch upstream
git checkout main
git merge upstream/main
```

## 🔧 Полезные команды

### Отмена изменений
```bash
git checkout -- filename.txt     # Отменить изменения в файле
git reset HEAD filename.txt      # Убрать файл из staging area
git reset --soft HEAD~1          # Отменить последний коммит, сохранив изменения
git reset --hard HEAD~1          # Отменить последний коммит и изменения
git revert commit-hash           # Создать коммит, отменяющий изменения
```

### Stash (временное сохранение)
```bash
git stash                        # Сохранить изменения в stash
git stash pop                    # Применить и удалить из stash
git stash list                   # Список сохраненных stash
git stash apply                  # Применить stash без удаления
git stash drop                   # Удалить stash
```

### Теги
```bash
git tag                          # Список тегов
git tag v1.0.0                   # Создать тег
git tag -a v1.0.0 -m "Версия 1.0.0"  # Создать аннотированный тег
git push origin --tags           # Отправить теги на сервер
```

## 📋 Лучшие практики

### Сообщения коммитов
- Используйте повелительное наклонение: "Add feature" вместо "Added feature"
- Первая строка до 50 символов
- Если нужно больше текста, оставьте пустую строку и добавьте описание
- Используйте префиксы: feat:, fix:, docs:, style:, refactor:, test:

### Структура .gitignore
```
# Операционная система
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
*.swp
*.swo

# Языки программирования
node_modules/
*.pyc
__pycache__/
*.class
*.jar

# Логи и временные файлы
*.log
*.tmp
*.temp
```

### Workflow
1. Создать ветку для новой функции
2. Регулярно коммитить небольшие изменения
3. Писать понятные сообщения коммитов
4. Тестировать перед push
5. Создать Pull Request для ревью
6. Удалить ветку после слияния

## 🚨 Частые ошибки

### Проблема с push
```bash
# Если отклонен push из-за конфликтов
git pull origin main
# Разрешить конфликты
git push origin main
```

### Случайно закоммитили в main
```bash
git checkout -b feature-branch   # Создать ветку для функции
git checkout main
git reset --hard HEAD~1          # Отменить коммит в main
git checkout feature-branch      # Вернуться к работе над функцией
```

### Забыли добавить файлы в коммит
```bash
git add forgotten-file.txt
git commit --amend --no-edit     # Добавить к последнему коммиту
```

## 🔗 Полезные ссылки

- [GitHub Desktop](https://desktop.github.com/) - GUI клиент
- [Git Kraken](https://www.gitkraken.com/) - Продвинутый GUI
- [GitHub CLI](https://cli.github.com/) - Командная строка для GitHub
- [Conventional Commits](https://www.conventionalcommits.org/) - Стандарт для сообщений коммитов
- [GitHub Flow](https://guides.github.com/introduction/flow/) - Рабочий процесс GitHub

## 📊 Шпаргалка по командам

| Команда | Описание |
|---------|----------|
| `git init` | Инициализация репозитория |
| `git add .` | Добавить все файлы |
| `git commit -m "msg"` | Создать коммит |
| `git push` | Отправить изменения |
| `git pull` | Получить изменения |
| `git status` | Статус файлов |
| `git log` | История коммитов |
| `git branch` | Список веток |
| `git checkout` | Переключить ветку |
| `git merge` | Слить ветки |
| `git clone` | Клонировать репозиторий |
| `git stash` | Временно сохранить изменения |

---

*Создано для быстрого изучения Git и GitHub 🚀*