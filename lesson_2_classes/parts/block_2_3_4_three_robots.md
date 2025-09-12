# Блок 2.3.4: Движение по квадрату сразу трех роботов (5 мин)

## 📖 Текстовая ячейка (интро)

### 🏭 Фабрика роботов

Теперь мы создадим **трех роботов** с разными стартовыми позициями. Каждый нарисует свой квадрат, и мы увидим, насколько элегантно это работает с классами!

### 🚀 Масштабируемость

С методами легко управлять множеством роботов:
```python
robots = [robot1, robot2, robot3]
for robot in robots:
    robot.walk_square(3)
    robot.show_info()
```

Один цикл вместо копирования кода!

### 🎯 Задача: три робота из разных точек

Мы создадим трех роботов:
- **Альфа** - в позиции (0, 0), рисует квадрат 2x2
- **Бета** - в позиции (10, 5), рисует квадрат 3x3  
- **Гамма** - в позиции (20, 10), рисует квадрат 4x4

---

## 💻 Код для ученика

```python
# Блок 2.3.4: Три робота рисуют квадраты одновременно

class Robot:
    """Продвинутый робот с красивым выводом информации"""
    
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
    
    def move_right(self, steps=1):
        """Движение вправо на указанное количество шагов"""
        if steps <= 0:
            print(f"❌ {self.name}: нельзя двигаться на {steps} шагов!")
            return
        
        for step in range(steps):
            self.x += 1
            self.steps_made += 1
            print(f"    ➡️ {self.name} шаг {step+1} → ({self.x}, {self.y})")
    
    def move_left(self, steps=1):
        """Движение влево на указанное количество шагов"""
        if steps <= 0:
            print(f"❌ {self.name}: нельзя двигаться на {steps} шагов!")
            return
        
        for step in range(steps):
            self.x -= 1
            self.steps_made += 1
            print(f"    ⬅️ {self.name} шаг {step+1} → ({self.x}, {self.y})")
    
    def move_up(self, steps=1):
        """Движение вверх на указанное количество шагов"""
        if steps <= 0:
            print(f"❌ {self.name}: нельзя двигаться на {steps} шагов!")
            return
        
        for step in range(steps):
            self.y += 1
            self.steps_made += 1
            print(f"    ⬆️ {self.name} шаг {step+1} → ({self.x}, {self.y})")
    
    def move_down(self, steps=1):
        """Движение вниз на указанное количество шагов"""
        if steps <= 0:
            print(f"❌ {self.name}: нельзя двигаться на {steps} шагов!")
            return
        
        for step in range(steps):
            self.y -= 1
            self.steps_made += 1
            print(f"    ⬇️ {self.name} шаг {step+1} → ({self.x}, {self.y})")
    
    def walk_square(self, size=3):
        """Робот рисует квадрат заданного размера"""
        print(f"\n🎨 {self.name} начинает рисовать квадрат {size}x{size}")
        
        # Вправо
        print(f"  ➡️ Идем вправо ({size} шагов):")
        self.move_right(___)
        
        # Вверх
        print(f"  ⬆️ Идем вверх ({size} шагов):")
        self.move_up(___)
        
        # Влево
        print(f"  ⬅️ Идем влево ({size} шагов):")
        self.move_left(___)
        
        # Вниз
        print(f"  ⬇️ Идем вниз ({size} шагов):")
        self.move_down(___)
        
        print(f"✅ {self.name} завершил квадрат!")

# Создаем трех роботов в разных позициях
print("🏭 Запускаем фабрику роботов!")

# TODO: Создайте трех роботов
# Робот 1: "Альфа" в позиции (0, 0)
robot1 = Robot("___", ___, ___)

# Робот 2: "Бета" в позиции (10, 5)  
robot2 = Robot("___", ___, ___)

# Робот 3: "Гамма" в позиции (20, 10)
robot3 = Robot("___", ___, ___)

# Показать начальную информацию
print("\n📊 НАЧАЛЬНОЕ СОСТОЯНИЕ РОБОТОВ:")
# TODO: Вызвать show_info() для каждого робота
robot1.___()
robot2.___()
robot3.___()

# Запустить всех роботов рисовать
print("\n🎨 ВСЕ РОБОТЫ НАЧИНАЮТ РИСОВАТЬ:")

# TODO: Заставить каждого робота нарисовать квадрат разного размера
# Альфа рисует квадрат 2x2
robot1.walk_square(___)

# Бета рисует квадрат 3x3
robot2.walk_square(___)

# Гамма рисует квадрат 4x4  
robot3.walk_square(___)

# Показать финальную информацию
print("\n📊 ФИНАЛЬНОЕ СОСТОЯНИЕ РОБОТОВ:")
# TODO: Снова показать информацию о всех роботах
robot1.___()
robot2.___()
robot3.___()

# Проверка: кто вернулся домой?
print("\n🏠 ПРОВЕРКА: КТО ВЕРНУЛСЯ ДОМОЙ?")
robots = [robot1, robot2, robot3]
for robot in robots:
    if robot.x == robot.start_x and robot.y == robot.start_y:
        print(f"✅ {robot.name} вернулся домой!")
    else:
        print(f"❌ {robot.name} заблудился!")

print(f"\n🎉 Задание выполнено! Мы управляли {len(robots)} роботами одновременно!")
```
