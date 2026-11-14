---
name: tsukiyo-design-system
description: "v1.1.0 — Сборка макетов в Figma на дизайн-системе Tsukiyo (edtech, ночь/луна, тёмная тема, десктоп 1440 и мобилка 390): каталог компонентов, иконки, логотип, токены цвета/отступов/радиусов, моды Desktop/Mobile, текстовые стили, правила консистентности. Use when building any Tsukiyo screen in Figma for desktop or mobile — sign in, sign up, onboarding, home, catalog, course, checkout, lesson, quiz, profile, settings, modal, bottom sheet, toast, empty/error/loading state; when choosing a component, icon, color, spacing or text style; when reviewing a Tsukiyo mockup. Собери экран, сделай мобильную версию, сделай макет, добавь состояние ошибки."
---

# Дизайн-система Tsukiyo — как собирать макеты

Tsukiyo (月夜, «лунная ночь») — учебная платформа. Настроение: ночное небо, луна, тонкие красные линии.
Файл-источник: Karsakbayev Medet — Tsukiyo, fileKey `ASsAM4YvBYzXIcNnqAA16j`.
Страницы файла: **Design System** (мастер-компоненты, id `16:49`), **Design** (экраны, id `21:2002`), **UX Research**.

## Как устроен скилл

| Справочник | Что внутри | Когда открывать |
|---|---|---|
| references/keys.md | компоненты: node id, key, свойства и значения | пишешь скрипт сборки, вставляешь инстанс |
| references/icons.md | иконки: имена, id, ключи | нужна иконка |
| references/tokens.md | переменные, моды Desktop/Mobile, текстовые и эффект-стили, сетка | красишь, ставишь отступы, текст, тени |
| references/patterns.md | шаблоны экранов десктоп и мобилка, нейминг, состояния, прототип | собираешь новый экран или модуль |
| references/changelog.md | история версий | дописываешь версию |

## Платформа и тема

| | Десктоп | Мобилка |
|---|---|---|
| Фрейм | 1440 × 900 (выше — по контенту) | 390 × 844 (выше — по контенту) |
| Мода `Platform` на фрейме | `Desktop` | `Mobile` |
| Поля страницы `layout/margin` | 80 | 16 |
| Сетка | `Grid/Desktop 12 col` | 4 колонки, поля 16, gutter 16 |
| Навигация | Header + Footer | Status bar + App bar сверху, Tab bar снизу |
| Модалка | Modal 480 по центру | Bottom sheet во всю ширину снизу |

- Мода переключается одной строкой на корневом фрейме: `frame.setExplicitVariableModeForCollection(platformCollection, mobileModeId)`. Размер заголовков (`Display`, `H1`–`H3`), `layout/margin`, `layout/gutter`, `layout/section-gap` меняются сами. Отдельных «мобильных» стилей и компонентов-копий не делать.
- Только **тёмная тема**: одна мода `Night`. Светлой темы в продукте нет — не делай её.
- Язык интерфейса — русский; текстовые стили проверены на казахском (ә, ғ, қ, ң, ө, ұ, ү, һ, і).

## Железные правила

