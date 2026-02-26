# robots-txt

Canonical `robots.txt` for Leftium projects.

## Default policy

- **Allow:** search engines (Googlebot, Bingbot) and social preview/link-unfurl bots
- **Block:** everything else — AI crawlers, TikTokSpider, scrapers, etc.

## Usage

From your project root:

```bash
bash scripts/update.sh
```

This fetches the canonical base from GitHub and writes `static/robots.txt`.

## Per-project overrides

Create `static/robots.override.txt` with any additional rules. They are appended after the base on each update.

Example — allow an extra bot and block a whitelisted one:

```
# Allow Yeti (Naver search crawler)
User-agent: Yeti
Allow: /

# Block Googlebot for this project
User-agent: Googlebot
Disallow: /
```

> Note: `robots.txt` is honor-based. Legitimate bots respect it; malicious scrapers may not.

## Installing the update script

Copy `scripts/update.sh` into your project:

```bash
curl -fsSL https://raw.githubusercontent.com/Leftium/robots-txt/main/scripts/update.sh \
    -o scripts/update.sh
chmod +x scripts/update.sh
```

Then add to your `package.json`:

```json
"scripts": {
    "robots": "bash scripts/update.sh"
}
```
