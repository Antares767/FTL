# Блок 3.2.2: Рисование нескольких роботов (4 мин)

## 📖 Текстовая ячейка (интро)

### 🤖🤖🤖 Армия роботов

Теперь, когда мы умеем рисовать одного робота, давайте создадим **целую армию**! Мы научимся рисовать несколько роботов на одном графике.

### 🎨 Множественная визуализация

Когда у нас много роботов, важно:
- 🎯 Использовать разные цвета для каждого робота
- 📍 Размещать их в разных позициях
- 🏷️ Подписывать каждого робота
- 📊 Создавать красивые визуализации

### 🔄 Циклы для множественных объектов

Вместо рисования каждого робота отдельно, мы используем циклы:
```python
for robot in robots:
    robot.draw()  # Рисуем всех роботов одной командой!
```

Это намного эффективнее, чем копировать код!

---

## 💻 Код для ученика

```python
# Блок 3.2.2: Рисование нескольких роботов
# Создаем армию роботов на одном графике!

import matplotlib.pyplot as plt
import numpy as np

class Robot:
    """Робот, который умеет рисовать себя на экране"""
    
    def __init__(self, name, start_x=0, start_y=0, color="blue"):
        self.name = name
        self.x = start_x
        self.y = start_y
        self.start_x = start_x
        self.start_y = start_y
        self.color = color
        self.steps_made = 0
        print(f"🤖 {name} ({color}) создан в ({start_x}, {start_y})")
    
    def draw(self, size=100):
        """Рисует робота на текущем графике"""
        plt.scatter(self.x, self.y, 
                   color=self.color, 
                   s=size, 
                   alpha=0.8,
                   label=self.name)
        
        plt.annotate(f'{self.name}\n({self.x},{self.y})', 
                    (self.x, self.y), 
                    xytext=(10, 10), 
                    textcoords='offset points',
                    fontsize=8,
                    bbox=dict(boxstyle="round,pad=0.3", 
                             facecolor=self.color, 
                             alpha=0.3))

# Тест: Армия роботов на одном графике
print("🎨 ТЕСТ: Армия роботов на одном графике")

# TODO: Создайте несколько роботов в разных позициях
robots = [
    Robot("Альфа", ___, ___, "red"),
    Robot("Бета", ___, ___, "blue"),  
    Robot("Гамма", ___, ___, "green"),
    Robot("Дельта", ___, ___, "orange")
]

# Рисуем всех роботов
plt.figure(figsize=(10, 8))

# TODO: Нарисуйте всех роботов в цикле
for robot in robots:
    robot.___()

# Красивое оформление
plt.grid(True, alpha=0.3)
plt.xlim(-1, 15)
plt.ylim(-1, 12)
plt.title("🤖🤖🤖 Армия роботов готова к бою!")
plt.xlabel("X координата") 
plt.ylabel("Y координата")
plt.legend()
plt.show()

print("✅ Тест завершен! Армия нарисована!")

print("\n🎉 Отлично! Теперь вы умеете рисовать армии роботов!")
```
