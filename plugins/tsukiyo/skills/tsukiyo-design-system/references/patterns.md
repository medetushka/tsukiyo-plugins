# Шаблоны экранов Tsukiyo

## Нейминг и раскладка

- Экраны лежат на странице **Design** в секциях `Design / <Module>`: Sign in, Onboarding, Home, Offer, Core feature, Profile.
- Имя фрейма: `Module / Screen / State`, например `Sign in / Login / Error`, `Offer / Checkout / Success`.
- Фрейм 1440 × 900 (или выше по контенту), заливка `color/bg`, сетка `Grid/Desktop 12 col`.
- Рядом с секцией модуля — фрейм `Research notes / <Module>` с выводами ресёрча.

## Шаблоны

| Шаблон | Где | Структура |
|---|---|---|
| Auth split | Sign in, Sign up, восстановление пароля | слева Illustration/Night 720 × 900; справа по центру карточка 480 (`color/card`, `radius/lg`, `Shadow/Card`, padding 48, gap 16): H1 → Body-подзаголовок → Input-ы → Primary → Text-ссылки → Social |
| Onboarding step | Goal, Interests, Schedule, Plan | Header Guest/User; по центру колонка 6 из 12: Progress bar → H1 → варианты (Chip / Radio) → Primary «Далее» + Text «Назад» |
| App page | Home, Catalog, Course, Profile | Header Type=User → контент по сетке 12 колонок с полями 80 → Footer |
| Lesson | Core feature | Header User → слева список Lesson item (4 колонки) → справа плеер/вопрос (8 колонок) |
| Overlay | подтверждение, выход | Modal 480 по центру поверх `color/scrim`; в прототипе — Open overlay, центр, закрытие по клику снаружи |

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
- Empty — компонент Empty state с одним действием.
- Успех после действия — `Toast Type=Success`.

## Прототип

- Связи: `setReactionsAsync` с NAVIGATE между экранами, OVERLAY для Modal, CLOSE для закрытия, AFTER_TIMEOUT для Loading → Success.
- Каждый модуль — свой flow starting point; плюс общий `End-to-end: Sign up → Onboarding → Home → Offer → Core → Profile`.
- Без тупиков: с каждого экрана есть путь дальше или назад.

## Тексты и форматы

- Язык — русский, обращение на «ты» не использовать, нейтрально: «Войти», «Продолжить обучение».
- Цены: `4 990 ₸`, `49 900 ₸ / год`. Даты: `23.10.2026`.
- Никаких реальных персональных данных в макетах: имя-пример «Айгерим С.», email `student@tsukiyo.kz`.
