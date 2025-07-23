# Linux: Домашнее задание 12 (Python) - Полное выполнение

## Цели задания
- Освоить клонирование репозиториев
- Научиться работать с несколькими ветками
- Изучить команду `git commit --amend`
- Понять процесс слияния веток (merge)
- Работа с историей команд

---

## Шаг 1: Создание нового репозитория с .gitignore

### 1.1 Создание репозитория на GitHub:
1. Откройте https://github.com
2. Нажмите **"New repository"**
3. Заполните форму:
   - **Repository name:** `git-homework-12` (или любое другое имя)
   - **Description:** "Git homework 12 - branches and merge"
   - **Public** (оставьте выбранным)
   - ✅ **Add a README file** (поставьте галочку)
   - ✅ **Add .gitignore** → выберите **Python** из списка
   - Лицензию можно не добавлять
4. Нажмите **"Create repository"**

### 1.2 Результат:
Репозиторий создан с файлами:
- `README.md`
- `.gitignore` (для Python проектов)

---

## Шаг 2: Клонирование репозитория

### 2.1 Получение ссылки на репозиторий:
1. На странице вашего репозитория нажмите зеленую кнопку **"Code"**
2. Скопируйте HTTPS ссылку (например: `https://github.com/YOUR_USERNAME/git-homework-12.git`)

### 2.2 Клонирование на локальный компьютер:

```bash
# Переходим в папку, где хотим разместить проект
cd ~/Desktop  # или любая другая папка

# Клонируем репозиторий (замените ссылку на свою)
git clone https://github.com/YOUR_USERNAME/git-homework-12.git

# Переходим в склонированную папку
cd git-homework-12

# Проверяем содержимое
ls -la

# Проверяем Git статус
git status

# Проверяем удаленные репозитории
git remote -v
```

**Результат:** Должны увидеть файлы `README.md` и `.gitignore`

---

## Шаг 3: Создание ветки feature и внесение изменений

### 3.1 Создание и переключение на ветку feature:

```bash
# Создаем и переключаемся на ветку feature
git checkout -b feature

# Проверяем текущую ветку
git branch
```

### 3.2 Внесение изменений в README.md:

```bash
# Открываем README.md для редактирования (выберите удобный редактор)
nano README.md
# или: vim README.md, code README.md, gedit README.md
```

**Добавьте в README.md следующий контент:**
```markdown
# Git Homework 12

Это домашнее задание по работе с Git ветками и слиянием.

## Изучаемые команды:
- git clone
- git checkout -b
- git merge
- git commit --amend
- history

## Автор
[Ваше имя]

## Дата
$(date)
```

### 3.3 Внесение изменений в .gitignore:

```bash
# Открываем .gitignore для редактирования
nano .gitignore
```

**Добавьте в конец файла .gitignore:**
```gitignore

# Custom additions for homework
*.tmp
*.backup
homework_temp/
*.test
logs/

# Personal files
personal_notes.txt
draft_*
```

### 3.4 Проверка изменений:

```bash
# Проверяем статус изменений
git status

# Смотрим конкретные изменения
git diff README.md
git diff .gitignore
```

### 3.5 Коммит изменений:

```bash
# Добавляем изменения в индекс
git add README.md .gitignore

# Проверяем статус
git status

# Делаем коммит
git commit -m "Update README.md and .gitignore with homework content"

# Проверяем историю коммитов
git log --oneline
```

---

## Шаг 4: Отправка ветки feature в удаленный репозиторий

### 4.1 Push ветки feature:

```bash
# Отправляем ветку feature на GitHub
git push -u origin feature

# Проверяем все ветки (локальные и удаленные)
git branch -a
```

### 4.2 Проверка в GitHub:
1. Обновите страницу репозитория на GitHub
2. Должно появиться уведомление о новой ветке `feature`
3. Переключитесь на ветку `feature` через выпадающий список
4. Убедитесь, что изменения в файлах видны

---

## Шаг 5: Использование git commit --amend

### 5.1 Изменение сообщения последнего коммита:

```bash
# Убедимся, что мы на ветке feature
git branch

# Изменяем сообщение последнего коммита, добавляя "amend"
git commit --amend -m "Update README.md and .gitignore with homework content amend"

# Проверяем изменения в истории
git log --oneline
```

**Важно:** После `git commit --amend` история изменилась локально, но на GitHub еще старая версия.

### 5.2 Принудительная отправка изменений:

