
````markdown
# 📘 LaTeX-шаблон для домашних по математике (VS Code + TeX Live)

Этот проект — аккуратный шаблон для домашних заданий по математике  
с автоматической нумерацией задач, удобными математическими командами  
и возможностью считать прямо в LaTeX через SymPy.

---

# 🚀 Требования

## 1️⃣ TeX Live (рекомендуется Full)

Установите **TeX Live Full**, чтобы не возникало ошибок отсутствующих пакетов.

Проверка:
```bash
latexmk -v
````

---

## 2️⃣ VS Code + LaTeX Workshop

1. Установите VS Code
2. Extensions → установите **LaTeX Workshop (James Yu)**
3. Откройте папку проекта
4. Откройте `main.tex`
5. Нажмите:

* `Ctrl + Alt + B` — собрать
* `Ctrl + Alt + V` — открыть PDF

---

# 📄 Структура документа

## Заголовок

Редактируется здесь:

```latex
\title{Линейная алгебра\\ \large Домашнее задание 5}
\author{Ваше имя}
\affil{Группа}
\date{\today}
```

Выводится через:

```latex
\maketitle
```

---

# 🧮 Автоматическая нумерация задач

## Новая задача

```latex
\task
```

Результат:

```
Задача 1.
Задача 2.
Задача 3.
```

Нумерация увеличивается автоматически.

---

## Задача с названием

```latex
\task[Теорема о ранге]
```

Вывод:

```
Задача 4. Теорема о ранге
```

---

## Ссылка на задачу

```latex
\task
\label{t:example}

См. задачу \ref{t:example}.
```

---

# ✍ Оформление решения

## Решение

```latex
\begin{solution}
Текст решения...
\end{solution}
```

Вывод:

**Решение:** текст

---

## Ответ

```latex
\begin{answer}
42
\end{answer}
```

Вывод:

**Ответ:** 42

---

# 🔢 Математические множества

| Команда | Результат |
| ------- | --------- |
| `\R`    | ℝ         |
| `\Q`    | ℚ         |
| `\Z`    | ℤ         |
| `\N`    | ℕ         |
| `\C`    | ℂ         |
| `\F`    | 𝔽        |

Пример:

```latex
$x \in \R$
```

---

# 📊 Математические операторы

| Команда | Значение |
| ------- | -------- |
| `\ord`  | ord      |
| `\Ima`  | Im       |
| `\Rea`  | Re       |
| `\rk`   | rk       |
| `\tr`   | tr       |
| `\spec` | spec     |
| `\grad` | grad     |
| `\Mat`  | Mat      |

Пример:

```latex
\rk A = 3
```

---

# 🔍 Частные производные

```latex
\p{f}{x}
```

Результат:

∂f / ∂x

---

# ∑ Сумма

```latex
\Sum{i=1}{n}
```

Пример:

```latex
\Sum{i=1}{n} i
```

---

# lim Предел

```latex
\Lim{x}{0}
```

Пример:

```latex
\Lim{x}{0} \frac{\sin x}{x}
```

---

# 📐 Межстрочный интервал

```latex
\onehalfspacing
```

Полуторный интервал.

---

# 📄 Геометрия страницы

```latex
\usepackage[margin=2cm]{geometry}
```

Поля по 2 см.

---

# ➕ Как добавить новую команду

В блоке математических команд:

```latex
\newcommand{\Ker}{\operatorname{Ker}}
```

Использование:

```latex
\Ker A
```

---

# ➕ Как добавить новый оператор

```latex
\DeclareMathOperator{\diam}{diam}
```

---

# ⚠ Что не рекомендуется менять

* `amsmath`
* `amssymb`
* счётчик `task`
* базовую структуру документа

---

````markdown
# 📊 Графики в LaTeX (2D и 3D)

В шаблоне уже подключены:

- `tikz`
- `pgfplots`
- автоматический стиль для 2D
- автоматический стиль для 3D

Ничего дополнительно подключать не нужно.

---

# 📈 2D Графики

## ✅ Базовый график функции

```latex
\begin{tikzpicture}
\begin{axis}
\addplot {x^2};
\end{axis}
\end{tikzpicture}
````

Стиль применяется автоматически:

* оси по центру
* сетка
* аккуратные подписи
* толстые линии
* одинаковый размер

---

## 📌 Несколько графиков

