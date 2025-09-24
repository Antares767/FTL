# Блок 3.2.3: Роботы до и после работы (3 мин)

## 📖 Текстовая ячейка (интро)

### 🔄 Сравнение состояний

Теперь мы научимся показывать, как роботы **изменяются** после выполнения работы! Мы создадим **два графика рядом**:
- **ЛЕВЫЙ** - роботы до работы (в стартовых позициях)
- **ПРАВЫЙ** - роботы после работы (в финальных позициях)

### 📊 Подграфики (subplots)

Для создания двух графиков рядом мы используем `plt.subplot()`:
```python
plt.subplot(1, 2, 1)  # 1 строка, 2 столбца, график 1 (левый)
# рисуем роботов ДО работы

plt.subplot(1, 2, 2)  # 1 строка, 2 столбца, график 2 (правый)  
# рисуем роботов ПОСЛЕ работы
```

### 🚶 Движение роботов

Роботы будут просто идти вправо на разное количество шагов. Это покажет, как они перемещаются в пространстве!

---

## 💻 Код для ученика

```python
# Блок 3.2.3: Роботы до и после работы
# Показываем, как роботы изменяются!

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
        self.path = [(start_x, start_y)]  # для будущего draw_path()
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
    
    def move_right(self, steps=1):
        """Движение вправо на указанное количество шагов"""
        if steps <= 0:
            print(f"❌ {self.name}: нельзя двигаться на {steps} шагов!")
            return
        
        for step in range(steps):
            self.x += 1
            self.steps_made += 1
            self.path.append((self.x, self.y))
            print(f"    ➡️ {self.name} шаг {step+1} → ({self.x}, {self.y})")

# Тест: Роботы до и после работы
print("🎨 ТЕСТ: Роботы до и после работы")

# Создаем роботов для эксперимента
work_robots = [
    Robot("Рабочий-1", 2, 2, "purple"),
    Robot("Рабочий-2", 8, 3, "cyan"),
    Robot("Рабочий-3", 5, 7, "magenta")
]

# График ДО работы
plt.figure(figsize=(15, 5))

# Подграфик 1: ДО
plt.subplot(1, 2, 1)
for robot in work_robots:
    robot.draw()

plt.grid(True, alpha=0.3)
plt.xlim(0, 12)
plt.ylim(0, 12)
plt.title("ДО работы")
plt.xlabel("X")
plt.ylabel("Y")
plt.legend()

# Заставляем роботов работать
steps = [2, 3, 4]
for i, robot in enumerate(work_robots):
    robot.move_right(steps[i])
    print(f"✅ {robot.name} прошел {steps[i]} шагов вправо")

# Подграфик 2: ПОСЛЕ
plt.subplot(1, 2, 2)

# TODO: Нарисуйте роботов после работы
for robot in work_robots:
    robot.___()

plt.grid(True, alpha=0.3)
plt.xlim(0, 12)
plt.ylim(0, 12)
plt.title("ПОСЛЕ работы")
plt.xlabel("X")
plt.ylabel("Y")
plt.legend()

plt.tight_layout()
plt.show()

print("✅ Тест завершен! Видно, как роботы поработали!")

print("\n🎉 Модуль визуализации освоен! Роботы теперь видны!")
```
