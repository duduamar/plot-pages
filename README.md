Plot — Pages
============

The public landing, support and privacy pages for the **Plot** iOS app (a
poker session and bankroll tracker), plus its `app-ads.txt`.

Why a separate repo
-------------------
GitHub Pages on the free plan only serves from **public** repos. The app's
source lives in the private `plot` repo; this one holds nothing but static
HTML, so nothing about the app itself is exposed.

Where it's served
-----------------
<https://plotpokertracker.com> — a custom apex domain on Cloudflare, not the old
`duduamar.github.io/plot-pages/` path. GitHub redirects the old URLs, so
nothing that already linked there breaks.

The site moved here from `chiplogapp.com` with the rename off "ChipLog"
(`duduamar/plot` #87). That zone is being torn down and its registration is set
to lapse — nothing should point at it again.

The domain isn't cosmetic. Google's `app-ads.txt` crawler takes the developer
website from the store listing and fetches `/app-ads.txt` at **that domain's
root** — which a `github.io` repo path can never satisfy. Serving from an apex
we own is what makes the ad-seller authorization reachable at all.

DNS notes, because both are easy to get wrong later:
- The apex `A`/`AAAA` records must be **DNS-only (grey cloud)** in Cloudflare.
  Proxying them breaks GitHub's Let's Encrypt validation.
- Email Routing owns the `SPF` TXT record. A domain may have only **one** SPF
  record, so anything added later (e.g. `include:_spf.google.com` for Gmail
  send-as) has to be merged into it, never added alongside.

Contents
--------
- `index.html` — landing page
- `support.html` — support / contact
- `privacy.html` — privacy policy
- `app-ads.txt` — AdMob seller authorization (required for the app's ad units)
- `CNAME` — the custom domain, written by GitHub's Pages settings UI
- `screenshots/` — the images the landing page uses

Every page is a single self-contained file: no build step, no dependencies, no
external requests. Inline `<style>` only, and light/dark via
`prefers-color-scheme`. Keep it that way — the pages are read on a phone, from
a link in the app's Settings tab.

Status
------
Launch content is in place and carries the **PLOT** name throughout
(`duduamar/plot` #22). The one thing still missing is the **App Store link**,
which can't exist until the app is live — `index.html` says "Coming soon" and
carries an HTML comment where the link and badge go. Tracked in
`duduamar/plot` #23.

The name is written **PLOT** in copy, matching `CFBundleDisplayName` and the
home screen's header. `Plot` is only ever the code-side prefix, so it doesn't
belong on these pages.

The privacy policy describes the app as it actually ships: local + private
CloudKit storage, no developer server, no analytics SDK, AdMob banner with the
ATT prompt and a non-personalized fallback, and the one-time Remove Ads
purchase. **If any of that changes, this page changes with it** — and the
"Last updated" date moves.

The privacy policy and support URLs served from here go into App Store Connect's
"Privacy Policy URL" and "Support URL" fields, and are the same two URLs
`PlotLinks` opens from the app's Settings tab:

- <https://plotpokertracker.com/privacy.html>
- <https://plotpokertracker.com/support.html>

Contact on both pages is **support@plotpokertracker.com**, forwarded to a personal
inbox by Cloudflare Email Routing. Keep it that way — a personal address on a
page built to be indexed is the thing the alias exists to avoid.

Screenshots
-----------
`screenshots/*.png` are real Simulator captures (iPhone 17 Pro), cropped above
the ad banner and scaled to 804px wide. The data in them is invented demo data
imported from a CSV, not anyone's real results. Re-capture them whenever the UI
moves on far enough that they'd mislead.

**Don't invent a fresh history to re-shoot one screen.** The numbers here are
published — the bankroll appears on both the Home and Stats shots, and the
Sessions list has to agree with them — so the dataset is committed in the app
repo, along with the crop step and the order to shoot the screens in:

- `duduamar/plot` — `scripts/demo-data.csv` (built by `scripts/make-demo-data.mjs`,
  which fails if the totals drift off what this site states)
- `duduamar/plot` — `docs/screenshots.md`, the full recipe
