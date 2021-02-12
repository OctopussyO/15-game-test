# Пятнашки
<img align="right" height="400px" src="https://psv4.userapi.com/c536236/u1190603/docs/d26/8539367584f3/15.png?extra=6AOFknrflZ4_oMbfHalGCxjiDBk9CMEFbQJimLnv8gSrMNC_-74Rlzx7t3RocIe4G44r6ilSD273v9hZTnyDVUALk1HG3sYRAo1MSE_IEGogkATNLa8HLlZGfjAVVca-jPbsScp3GJtlSvC2vFM" alt="Иллюстрация к проекту">

**Цель игры** — перемещая костяшки по коробке, добиться упорядочивания их по номерам, желательно сделав как можно меньше перемещений.

Ознакомиться с приложением можно по [ссылке](https://15-game-test.netlify.app/ 'Ссылка')

### Функциональность

Реализовано:
- перемешивание костяшек при старте новой игры и [проверка](https://ru.wikipedia.org/wiki/%D0%98%D0%B3%D1%80%D0%B0_%D0%B2_15#%D0%9C%D0%B0%D1%82%D0%B5%D0%BC%D0%B0%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B5_%D0%BE%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5 'Википедия') на решаемость комбинации
- анимированное перемещение костяшек [средствами](https://ru.vuejs.org/v2/guide/transitions.html, 'Анимация') Vue.js
- таймер при запуске новой игры
- уведомления при решении и по истечении времени
- "дизайн" в стиле Glassmorphism

### Используемый стек
[![JavaScript](https://img.shields.io/badge/-JavaScript-464646??style=flat-square&logo=javascript)](https://www.javascript.com/)
[![Vue.js](https://img.shields.io/badge/-Vue.js-464646??style=flat-square&logo=vue.js)](https://ru.vuejs.org/)
[![Nuxt.js](https://img.shields.io/badge/-Nuxt.js-464646??style=flat-square&logo=nuxt.js)](https://https://nuxtjs.org/)
[![SCSS](https://img.shields.io/badge/-SCSS-464646??style=flat-square&logo=scss)](https://https://sass-scss.ru/)
[![CSS](https://img.shields.io/badge/-CSS-464646??style=flat-square&logo=css3)](https://www.w3.org/Style/CSS/specs.ru.html)
[![HTML](https://img.shields.io/badge/-HTML-464646??style=flat-square&logo=HTML5)](https://www.w3.org/TR/html52/introduction.html#introduction)
[![Netlify](https://img.shields.io/badge/-Netlify-464646??style=flat-square&logo=netlify)](https://https://www.netlify.com/)

### Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).

### Планы по доработке:
- добавить кнопки паузы/возобновления игры
- пересмотреть количество необходимых стейтов для уведомлений
