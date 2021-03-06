---
title: Background
localeTitle: Задний план
---
## Background

Свойство background позволяет использовать изображения и цвета для создания фонов для ваших веб-страниц.

### Background Color

Свойство background color позволяет вам выбрать цвет вашего элемента. Это может быть фон для всей страницы или фон одного раздела вашей страницы.

*   Элемент представляет собой часть HTML, такую как заголовок или абзац на веб-странице.

Вот пример установки цвета фона для веб-страницы на зеленый.

```css
  body { 
    background-color: green; 
  } 
```

![fullbackground](https://user-images.githubusercontent.com/26467304/31036038-845567f2-a538-11e7-8e6c-8a52bb0d44b8.png)

Ниже приведен пример установки цветов для двух элементов. Это установит фон заголовка фиолетовый, а остальная часть страницы - синяя.

```css
  body { 
    background-color: blue; 
  } 
  h1 { 
    background–color: purple; 
  } 
```

![twobackground](https://user-images.githubusercontent.com/26467304/31036152-0607936a-a539-11e7-9e9f-a5e60ade042d.png)

Цвет CSS можно определить тремя способами:

*   Допустимое имя цвета, такое как `blue`
*   Значение HEX, такое как `#FFFFF` (это шестнадцатеричное значение для белого).
*   Значение RGB, такое как `rgb(76,175,80)` (Это значение RGB для светло-зеленого.)

### Фоновые изображения

Вы можете использовать свойство background image для установки изображения в качестве фона для элемента. Изображение повторяется по умолчанию, так что оно охватывает весь элемент.

```css
body { 
  background-image: url("barn.jpg"); 
 } 
```

![образ](https://user-images.githubusercontent.com/26467304/31036366-eb1fc260-a539-11e7-835d-e3f935a22c86.png)

Вы также можете связать фотографии или gif, которые вы найдете в Интернете, используя их ссылку (т. Е. Из изображений Google для поиска).

```css
body { 
  background-image: url("https://mdn.mozillademos.org/files/11983/starsolid.gif"); 
 } 
```

### Фоновый рисунок - свойство повтора

Фоновое изображение повторяется как по вертикали (вверх и вниз), так и по горизонтали (по веб-странице) по умолчанию. Вы можете использовать свойство background-repeat для повторения изображения по вертикали или по горизонтали.

Вот пример, который повторяет изображение по вертикали.

```css
body { 
  background-image: url("barn.jpg"); 
  background-repeat: repeat-y; 
 } 
```

![вертикальный](https://user-images.githubusercontent.com/26467304/31039770-8962c7a6-a54e-11e7-9d25-4fb09760d219.PNG)

Вы можете повторить изображение по горизонтали, установив для свойства background-repeat значение «repeat-x».

```css
body { 
  background-image: url("barn.jpg"); 
  background-repeat: repeat-x; 
 } 
```

Вы также можете использовать свойство background-repeat, чтобы установить, что изображение не повторяется.

```css
body { 
  background-image: url("barn.jpg"); 
  background-repeat: no-repeat; 
 } 
```

![norepeat](https://user-images.githubusercontent.com/26467304/31039801-c8761efc-a54e-11e7-8bb9-ec5b88885a50.PNG)

### Фоновое изображение - свойство позиции

Вы можете использовать свойство position, чтобы указать, где ваше изображение будет расположено на веб-странице.

```css
body { 
  background-image: url("barn.jpg"); 
  background-repeat: no-repeat; 
  background-position: right top; 
 } 
```

![позиция](https://user-images.githubusercontent.com/26467304/31039828-077d1038-a54f-11e7-8aa6-092253ca92b8.PNG)

### Фоновое изображение - фиксированное положение

Вы можете использовать свойство background-attachment для установки изображения в фиксированную позицию. Фиксированное положение делает его таким, чтобы изображение не прокручивалось вместе с остальной частью страницы.

```css
body { 
  background-image: url("barn.jpg"); 
  background-repeat: no-repeat; 
  background-position: right top; 
  background-attachment: fixed; 
 } 
```

![фиксированный](https://user-images.githubusercontent.com/26467304/31039859-39612c92-a54f-11e7-93ca-9d7bcb938225.PNG)

### Фоновые градиенты

Градиент - это переход между двумя или более цветами и может использоваться с помощью CSS, аналогичного фоновому изображению.

Синтаксис фона градиента может быть довольно сложным и часто по-прежнему используется с префиксами поставщиков из-за несоответствий между поддерживаемыми браузерами.

[Редактор Colorzilla Gradient Editor](http://www.colorzilla.com/gradient-editor/) - отличный инструмент для создания пользовательских градиентов и связанной с ним разметки css.

### Фон - стенографическая собственность

Вы можете написать свойства фона в одной строке. Это называется сокращенной собственностью.

```css
body { 
  background: url("barn.jpg") no-repeat right top; 
 } 
```

Вы можете оставить свойства, которые вам не нужны при использовании сокращенного свойства, но свойства должны использоваться в определенном порядке. Заказ:

*   цвет
*   образ
*   повторение
*   прикрепление
*   позиция

### Несколько фоновых изображений

Вы можете указать несколько фоновых изображений в одном свойстве фона.

```css
body { 
  background: url("barn.jpg"), url("stars.jpg"), linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)); 
 } 
```

Первое заданное изображение (или градиент) больше всего на вершине, второе - после и так далее. Если один из элементов не является правильным из-за его URL-адреса или его синтаксиса, вся строка будет игнорироваться браузером.

### Некоторые базовые свойства фона CSS

Свойства фона CSS используются для определения фоновых эффектов для элементов.

Свойства фона CSS: фоновый цвет изображение на заднем плане фон-повторить фон-вложение фон положение

Вы можете обратиться к следующей ссылке в школах W3, чтобы узнать больше о фоновых и связанных с ними материалах в CSS. [Фоновая ссылка на W3](https://www.w3schools.com/css/css_background.asp)

### Другие источники

*   [Список значений цвета](http://cloford.com/resources/colours/500col.htm)
*   [Инструмент выбора цвета](http://colrd.com/create/palette/)
