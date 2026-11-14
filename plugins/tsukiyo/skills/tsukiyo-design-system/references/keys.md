# Компоненты Tsukiyo — id, ключи, свойства

Файл: fileKey `ASsAM4YvBYzXIcNnqAA16j`, страница **Design System** (`16:49`).

- Внутри этого файла: `const set = await figma.getNodeByIdAsync(ID)` → нужный вариант из `set.children` → `.createInstance()`.
- В другом файле (после публикации библиотеки): `await figma.importComponentSetByKeyAsync(KEY)` для наборов, `importComponentByKeyAsync(KEY)` для одиночных компонентов.
- Вариант выбирать через `instance.setProperties({ Type: 'Primary', State: 'Default' })`, а не перебором имён.

## Действия и ввод

| Компонент | Тип | Node id | Key | Свойства | По умолчанию |
|---|---|---|---|---|---|
| Button | set (30) | `30:21700` | `00d19b53b05d21f190412a95684c9c359dbe1e39` | Type: Primary, Secondary, Text, Social, Destructive · State: Default, Hover, Pressed, Focus, Disabled, Loading | Primary, Default · 400 × 48 |
| Input | set (17) | `30:21647` | `77225fc71cbb2d728af01a80ce5a5381091427bc` | Type: Text, Password, Search · State: Default, Hover, Focus, Filled, Error, Success, Disabled · Label (text, «Email») · Show helper (bool, true) · Show icon (bool, false) | Text, Default · 400 × 100 |
| Checkbox | set (2) | `30:21754` | `26ab66f4c8f6d018d74c290e63a425f08c8e73f3` | Checked: False, True · Label (text, «Запомнить меня») | False |
| Radio | set (4) | `40:2479` | `1f7eef1adb62b934943ef758da7389bbb1029a19` | Selected: False, True · State: Default, Disabled | False, Default |
| Switch | set (4) | `40:2496` | `e6b09009bc64ba6e618371bdaf7772c282152ebf` | On: False, True · State: Default, Disabled | False, Default |
| Dropdown | set (3) | `40:2522` | `9046f9df48b047319e1eb75b616b2705336ee5a4` | State: Default, Open, Disabled | Default · 320 × 76 |
| Chip | set (4) | `49:2916` | `b296443fc5d9c68415bc099faf7452882fcfd1a5` | Selected: False, True · State: Default, Hover | False, Default |

Не все сочетания Input существуют (17 из 21): Password и Search есть не во всех состояниях — проверяй `set.children` перед `setProperties`.

## Пароль

| Компонент | Тип | Node id | Key | Свойства |
|---|---|---|---|---|
| Password/Strength | set (5) | `30:21887` | `acbfdc2feeae63fd8f3c60eabdde73fc113318c0` | Strength: Empty, Weak, Medium, Strong, Very strong · 400 × 16 |
| Checklist/Item | set (3) | `30:21907` | `53e5c205663f156e2e6aae0c551f84bb120bf52b` | State: Pending, Met, Unmet · Text (text, «Минимум 8 символов») |
| Checklist/Password | component | `30:21908` | `d70e5e694e7d518089bcd65bd91a5be2d6078224` | собран из 4–5 Checklist/Item |

## Навигация

| Компонент | Тип | Node id | Key | Свойства |
|---|---|---|---|---|
| Header | set (2) | `40:2595` | `e305085953a94d223599bd5636bbd6af2f07f84b` | Type: Guest, User · 1440 × 72 |
| Footer | component | `40:2596` | `f0fa81320e47ac5bb781d319dd14d077c1ba52d2` | 1440 × 85 |
| Tab | set (3) | `40:2537` | `60905b981af3569fe7b8d1c639500d31d888b75e` | State: Default, Hover, Active |
| Tabs | component | `40:2538` | `1d1c7b2b4ebd5233783796bf038b734276893ec0` | ряд из Tab · 488 × 39 |
| Progress bar | set (6) | `49:2929` | `3566a8b86f96bfda02747d1ae294109eb765576a` | Value: 25, 33, 50, 66, 68, 100 · растягивается по ширине |

## Контент

| Компонент | Тип | Node id | Key | Свойства |
|---|---|---|---|---|
| Course card | set (2) | `42:2521` | `b86e0c01f7a2b1c82c1f4a42790b675d7063a38f` | Type: Catalog, Continue · 312 × 338 |
| Lesson item | set (4) | `42:2549` | `490c4956616db8c792c004559b2436e97273d21c` | State: Completed, Current, Default, Locked · 560 × 74 |
| Empty state | component | `42:2590` | `4cd7c1529c821a421a3dbc2f52a866e6011f103e` | 480 × 332 |
| Illustration/Night | component | `21:2003` | `f8e2c215e3721734ee04bb24874384c1cbb66aa9` | 720 × 900, левая половина экранов входа |
| Moon/Phase | set (5) | `30:21779` | `1026d82f8f000efba5af2d3e8cbab21c28d62a34` | Phase: New, Crescent, Quarter, Gibbous, Full · 24 × 24 |

## Обратная связь

