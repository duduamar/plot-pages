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

Status
------
The pages are a **skeleton** — real copy, the contact address and the policy's
effective date are filled in before App Store submission. Look for `[TODO]`
markers. Tracked in `duduamar/chiplog`: skeleton in #4, final content in #22.

The privacy policy and support URLs served from here go into App Store Connect's
"Privacy Policy URL" and "Support URL" fields.
