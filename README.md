# Тестовое задание программиста С++

Данное тестовое задание представляет собой написание одной большой программы в несколько этапов. Каждый этап - новая версия программы с расширением ее функционала.

Необходимо создать новый репозиторий на GitHub, в котором каждый коммит будет решением соответствующей задачи и новой итерацией/версией программы (если коммитов много, то допустимо использовать теги для отметки решения конкретных заданий).

В качестве решения должна быть прикреплена ссылка на публичный репозиторий для возможности задать вопросы по заданию или реализации текущей версии программы. Сборка программы должна совершаться с помощью qmake.

Для обратной связи и вопросов дополнительно можно использовать электронную почту: [programmer.niisk@gmail.com](programmer.niisk@gmail.com)

## Основные задачи

### Задача 1

##### Дано

Два манипулятора, которые с помощью кода двигаются по определенным координатам, для сборки того или иного компонента, описываются стартовыми центрами O1 и O2 и радиусом их действия R1 и R2 в декартовой системе координат. Радиус действия не изменяется в течение работы программы.

Также дан массив точек, где лежат детали P1…Pn. Координаты точек должны быть описаны в отдельном текстовом файле (должно быть указано 5 точек, как минимум). Синтаксис файла с точками на усмотрение программиста.

До детали должен дойти оптимальный манипулятор на текущей итерации процесса. Оптимальность определяется по расстоянию от центра текущего
положения манипулятора до точки. Если точка лежит вне радиусов действия обоих манипуляторов, то оба манипулятора остаются на месте.

##### Задача

Распарсить файл с координатами точек и вывести в консоли две строки, в каждой из которых будет указано какие точки обойдет каждый манипулятор. Использованный файл с точками необходимо прикрепить.

##### Пример

Массив точек:

```
{ 1 , 3 } , { 2 , 1.41 } , { 0.2 , -7 } , { -5 , -1 } , { 0, 9 }
```

Манипуляторы на старте:

```
M1 - ({ 0, 0 }, 8 )
```

```
M2 - ({ 2, 1 }, 10 )
```

Результат:

| Итерация         | 1         | 2            | 3            | 4            | 5            |
| ------------------------ | --------- | ------------ | ------------ | ------------ | ------------ |
| Манипулятор 1 | {0,0}     | {0,0}        | { 0.2 , -7 } | { 0.2 , -7 } | { 0.2 , -7 } |
| Манипулятор 2 | { 1 , 3 } | { 2 , 1.41 } | { 2 , 1.41 } | { -5 , -1 }  | { -5 , -1 }  |

---

### Задача 2

Добавить к предыдущей версии программы графический интерфейс (**предпочтительнее** **QML**).

В интерфейсе должны присутствовать следующие поля:

* Поле ввода для начальной координаты Х Манипулятора 1
* Поле ввода для начальной координаты Y Манипулятора 1
* Поле ввода для начальной координаты Х Манипулятора 2
* Поле ввода для начальной координаты Y Манипулятора 2
* Поле ввода радиуса действия Манипулятора 1
* Поле ввода радиуса действия Манипулятора 2
* Поле для отображения текущей координаты Х Манипулятора 1
* Поле для отображения текущей координаты Y Манипулятора 1
* Поле для отображения текущей координаты X Манипулятора 2
* Поле для отображения текущей координаты Y Манипулятора 2
* Кнопка « *начать чтение файл*а »

При нажатии на кнопку « *начать чтение файла* », в полях с текущими координатами манипуляторов должны установиться начальные координаты, установленные в соответствующих полях. Затем через 3 секунды должен начаться парсинг файла с массивом точек из предыдущего задания. Парсинг  каждой новой точки должен происходить с интервалом в 3 секунды и при изменении координат манипуляторов должны меняться поля с текущим положением соответствующего манипулятора в реальном времени (интервал в 3 секунды, соответственно, нужен для фиксирования изменения координаты).

При дополнительных нажатиях на кнопку « *начать чтение файла* », повторяются те же действия.

---

### Задача 3

Добавить в графический интерфейс из предыдущего задания следующие поля:

* Поле текущей координаты Х Манипулятора 1 (обратная связь)
* Поле текущей координаты Y Манипулятора 1 (обратная связь)
* Поле текущей координаты X Манипулятора 2 (обратная связь)
* Поле текущей координаты Y Манипулятора 2 (обратная связь)

Необходимо добавить в программу функционал ModbusTCPMaster, который отправляет на Slave-программу данные о **текущем** состоянии координат, после чего считывает из Input-регистров обработанные данные и отображает их в соответствующих добавленных полях (предполагается, что Slave имитирует сам манипулятор, реализует простую обработку полученных данных, например, умножение на 2, и отправляет обработанные данные обратно Master'у).

Дополнительно необходимо создать еще один репозиторий с кодом Slave-программы. ***Использование сегментов кода из Примеров программ внутри QtCreator НЕ возбраняется.***

---

## Дополнительные задачи

Данные задачи являются опциональными и их выполнение н несет такой же приоритет как выполнение основных.

### Доп.задача 1 (задача *)

Добавить отображение координатной плоскости с отрисовкой пути, который пройдет каждый манипулятор. Допустима отрисовка обоих путей на одной плоскости или отображение двух координатных плоскостей для каждого манипулятора.

---

### Доп.задача 2 (задача **)

Добавить в отрисовку пути плавную анимацию с перемещением соответствующих манипуляторов.
