# 📌 Урок: Таймер с изменением фона

## 📅 Что делаем на уроке?

На этом занятии мы сделаем секундомер, который:

* запускается по кнопке
* считает секунды
* каждые 5 секунд меняет цвет фона
* останавливается по кнопке "Стоп"

Очень весело, ярко и полезно — всё, что надо для практики JavaScript!

---

## 🧱 Шаг 1. Вёрстка

Создаём структуру в `index.html`:

```html
<div class="container">
  <h1>Секундомер</h1> <!-- Заголовок -->
  <p>Прошло секунд: <span id="seconds">0</span></p> <!-- Здесь будет показываться время -->

  <button id="startBtn">Старт</button> <!-- Кнопка запуска -->
  <button id="stopBtn">Стоп</button>  <!-- Кнопка остановки -->
</div>
```

> Здесь у нас есть два элемента:
>
> * `#seconds` — сюда будем выводить количество секунд
> * две кнопки для запуска и остановки таймера

---

## 📎 Шаг 2. Подключаем JS

Создаём файл `timer.js` и не забываем подключить его внизу `index.html`:

```html
<script src="timer.js"></script> <!-- Подключаем наш JS-файл -->
```

---

## 🔁 Шаг 3. Секундомер

В `timer.js` пишем:

```js
let seconds = 0; // Переменная, в которой будем хранить количество секунд
let timer = null; // Сюда положим ID таймера, чтобы потом его остановить

// Получаем элементы со страницы
const secondsDisplay = document.getElementById('seconds'); // span, в который пишем время
const startBtn = document.getElementById('startBtn'); // кнопка Старт
const stopBtn = document.getElementById('stopBtn');   // кнопка Стоп
const main = document.querySelector('main');

// Массив с цветами, которые будут меняться
const colors = ['#FF6B6B', '#FFD93D', '#6BCB77', '#4D96FF', '#C084FC'];
let colorIndex = 0; // Индекс текущего цвета

// Функция, которая запускается каждую секунду
function updateTimer() {
  seconds++; // Увеличиваем счётчик секунд на 1
  secondsDisplay.textContent = seconds; // Обновляем текст в span

  // Проверяем: если секунд кратно 5 (то есть каждые 5 секунд)
  if (seconds % 5 === 0) {
    main.style.backgroundColor = colors[colorIndex]; // Меняем фон на текущий цвет
    colorIndex = (colorIndex + 1) % colors.length; // Переходим к следующему цвету по кругу
  }
}

// Обработчик кнопки Старт
startBtn.addEventListener('click', () => {
  if (timer === null) { // Запускаем таймер, только если он ещё не работает
    timer = setInterval(updateTimer, 1000); // Каждую секунду вызываем updateTimer
  }
});

// Обработчик кнопки Стоп
stopBtn.addEventListener('click', () => {
  clearInterval(timer); // Останавливаем таймер
  timer = null; // Сбрасываем переменную, чтобы можно было снова запустить
});
```

---

## 🎨 Шаг 4. Немного стилей

Добавим в `style.css`:

```css
body {
  transition: background-color 0.5s; /* Плавная смена цвета */
  font-family: sans-serif; /* Шрифт */
  text-align: center; /* Центрируем текст */
  margin-top: 50px; /* Отступ сверху */
}
button {
  padding: 10px 20px; /* Размеры кнопки */
  margin: 10px; /* Отступ между кнопками */
  font-size: 16px; /* Размер текста */
  cursor: pointer; /* Курсор-рука при наведении */
}
```

---

## ✅ Что мы узнали?

* Как использовать `setInterval` и `clearInterval` — запуск и остановка повторяющихся действий
* Как менять текст на странице через `textContent`
* Как менять цвет фона и работать с массивом
* Как отслеживать нажатия кнопок с помощью `addEventListener`

---

💡 Этот урок можно легко расширить:

* добавить кнопку сброса секунд
* сделать пользовательский выбор цвета
* вывести лог всех изменений

🎉 Урок завершён! Отличная работа!