1. **Сначала компоненты системы.** Всё, что есть в каталоге ниже, вставляется только инстансом (`importComponentByKeyAsync(key)` из библиотеки или `getNodeByIdAsync(id).createInstance()` внутри файла-источника). Причина: правки мастера должны доезжать до всех экранов.
2. **Не детачить инстансы.** Нет нужного состояния — скажи об этом и предложи добавить вариант в мастер; не рисуй копию.
3. **Никаких сырых значений.** Цвет — только переменные `color/*`, отступы и gap — `spacing/*` и `layout/*`, радиусы — `radius/*`, текст — стили `Tsukiyo/*`, тени и свечение — эффект-стили `Tsukiyo/Glow/*`, `Tsukiyo/Shadow/Card`. Нужна полупрозрачность — бери готовый альфа-токен (`color/text-a60`, `color/error-a10`…), а не opacity на заливке.
4. **Примитивы (`moon/*`, `night/*`, `red/*`…) напрямую не использовать** — только через семантику `color/*`.
5. **Заголовки — Cormorant Garamond** (`Tsukiyo/Display`, `H1`–`H3`), **весь UI-текст — Inter** (`Body`, `Small`, `Caption`, `Label`, `Button`). Не смешивать.
6. **Одно главное действие на экран** — `Button Type=Primary`. Второе действие — `Secondary` или `Text`. Удаление/выход — `Destructive`.
7. **Ошибка поля — фирменная «трещина»**: `Input State=Error` или `Text area State=Error` (ломаная красная линия под полем + `Glow/Error`) + текст ошибки в helper. Не заменять обычной красной рамкой.
8. **Загрузка — луна**: `Moon/Loader` или `Button State=Loading`. Не использовать стандартные спиннеры.
9. **Форматы**: цены в тенге — `4 990 ₸` (пробел-разделитель тысяч, знак после числа); даты — `DD.MM.YYYY`.
10. **Фокус** всегда виден: `State=Focus` у Input/Text area/Button даёт `Glow/Focus`.
11. Перед созданием экрана проверь, нет ли уже фрейма с таким именем `Module / Screen / State`. Есть — правь его или спроси, заменять ли; при замене перенеси на новый экран все входящие и исходящие связи прототипа, потом удали старый. Причина: дубли путают флоу и ломают прототип.
12. **Иконки только из пака** (`references/icons.md`), outline 1.5, 24 × 24. В компонентах — через свойство Instance swap, цвет — override обводки переменной `color/*`. Не рисовать иконки векторами и не брать из других паков.
13. **Логотип — только компонент Logo**: `Type=Full` в Header и на экранах входа, `Type=Mark` в App bar. Не набирать «Tsukiyo» текстом.
14. **Мобилка**: тач-зона любого нажимаемого элемента не меньше 44 × 44 (`size/touch`); в одной строке не больше 2 карточек; Tab bar скрывать в уроке, тесте и оплате; длинные списки — Pagination на десктопе, подгрузка «Показать ещё» (Button Secondary) на мобилке.
15. **Списки длиннее одной страницы на десктопе** (каталог, отзывы, история оплат) — внизу `Pagination`.

## Каталог: что когда брать

| Задача | Компонент | По умолчанию |
|---|---|---|
| Главное действие экрана | Button, Type=Primary | State=Default, ширина 400 в формах, во всю ширину на мобилке |
| Второстепенное действие | Button, Type=Secondary | — |
| Ссылка-действие («Забыли пароль?», «Назад») | Button, Type=Text | — |
| Вход через Google | Button, Type=Social | — |
| Удалить, выйти из аккаунта | Button, Type=Destructive | внутри Modal или Bottom sheet |
| Ввод одной строки (email, имя) | Input, Type=Text | Label через свойство `Label` |
| Многострочный ввод (вопрос к уроку, отзыв, комментарий) | Text area | высота 128, счётчик «0 / 500» в helper |
| Пароль | Input, Type=Password + Password/Strength + Checklist/Password | Strength по длине/сложности |
| Поиск | Input, Type=Search | `Show icon=true` |
| Один вариант из нескольких | Radio | — |
| Галочка («Запомнить меня», согласие) | Checkbox | — |
| Вкл/выкл настройки | Switch | — |
| Выбор из списка | Dropdown | State=Default / Open |
| Темы, интересы, фильтры | Chip | Selected=False/True |
| Переключение разделов страницы | Tabs (из Tab) | одна Tab с State=Active |
| Шаги онбординга, прогресс курса | Progress bar | Value=25/33/50/66/68/100 |
| Логотип | Logo | Type=Full / Mark |
| Шапка десктопа | Header | Type=Guest до входа, Type=User после |
| Подвал десктопа | Footer | — |
| Верх мобильного экрана | Status bar + App bar | App bar Type=Main на корневых, Type=Back на вложенных |
| Нижняя навигация мобилки | Tab bar (из Tab bar/Item) | 4 пункта: Главная, Каталог, Мои курсы, Профиль |
| Длинный список на десктопе | Pagination (из Pagination/Item) | Prev Disabled на первой странице |
| Курс в каталоге | Course card, Type=Catalog | — |
| «Продолжить обучение» на Home | Course card, Type=Continue | — |
| Урок в списке курса | Lesson item | Completed / Current / Default / Locked |
| Достижение | Achievement card | Unlocked / Locked |
| Отзыв о курсе | Review card | Avatar + Rating + текст + дата |
| Цифра прогресса | Stat card | Icon через Instance swap |
| Пользователь, преподаватель | Avatar | S 32 списки, M 40 шапки, L 64 профиль |
| Статус на карточке | Badge | Accent / Success / Warning / Error / Neutral |
| Оценка | Rating | Value 1–5, Show score |
| Разделитель | Divider | Horizontal / Vertical |
| Подсказка | Tooltip | Top / Bottom |
| Прокрутка внутри блока | Scrollbar | — |
| Сообщение на экране (баннер) | Alert | Error / Warning / Success / Info |
| Короткое уведомление после действия | Toast | Success / Error / Info |
| Подтверждение на десктопе | Modal | overlay поверх `color/scrim` |
| Подтверждение, фильтры, выбор на мобилке | Bottom sheet | снизу поверх `color/scrim` |
| ИИ-помощник по уроку | Chat button | правый нижний угол, один на экран |
| Пусто / ничего не найдено | Empty state | — |
| Иллюстрация слева на экранах входа (десктоп) | Illustration/Night | половина экрана 720 × 900 |
| Индикатор фазы/прогресса в виде луны | Moon/Phase | New → Full |
| Загрузка | Moon/Loader | Frame 1–8 (анимация через smart animate) |

