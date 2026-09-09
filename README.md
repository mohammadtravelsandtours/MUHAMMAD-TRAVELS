# Mohammad Travels — Flight Booking Prototype

A single-file, front-end-only prototype of a B2B/B2C flight booking platform, built as an original design for **Mohammad Travels** (no real airline branding, logos, or UI is copied from any existing OTA).

**[View it live](#)** once GitHub Pages is enabled (see below), or just open `index.html` in any browser — no build step, no server, no dependencies beyond the page itself.

## What's in here

- **Consumer site**: one-way / round-trip / multi-city flight search, results with filters and sorting, full booking flow (passengers → review → price revalidation → payment → confirmation), hotels, visa/travel-services request forms, "Find My Booking" with a 75-airline real-website directory (Asia + Middle East), and a scripted AI assistant with a simulated price-check feature.
- **Accounts**: unified login/register flow (an unrecognized email hands off to registration automatically), with a human-verification widget on auth and payment.
- **B2B agency portal**: a separate login for travel agents booking on behalf of clients.
- **Admin Portal**: a gated internal dashboard — B2B partner management, a simulated fare-collection engine, pricing/markup rules, booking records, and an activity log. Demo login accepts any well-formed email + password, with test credentials shown openly on the login screen.

## Important: what this is and isn't

This is a **static front-end demo**. Specifically:

- **No backend.** All state lives in memory in the browser tab and resets on reload. Nothing is saved to a database.
- **No real prices or schedules.** Flight results use real Asian/Middle East airline *names* (with correct IATA codes) for realism, but the specific flight numbers, times, and fares attached to them are simulated — not live data from any airline.
- **No real payments.** The payment screen is UI only; no card data is transmitted or stored anywhere.
- **No real credentials of any kind are stored in this file.** The admin login intentionally does *not* check a real account — baking a real password into a static HTML file would expose it to anyone viewing the page source, not protect it. The same applies to the "B2B partner" credential form in the admin dashboard: any password typed there is read once and discarded, never persisted.
- **The "role-based access" (admin gating, login state) is cosmetic**, implemented in client-side JavaScript for demonstration. It is trivially bypassable via browser dev tools and must not be treated as real security. A production version needs a real server enforcing auth on every request.

Every one of these limitations is also called out in-context inside the app itself (toasts, security notes on relevant screens) — this README just collects them in one place.

## Running it

No installation needed.

- **Locally**: double-click `index.html`, or serve the folder with any static file server (`python3 -m http.server`, `npx serve`, etc.).
- **GitHub Pages**: in the repo's Settings → Pages, set the source to the branch/root containing this file, and GitHub will serve `index.html` automatically at `https://<username>.github.io/<repo>/`.

The only external dependency is Google Fonts (Space Grotesk, Inter), loaded via `<link>` tags in `<head>`. Everything else — all logic, all styling, all mock data — is self-contained in this one file. If the fonts fail to load (e.g. viewing offline), the page falls back to system sans-serif fonts gracefully.

## Testing

This prototype was verified with an automated headless test suite (Node.js + a minimal DOM stub) covering booking flows, B2B/admin features, HTML structural validity across every view, and pricing/security edge cases — 200+ assertions, not included in this repo but described in the development history. If you're extending this project, consider adding your own test coverage for new features following the same pattern.

## License

Add a license of your choosing before publishing publicly if you intend for others to reuse this code.
