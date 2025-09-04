# 🏠 Домашнее задание: Практика Merge vs Rebase

> 🎯 **Цель:** Закрепить навыки работы с merge и rebase на групповом проекте

---

## 📋 Описание задания

### 👥 **Групповой проект (3–4 человека)**

**Задача:** Создать проект, который наглядно демонстрирует разницу между merge и rebase подходами.

**Результат:** Два варианта истории коммитов — ветвистая (merge) и линейная (rebase).

---

## 🎯 Пошаговое выполнение

### 1. 🏗️ Создание общего репозитория

```bash
# Один участник создаёт репозиторий на GitHub
# Остальные клонируют его
git clone git@github.com:username/merge-rebase-demo.git
cd merge-rebase-demo
```

### 2. 🌿 Создание веток для каждого участника

```bash
# Каждый участник создаёт две ветки:
git checkout -b feature-merge-ivanov
git checkout -b feature-rebase-ivanov

# Аналогично для других участников:
git checkout -b feature-merge-petrov
git checkout -b feature-rebase-petrov
git checkout -b feature-merge-sidorov
git checkout -b feature-rebase-sidorov
```

> 💡 **Соглашение по именованию:** `feature-merge-<имя>` и `feature-rebase-<имя>`

### 3. 📝 Внесение изменений в ветки

**Каждый участник работает в своих ветках:**

```bash
# В ветке feature-merge-ivanov
git checkout feature-merge-ivanov
echo "Файл от Иванова для merge" > ivanov-merge.txt
git add ivanov-merge.txt
git commit -m "Add Ivanov's file for merge"

# В ветке feature-rebase-ivanov
git checkout feature-rebase-ivanov
echo "Файл от Иванова для rebase" > ivanov-rebase.txt
git add ivanov-rebase.txt
git commit -m "Add Ivanov's file for rebase"
```

**Аналогично для других участников:**
- Петров создаёт `petrov-merge.txt` и `petrov-rebase.txt`
- Сидоров создаёт `sidorov-merge.txt` и `sidorov-rebase.txt`

### 4. 🔀 Объединение через Merge

```bash
# Переключаемся на main
git checkout main

# Объединяем все merge-ветки
git merge feature-merge-ivanov
git merge feature-merge-petrov
git merge feature-merge-sidorov

# Смотрим результат
git log --oneline --graph --all
```

### 5. 🔄 Объединение через Rebase

```bash
# Перебазируем каждую rebase-ветку на main
git checkout feature-rebase-ivanov
git rebase main

git checkout feature-rebase-petrov
git rebase main

git checkout feature-rebase-sidorov
git rebase main

# Смотрим результат
git log --oneline --graph --all
```

### 6. 📊 Сравнение результатов

```bash
# Сравниваем истории
git log --oneline --graph --all

# Смотрим содержимое файла
cat shared.txt
```

---

## 🎯 Ожидаемые результаты

### 📈 **История после Merge:**
```
*   abc1234 Merge branch 'feature-merge-sidorov'
|\  
| * def5678 Add Sidorov's file for merge
* | ghi9012 Merge branch 'feature-merge-petrov'
|\| 
| * jkl3456 Add Petrov's file for merge
* | mno7890 Merge branch 'feature-merge-ivanov'
|\| 
| * pqr1234 Add Ivanov's file for merge
* | stu5678 Initial commit
|/  
* vwx9012 Initial commit
```

### 📈 **История после Rebase:**
```
* def5678 Add Sidorov's file for rebase
* jkl3456 Add Petrov's file for rebase
* pqr1234 Add Ivanov's file for rebase
* stu5678 Initial commit
```

### 📄 **Содержимое файлов после merge:**
```
# В main ветке после merge будут файлы:
ivanov-merge.txt    # "Файл от Иванова для merge"
petrov-merge.txt    # "Файл от Петрова для merge"
sidorov-merge.txt   # "Файл от Сидорова для merge"
```