## Размеры

| Элемент | Десктоп | Мобилка |
|---|---|---|
| Button, Input | высота 48, в формах ширина 400 | высота 48, во всю ширину (390 − 2 × 16) |
| Text area | ширина 400, поле 128 | во всю ширину, поле 128 |
| Карточка формы входа | 480, `color/card`, `radius/lg`, `Shadow/Card` | без карточки, форма на `color/bg` |
| Course card | 312 × 338, 4 в ряд | во всю ширину, 1 в ряд |
| Achievement card / Stat card | 280 / 180, 4 в ряд | 2 в ряд, FILL |
| Review card | 400 | во всю ширину |
| Modal / Bottom sheet | Modal 480 | Bottom sheet 390 |
| Toast | 380, верхний правый угол, отступ 24 | во всю ширину сверху, отступ 16 |
| Шапка / низ | Header 1440 × 72, Footer 1440 × 85 | Status bar 44 + App bar 56, Tab bar 91 |
| Chat button | 56, отступ 24 от края | 56, отступ 16 над Tab bar |
| Pagination/Item | 40 × 40 | не используется |

Радиусы: `radius/sm` 6 — чипы, бейджи, тултип; `radius/md` 10 — поля, кнопки, пагинация; `radius/lg` 20 — карточки, модалки, Bottom sheet; `radius/full` — аватары, пилюли, Chat button.
Отступы: шкала 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 / 80. Поля внутри формы — gap 16, между карточками — `layout/gutter`, между крупными блоками — `layout/section-gap`, поля страницы — `layout/margin`.

## Чего в системе нет

Светлой темы нет, таблиц нет, графиков нет, маскота нет.
Не собирай недостающий компонент из фреймов. Скажи, чего не хватает, и предложи ближайший существующий (например, вместо таблицы — список из Lesson item, вместо графика — Stat card + Progress bar).

## Порядок работы

1. Правила и каталог отсюда; шаблон экрана — references/patterns.md.
2. Ключи и id — references/keys.md и references/icons.md; токены — references/tokens.md.
3. Сборка на странице Design: фрейм 1440 (мода Desktop) или 390 (мода Mobile), имя `Module / Screen / State` (мобилка: `Module / Mobile / State`).
4. Скриншот экрана и сверка с железными правилами: нет сырых HEX/чисел, нет детачей, одна Primary-кнопка, тач-зоны 44 на мобилке, форматы ₸ и дат.
