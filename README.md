# ⚡ Pixel LiteX — Userscript Edition

> A modern automation userscript toolkit focused on checkout flow helpers, hCaptcha integration hooks, BIN insights, proxy/session utilities, and a configurable dashboard UI.

---

## ✅ Status Update

This project should now be treated as a **userscript project**.

Even though this repository still contains older Chromium-extension scaffolding (like `manifest.json`, background/content script split, and extension assets), the **intended direction is userscript-style deployment and usage**.

---

## What this project includes

The codebase currently contains:

- A large **automation runtime** (in `script/content.js`) that drives in-page behavior.
- A **dashboard UI** (`dashboard.html` + styles + dashboard logic) for control panels and state display.
- Supporting modules for:
  - proxy/session flows (`script/proxyhandler.js`)
  - form/autofill flows (`script/autofill.js`)
  - country data (`script/country.js`, `script/countrylist.json`)
  - hCaptcha-specific hooks (`script/hcaptcha.js`)
  - storage and data passing (`script/storage.js`)
  - version/update logic (`script/version.js`)
  - helper libraries (`script/binlibrary.js`)

---

## Repository structure

```text
Pixel_litex_Edition/
├─ dashboard.html           # Main control panel UI
├─ styles.css               # Shared style definitions
├─ script/
│  ├─ content.js            # Core runtime injected into pages
│  ├─ background.js         # Legacy extension background worker
│  ├─ hcaptcha.js           # hCaptcha-related hooks
│  ├─ autofill.js           # Form automation helpers
│  ├─ proxyhandler.js       # Proxy/session handling helpers
│  ├─ storage.js            # State persistence bridge
│  ├─ version.js            # Version/check logic
│  ├─ country.js            # Country helpers
│  ├─ countrylist.json      # Country dataset
│  ├─ binlibrary.js         # BIN-related helper logic
│  └─ inject.js             # Injection helper entry
├─ icons/
├─ fonts/
├─ sounds/
├─ rules.json
├─ offscreen.html
└─ manifest.json            # Legacy extension manifest
```

---

## Userscript migration guide

If you’re running this through **Tampermonkey / Violentmonkey / Greasemonkey**, use this approach:

1. Create a new userscript in your manager.
2. Add a metadata header similar to:

```javascript
// ==UserScript==
// @name         Pixel LiteX Userscript
// @namespace    https://bypixel.site/
// @version      1.0.0
// @description  Automation toolkit (userscript edition)
// @match        *://*/*
// @run-at       document-start
// @grant        GM_setValue
// @grant        GM_getValue
// @grant        GM_xmlhttpRequest
// @connect      *
// ==/UserScript==
```

3. Port runtime logic from `script/content.js` and related helper modules into userscript-compatible modules.
4. Replace Chrome-extension APIs (`chrome.*`) with userscript-compatible APIs (`GM_*`, `fetch`, page-context messaging).
5. Keep dashboard controls as in-page UI overlays or external config pages.

---

## Key capability areas

### 1) Page automation runtime
The main runtime is geared toward observing page state and reacting to dynamic checkout/payment conditions.

### 2) hCaptcha integration
Dedicated logic exists for hCaptcha contexts and frame coverage.

### 3) Proxy/session workflow
Proxy application, state checks, and session utilities are separated into proxy-focused modules.

### 4) BIN + card intelligence helpers
BIN helper files and related notification paths are present for card/payment context enrichment.

### 5) Dashboard operations
A fully styled control dashboard is included with multi-section controls and status indicators.

---

## Notes about current code

- Some core JS files are heavily minified/obfuscated for distribution.
- You may want to maintain a readable source branch and a build/minify output branch.
- Keep sensitive endpoints/secrets out of client-side bundles.

---

## Recommended next steps

- [ ] Extract clean source modules from minified runtime.
- [ ] Add a build pipeline for userscript bundling.
- [ ] Split config, UI, and runtime into separate packages.
- [ ] Add `.md` docs for each major module (proxy, hcaptcha, autofill, dashboard).
- [ ] Add changelog + semantic versioning for reliable updates.

---

## Credits

Original attribution in the project points to:

- Developer: `@xunez`
- Channel: `@b3charge`
- Help/tutorial links in `READ_ME.txt`

---

## Disclaimer

Use automation responsibly and only where permitted by site terms, local law, and platform rules.

