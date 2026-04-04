# Публикация лендинга

Статический сайт без сборки. Репозиторий: [github.com/maksimdor95/lendingMD](https://github.com/maksimdor95/lendingMD).

## Файлы в репозитории

| Путь | Назначение |
|------|------------|
| `index.html`, `styles.css` | Разметка и стили |
| `hero-photo.svg` | Плейсхолдер портрета в герое (можно заменить на `hero-photo.jpg`) |
| `favicon.svg` | Иконка вкладки |
| `robots.txt`, `404.html` | Служебные страницы |
| `assets/` | Опционально: свои иконки (сейчас карточки используют favicons Google) |
| `vercel.json` | Настройки **Vercel** (заголовки безопасности) |
| `netlify.toml` | Настройки **Netlify** |
| `.htaccess` | Только **Apache** (общий хостинг) |

## Vercel (рекомендуется с GitHub)

1. Зайдите на [vercel.com](https://vercel.com) и войдите через GitHub.
2. **Add New… → Project → Import** репозиторий `maksimdor95/lendingMD`.
3. Настройки по умолчанию:
   - **Framework Preset:** Other (или Vite — не важно, сборки нет).
   - **Root Directory:** `./` (корень).
   - **Build Command:** оставьте пустым.
   - **Output Directory:** оставьте пустым (корень с `index.html`).
4. Нажмите **Deploy**. Через минуту сайт будет на `*.vercel.app`.
5. **Settings → Domains** — подключите свой домен (DNS по подсказкам Vercel).

HTTPS и CDN включены автоматически. При каждом `git push` в выбранную ветку деплой обновится.

## Первый push в GitHub (если ещё не пушили)

В терминале из папки проекта:

```bash
git init
git add .
git commit -m "Landing: static site"
git branch -M main
git remote add origin https://github.com/maksimdor95/lendingMD.git
git push -u origin main
```

Если репозиторий уже не пустой, сначала `git pull origin main --rebase`, затем `git push`.

## Netlify

1. [app.netlify.com/drop](https://app.netlify.com/drop) — перетащить папку, **или** Import из GitHub.
2. Build: не нужен, publish directory — корень.

## Cloudflare Pages / обычный хостинг / GitHub Pages

См. предыдущие версии инструкций: залить те же файлы в корень сайта; для GitHub Pages — Settings → Pages → ветка `main`, папка `/ (root)`.

## Замена плейсхолдера на фото

1. Положите `hero-photo.jpg` рядом с `index.html`.
2. В `index.html` у тега `<img>` в герое замените `src="hero-photo.svg"` на `src="hero-photo.jpg"`.
3. Уберите или оставьте комментарий над тегом — по желанию.

## После появления домена

В `<head>` добавьте (свой URL):

```html
<link rel="canonical" href="https://ваш-домен.ru/" />
<meta property="og:url" content="https://ваш-домен.ru/" />
<meta property="og:image" content="https://ваш-домен.ru/hero-photo.jpg" />
```

После правок CSS увеличьте `?v=` в ссылке на `styles.css`.

## Проверка

- Вкладка Network: нет 404 на `styles.css`, `hero-photo.svg` (или `.jpg`), `favicon.svg`.
- Пройти по якорям меню, проверить кнопки (Telegram, hh.ru).
