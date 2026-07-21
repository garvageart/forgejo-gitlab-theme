# Forgejo 14 GitLab Theme

A modern, pixel-perfect GitLab theme for Forgejo v14+ and Gitea featuring GitLab Slate dark/light modes, signature GitLab Orange accents (`#e24329` / `#fc6d26`), and clean typography with **Inter** for UI and **JetBrains Mono** for code views.

## Features

- **`gitlab-auto`**: Automatically switches between GitLab Dark and GitLab Light based on system/browser dark mode settings (`prefers-color-scheme`).
- **`gitlab-dark`**: Explicit GitLab Dark Slate theme (`#18171d` background, `#1f1e24` cards, `#28272d` headers).
- **`gitlab-light`**: Explicit GitLab Light Slate theme (`#f9f9fb` background, `#ffffff` cards, `#1f1e24` dark top navigation header).
- **GitLab Signature Orange Accent**: `#e24329` primary brand color with `#fc6d26` hover highlights.
- **Typography**: Google Fonts **Inter** (UI) and **JetBrains Mono** (Code & Monospace).

## Installation (Docker)

1. Copy the CSS files into your Forgejo container's custom public directory (`/data/gitea/public/assets/css/`):

```bash
docker cp theme-gitlab-auto.css gitea-gitea-1:/data/gitea/public/assets/css/
docker cp theme-gitlab-dark.css gitea-gitea-1:/data/gitea/public/assets/css/
docker cp theme-gitlab-light.css gitea-gitea-1:/data/gitea/public/assets/css/
```

2. Register the themes in your `docker-compose.yml`:

```yaml
environment:
  - GITEA__ui__THEMES=gitlab-auto,gitlab-dark,gitlab-light,forgejo-auto,forgejo-light,forgejo-dark
  - GITEA__ui__DEFAULT_THEME=gitlab-auto
```

3. Restart your Forgejo container:

```bash
docker compose restart gitea
```