| Компонент | Тип | Node id | Key | Свойства |
|---|---|---|---|---|
| Alert | set (4) | `30:21741` | `92d983a6b39c902e86dd5f47d9c9d7aca99b942e` | Type: Error, Warning, Success, Info · 400 × 96 |
| Toast | set (3) | `42:2578` | `c19d76f545d96e32e3d7634987f5ec1c647fec64` | Type: Success, Error, Info · 380 × 54 |
| Modal | component | `42:2579` | `b16dad357ab98b18cb5d2b57c0d5847eb238d994` | 480 × 244 |
| Moon/Loader | set (8) | `30:21811` | `9ce4e5f7e9f8ddbb3d0fe6d45a4ee7ab4de782ea` | Frame: 1–8 · 48 × 48 |

## Интерактивность мастеров

Button, Chip, Tab и Input уже связаны interactive components: hover и press внутри самого компонента. В прототипе на экране достаточно ставить инстанс в State=Default.

## Добавлено в 1.1.0

### Бренд и формы

| Компонент | Тип | Node id | Key | Свойства |
|---|---|---|---|---|
| Logo | set (2) | `91:5322` | `11c77011297ab746b34f8f4f2558f2a621d9aec3` | Type: Full (полумесяц + wordmark), Mark (полумесяц 32) |
| Text area | set (5) | `92:5175` | `189eeb34a5ff8252f78f24679c42d1814d97eae2` | State: Default, Focus, Filled, Error, Disabled · ширина 400, поле 128 |
| Scrollbar | component | `92:5113` | `cccf390fa8554cc25edce819025a55ee3c58886b` | 4 × 80, растягивается по высоте |

### Навигация

| Компонент | Тип | Node id | Key | Свойства |
|---|---|---|---|---|
| Pagination/Item | set (8) | `92:5196` | `f4ee40b342539d5788b339bd03e8c70a04b8072f` | Type: Number, Ellipsis, Prev, Next · State: Default, Hover, Active (Number), Disabled (Prev/Next) · Page (text) · 40 × 40 |
| Pagination | component | `92:5197` | `7fb3a78675c4fef8ae35cc90e10987b3bdc1b149` | Prev · 1 · 2 · 3 · … · 12 · Next; номера меняются свойством Page у вложенных Item |

### Data display

| Компонент | Тип | Node id | Key | Свойства |
|---|---|---|---|---|
| Avatar | set (3) | `93:5142` | `2492bb2031026a90385d05e3cf73158f8de2094d` | Size: S 32, M 40, L 64 · Initials (text) |
| Badge | set (5) | `93:5153` | `b6f4ae705d9ac9eef4cfdc09bf0a15c663eb5660` | Type: Accent, Success, Warning, Error, Neutral · Label (text) |
| Rating | set (5) | `93:5214` | `a3c10215335d1855de50baaad21017a96d09b4be` | Value: 1–5 · Show score (bool) |
| Divider | set (2) | `93:5217` | `ecc315527f0e92eb758f61c9b569793503fc529a` | Orientation: Horizontal, Vertical |
| Tooltip | set (2) | `93:5226` | `8f382de72c19388ef182cff7b4071f925f02d726` | Position: Top, Bottom · Text (text) |

### Карточки

| Компонент | Тип | Node id | Key | Свойства |
|---|---|---|---|---|
| Achievement card | set (2) | `94:5175` | `63008bf9f4fc675f600bf887672cd7961cdaac81` | State: Unlocked, Locked · Title, Description (text) · ширина 280 |
| Review card | component | `94:5176` | `5e7c64c2d2e8dec5182b9f73fe38a58bc5a509ad` | Name, Text, Date (text) · ширина 400 |
| Stat card | component | `94:5197` | `84e232f37ca6791ba4965867cb8dfebd7e7f344a` | Value, Label (text) · Icon (instance swap) · ширина 180 |

### Мобилка

| Компонент | Тип | Node id | Key | Свойства |
|---|---|---|---|---|
| Status bar | component | `95:5179` | `fe618e461700fe9ef04f6cb737a37f2e2220b025` | 390 × 44 |
| App bar | set (2) | `95:5204` | `dbdab36b7040f254ebe4dc5ecf9be2b3102d7145` | Type: Main (`95:5185`), Back (`95:5196`) · Title (text) · 390 × 56 |
| Tab bar/Item | set (2) | `95:5213` | `a4d423c52b7ff873d99649deac67374e7eea781b` | State: Default, Active · Label (text) · Icon (instance swap) · 88 × 56 |
| Tab bar | component | `95:5214` | `9f27d700de6514a73496c6cdcab0b01770886b07` | 390 × 91, 4 пункта + home indicator |
| Bottom sheet | component | `95:5238` | `12f18d1213b48f4295e261e9b50fe311c5d23c43` | Title, Text (text) · Destructive + Text кнопки · 390 |
| Chat button | component | `95:5246` | `d29507f2eb4ab6f88bb46b9694fde09e13ffcc8f` | 56 × 56, `Glow/Button` |

Пример мобильного экрана, собранного только из инстансов: `Home / Dashboard / Default · Mobile` (`95:5253`), `Sign in / Login / Default · Mobile` (`97:5205`) в секции Design / Mobile.

### Маскот

| Компонент | Тип | Node id | Key | Свойства |
|---|---|---|---|---|
| Mascot (Ёру) | set (4) | `99:5392` | `1a48f70eb3aa97748ad0d73b594d8ad726dee51d` | Mood: Happy, Thinking, Sad, Sleeping · 120 × 120, масштабировать целиком (Scale): 120 / 64 / 40 |
