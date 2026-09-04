# SubDesk — legal site

The privacy policy and data-deletion page for the SubDesk Android app
(`app.subdesk` on Google Play), published at
**<https://mar-devl.github.io/subdesk-legal/>**.

This repository contains no application code. It is public because GitHub Pages
requires a public repository on the Free plan, and the app repository is
private — it carries the Firebase configuration and names the admin account in
its Firestore rules. The requirement was a public URL, not a public app.

## The URLs

| Purpose | URL |
|---|---|
| Play Console → Privacy policy | `https://mar-devl.github.io/subdesk-legal/privacy.html` |
| Play Console → Data deletion | `https://mar-devl.github.io/subdesk-legal/data-deletion.html` |
| AdMob → GDPR message → Privacy policy | `https://mar-devl.github.io/subdesk-legal/privacy.html` |
| In-app: Settings → About | both of the above |

**These are compiled into the app.** `app/src/main/java/app/subdesk/util/Legal.kt`
in the app repository holds the same strings, and its verification pass
(`tools/consent.py`) asserts they point here. Renaming a file in this
repository breaks the app, the store listing and the consent message at once —
so if you rename one, change `Legal.kt` in the same sitting.

## Setup

Once, at repository creation:

> Settings → Pages → Build and deployment → Source → **GitHub Actions**

Not "Deploy from a branch". Without it every workflow run fails at *Setup
Pages* with a 404.

## Editing

Edit the HTML and push to `main`. The workflow republishes in about a minute.

- Bump the **effective date** in the hero of `privacy.html` whenever the
  substance changes, not when a typo is fixed.
- Keep the policy true to the app. It describes local storage, the optional
  Firestore backup, AdMob and the UMP consent flow, Logo.dev and Frankfurter,
  because those are what the app actually does. Adding an SDK to the app means
  editing this page in the same patch.
- Do not link to `github.com/mar-devl/subdesk`. It is private and will 404;
  the workflow fails the build if a link creeps back in.

## Structure

```
index.html            landing page / support URL
privacy.html          the policy — the URL Play and AdMob check
data-deletion.html    account and data deletion route
assets/subdesk.css    brand tokens: Iris, Paper, Space Grotesk, Manrope
assets/*.svg          logo, generated from the app's master artwork
.nojekyll             serve files as-is; no Jekyll build
```

Design follows **SubDesk Brand Identity v1.0**: Ink `#12121A` hero, Paper
`#F6F5F2` body, white cards with `#12121A12` hairlines at 20px radius and no
elevation, section indices in Iris `#5B3DF5`, Space Grotesk for display and
Manrope for prose.

The logo is generated from `design-system/subdesk/subdesk-mark.svg` in the app
repository — the same master the launcher icon and the Play icon come from. The
identity document still shows the older two-arc mark; that one is retired.
