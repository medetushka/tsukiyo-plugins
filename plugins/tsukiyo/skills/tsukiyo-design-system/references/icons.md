# Иконки Tsukiyo

Один стиль: outline, линия 1.5, кадр 24 × 24, скругленные концы. Имена `Категория / Имя`.
Страница Design System, секция «Icons & Logo» (`91:5113`).

- Вставка: `(await figma.getNodeByIdAsync(id)).createInstance()` или `importComponentByKeyAsync(key)`.
- Цвет: у инстанса найти слой `icon` и задать `strokes` с переменной `color/*` (по умолчанию `color/text`). У `Status / Star Filled` — заливка и обводка `color/warning`.
- В компонентах иконка подключается свойством Instance swap (Stat card → Icon, Tab bar/Item → Icon).
- Размер в UI — 24; в Rating звёзды 16. На мобилке иконку-кнопку оборачивать в зону 44 × 44.

| Иконка | Node id | Key | Где |
|---|---|---|---|
| Navigation / Home | `91:5121` | `f66026bd3cd5363bedea2a085a6b16e481314c58` | Tab bar «Главная» |
| Navigation / Catalog | `91:5131` | `f8e5544cdcb12747d799a2a5d73de4fcbfbf5072` | Tab bar «Каталог» |
| Navigation / Courses | `91:5139` | `3a3acf0f4435c6866cf39eaed85d40d65f7ced64` | Tab bar «Мои курсы» |
| Navigation / Profile | `91:5147` | `c171c84d4659d2644e0f1c4e6e61f01dbc90a57c` | Tab bar «Профиль» |
| Navigation / Menu | `91:5154` | `a4eb175397556705e5d8cb17662861e8a29eea4d` | действие в App bar Back |
| Navigation / Chevron Left | `91:5161` | `bd1231ce340825ac3cadb615aa06922e33bf1ba7` | назад в App bar, Pagination Prev |
| Navigation / Chevron Right | `91:5168` | `066597951904890ad039c428e4bdbafd9465bd80` | Pagination Next, строки списков |
| Navigation / Arrow Left | `91:5175` | `3904a9713f87e2343278ff19f675a1596255cc33` | «Вернуться» в формах |
| Navigation / Close | `91:5182` | `29b28629c1196b05b73f323d3456ea9a4c6ee281` | закрыть Modal, Toast, поиск |
| Navigation / Search | `91:5190` | `9cf4f102dc74fd94549e9db3c94e1fae4d0c8e85` | поиск |
| Navigation / Bell | `91:5198` | `44ed0a5228cb827083ca6bd0acb7f7f2fac05597` | уведомления |
| Navigation / Settings | `91:5208` | `e3d70cf18203619275d828a67e1a9fbdb3a09c6b` | настройки, фильтры каталога |
| Action / Play | `91:5215` | `34b928b55c9dd8740a68490bb2244772db58e2cb` | запуск видеоурока |
| Action / Check | `91:5222` | `6de8d939aa6a40ec84bcd82b72fa9656fef71856` | пройдено, верный ответ |
| Action / Plus | `91:5229` | `736a71e647e7b370383c805540b2aa45fa1dabc0` | добавить |
| Action / Send | `91:5236` | `d2b5ea89013824a4e35471b19a79993bdc429e5d` | отправить вопрос, чат |
| Action / Edit | `91:5243` | `88a5f0da2800e273ad39eff8795f22df970140d1` | редактировать профиль |
| Action / Logout | `91:5250` | `5e98ca49ea1bc2edaa8bbd95edca5896890520bb` | выход |
| Action / Filter | `91:5257` | `99bc577a979a4ae1d6688a259a7323da914ac290` | фильтры каталога |
| Action / Chat | `91:5303` | `c8331b99fcbaff1a01a9efefa35425eaf4c280c1` | Chat button |
| Status / Star | `91:5264` | `ef28363d35d31f60bec4bf40d5e0b50e92b383bf` | пустая звезда Rating |
| Status / Star Filled | `91:5308` | `d4968df7a7a16fdbde2242abbdc9165dcc5ffabf` | заполненная звезда Rating |
| Status / Lock | `91:5272` | `667cfed70da402be99a11831cdd12b051261a836` | заблокированный урок, достижение |
| Status / Info | `91:5280` | `744ed5f0511e9a7c25e2087eadaeeb9b44129d21` | подсказка, Alert Info |
| Status / Alert | `91:5288` | `56b6dff4c307e650ffe955d6269a368222dca93c` | предупреждение |
| Status / Clock | `91:5296` | `96232b26707a4d29efcb42b13b43ec3f893b55eb` | длительность, расписание |

Нужной иконки нет — не рисуй новую на экране. Скажи, какой не хватает, и предложи ближайшую из списка.
