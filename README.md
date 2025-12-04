Royalty Cucina — Local site instructions
======================================

What I changed
- Added `favicon.svg` and referenced it from every page.
- Wired the contact form to Formspree using a placeholder endpoint `https://formspree.io/f/{your-form-id}`. Replace `{your-form-id}` with your real Formspree ID.
- Improved keyboard focus styles and added visually-hidden labels for form inputs.
- Added Open Graph meta tags placeholders for better social sharing previews.

Quick setup — enable contact form (Formspree)
1. Visit https://formspree.io and sign up (free tier available).
2. Create a new form; Formspree will give you a form endpoint like `https://formspree.io/f/mwkz1234`.
3. Open `contact.html` and replace `https://formspree.io/f/{your-form-id}` with your actual endpoint.
4. Optionally configure the destination email in Formspree settings.

Test the form locally
1. Open `index.html` (or `Restaurant.html`) in your browser.
2. Go to the Contact page and submit the form — you should receive a confirmation email from Formspree or see the submission in your Formspree dashboard.

Running Lighthouse (recommended)
- Open Chrome and go to the page you want to audit (start with `Restaurant.html`).
- Open DevTools (F12) → Lighthouse tab.
- Choose categories (Performance, Accessibility, Best Practices, SEO) and Device (Mobile/Desktop), then click "Generate report".
- Review the report: Lighthouse will list prioritized issues and suggested fixes.

Common Lighthouse quick wins I already applied
- Added `rel="canonical"` and Open Graph meta tags.
- Added `rel="preload"` for the hero image and `loading="lazy"` plus `width`/`height` on images to reduce CLS.
- Added keyboard focus styles and accessible labels.

If you want, I can run these steps for you and produce a prioritized fix list based on Lighthouse recommendations you paste here.

Performance changes made in this commit
- Inlined a small set of critical CSS into `Restaurant.html` to speed first render.
- Switched stylesheet loading to `rel="preload"` + `onload` across pages (with `<noscript>` fallback) so rendering isn't blocked while the full stylesheet downloads.
- Added `srcset`/`sizes` and `loading="lazy"` to hero and menu images to serve appropriate sizes and reduce layout shifts.
- Preloaded the hero image using `rel="preload" as="image"`.

If you'd like more aggressive optimizations I can:
- Create optimized local image files (webp) and update image references, or
- Generate critical CSS automatically and inline it in all pages, or
- Add service-worker based caching for assets.

Notes & next steps
- Add a real `og:url` canonical link per page once you have a live site URL (replace `https://example.com/...`).
- If you prefer a server-side solution, I can add a simple Node/Express endpoint or integrate a serverless function.
- To check performance/accessibility scores, open Chrome DevTools → Lighthouse and run an audit.

If you'd like, I can replace the Formspree placeholder with a working free endpoint I create for you, or set up a tiny serverless webhook to collect messages into a file.
