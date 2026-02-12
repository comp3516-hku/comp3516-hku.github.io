# COMP3516 HKU Offerings Portal

This repository is the portal site for COMP3516 offerings.

- Root page lists available offerings by year.
- `/2025/` redirects to `https://comp3516-hku.github.io/comp3516-2025/`
- `/2026/` redirects to `https://comp3516-hku.github.io/comp3516-2026/`

To add a new year:

1. Create or fork a new year repo (for example `comp3516-2027`).
2. Set `url` and `baseurl` in that repo's `_config.yml`.
3. Add a new redirect page in this portal repo (`/2027/index.html`).
4. Add the year entry in this portal's `index.md`.

