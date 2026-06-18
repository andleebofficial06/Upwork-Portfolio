# Andleeb Asghar — Portfolio Website

This repository contains the source files for Andleeb Asghar's personal SEO strategist & medical content writer portfolio website.

## Files

| File | Purpose |
|---|---|
| `index.html` | Main public-facing website (full version — includes Calendly booking, contact form, pricing, etc.) |
| `profile.png` | Profile photo (background removed), used across the hero and About sections |
| `upwork-portfolio.html` | Self-contained version of the site to send directly to Upwork clients — no personal contact info, booking links, or off-platform contact methods. All CTAs point to the Upwork profile instead. Images are embedded, so this file works standalone with no other assets needed. |

## Setup — `index.html`

1. Keep `index.html` and `profile.png` in the **same folder**.
2. Upload both files to your hosting (e.g. GitHub Pages, Netlify, or any static host).
3. The site is plain HTML/CSS/JS — no build step required.

### Contact form (EmailJS)
The contact form uses [EmailJS](https://emailjs.com) to deliver messages straight to your inbox without a backend server.

- **Service ID:** `service_qsuynvk`
- **Template ID:** `template_mq9unrl`
- **Public Key:** set in the `emailjs.init("...")` call near the top of `index.html`

If you ever need to change where messages are delivered, update the **To Email** field inside your EmailJS template (not in the code) — EmailJS templates control the destination address.

Template variables sent from the form:
```
from_name, from_email, website, service, message, email
```
Make sure these match exactly inside your EmailJS template content and "To Email" field.

### Booking (Calendly)
The "Book a Call" buttons open a Calendly popup using:
```
https://calendly.com/andleebasghar06/seo-support-discussion
```
To change the link, search for `calendly.com` inside `index.html` and replace the URL in both the button `onclick` handlers.

## Setup — `upwork-portfolio.html`

This file is meant to be sent or shared **as-is** with Upwork clients during proposals or messages. It requires no setup:

- Fully self-contained — all images are embedded as base64, so there are no external file dependencies.
- No contact form, no email, no booking links — every call-to-action points to:
  ```
  https://www.upwork.com/freelancers/andleeba7
  ```
- Includes a footer disclaimer stating all work is conducted exclusively through Upwork.

To update it later (e.g. add new testimonials or case studies), edit the testimonial cards inside the `<!-- TESTIMONIALS -->` section, or update the Upwork profile screenshot by replacing the embedded image.

## Customizing

- **Colors / fonts:** defined as CSS variables at the top of the `<style>` block (`--ink`, `--gold`, `--teal`, etc.) and the Google Fonts `<link>` tag (currently using **Inter**).
- **Stats / numbers:** hero stats and result cards use `data-target="600"` style attributes — the counter animation reads this value automatically.
- **Sections:** each section is wrapped in `<section id="...">` and linked from the nav via `href="#..."` — keep IDs and links in sync if you rename or reorder sections.

## Notes

- This site has no backend — it's static HTML/CSS/JS that runs entirely in the browser.
- Large file sizes (`index.html` and `upwork-portfolio.html`) come from embedded base64 images. If you want smaller, faster-loading files, you can re-host the images separately (e.g. `profile.png`, `upwork-profile.png`) and reference them with a normal `<img src="...">` path instead.
