# 📌 Урок: Переключение светлой и тёмной темы на сайте

## 📅 Что делаем на уроке?

На этом уроке мы:

* Создадим кнопку для смены темы
* Научимся добавлять и удалять классы через JS
* Сохраним выбор пользователя в `localStorage`, чтобы тема запоминалась

---

## 🔦 Что такое тема сайта?

У сайта может быть **тёмная тема** (как сейчас у нас — фон тёмный, текст светлый) и **светлая тема** (белый фон, тёмный текст). Мы сделаем так, чтобы пользователь мог сам выбрать, что ему удобнее.

---

## 🧱 Шаг 1. HTML — кнопка для переключения

Добавим кнопку в `index.html`, например в header или внутри `#lesson-content`:

```html
<button id="themeToggle" class="btn btn-outline-light mt-3">Сменить тему</button>
```

---

## 🎨 Шаг 2. CSS классы для светлой темы

Добавим стиль, который будет включаться при активации светлой темы:

```css
body.light-theme {
  background: radial-gradient(circle at top left, #f0f0f0, #ffffff);
  color: #1a1a1a;
}

body.light-theme header {
  background: linear-gradient(90deg, #ffd700, #ffa500);
}

body.light-theme .card,
body.light-theme #lesson-content,
body.light-theme footer {
  background-color: rgba(0, 0, 0, 0.05);
  color: #000;
}

body.light-theme .btn-outline-light {
  color: #333;
  background-color: #ffffff;

}

body.light-theme .btn-outline-light:hover {
  background-color: #ffffff;
  color: rgb(0, 0, 0);
}
```

---

## 💡 Шаг 3. JS — переключение темы

В `script.js` добавим:

```js
const toggleBtn = document.getElementById('themeToggle');

// Проверяем, есть ли сохранённая тема
if (localStorage.getItem('theme') === 'light') {
  document.body.classList.add('light-theme');
}

// При клике — переключаем тему
toggleBtn.addEventListener('click', () => {
  document.body.classList.toggle('light-theme');

  // Сохраняем тему в localStorage
  if (document.body.classList.contains('light-theme')) {
    localStorage.setItem('theme', 'light');
  } else {
    localStorage.setItem('theme', 'dark');
  }
});
```

---

## ✅ Что мы узнали?

* Как создавать переключатели тем на сайте
* Как добавлять классы к `body`
* Как сохранять выбор пользователя с помощью `localStorage`

🎉 Теперь твой сайт ещё удобнее — пользователь может выбрать, как ему комфортно работать: в темноте или на свету!