### 📄 **Содержимое файлов после rebase:**
```
# В main ветке после rebase будут файлы:
ivanov-rebase.txt   # "Файл от Иванова для rebase"
petrov-rebase.txt   # "Файл от Петрова для rebase"
sidorov-rebase.txt  # "Файл от Сидорова для rebase"
```

---

## 📸 Требования к отчёту

### 📋 **Что нужно сделать:**

1. **Создать проект** с двумя подходами к объединению веток
2. **Сделать скриншоты** истории коммитов:
   - После merge (ветвистая история)
   - После rebase (линейная история)
3. **Приложить скриншоты** к отчёту
4. **Объяснить различия** в подходах

### 📊 **Скриншоты для отчёта:**

#### **Merge история:**
```bash
git log --oneline --graph --all
# Сделать скриншот ветвистой истории
```

#### **Rebase история:**
```bash
git log --oneline --graph --all
# Сделать скриншот линейной истории
```

#### **Содержимое файлов:**
```bash
ls -la *.txt
# Сделать скриншот списка файлов
```

---

## 💡 Ключевые выводы

### 🔀 **Merge:**
- ✅ **Сохраняет** разветвлённую историю
- ✅ **Безопасно** для общих веток
- ✅ **Показывает** где происходило ветвление
- ❌ **Загромождает** историю merge-коммитами

### 🔄 **Rebase:**
- ✅ **Создаёт** линейную историю
- ✅ **Чище** для чтения
- ✅ **Меньше** коммитов в логе
- ❌ **Требует внимательности** на общих ветках
- ❌ **Изменяет** историю коммитов

### 🎯 **Когда что использовать:**

| Ситуация | Рекомендация | Причина |
|----------|--------------|---------|
| **Общие ветки** | Merge | Безопасность |
| **Личные ветки** | Rebase | Чистота истории |
| **Feature ветки** | Rebase + Merge | Лучшее из обоих |
| **Release ветки** | Merge | Сохранение истории |

---

## 🆘 Если что-то не работает

### ⚔️ **Конфликты при merge:**
```bash
# Разрешить конфликт
git status
# Отредактировать файл, убрав маркеры конфликта
git add shared.txt
git commit -m "Resolve merge conflicts"
```

### ⚔️ **Конфликты при rebase:**
```bash
# Разрешить конфликт
git status
# Отредактировать файл
git add shared.txt
git rebase --continue
```

### 🔄 **Отмена операций:**
```bash
# Отменить merge
git merge --abort

# Отменить rebase
git rebase --abort
```

---

## ✅ Проверка готовности

Убедитесь, что у вас есть:

- [ ] **Создан групповой репозиторий** с участниками
- [ ] **Созданы ветки** для каждого участника (merge + rebase)
- [ ] **Внесены изменения** в обе ветки каждого участника
- [ ] **Выполнен merge** всех merge-веток
- [ ] **Выполнен rebase** всех rebase-веток
- [ ] **Сделаны скриншоты** истории коммитов
- [ ] **Подготовлен отчёт** с объяснением различий

### 🎯 **Ожидаемый результат:**
- Понимание разницы между merge и rebase
- Практический опыт работы с обоими подходами
- Визуальное сравнение истории коммитов
- Готовность объяснить когда что использовать

---

## 🏆 Дополнительные задания

### 🌟 **Для продвинутых:**

1. **Создайте конфликт** намеренно и разрешите его
2. **Используйте интерактивный rebase** (`git rebase -i`)
3. **Создайте Pull Request** для объединения веток
4. **Напишите автоматические тесты** для проверки содержимого файла

### 📚 **Для изучения:**

- **Git Flow** — популярная модель ветвления
- **Conventional Commits** — стандарт сообщений коммитов
- **Git Hooks** — автоматизация процессов
- **Git Submodules** — работа с зависимостями

> 💡 **Помните:** Практика — лучший способ закрепить знания. Чем больше вы экспериментируете, тем лучше понимаете Git!
