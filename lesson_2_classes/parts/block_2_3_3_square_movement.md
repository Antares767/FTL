# Блок 2.3.3: Движение по квадрату (5 мин)

## 📖 Текстовая ячейка (интро)

### 🎨 Автоматическое рисование квадрата

Теперь мы создадим **метод `walk_square()`**, который автоматически заставляет робота нарисовать квадрат заданного размера. Это покажет мощь методов - один вызов вместо множества команд!

### 🔄 Алгоритм движения по квадрату

1. **Вправо** - `size` шагов
2. **Вверх** - `size` шагов  
3. **Влево** - `size` шагов
4. **Вниз** - `size` шагов

### 🎯 Преимущества метода

- 🚀 Один вызов вместо 12 команд
- 📏 Настраиваемый размер квадрата
- 🔄 Переиспользуемый код
- 📊 Автоматический подсчет шагов

---

## 💻 Код для ученика

```python
# Блок 2.3.3: Автоматическое движение по квадрату

class Robot:
    """Робот с методом рисования квадрата"""
    
    def __init__(self, name, start_x=0, start_y=0):
        """Создаем робота с именем и стартовой позицией"""
        self.name = name
        self.x = start_x
        self.y = start_y
        self.start_x = start_x
        self.start_y = start_y
        self.steps_made = 0
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
        
        # TODO: Заполните движение вверх
        print(f"  ⬆️ Идем вверх ({size} шагов):")
        self.move_up(___)
        
        # TODO: Заполните движение влево  
        print(f"  ⬅️ Идем влево ({size} шагов):")
        self.move_left(___)
        
        # TODO: Заполните движение вниз
        print(f"  ⬇️ Идем вниз ({size} шагов):")
        self.move_down(___)
        
        print(f"✅ {self.name} завершил квадрат!")

# Создаем робота
print("🏭 Создаем робота!")
robot = Robot("Гамма", 0, 0)

print("\n📊 НАЧАЛЬНОЕ СОСТОЯНИЕ:")
robot.show_info()

print("\n🎨 РИСУЕМ КВАДРАТЫ РАЗНОГО РАЗМЕРА:")

# TODO: Заставьте робота нарисовать квадрат 2x2
robot.walk_square(___)

print("\n📊 СОСТОЯНИЕ ПОСЛЕ ПЕРВОГО КВАДРАТА:")
robot.show_info()

# TODO: Заставьте робота нарисовать квадрат 4x4
robot.walk_square(___)

print("\n📊 ФИНАЛЬНОЕ СОСТОЯНИЕ:")
robot.show_info()

# Проверка: вернулся ли робот домой?
print("\n🏠 ПРОВЕРКА: ВЕРНУЛСЯ ЛИ РОБОТ ДОМОЙ?")
if robot.x == robot.start_x and robot.y == robot.start_y:
    print(f"✅ {robot.name} вернулся домой!")
else:
    print(f"❌ {robot.name} заблудился!")

print("\n✅ Отлично! Теперь робот может автоматически рисовать квадраты!")
```
