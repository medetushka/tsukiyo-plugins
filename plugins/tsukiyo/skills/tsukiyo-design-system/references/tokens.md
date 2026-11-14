# Токены Tsukiyo — переменные и стили

Три коллекции:

- **Tsukiyo** — семантика, одна мода `Night`. Используется во всех компонентах и макетах.
- **Primitives** — палитра, одна мода `Value`. Напрямую не используется, только как значение для семантики; скрыта от публикации.
- **Platform** — размеры, которые отличаются на десктопе и мобилке, моды `Desktop` и `Mobile`. Мода ставится на корневой фрейм экрана.

Привязка цвета: `figma.variables.setBoundVariableForPaint(paint, 'color', variable)` — возвращает новую заливку, её нужно присвоить. Отступы: `node.setBoundVariable('itemSpacing' | 'paddingLeft' | …, variable)`. Радиус: `setBoundVariable('topLeftRadius', …)` по всем углам.
Импорт из библиотеки: `await figma.variables.importVariableByKeyAsync(KEY)`.

## Цвет: роли (Tsukiyo)

| Переменная | Значение | Key | Где |
|---|---|---|---|
| color/bg | → night/900 #0B1026 | `7ff2d194f9fe6d35fe8c0b0d0361bc024b2b56d5` | фон страницы |
| color/card | → night/800 #141A3A | `688695c2fd332accaee768457e2f05f70e2249a6` | карточки, форма, модалка |
| color/input | → night/700 #1C2350 | `d45c98333313f5fdf3d4436aeb13c5c92e47f6a4` | фон поля ввода |
| color/border | → night/600 #2E3770 | `0a4104dc88cdb35009758a3cafdee4f9c054f328` | обводки, разделители |
| color/border-strong | → night/400 #7581B4 | `7f9a949123a11570695664a5b0ce0d3631af1ca2` | обводка поля (3.95:1 на input) |
| color/text | → night/100 #E8ECF8 | `2bd0c547c2fc376a6382a442180d1cf1c0e1d681` | основной текст |
| color/text-secondary | → night/300 #9AA3C7 | `590236855858cad21afecad1e7be10ef961305a2` | подписи, плейсхолдеры |
| color/accent | → moon/400 #7AA2FF | `a612a6e9ed8e0f06d6d2bc2b3330a0f506d9dea8` | Primary-кнопка, ссылки, фокус |
| color/accent-hover | → moon/300 #9BB7FF | `689ac03b4ff35c742295508e408bff7df23db1c7` | hover акцента |
| color/accent-pressed | → moon/500 #5B86F0 | `51444c8dac5cbb4f9df5e3d365d6774988010f41` | pressed акцента |
| color/on-accent | → night/900 #0B1026 | `70d66206677f38aa79d88f75f782da02511e670d` | текст на акцентной кнопке |
| color/error | → red/500 #FF4D5E | `2c5c096859152a2bc31b73d7a8b8203eb36cccde` | ошибки, трещина под полем |
| color/error-hover | → red/300 #FF8A95 | `fde7159585cd217d2e06f31da726d14de6691e1f` | hover Destructive |
| color/error-pressed | → red/700 #C42235 | `bc83881f1c66f53621ed3fdaff7b332d2bf934e5` | pressed Destructive |
| color/success | → green/500 #5FD3A4 | `5e91d660041f175b935951cad5e403c5aca854ac` | успех |
| color/warning | → amber/500 #F2B84B | `f63bf4f1f97ef175c31ef0597b2f23226477a2cb` | предупреждения, блокировка |
| color/info | → sky/500 #4FC3F7 | `9a6126c43bc0697b5bd84e6415ad3696c31e8176` | информация |
| color/crimson | → crimson/500 #B0213A | `94d1ae5af1020acd00b5d9ae03b170d3863062ca` | декор: тонкие красные линии |
| color/scrim | #03050F @72% | `e342f7714c3537df90630556650ec2beb3ff846c` | затемнение под модалкой |
| color/white | #FFFFFF | `e44495e57ca8cef054b26f62f29105e5427639fe` | только кнопка Social (Google) |
| color/black | #000000 | `110e35387b88600eeb2994493776f5fac2b489e6` | служебный |