```bash
# Принудительно обновляем удаленную ветку (ОСТОРОЖНО с этой командой!)
git push --force origin feature
```

**⚠️ Внимание:** `git push --force` перезаписывает историю на удаленном сервере. Используйте осторожно!

---

## Шаг 6: Слияние ветки feature с main

### 6.1 Переключение на ветку main:

```bash
# Переключаемся на ветку main
git checkout main

# Проверяем текущую ветку
git branch

# Проверяем статус
git status
```

### 6.2 Обновление ветки main:

```bash
# Получаем последние изменения из удаленного репозитория
git pull origin main
```

### 6.3 Слияние ветки feature:

```bash
# Выполняем слияние ветки feature с main
git merge feature

# Проверяем результат слияния
git log --oneline --graph

# Проверяем содержимое файлов
cat README.md
cat .gitignore
```

### 6.4 Отправка обновленной ветки main:

```bash
# Отправляем обновленную ветку main на GitHub
git push origin main
```

---

## Шаг 7: Создание файла с историей команд

### 7.1 Создание файла с историей:

```bash
# Создаем файл с историей команд
history > history.txt

# Проверяем содержимое файла (первые 20 строк)
head -20 history.txt

# Проверяем размер файла
wc -l history.txt
```

### 7.2 Коммит и отправка файла:

```bash
# Добавляем файл в индекс
git add history.txt

# Проверяем статус
git status

# Делаем коммит
git commit -m "Add command history file"

# Отправляем изменения в ветку main
git push origin main

# Проверяем финальное состояние
git log --oneline
```

---

## Проверка финального результата

### Команды для самопроверки:

```bash
# Проверяем все ветки
git branch -a

# Проверяем содержимое репозитория
ls -la

# Проверяем историю коммитов с графиком
git log --oneline --graph --all

# Проверяем статус
git status
```

### Что должно быть в репозитории:
1. ✅ Ветка `main` с тремя файлами:
   - `README.md` (обновленный)
   - `.gitignore` (обновленный)
   - `history.txt` (новый)

2. ✅ Ветка `feature` на GitHub

3. ✅ История коммитов показывает:
   - Начальный коммит
   - Коммит с изменениями (с "amend" в сообщении)
   - Коммит с файлом истории

---

## Полезные команды для работы

```bash
# Показать все ветки с последними коммитами
git branch -v

# Показать граф истории всех веток
git log --oneline --graph --all --decorate

# Показать разницу между ветками
git diff main feature

# Показать статус всех файлов
git status --porcelain

# Показать информацию о последнем коммите
git show

# Показать удаленные репозитории
git remote -v

# Показать какие файлы игнорируются
git status --ignored
```

---

## Возможные проблемы и решения

### Проблема 1: Конфликт при merge
```bash
# Если возник конфликт при git merge feature
git status  # покажет конфликтующие файлы
# Отредактируйте файлы, удалив маркеры конфликта
git add <исправленные_файлы>
git commit -m "Resolve merge conflict"
```

### Проблема 2: "Permission denied" при push
**Решение:** Настройте аутентификацию GitHub (Personal Access Token)

### Проблема 3: git commit --amend не работает
```bash
# Убедитесь, что есть коммиты для изменения
git log --oneline
# Если коммитов нет, сначала сделайте обычный коммит
```

### Проблема 4: history команда не найдена
```bash
# В некоторых системах используйте:
fc -l > history.txt
# или
cat ~/.bash_history > history.txt
```

---

## Важные концепции

### git commit --amend
- Изменяет **последний** коммит
- Можно изменить сообщение или добавить файлы
- **НЕ используйте** после push (если не планируете force push)

### git merge
- Объединяет изменения из одной ветки в другую
- Создает merge commit (если истории веток разошлись)
- Сохраняет историю обеих веток

### Работа с ветками
- `git checkout -b` создает и переключается на ветку
- `git branch` показывает список веток
- `git branch -a` показывает все ветки (включая удаленные)

---

## Финальная самопроверка

После выполнения всех шагов у вас должно быть:
1. ✅ Репозиторий на GitHub с ветками `main` и `feature`
2. ✅ Локальный клон репозитория
3. ✅ Обновленные файлы `README.md` и `.gitignore`
4. ✅ Файл `history.txt` с историей команд
5. ✅ Коммит с сообщением, содержащим "amend"
6. ✅ Успешное слияние ветки `feature` с `main`

**Ссылка на репозиторий для отправки:**
`https://github.com/YOUR_USERNAME/git-homework-12`