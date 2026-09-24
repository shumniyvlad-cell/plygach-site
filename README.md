# Полная запись — сайт встречи

Лендинг открытой встречи Елены Плыгач для психологов и коучей.
Одна страница, без сборки и зависимостей: `index.html` + папка `img/`.
Ведёт в телеграм-бота регистрации `@Psyplygach_bot` с метками источника
(`?start=site`, `?start=site_top`, `?start=site_bottom`) — в `/stats` бота видно, откуда пришли.

## Где что менять

| Что | Где |
| --- | --- |
| Дата и время эфира | `index.html`: строка `new Date('2026-09-29T19:00:00+03:00')` и тексты с «29 сентября» |
| Ссылка на бота | все `href="https://t.me/Psyplygach_bot?start=..."` |
| Фото | `img/hero.jpg` (студия), `img/elena.jpg` (кресло), `img/og.jpg` (превью в соцсетях) |
| Адрес сайта для превью | `og:image` и `og:url` в `<head>` |

После эфира счётчик сам переключится на «Встреча идёт», через 100 минут — на «Встреча прошла».

## Публикация

GitHub Pages: Settings → Pages → Source: `Deploy from a branch` → `main` / `(root)`.
Сайт появится по адресу `https://<username>.github.io/<repo>/` через минуту-две.

## Первая публикация с компьютера

Из этой папки, при залогиненном `gh`:

```bash
git init -b main
git add -A
git commit -m "Лендинг встречи «Полная запись»"
gh repo create plygach-site --public --source=. --push
gh api -X POST repos/{owner}/plygach-site/pages -f 'source[branch]=main' -f 'source[path]=/'
```

Через пару минут сайт откроется по адресу `https://<username>.github.io/plygach-site/`.
После этого впишите его в `index.html` вместо `__SITE_URL__` (два места в `<head>`) и запушьте ещё раз —
это адрес для превью в Telegram и соцсетях.