## Цвет: альфа-варианты (Tsukiyo)

Для подложек и полупрозрачного текста. Не ставь opacity на заливку — бери токен.

| Группа | Переменные |
|---|---|
| text | color/text-a10, -a30, -a40, -a50, -a60, -a70, -a80, -a90 |
| accent | color/accent-a10, -a30, -a90 |
| error | color/error-a10 (фон Alert/Toast Error), -a30 (обводка) |
| success | color/success-a10, -a30 |
| warning | color/warning-a10, -a30, -a60, -a70, -a80, -a90 |
| прочее | color/card-a50, color/bg-a20, color/black-a10 |
| иллюстрация | color/illustration/crater #A9B3DA, crater-a30, skyline #05070F — только внутри Illustration/Night и луны |

## Отступы и радиусы (Tsukiyo, FLOAT)

| Переменная | px | Key |
|---|---|---|
| spacing/4 | 4 | `28245ca6f42cb7c589e956315d6917100bda6aaf` |
| spacing/8 | 8 | `977be0fd0624a9c8c2cc6014b14c913a0ed03202` |
| spacing/12 | 12 | `a227978ce0e0a0dbfa8fcee8ecdad180f59bd0e7` |
| spacing/16 | 16 | `66501bf36c012285434013e5de7d2b61595cb60a` |
| spacing/24 | 24 | `7d39d803655016bb9fbb561420fb79bf08cd4281` |
| spacing/32 | 32 | `97b5a58f933beb76eef3a4c0f25a68d2ff3036ee` |
| spacing/48 | 48 | `b3087adba32b7a0fbe2caaf17eb104dbe68b5626` |
| spacing/64 | 64 | `ec5125dfb7f768871547c25b098ef87faa514a5b` |
| spacing/80 | 80 | `c1ec277c19eacfb8f5761ad9469e47b1befd0557` |
| radius/sm | 6 | `2dee01315294bafe706bea72d74a020b7c6084db` |
| radius/md | 10 | `af77ac58939c5aecca70b4821713d9acbe2ed945` |
| radius/lg | 20 | `19c439fac0cbdeedd81c61ab6be8598f3b9f138c` |
| radius/full | 999 | `0eab35989f97fa2b5b18e74d6eb1bd9f2cb7fbe2` |

## Platform (Desktop / Mobile)

Коллекция `VariableCollectionId:90:5113`, моды `Desktop` (`90:0`) и `Mobile` (`90:1`).
Переключение: `frame.setExplicitVariableModeForCollection(collection, '90:1')` на корневом фрейме мобильного экрана.

| Переменная | Desktop | Mobile | Где |
|---|---|---|---|
| type/display/size · line | 56 · 64 | 40 · 48 | стиль Tsukiyo/Display |
| type/h1/size · line | 36 · 44 | 28 · 36 | стиль Tsukiyo/H1 |
| type/h2/size · line | 28 · 34 | 24 · 32 | стиль Tsukiyo/H2 |
| type/h3/size · line | 22 · 28 | 20 · 28 | стиль Tsukiyo/H3 |
| layout/margin | 80 | 16 | боковые поля страницы (padding контента) |
| layout/gutter | 24 | 16 | gap между карточками и колонками |
| layout/section-gap | 64 | 32 | gap между крупными блоками |
| size/control | 48 | 48 | высота кнопок и полей |
| size/touch | 44 | 44 | минимальная тач-зона |
| size/screen-width | 1440 | 390 | ширина экранного фрейма |

## Примитивы (Primitives)

