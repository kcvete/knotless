# knotless-site

Static website for the Android app **Knotless: Untie Your Mind** by Lunaria Studios.

- Homepage (developer website): https://kcvete.github.io/knotless/
- Privacy policy (Play Console URL): https://kcvete.github.io/knotless/privacy/

Plain HTML and CSS: no build step, no scripts, no trackers, no cookies. The fonts
(Bricolage Grotesque, Figtree; SIL OFL 1.1) are self-hosted in `assets/fonts/`,
and the policy page inlines them, so neither page makes third-party requests.
All links are relative, so the site works under the `/knotless/` subpath.

## Files

- `index.html`: homepage
- `privacy/index.html`: privacy policy (source: `docs/play-store/privacy-policy.html`
  in the app repo)
- `assets/`: icon, favicon, feature graphic (Open Graph image), fonts
- `.nojekyll`: serve files as they are, without Jekyll

## Placeholders

- `[SUPPORT EMAIL]` in `index.html` (footer) and `privacy/index.html` (section 11).
  Replace both; on the homepage, turn it into a `mailto:` link.
- "Coming soon to Google Play" in `index.html`: swap for the Play link at launch
  (the URL is in an HTML comment next to it).

## Preview locally

```sh
python3 -m http.server 8000   # then open http://localhost:8000/
```

## Publish (GitHub Pages)

```sh
gh repo create kcvete/knotless --public --source . --remote origin \
  --description "Website and privacy policy for the Knotless Android app"
git push -u origin main
gh api -X POST repos/kcvete/knotless/pages \
  -f "source[branch]=main" -f "source[path]=/"
```

Pages is served from `main`, folder `/` (root). The first build takes a minute
or two; check it with `gh api repos/kcvete/knotless/pages`.
