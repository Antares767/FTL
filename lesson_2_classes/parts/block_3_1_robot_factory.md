# Блок 3.1: Фабрика роботов (15 мин)

## 📖 Текстовая ячейка (интро)

### 🏭 Массовое производство роботов

Создавать роботов по одному - это медленно! Представьте, что нам нужна **армия из 100 роботов**. Неужели писать 100 строк `Robot("имя", x, y)`?

Программисты ленивые (в хорошем смысле!) и всегда ищут способы автоматизировать повторяющиеся задачи.

### 📚 Словари - база данных роботов

**Словарь** в Python - это структура данных, которая хранит пары "ключ: значение". Идеально для хранения информации о роботах!

```python
robot_data = {
    "name": "R2D2",
    "x": 5,
    "y": 3,
    "color": "blue"
}
```

### 📋 Список - коллекция роботов

**Список** позволяет хранить много объектов и работать с ними в цикле:

```python
robots = [robot1, robot2, robot3]
for robot in robots:
    robot.walk_square()  # Все роботы одновременно!
```

### 🔄 Цикл for - автоматизация

Вместо копирования кода мы используем циклы:

```python
# Плохо - копирование
robot1 = Robot("Робот-1", 0, 0)
robot2 = Robot("Робот-2", 5, 0)
robot3 = Robot("Робот-3", 10, 0)

# Хорошо - цикл
for i in range(3):
    robot = Robot(f"Робот-{i+1}", i*5, 0)
```

### 🎯 Задача: создать 5 роботов

Мы создадим **"фабрику роботов"** - систему, которая:
1. Читает данные о роботах из списка словарей
2. Автоматически создает всех роботов
3. Запускает их всех работать одновременно
4. Собирает статистику

---

## 💻 Код для ученика

```python
# Блок 3.1: Фабрика роботов - массовое производство!
# Создаем много роботов из списка данных

class Robot:
    """Робот для массового производства"""
    
    def __init__(self, name, start_x=0, start_y=0, color="blue"):
        self.name = name
        self.x = start_x
        self.y = start_y
        self.start_x = start_x
        self.start_y = start_y
        self.color = color
        self.steps_made = 0
        print(f"🤖 {name} ({color}) создан в ({start_x}, {start_y})")
    
    def show_info(self):
        """Компактный вывод информации"""
        status = "🏠" if (self.x == self.start_x and self.y == self.start_y) else "🗺️"
        print(f"{status} {self.name:<10} | Позиция: ({self.x:2}, {self.y:2}) | Шагов: {self.steps_made:2} | Цвет: {self.color}")
    
    def walk_square(self, size=3):
        """Быстрое рисование квадрата (без детального вывода)"""
        directions = ["right", "up", "left", "down"]
        
        for direction in directions:
            for step in range(size):
                if direction == "right":
                    self.x += 1
                elif direction == "up":
                    self.y += 1
                elif direction == "left":
                    self.x -= 1
                elif direction == "down":
                    self.y -= 1
                self.steps_made += 1
        
        print(f"✅ {self.name} завершил квадрат {size}x{size}")

# База данных роботов для создания концентрических квадратов
# Каждый словарь должен содержать: "name", "x", "y", "color"
# Стартовые позиции и размеры подобраны так, чтобы получились концентрические квадраты
robots_data = [
    # TODO: Заполните словари данными для роботов
    # Стартовые позиции: (0,0), (1,1), (2,2)
    # Цвета можете выбрать любые
    {},
    {},
    {}
]

print("🏭 ФАБРИКА РОБОТОВ ЗАПУЩЕНА!")
print(f"📋 В очереди на производство: {len(robots_data)} роботов")

# TODO: Создайте всех роботов из списка данных
robot_army = []  # список для хранения роботов

print("\n🔧 ПРОИЗВОДСТВО РОБОТОВ:")
for robot_data in robots_data:
    # TODO: Создайте робота из данных словаря
    # Подсказка: robot_data["name"], robot_data["x"], и т.д.
    robot = Robot(
        robot_data["___"],    # имя
        robot_data["___"],    # x координата  
        robot_data["___"],    # y координата
        robot_data["___"]     # цвет
    )
    robot_army.append(robot)

print(f"\n✅ Произведено роботов: {len(robot_army)}")

# Показать информацию о всех роботах
print("\n📊 РЕЕСТР РОБОТОВ:")
print("   Статус | Имя        | Позиция    | Шагов | Цвет")
print("   " + "─" * 50)

# TODO: Покажите информацию о каждом роботе
for robot in robot_army:
    robot.___()

# Запустить всех роботов работать
print("\n🎨 МАССОВОЕ ПРОИЗВОДСТВО КВАДРАТОВ:")

# TODO: Заставьте всех роботов нарисовать квадраты разного размера
# Для концентрических квадратов используйте размеры: 4, 3, 2
sizes = [4, 3, 2]  # размеры квадратов для концентрических квадратов

for i, robot in enumerate(robot_army):
    size = sizes[i]
    print(f"🤖 {robot.name} рисует квадрат {size}x{size}...")
    robot.walk_square(___)

# Финальная статистика
print("\n📊 ФИНАЛЬНАЯ СТАТИСТИКА:")
print("   Статус | Имя        | Позиция    | Шагов | Цвет") 
print("   " + "─" * 50)

# TODO: Снова покажите информацию о всех роботах


# Анализ результатов  
print(f"\n📈 АНАЛИЗ ПРОИЗВОДСТВА:")

# TODO: Подсчитайте статистику
total_steps = 0
robots_at_home = 0

for robot in robot_army:
    total_steps += robot.___  # добавьте шаги робота
    
    # Проверьте, дома ли робот
    if robot.x == robot.___ and robot.y == robot.___:
        robots_at_home += 1

print(f"   🤖 Всего роботов: {len(robot_army)}")
print(f"   👣 Общее количество шагов: {total_steps}")
print(f"   📊 Среднее шагов на робота: {total_steps / len(robot_army):.1f}")
print(f"   🏠 Роботов вернулось домой: {robots_at_home}")
print(f"   📏 Эффективность возврата: {robots_at_home / len(robot_army) * 100:.1f}%")

# Поиск чемпионов
most_active = max(robot_army, key=lambda r: r.steps_made)
print(f"   🏆 Самый активный: {most_active.name} ({most_active.steps_made} шагов)")

print(f"\n🎉 ФАБРИКА ЗАВЕРШИЛА РАБОТУ! Все роботы готовы к службе!")
```
