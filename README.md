# Tsukiyo plugins

Скилл для Claude Code: сборка макетов в Figma на дизайн-системе Tsukiyo
(edtech-платформа, ночь и луна, тёмная тема, десктоп 1440 и мобилка 390).

## Установка

    /plugin marketplace add medetushka/tsukiyo-plugins
    /plugin install tsukiyo@tsukiyo-plugins

После установки перезапустите Claude Code. Скилл срабатывает сам,
когда речь идёт о сборке экрана Tsukiyo, выборе компонента или токена.
Для работы с файлом нужен подключённый Figma (плагин Figma для Claude).

## Обновление

    /plugin marketplace update tsukiyo-plugins
    /plugin update tsukiyo@tsukiyo-plugins

## Состав

- `plugins/tsukiyo/skills/tsukiyo-design-system/SKILL.md` — правила и каталог
- `references/keys.md` — компоненты, node id и ключи
- `references/icons.md` — иконки: имена, id и ключи
- `references/tokens.md` — переменные, моды Desktop/Mobile, текстовые и эффект-стили
- `references/patterns.md` — шаблоны экранов, состояния, прототип
- `references/changelog.md` — история версий
