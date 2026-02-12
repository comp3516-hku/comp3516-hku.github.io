# COMP3516 HKU Offerings Portal

This repository is the landing portal for all COMP3516 yearly offerings.

- Portal homepage: `https://comp3516-hku.github.io/`
- Year shortcut routes: `/2025/`, `/2026/`, ...
- Each shortcut redirects to the corresponding year repo page:
  - `https://comp3516-hku.github.io/comp3516-2025/`
  - `https://comp3516-hku.github.io/comp3516-2026/`

## Repository layout strategy

- `comp3516-hku.github.io`: portal only (year list + redirects).
- `comp3516-20XX`: one repo per offering year, containing full course content.

## Add a new offering year (for future TAs)

### 1) Create the new year repo

Recommended: fork/copy from the latest year repo (for example from `comp3516-2026` to `comp3516-2027`) so layout and workflows stay consistent.

### 2) Update the new year repo content/config

In the new repo, edit `_config.yml`:

- `course_semester`: set the new semester/year label.
- `baseurl`: set to `"/comp3516-20YY"` (example: `"/comp3516-2027"`).
- `url`: set to `"https://comp3516-hku.github.io"`.
- `repository`: set to `"comp3516-hku/comp3516-20YY"`.

The year repo navbar already includes a `Portal` link. Keep it as:

- `https://comp3516-hku.github.io/`

### 3) Modify the portal repo for the new year

In `comp3516-hku.github.io`:

1. Add one year entry in `index.md`.
2. Add a redirect file `20YY/index.html` with target:
   - `https://comp3516-hku.github.io/comp3516-20YY/`

Redirect template:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Redirecting to COMP3516 Spring 20YY</title>
  <meta http-equiv="refresh" content="0; url=https://comp3516-hku.github.io/comp3516-20YY/">
  <link rel="canonical" href="https://comp3516-hku.github.io/comp3516-20YY/">
  <script>
    window.location.replace("https://comp3516-hku.github.io/comp3516-20YY/");
  </script>
</head>
<body>
  If you are not redirected automatically, please
  <a href="https://comp3516-hku.github.io/comp3516-20YY/">open the 20YY course page</a>.
</body>
</html>
```

## GitHub settings (required)

### Portal repo (`comp3516-hku.github.io`)

- `Settings` -> `Pages` -> `Build and deployment`:
  - `Source = GitHub Actions`
- `Settings` -> `Actions` -> `General`:
  - allow GitHub Actions
  - workflow permissions: `Read and write permissions`

### Each year repo (`comp3516-20YY`)

- `Settings` -> `Pages` -> `Build and deployment`:
  - `Source = GitHub Actions`
- `Settings` -> `Actions` -> `General`:
  - allow GitHub Actions
  - workflow permissions: `Read and write permissions`
- Do not set custom domain on year repos.

## Deployment checklist

1. Push changes to portal repo.
2. Push changes to new year repo.
3. Ensure Actions workflows pass in both repos.
4. Verify URLs:
   - `https://comp3516-hku.github.io/`
   - `https://comp3516-hku.github.io/20YY/`
   - `https://comp3516-hku.github.io/comp3516-20YY/`

