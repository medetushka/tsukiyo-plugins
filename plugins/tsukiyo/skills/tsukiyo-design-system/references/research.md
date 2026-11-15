# Ресерч других дизайн-систем

Что мы сравнили с Tsukiyo, что взяли в правила и что сознательно не взяли. Дата: 14.11.2026.

Смотрели документацию: Material 3 (Google), Human Interface Guidelines (Apple), Carbon (IBM), Polaris (Shopify), Atlassian Design System, Wonder Blocks (Khan Academy — edtech, как Tsukiyo), Primer (GitHub). В Figma открыли библиотеки, доступные файлу Tsukiyo: **Material 3 Design Kit** и **Simple Design System** (Community).

## Что взяли

| Тема | Как у них | Что у нас теперь | Правило |
|---|---|---|---|
| Нижняя навигация | Material 3: navigation bar для 3–5 равноценных разделов; меньше 3 — табы, больше 5 — drawer/rail. Apple: таб-бар только для навигации, не для действий; избегать переполнения «Ещё» | Tab bar остаётся на 4 пункта; новые разделы — внутрь существующих, а не пятым-шестым пунктом; действий в Tab bar нет | 16 |
| Тач-зоны | Apple: минимум 44 × 44 pt и ~8 pt между соседними целями. Material 3: 48 dp | Было 44; добавили зазор ≥ 8 (`spacing/8`) между соседними нажимаемыми элементами | 17 |
| Короткие уведомления | Material 3 snackbar: одно за раз, не стопкой, максимум одно действие, исчезает сам. Polaris: не использовать toast для ошибок | Toast — по одному, ≤ 1 действие, сам исчезает; Toast Error только для фоновых сбоев, не для ошибок ввода | 18 |
| Тексты ошибок | Polaris: объяснить, что не так и как исправить; конкретно (числа, даты); ошибка — прямо под полем; не в модалке; красный — только для критичного, остальное — жёлтый с иконкой | Валидация — трещина + текст под полем; ошибка всей формы — Alert над формой; текст «что случилось + как исправить», без обвинения; Warning для некритичного | 19 |
| Bottom sheet или модалка | Material 3: модальный bottom sheet — замена меню и простых диалогов на мобилке, для списков действий и выбора. SAP Fiori (на базе M3): не использовать bottom sheet, чтобы заставить пользователя срочно что-то сделать | Bottom sheet — выбор, фильтры, список действий, обратимые подтверждения (выход). Необратимое (удалить аккаунт, оплатить) — Modal по центру и на мобилке | 20 |
| Пустые состояния | Carbon: empty state заменяет тот элемент, который был бы на месте; главная кнопка страницы не переезжает в пустую область. Primer, eBay: сказать, что пусто и почему, и дать следующий шаг | Empty state стоит на месте пустого блока; текст = что пусто + почему + что сделать; кнопка — только следующий шаг, а не дубль главной кнопки страницы | 21 |
| Описания компонентов | В Material 3 Design Kit у каждого компонента в Figma есть описание с правилом применения («Navigation bars provide access to three to five destinations») | Уже делаем: у всех 41 компонента Tsukiyo есть Description «когда использовать» — подтверждение практики | — |
| Движение | Видео «20 Principles of UX & Animation»: 12 принципов анимации Disney (slow in & slow out, snappy timing, follow through) | Три длительности 150 / 250 / 400 мс, ease-out для появления, короткий отклик Pressed, одно вторичное подтверждение | 25, 27 |
| Частота использования | То же видео: чем чаще действие, тем меньше анимации | Навигация и вкладки — 150 мс; празднование только для редких событий | 26 |
| Ввод | Законы UX: Миллер (группировать), Постел (принимать неаккуратный ввод), порог Доэрти (400 мс) | Карта, телефон и ИИН группами; терпимые форматы даты и телефона; Loader после 400 мс | 27, 28 |

## Что не взяли (пока)

| Идея | Откуда | Почему не сейчас |
|---|---|---|
| Имена токенов по схеме `color.background.danger.bold.hovered` (основа · свойство · роль · акцент · состояние) | Atlassian | У нас короче: `color/error-hover`. Переименование сломает привязки на 46 экранах. Кандидат для 2.0 |
| Отдельный «учебный» домен токенов (Core / Learning / Component) | Wonder Blocks, Khan Academy | Хорошо для edtech: `color/learning/correct`, `streak`, `due`. Пока покрываем `color/success`, `color/warning` и Badge; вернуться, если появятся 3+ учебных состояния |
| Тач-зона 48 вместо 44 | Material 3 | Опираемся на 44 (Apple) как минимум; кнопки и поля у нас и так 48 |
| Toast внизу над нижней навигацией | Material 3 snackbar | Внизу справа у нас Chat button; Toast на мобилке остаётся сверху |
| Solid drawing in 3D (перспектива и объём у карточек), moving in arcs (элементы летят по дуге) | Видео «20 Principles of UX & Animation» | Не вяжутся со спокойным ночным стилем и учебным продуктом; негде применить |

## Источники

- Material 3 — Navigation bar: https://m3.material.io/components/navigation-bar/overview
- Android — Layout and navigation patterns: https://developer.android.com/design/ui/mobile/guides/layout-and-content/layout-and-nav-patterns
- Material — Snackbars: https://material.io/components/snackbars
- Material 3 — Modal bottom sheet (Compose): https://developer.android.com/reference/kotlin/androidx/compose/material3/ModalBottomSheet.composable
- SAP Fiori for Android (M3) — Bottom sheet: https://www.sap.com/design-system/fiori-design-android/v25-8/components/system-components/bottom-sheet/usage
- Apple HIG — Tab bars: https://developer.apple.com/design/human-interface-guidelines/tab-bars
- Apple — Design tips (hit targets): https://developer.apple.com/design/tips
- Carbon — Empty states: https://carbondesignsystem.com/patterns/empty-states-pattern/
- Primer — Empty states: https://primer.style/design/ui-patterns/empty-states
- Polaris — Error messages: https://polaris.shopify.com/content/error-messages
- Shopify — Messages and feedback: https://shopify.dev/docs/apps/design/user-experience/alerts
- Atlassian — Design tokens: https://atlassian.design/tokens/design-tokens
- Khan Academy — Wonder Blocks color system: https://blog.khanacademy.org/how-we-rebuilt-khan-academys-color-system-from-the-ground-up
- Figma Community: Material 3 Design Kit, Simple Design System (библиотеки, доступные файлу Tsukiyo)
- Видео «20 Principles of UX & Animation (in under 30 seconds)» — прислано пользователем, 15.11.2026
- Laws of UX (Фиттс, Хик, Миллер, Постел, Доэрти, Якоб): https://lawsofux.com
