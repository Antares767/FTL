# Блок 2.3.2: Отдельные методы движения (5 мин)

## 📖 Текстовая ячейка (интро)

### 🎮 Управление роботом отдельными методами

Теперь мы создадим **отдельные методы движения** для каждого направления. Это сделает управление роботом более структурированным и понятным!

### 🔧 Отдельные методы движения

Вместо одного универсального метода, мы создадим четыре специализированных метода:
- `move_right(steps)` - движение вправо на N шагов
- `move_left(steps)` - движение влево на N шагов  
- `move_up(steps)` - движение вверх на N шагов
- `move_down(steps)` - движение вниз на N шагов

**Преимущества:**
- 🎯 Четкое разделение функций
- 📊 Контроль количества шагов
- 🔄 Легко использовать в циклах
- 📝 Понятные названия методов

### 🗺️ Поддерживаемые методы

- `move_right(steps)` - движение вправо на steps шагов
- `move_left(steps)` - движение влево на steps шагов
- `move_up(steps)` - движение вверх на steps шагов
- `move_down(steps)` - движение вниз на steps шагов

### 🛡️ Обработка ошибок

Что произойдет, если передать отрицательное количество шагов? Например, `move_right(-5)`? 

**Задача:** Добавьте проверку количества шагов, чтобы робот не двигался назад при отрицательных значениях!

---

## 💻 Код для ученика

```python
# Блок 2.3.2: Отдельные методы движения

class Robot:
    """Робот с отдельными методами движения"""
    
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
        # TODO: Проверьте, что steps > 0
        if steps <= 0:
            print(f"❌ {self.name}: нельзя двигаться на {steps} шагов!")
            return
        
        # TODO: Реализуйте движение вправо
        for step in range(steps):
            self.x += ___
            self.steps_made += 1
            print(f"    ➡️ {self.name} шаг {step+1} → ({self.x}, {self.y})")
    
    def move_left(self, steps=1):
        """Движение влево на указанное количество шагов"""
        # TODO: Проверьте, что steps > 0
        if steps <= ___:
            print(f"❌ {self.name}: нельзя двигаться на {steps} шагов!")
            return
        
        # TODO: Реализуйте движение влево
        for step in range(steps):
            self.x -= ___
            self.steps_made += 1
            print(f"    ⬅️ {self.name} шаг {step+1} → ({self.x}, {self.y})")
    
    def move_up(self, steps=1):
        """Движение вверх на указанное количество шагов"""
        # TODO: Проверьте, что steps > 0
        if steps <= ___:
            print(f"❌ {self.name}: нельзя двигаться на {steps} шагов!")
            return
        
        # TODO: Реализуйте движение вверх
        for step in range(steps):
            self.y += ___
            self.steps_made += 1
            print(f"    ⬆️ {self.name} шаг {step+1} → ({self.x}, {self.y})")
    
    def move_down(self, steps=1):
        """Движение вниз на указанное количество шагов"""
        # TODO: Проверьте, что steps > 0
        if steps <= ___:
            print(f"❌ {self.name}: нельзя двигаться на {steps} шагов!")
            return
        
        # TODO: Реализуйте движение вниз
        for step in range(steps):
            self.y -= ___
            self.steps_made += 1
            print(f"    ⬇️ {self.name} шаг {step+1} → ({self.x}, {self.y})")

# Создаем робота
print("🏭 Создаем робота!")
robot = Robot("Бета", 0, 0)

print("\n📊 НАЧАЛЬНОЕ СОСТОЯНИЕ:")
robot.show_info()

print("\n🎮 УПРАВЛЯЕМ РОБОТОМ ОТДЕЛЬНЫМИ МЕТОДАМИ:")
# TODO: Заставьте робота двигаться разными методами
robot.move_right(___)  # 2 шага вправо
robot.move_up(___)     # 3 шага вверх
robot.move_left(___)   # 1 шаг влево
robot.move_down(___)   # 2 шага вниз

print("\n🧪 ТЕСТИРУЕМ ОШИБКИ:")
# TODO: Попробуйте отрицательные шаги - что произойдет?
robot.move_right(___)

print("\n📊 ФИНАЛЬНОЕ СОСТОЯНИЕ:")
robot.show_info()

print("\n✅ Отлично! Теперь мы можем управлять роботом отдельными методами!")
print("💡 Не забудьте добавить проверку количества шагов!")
```
