# Блок 2.3.1: Вывод информации о роботе (5 мин)

## 📖 Текстовая ячейка (интро)

### 📢 Улучшаем вывод информации

В прошлом блоке мы вручную выводили информацию о роботе через `print()`. Это неудобно! Давайте создадим **специальный метод** `show_info()`, который будет красиво показывать всю информацию о роботе.

### 🔄 Принцип DRY (Don't Repeat Yourself)

**DRY** = "Не повторяйся" - основной принцип программирования.

**Плохо** (повторение):
```python
print(f"Робот {robot1.name} в ({robot1.x}, {robot1.y})")
print(f"Робот {robot2.name} в ({robot2.x}, {robot2.y})")
print(f"Робот {robot3.name} в ({robot3.x}, {robot3.y})")
```

**Хорошо** (метод):
```python
robot1.show_info()
robot2.show_info()
robot3.show_info()
```

### 🎨 Красивый вывод

Мы сделаем метод `show_info()`, который показывает:
- 🤖 Имя робота
- 📍 Текущие координаты  
- 📊 Статистику (сколько шагов сделал)
- 🎨 Красивое оформление

---

## 💻 Код для ученика

```python
# Блок 2.3.1: Красивый вывод информации о роботе

class Robot:
    """Робот с красивым выводом информации"""
    
    def __init__(self, name, start_x=0, start_y=0):
        """Создаем робота с именем и стартовой позицией"""
        self.name = name
        self.x = start_x
        self.y = start_y
        self.start_x = start_x  # запоминаем дом
        self.start_y = start_y
        self.steps_made = 0     # счетчик шагов
        print(f"🤖 {name} создан в позиции ({start_x}, {start_y})")
    
    def show_info(self):
        """Красивый вывод информации о роботе"""
        print(f"┌{'─' * 40}┐")
        print(f"│ 🤖 Робот: {self.name:<30} │")
        print(f"│ 📍 Позиция: ({self.x}, {self.y}){' ' * (22 - len(str(self.x)) - len(str(self.y)))}│")
        print(f"│ 🏠 Дом: ({self.start_x}, {self.start_y}){' ' * (26 - len(str(self.start_x)) - len(str(self.start_y)))}│")
        print(f"│ 👣 Шагов сделано: {self.steps_made:<18} │")
        print(f"└{'─' * 40}┘")
    
    def move_right(self):
        """Движение вправо"""
        self.x += 1
        self.steps_made += 1
        print(f"    👣 {self.name} в ({self.x}, {self.y})")

# Создаем робота и показываем информацию
print("🏭 Создаем робота!")
robot = Robot("Альфа", 5, 3)

print("\n📊 ИНФОРМАЦИЯ О РОБОТЕ:")
# TODO: Вызовите метод show_info() для робота
robot.___()

print("\n🚶 Робот делает несколько шагов:")
robot.move_right()
robot.move_right()

print("\n📊 ОБНОВЛЕННАЯ ИНФОРМАЦИЯ:")
# TODO: Снова покажите информацию о роботе
robot.___()

print("\n✅ Отлично! Теперь у нас есть красивый способ показать информацию о роботе!")
```
