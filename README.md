# WebForge — Instant Website Generator (SaaS demo)

WebForge is a single-file SaaS demo that generates a small business website preview and brand kit.  
This repository contains a single `index.html` you can host on GitHub Pages.

## How it works (user flow)
1. User fills business details (name, services, email, phone, logo...).  
2. Click **Generate Preview** to render a live website preview (iframe).  
3. The preview is visible for free — **exporting** (copy/download) is locked until the user pays.  
4. After successful payment the export actions become available (copy HTML, download .html, export brand kit).

## Where to add real payments
The demo simulates payment with a browser confirm() box. Replace the payment handler in `index.html` (the `payBtn` click listener) with your real integration:
- **Stripe Checkout**: create a Checkout Session server-side, redirect the user to the session URL, then verify the payment and unlock export.
- **Paystack** (Nigeria): integrate Paystack inline or redirect to a payment page, then verify webhook / reference and unlock export.

## How to deploy
1. Create a public GitHub repository (e.g., `webforge`).
2. Upload `index.html` and `README.md`.
3. In repo settings → GitHub Pages → set source to `main` branch / `index.html`.
4. Visit `https://<your-username>.github.io/<repo-name>/`

## Notes / Security
- The generator refuses to place suspicious HTML (like `<script>` tags) from user inputs into the preview — this prevents the product from "returning code" inside the preview.
- For production: move payment verification server-side and avoid trusting client `paid` state.
- Add server-side quota & rate limits to prevent abuse.

## Next steps (recommended)
1. Hook up Stripe & Paystack server-side to accept payments.
2. Add a simple backend to verify payment and deliver downloadable zip (logo + HTML + README).
3. Add analytics and a minimal dashboard for user sites.
4. Build marketing: landing page + demo videos + pricing tiers.
