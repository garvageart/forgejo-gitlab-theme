# 🦊 Forgejo & Gitea GitLab Theme

[![Forgejo Version](https://img.shields.io/badge/Forgejo-v14%2B-orange.svg)](https://codeberg.org/forgejo/forgejo)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Theme Variants](https://img.shields.io/badge/Variants-Auto%20%7C%20Dark%20%7C%20Light-purple.svg)](#features)

A pixel-perfect, modern GitLab theme for **Forgejo v14+** and **Gitea**. Features GitLab Slate dark and light color palettes, signature GitLab Orange accents (`#e24329` / `#fc6d26`), and clean modern typography (**Inter** for UI elements and **JetBrains Mono** for code and diff views).

---

## 🎨 Features

- 🌓 **`gitlab-auto`**: Automatically switches between GitLab Dark Slate and GitLab Light Slate based on system or browser dark mode settings (`prefers-color-scheme`).
- 🌙 **`gitlab-dark`**: Explicit GitLab Dark Slate theme (`#18171d` main body, `#1f1e24` surface containers, `#28272d` card headers).
- ☀️ **`gitlab-light`**: Explicit GitLab Light Slate theme (`#f9f9fb` main body, `#ffffff` cards, with GitLab's signature `#1f1e24` dark top navigation header).
- 🟧 **GitLab Signature Orange Accent**: `#e24329` primary brand color with `#fc6d26` bright hover highlights across all buttons, badges, tabs, and focus rings.
- 🔤 **Typography**: Google Fonts **Inter** (UI) and **JetBrains Mono** (Code, Monospace, and Diff views).
- 🎛️ **Form Controls & Toggles**: Custom styled slider switches and checkboxes that smoothly transition from slate track indicators to active orange states.

---

## 📦 Theme Files

| File | Description |
| :--- | :--- |
| **`theme-gitlab-auto.css`** | Combined auto-switching theme (OS Light / Dark mode aware) |
| **`theme-gitlab-dark.css`** | Standalone GitLab Dark Slate theme |
| **`theme-gitlab-light.css`** | Standalone GitLab Light Slate theme |

---

## 🚀 Installation & Setup (Docker)

### 1. Copy Theme CSS Files into Container

Copy the theme CSS files into your Forgejo container's public assets directory (`/data/gitea/public/assets/css/`):

```bash
# Copy theme files to your running Forgejo container
docker cp theme-gitlab-auto.css gitea-gitea-1:/data/gitea/public/assets/css/
docker cp theme-gitlab-dark.css gitea-gitea-1:/data/gitea/public/assets/css/
docker cp theme-gitlab-light.css gitea-gitea-1:/data/gitea/public/assets/css/

# Fix ownership inside container
docker exec gitea-gitea-1 chown -R git:git /data/gitea/public/assets/css
```

### 2. Register Themes in `docker-compose.yml`

Update your `docker-compose.yml` environment variables to register the new themes:

```yaml
services:
  gitea:
    image: codeberg.org/forgejo/forgejo:14
    environment:
      - GITEA__ui__THEMES=gitlab-auto,gitlab-dark,gitlab-light,forgejo-auto,forgejo-light,forgejo-dark
      - GITEA__ui__DEFAULT_THEME=gitlab-auto
```

*(Alternatively, edit your `app.ini` under `[ui]` section:)*

```ini
[ui]
THEMES = gitlab-auto,gitlab-dark,gitlab-light,forgejo-auto,forgejo-light,forgejo-dark
DEFAULT_THEME = gitlab-auto
```

### 3. Restart Container

```bash
docker compose restart gitea
```

---

## ⚙️ User Preference Selection

1. Log in to your Forgejo instance.
2. Go to **User Settings** (`/user/settings`).
3. Under **Appearance**, select your preferred theme:
   - `gitlab-auto` (System Aware)
   - `gitlab-dark` (Always Dark)
   - `gitlab-light` (Always Light)
4. Click **Update Theme**.

---

## 📄 License

Distributed under the MIT License. Generated with assistance from Gemini.
