# Блок 3.2.1: Рисование одного робота (8 мин)

## 📖 Текстовая ячейка (интро)

### 📊 От текста к картинке

До сих пор мы видели роботов только в виде текста в консоли. Но роботы живут в **пространстве**! Давайте научимся их **рисовать на экране**.

### 🎨 Matplotlib - библиотека для рисования

**Matplotlib** - это мощная библиотека Python для создания графиков и визуализаций. Она умеет:
- 📍 Рисовать точки (`scatter`)
- 📏 Строить линии (`plot`)  
- 🎨 Использовать разные цвета и размеры
- 📊 Создавать красивые графики

### 📍 Как работает plt.scatter()

`plt.scatter()` - это функция для рисования точек на графике. Вот как она работает:

```python
# Простой пример
plt.scatter(5, 3, color="red", s=100)  # точка в (5,3), красная, размер 100

# С несколькими точками
x_coords = [1, 3, 5, 7]
y_coords = [2, 4, 1, 6]
plt.scatter(x_coords, y_coords, color="blue", s=150)

# С разными цветами и размерами
plt.scatter(2, 4, color="green", s=200, alpha=0.7)  # alpha = прозрачность
```

**Параметры scatter:**
- `x, y` - координаты точки
- `color` - цвет точки ("red", "blue", "green", или hex "#FF0000")
- `s` - размер точки (чем больше число, тем больше точка)
- `alpha` - прозрачность (от 0 до 1, где 1 = полностью непрозрачная)
- `label` - подпись для легенды

### 📝 Как работает plt.annotate()

`plt.annotate()` - это функция для добавления подписей и аннотаций к точкам на графике:

```python
# Простая подпись
plt.annotate("Робот", (5, 3))  # текст "Робот" рядом с точкой (5,3)

# Подпись с координатами
plt.annotate("Альфа\n(5,3)", (5, 3))  # \n = новая строка

# Подпись со смещением
plt.annotate("Робот", (5, 3), 
            xytext=(10, 10),           # смещение текста на 10 пикселей
            textcoords='offset points') # вправо и вверх

# Подпись с рамкой
plt.annotate("Робот", (5, 3),
            bbox=dict(boxstyle="round,pad=0.3",  # круглая рамка
                     facecolor="yellow",         # желтый фон
                     alpha=0.5))                # полупрозрачная
```

**Параметры annotate:**
- `text` - текст подписи
- `xy` - координаты точки, к которой добавляется подпись
- `xytext` - координаты текста (если не указано, текст рядом с точкой)
- `textcoords` - система координат для текста ('offset points', 'data', и т.д.)
- `bbox` - параметры рамки вокруг текста
- `fontsize` - размер шрифта

### 🗺️ Система координат

В matplotlib координаты работают так:
- **X** - горизонталь (слева направо)
- **Y** - вертикаль (снизу вверх)
- **(0, 0)** - левый нижний угол

### 🤖 Метод draw() для робота

Мы добавим в класс Robot новый метод `draw()`, который будет:
- Рисовать робота как цветную точку
- Показывать его координаты
- Отображать имя робота
- Красиво оформлять график

---

## 💻 Код для ученика

```python
# Блок 3.2.1: Рисование одного робота с помощью matplotlib
# Учимся рисовать робота на экране!

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
        # TODO: Нарисуйте робота как точку
        # Подсказка: используйте plt.scatter()
        plt.scatter(self.___, self.___, 
                   color=self.___, 
                   s=size, 
                   alpha=0.8,
                   label=self.name)
        
        # TODO: Добавьте подпись с именем и координатами
        # Подсказка: используйте plt.annotate()
        plt.annotate(f'{self.name}\n({self.x},{self.y})', 
                    (self.___, self.___), 
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
        self.move_right(size)
        
        # Вверх
        print(f"  ⬆️ Идем вверх ({size} шагов):")
        self.move_up(size)
        
        # Влево
        print(f"  ⬅️ Идем влево ({size} шагов):")
        self.move_left(size)
        
        # Вниз
        print(f"  ⬇️ Идем вниз ({size} шагов):")
        self.move_down(size)
        
        print(f"✅ {self.name} завершил квадрат!")

# Тест: Рисуем одного робота
print("🎨 ТЕСТ: Рисование одного робота")

# TODO: Создайте робота для тестирования
test_robot = Robot("___", ___, ___, "___")

# Настраиваем график
plt.figure(figsize=(8, 6))

# TODO: Нарисуйте робота
test_robot.___()

# Настройки графика
plt.grid(True, alpha=0.3)
plt.xlim(-2, 10)
plt.ylim(-2, 8)
plt.title("🤖 Мой первый робот на экране!")
plt.xlabel("X координата")
plt.ylabel("Y координата")
plt.legend()
plt.show()

print("✅ Тест завершен! Робот нарисован!")

# Дополнительное задание: попробуйте разные цвета и размеры
print("\n🎨 ДОПОЛНИТЕЛЬНОЕ ЗАДАНИЕ:")
print("Создайте еще одного робота с другим цветом и размером!")

# TODO: Создайте второго робота
second_robot = Robot("___", ___, ___, "___")

plt.figure(figsize=(8, 6))
# TODO: Нарисуйте второго робота с большим размером
second_robot.draw(size=___)

plt.grid(True, alpha=0.3)
plt.xlim(-2, 10)
plt.ylim(-2, 8)
plt.title("🤖🤖 Два робота на экране!")
plt.xlabel("X координата")
plt.ylabel("Y координата")
plt.legend()
plt.show()

print("🎉 Отлично! Теперь вы умеете рисовать роботов!")
```
