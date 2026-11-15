# Шаблоны экранов Tsukiyo

## Нейминг и раскладка

- Экраны лежат на странице **Design** в секциях `Design / <Module>`: Sign in, Onboarding, Home, Offer, Core feature, Profile.
- Имя фрейма: `Module / Screen / State`, например `Sign in / Login / Error`, `Offer / Checkout / Success`.
- Десктоп: фрейм 1440 × 900 (или выше по контенту), заливка `color/bg`, сетка `Grid/Desktop 12 col`, мода Platform = Desktop.
- Мобилка: фрейм 390 × 844 (или выше по контенту), заливка `color/bg`, мода Platform = Mobile, сетка `Grid/Mobile 4 col`, имя как у десктопного экрана + ` · Mobile` (`Sign in / Login / Default · Mobile`), секция `Design / Mobile`.
- Рядом с секцией модуля — фрейм `Research notes / <Module>` с выводами ресёрча.

## Шаблоны

| Шаблон | Где | Структура |
|---|---|---|
| Auth split | Sign in, Sign up, восстановление пароля | слева Illustration/Night 720 × 900; справа по центру карточка 480 (`color/card`, `radius/lg`, `Shadow/Card`, padding 48, gap 16): H1 → Body-подзаголовок → Input-ы → Primary → Text-ссылки → Social |
| Onboarding step | Goal, Interests, Schedule, Plan | Header Guest/User; по центру колонка 6 из 12: Progress bar → H1 → варианты (Chip / Radio) → Primary «Далее» + Text «Назад» |
| App page | Home, Catalog, Course, Profile | Header Type=User → контент по сетке 12 колонок с полями 80 → Footer |
| Lesson | Core feature | Header User → слева список Lesson item (4 колонки) → справа плеер/вопрос (8 колонок) |
| Overlay | подтверждение, выход | Modal 480 по центру поверх `color/scrim`; в прототипе — Open overlay, центр, закрытие по клику снаружи |

## Шаблоны мобилки (390)

| Шаблон | Структура |
|---|---|
| Mobile page | вертикальный auto layout: Status bar → App bar (Main на корневых, Back на вложенных) → Content (padding `layout/margin`, gap `spacing/24`) → Tab bar в конце; Chat button абсолютом в правом нижнем углу, 16 над Tab bar |
| Mobile auth | Status bar → Logo Mark по центру → H1 → Input-ы во всю ширину → Primary во всю ширину → Text-ссылки; без Illustration/Night и без Tab bar |
| Mobile onboarding | Status bar → App bar Back (шаг назад; на первом шаге без Back) → Progress bar → H1 → варианты во всю ширину (Chip с зазором ≥ 8 или Radio) → Primary «Далее» во всю ширину внизу. Text «Назад» не ставить — назад только в App bar; Tab bar нет. Выбор из длинного списка — Bottom sheet Type=Select |
| Mobile list | App bar Main, если это корневой экран вкладки Tab bar (каталог); App bar Back — если список вложенный → Input Search → Chip-фильтры в строку → Course card 1 в ряд → Button Secondary «Показать ещё» вместо Pagination |
| Mobile lesson | App bar Back (название урока) → Video player или вопрос во всю ширину → Progress bar → Primary снизу; Tab bar скрыт |
| Mobile confirm | экран + `color/scrim` + Bottom sheet снизу (OVERLAY, позиция Bottom) |

Примеры: `Sign in / Login / Default · Mobile` (`97:5205`) — шаблон Mobile auth; `Home / Dashboard / Default · Mobile` (`95:5253`) — Status bar, App bar Main, приветствие H1, Course card Continue, 2 Stat card, Achievement card ×2, Tab bar, Chat button.

## Обязательные состояния модуля

Для каждого модуля кроме основного экрана нужно хотя бы одно состояние ошибки, а для экранов с данными — Loading и Empty:

| Модуль | Состояния |
|---|---|
| Sign in | Login Default / Filled / Error / Loading, Forgot password, Reset success, Sign up Default / Error, Welcome |
| Onboarding | Goal, Interests Default / Error (не выбрано ни одной темы), Schedule, Plan Loading / Success |
| Home | Default, Empty, Loading, Error, Search No results |
| Offer | Catalog Default / Empty filters, Course, Plans, Checkout Default / Error / Success |
| Core feature | Lesson Video, Quiz Default / Wrong / Correct, Module Completed |
| Profile | Overview, Settings Default / Error / Success, Log out Confirm (Modal) |

- Error формы — `Input State=Error` + при необходимости `Alert Type=Error` над формой.
- Loading — `Moon/Loader` по центру области или `Button State=Loading`.
- Empty — компонент Empty state с одним действием; у вложенного Mascot Mood=Sleeping, если данных ещё нет, и Mood=Sad, если поиск или фильтры ничего не нашли.
- Успех после действия — `Toast Type=Success`.

## Прототип

- Связи: `setReactionsAsync` с NAVIGATE между экранами, OVERLAY для Modal, CLOSE для закрытия, AFTER_TIMEOUT для Loading → Success.
- Переходы (правила 25–27):

| Связь | Transition | Длительность | Easing |
|---|---|---|---|
| Обычный переход между экранами | Smart animate | 250 мс (`motion/base`) | ease-out |
| Из Tab bar, Tabs, Header | Smart animate | 150 мс (`motion/fast`) | ease-out |
| На экран с Bottom sheet | Move in снизу | 400 мс (`motion/slow`) | ease-out |
| Modal (Open overlay) | Dissolve | 250 мс | ease-out |
| На Success / Completed / Welcome | Smart animate | 400 мс | ease-in-out |
| Hover и Pressed внутри компонентов | Smart animate | 150 / 100 мс | ease-out |
- Каждый модуль — свой flow starting point; плюс общий `End-to-end: Sign up → Onboarding → Home → Offer → Core → Profile`.
- Без тупиков: с каждого экрана есть путь дальше или назад.

## Тексты и форматы

- Язык — русский, обращение на «ты» не использовать, нейтрально: «Войти», «Продолжить обучение».
- Цены: `4 990 ₸`, `49 900 ₸ / год`. Даты: `23.10.2026`.
- Никаких реальных персональных данных в макетах: имя-пример «Айгерим С.», email `student@tsukiyo.kz`.
