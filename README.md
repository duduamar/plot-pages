ChipLog — Pages
===============

The public landing, support and privacy pages for the **ChipLog** iOS app (a
poker session and bankroll tracker), plus its `app-ads.txt`.

Why a separate repo
-------------------
GitHub Pages on the free plan only serves from **public** repos. The app's
source lives in the private `chiplog` repo; this one holds nothing but static
HTML, so nothing about the app itself is exposed.

Contents
--------
- `index.html` — landing page
- `support.html` — support / contact
- `privacy.html` — privacy policy
- `app-ads.txt` — AdMob seller authorization (required for the app's ad units)
- `screenshots/` — the images the landing page uses

Every page is a single self-contained file: no build step, no dependencies, no
external requests. Inline `<style>` only, and light/dark via
`prefers-color-scheme`. Keep it that way — the pages are read on a phone, from
a link in the app's Settings tab.

Status
------
Launch content is in place (`duduamar/chiplog` #22). The one thing still
missing is the **App Store link**, which can't exist until the app is live —
`index.html` says "Coming soon" and carries an HTML comment where the link and
badge go. Tracked in `duduamar/chiplog` #23.

The privacy policy describes the app as it actually ships: local + private
CloudKit storage, no developer server, no analytics SDK, AdMob banner with the
ATT prompt and a non-personalized fallback, and the one-time Remove Ads
purchase. **If any of that changes, this page changes with it** — and the
"Last updated" date moves.

The privacy policy and support URLs served from here go into App Store Connect's
"Privacy Policy URL" and "Support URL" fields, and are the same two URLs
`ChipLogLinks` opens from the app's Settings tab:

- <https://duduamar.github.io/chiplog-pages/privacy.html>
- <https://duduamar.github.io/chiplog-pages/support.html>

Screenshots
-----------
`screenshots/*.png` are real Simulator captures (iPhone 17 Pro), cropped above
the ad banner and scaled to 804px wide. The data in them is invented demo data
imported from a CSV, not anyone's real results. Re-capture them whenever the UI
moves on far enough that they'd mislead.