```latex
\begin{tikzpicture}
\begin{axis}[legend pos=north west]
\addplot {x^2};
\addplot {x};
\legend{$x^2$, $x$}
\end{axis}
\end{tikzpicture}
```

---

## 📍 График по точкам

```latex
\begin{tikzpicture}
\begin{axis}
\addplot coordinates {
    (0,0)
    (1,1)
    (2,4)
    (3,9)
};
\end{axis}
\end{tikzpicture}
```

---

## 📊 Настройка диапазона

```latex
\begin{axis}[
    xmin=-5, xmax=5,
    ymin=-2, ymax=10
]
```

---

# 🌈 3D Графики

Для 3D используется стиль `3dstyle`.

---

## ✅ Поверхность

```latex
\begin{tikzpicture}
\begin{axis}[3dstyle]
\addplot3[
    surf,
    domain=-2:2,
]
{x^2 + y^2};
\end{axis}
\end{tikzpicture}
```

Включено автоматически:

* угол обзора
* цветовая шкала
* colormap (viridis)
* сглаживание поверхности
* сетка
* нормальный масштаб

---

## 🔄 Изменить угол обзора

```latex
\begin{axis}[3dstyle, view={45}{40}]
```

---

## 🎨 Убрать цветовую шкалу

```latex
\begin{axis}[3dstyle, colorbar=false]
```

---

## 🗺 Контурный график (вид сверху)

```latex
\begin{tikzpicture}
\begin{axis}
\addplot3[
    contour gnuplot,
    domain=-2:2,
]
{x^2 + y^2};
\end{axis}
\end{tikzpicture}
```

---

# ⚡ Полезные параметры

| Параметр         | Что делает        |
| ---------------- | ----------------- |
| `domain=a:b`     | диапазон по x     |
| `samples=100`    | гладкость         |
| `legend pos=...` | положение легенды |
| `xmin, xmax`     | диапазон оси X    |
| `ymin, ymax`     | диапазон оси Y    |
| `view={a}{b}`    | угол 3D           |

---

# 🚀 Рекомендации

* Для функций → используйте 2D стиль
* Для поверхностей → `3dstyle`
* Для линейной алгебры (плоскости, векторы) → 3D стиль + `addplot3`
* Для отчётов используйте одинаковые размеры (они уже заданы автоматически)

---

# 🛠 Если график не собирается

Проверьте:

```bash
latexmk -pdf main.tex
```

Если ошибка про пакет — значит TeX Live установлен не полностью.

---

# 🧠 Быстрые вычисления в LaTeX (SymPy)

Используется расширение:

**Latex Sympy Calculator**
Marketplace:
[https://marketplace.visualstudio.com/items?itemName=OrangeX4.latex-sympy-calculator](https://marketplace.visualstudio.com/items?itemName=OrangeX4.latex-sympy-calculator)

---

## 📦 Установка расширения

VS Code → Extensions → найти
**Latex Sympy Calculator** → Install

---

## ⚠ Требуется Python

Установите Python с python.org (не из Microsoft Store!)

Затем:

```powershell
python -m pip install latex2sympy2
python -m pip install Flask
```

Проверка:

```powershell
python
>>> import latex2sympy2
>>> import flask
```

---

# ⌨ Горячие клавиши Sympy Calculator

Выделите выражение в LaTeX и нажмите:

| Комбинация       | Действие               |
| ---------------- | ---------------------- |
| Shift+Ctrl+Alt+E | дописать `= результат` |
| Shift+Ctrl+Alt+R | заменить на результат  |
| Shift+Ctrl+Alt+N | численный результат    |
| Shift+Ctrl+Alt+F | факторизация           |
| Shift+Ctrl+Alt+X | раскрыть скобки        |
| Shift+Ctrl+Alt+T | rref (матрицы)         |
| Shift+Ctrl+Alt+D | задать переменную      |
| Shift+Ctrl+Alt+P | выполнить Python-код   |

---

# 🔄 Workflow для ДЗ

1. Написать `\task`
2. Оформить решение
3. Вычислить сложные выражения через SymPy
4. Написать `\begin{answer}`
5. Перейти к следующей задаче

---

# 🛠 Сборка вручную

```bash
latexmk -pdf main.tex
```

---

# 📁 Рекомендуемая структура проекта

```
project/
│
├── main.tex
├── README.md
└── (опционально) figures/
```