- moon/100–900 (основной, 9 оттенков): #DCE6FF, #BCCEFF, #9BB7FF, **#7AA2FF**, #5B86F0, #4269D6, #3150AD, #233B82, #18285A
- night/0–950 (нейтральные): #FFFFFF, #F4F6FC, #E8ECF8, #C9CFE6, #9AA3C7, #7581B4, #4A548A, #2E3770, #1C2350, #141A3A, #0B1026, #060818
- red 300/500/700: #FF8A95 / #FF4D5E / #C42235
- green 300/500/700: #9BE7C6 / #5FD3A4 / #2E9C72
- amber 300/500/700: #F7D08A / #F2B84B / #B9821A
- sky 300/500/700: #9DDCF5 / #4FC3F7 / #1E8DBF
- crimson/500: #B0213A
- black/scrim: #03050F

## Текстовые стили

| Стиль | Шрифт | Размер / строка | Key | Где |
|---|---|---|---|---|
| Tsukiyo/Display | Cormorant Garamond SemiBold | 56 / 64 | `4e572977f5db5f7d0404b0ee60dffca27a9545e8` | приветствие, промо |
| Tsukiyo/H1 | Cormorant Garamond SemiBold | 36 / 44 | `46e4606e68b3b5516763daf0c55e18a09afdf68e` | заголовок экрана |
| Tsukiyo/H2 | Cormorant Garamond SemiBold | 28 / 34 | `5d7f61235609779da288d33c033c389e77e76d4f` | заголовок блока |
| Tsukiyo/H3 | Cormorant Garamond SemiBold | 22 / 28 | `14e6c63a7bb86eb7fd89d47910869a96aab912fa` | заголовок карточки/модалки |
| Tsukiyo/Body | Inter Regular | 16 / 24 | `9d18b55bca79a5a365bf8bb8ab40a3ff4dba713e` | основной текст |
| Tsukiyo/Small | Inter Regular | 14 / 20 | `968834c4b51dde356eeab217d098624923f15352` | подписи, helper, мета |
| Tsukiyo/Caption | Inter Regular | 12 / 16 | `e5a9b6068b5725c35406035120c909dfaa42e633` | мелкие подписи |
| Tsukiyo/Label | Inter Medium | 14 / 20 | `d3cff7b2da07e2c7997d0b4498f97700bd4d5c63` | подписи полей, табы, чипы, шаги |
| Tsukiyo/Button | Inter Semi Bold | 16 / 24 | `567c14a2e4220db15c1fbcf5ea739a71d521e50d` | подписи кнопок, названия курсов |

Размер и высота строки `Display`, `H1`–`H3` привязаны к переменным `type/*` коллекции Platform: на мобилке Display 40/48, H1 28/36, H2 24/32, H3 20/28. Inter-стили одинаковые на обеих платформах.

Шрифтовой стиль Cormorant — `SemiBold` (без пробела), Inter — `Regular` / `Semi Bold` (с пробелом). Перед правкой текста загружай шрифт.

## Эффекты и сетка

| Стиль | Key | Где |
|---|---|---|
| Tsukiyo/Glow/Focus | `f81f2177fc1a87e1efc37f4170b98d6efe0dd48b` | фокус поля и кнопки |
| Tsukiyo/Glow/Error | `3b5728c0cc9527d2d57ad7be640299f46f8e611c` | поле с ошибкой |
| Tsukiyo/Glow/Button | `ebce634a8c086106208a9a0a4aa6b9b0914a198c` | Primary hover |
| Tsukiyo/Glow/Moon | `9f5541391fd359fbca8d2aa5a477d56a8bdf0c3c` | луна, иллюстрация |
| Tsukiyo/Shadow/Card | `6c48fdaaf5f44e2d8a0b08d1f7c18b1b35430482` | карточки, модалки |
| Grid/Desktop 12 col | `34f73d8027b24ff26b5a83265bb1e87088d3dff0` | на каждом экранном фрейме 1440 |
| Grid/Mobile 4 col | `93f9ab2592d10fb06f23049bb8e83478a4cc05f4` | на каждом мобильном фрейме 390 |

Применение: `node.setEffectStyleIdAsync(style.id)`, `frame.setGridStyleIdAsync(style.id)`, `text.setTextStyleIdAsync(style.id)`.
