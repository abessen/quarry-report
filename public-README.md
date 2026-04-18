# Hourly Production Report

A single-file HTML app that displays hourly totals from a RunData-style API for selected devices and a summary metric.

## Files

- `index.html` — the app
- `README.md` — setup and usage notes
- `.gitignore` — basic local file exclusions

## Public-facing cleanup included

- Removed organization-specific naming from the title, description, defaults, and documentation
- Replaced environment-specific host examples with generic placeholders
- Kept the app as a reusable template for any compatible RunData-style backend
- Preserved the earlier hardening for timezone handling, abortable refreshes, and safer date parsing

## How to use

1. Open `index.html` in a browser.
2. Enter your site root URL, such as `https://your-site.example.com`.
3. Choose the report date.
4. Optionally paste a bearer token if your API requires it.
5. Click **Refresh Report**.

## API assumptions

The app calls:

- `GET /api/RunData`

With query parameters:

- `start`
- `end`
- `deviceIds`
- `interval=Hourly`
- `dataType=Tons`

It also sends browser cookies with `credentials: include`.

## What you may still want to customize

- Device labels and IDs in the `DEVICES` object
- The table headers
- Demo data
- Branding, colors, and descriptive text
- Any backend-specific auth or payload differences

## Notes

- Do not commit real bearer tokens or internal hostnames.
- If live data fails to load, check network access, auth, HTTPS, CORS, and whether the server exposes the expected `RunData` route.
- The code assumes the browser supports `AbortController` and `Intl.DateTimeFormat`.
