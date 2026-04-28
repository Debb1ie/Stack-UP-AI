# Stack Up: Build the AI-Powered World Before It Builds Without You

**PUP CCIS Technical Seminar — Official Website**

A fully static, single-file seminar website for *Stack Up*, a technical seminar organized by the College of Computer and Information Sciences of the Polytechnic University of the Philippines. The site is built with vanilla HTML, CSS, and JavaScript — no frameworks, no dependencies, no build step required.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [File Structure](#file-structure)
- [Sections](#sections)
- [Customization Guide](#customization-guide)
- [Color Themes](#color-themes)
- [Typography](#typography)
- [Browser Support](#browser-support)
- [Deployment](#deployment)
- [Credits](#credits)

---

## Overview

The seminar is designed to transition students from AI users to AI builders. It delivers structured sessions on cloud-native deployment, autonomous agent development, real-world industry applications, and legal-ethical compliance.

This website serves as the public-facing landing page for the event — covering seminar objectives, speaker profiles, program flow, contact information, and event registration.

---

## Features

**Navigation**
- Fixed top navigation bar with smooth scroll to all sections
- Active section highlighting with a red underline indicator, updated on scroll
- Hamburger menu for mobile with animated open/close (three lines to X)
- Body scroll lock when the mobile menu is open
- Closes on Escape key or outside tap
- Register Now button embedded directly in the nav bar
- Nav shadow appears on scroll for depth

**Hero Section**
- Full-viewport animated landing with staggered text reveals
- Background grid pattern with radial mask and red glow effect
- Pulsing live badge indicator
- Scroll prompt with animated line

**Marquee Strip**
- Continuously scrolling topic ticker between hero and content sections

**Scroll Reveal**
- All content sections animate in on scroll using `IntersectionObserver`
- Directional reveals: upward, left-slide, right-slide

**Theme Toggle**
- Dark mode (black + red) and light mode (white + red)
- Preference persisted to `localStorage` — survives page reload

**Back to Top**
- Floating red circular button appears after scrolling 400px
- Smooth scrolls back to top on click

**Footer**
- Social links: Facebook, Instagram, Email
- Navigation links with smooth scroll
- External PUP links open in a new tab
- All anchor links share the same smooth scroll handler

---

## File Structure

```
stackup-seminar/
└── stackup-seminar.html    # Entire website — self-contained single file
└── README.md               # This file
```

All CSS, JavaScript, and HTML are contained in a single file. The only external resources loaded are Google Fonts (Bebas Neue, Barlow, Barlow Condensed) via a `<link>` tag in the `<head>`.

---

## Sections

| Section | ID | Description |
|---|---|---|
| Hero | `#home` | Animated landing with title, tagline, and CTA buttons |
| About CCIS | `#about` | College overview, emblem, and stat cards |
| Objectives | `#objectives` | Six objective cards covering seminar goals |
| Speakers | `#speakers` | Five speaker cards with image placeholders |
| Program Flow | `#program` | Full event timeline from registration to closing |
| Contact | `#contact` | Contact info and inquiry form |
| Footer | — | Navigation, social links, PUP external links |

---

## Customization Guide

### Registration Link

Search for all instances of `href="#"` paired with `title="Registration link coming soon"` and replace `#` with the actual registration URL.

There are two instances:
- The Register Now button in the hero section
- The Register Now link in the nav bar

```html
<!-- Before -->
<a href="#" class="btn-primary" title="Registration link coming soon">

<!-- After -->
<a href="https://your-registration-link.com" class="btn-primary">
```

### Speaker Information

Each speaker card is inside `.speakers-grid`. To update a speaker:

1. Replace the placeholder `<div class="speaker-img-placeholder">` block with an `<img>` tag:

```html
<!-- Before -->
<div class="speaker-img-placeholder">
  <div class="speaker-avatar">...</div>
  <span class="speaker-img-label">Speaker Photo</span>
</div>

<!-- After -->
<img src="path/to/photo.jpg" alt="Speaker Name" style="width:100%;height:100%;object-fit:cover;">
```

2. Update the name, role, and topic inside `.speaker-info`:

```html
<div class="speaker-name">Full Name Here</div>
<div class="speaker-role">Job Title / Designation</div>
<div class="speaker-org">Topic: Session Title Here</div>
```

### Program Flow

Each agenda item is a `.program-event` block. To add, remove, or edit an entry:

```html
<div class="program-event reveal">
  <div class="event-dot"></div>          <!-- red dot; add class "break" for gray -->
  <div class="event-body">
    <div class="event-time">8:00 AM - 9:00 AM</div>
    <div class="event-title">Session Title</div>
    <div class="event-desc">Short description of the session.</div>
    <span class="event-tag">Tag Label</span>
  </div>
</div>
```

Available tag styles:

| Class | Appearance |
|---|---|
| `event-tag` | Red (default) |
| `event-tag keynote` | Blue |
| `event-tag break-tag` | Gray |

### Event Date

Find the contact section and update the date:

```html
<p>To Be Announced — 2025</p>
```

### Social Links

In the footer, update the `href` values for Facebook and Instagram:

```html
<a href="https://www.facebook.com/your-page" ...>Facebook</a>
<a href="https://www.instagram.com/your-handle" ...>Instagram</a>
```

### Contact Email

Replace all instances of `ccis@pup.edu.ph` with the correct contact email.

---

## Color Themes

### Dark Mode (default)

| Role | Value |
|---|---|
| Background primary | `#0a0a0a` |
| Background secondary | `#111111` |
| Background tertiary | `#161616` |
| Text primary | `#f0f0f0` |
| Text secondary | `#a0a0a0` |
| Accent red | `#E8281A` |

### Light Mode

| Role | Value |
|---|---|
| Background primary | `#ffffff` |
| Background secondary | `#f7f7f7` |
| Text primary | `#111111` |
| Text secondary | `#555555` |
| Accent red | `#E8281A` |

All colors are declared as CSS custom properties under `[data-theme="dark"]` and `[data-theme="light"]` on the root `<html>` element. Switching themes is done by toggling the `data-theme` attribute.

---

## Typography

| Font | Usage | Source |
|---|---|---|
| Bebas Neue | Headings, logo, large display text | Google Fonts |
| Barlow Condensed | Labels, tags, nav links, section labels | Google Fonts |
| Barlow | Body text, descriptions, form fields | Google Fonts |

---

## Browser Support

The site uses standard modern CSS and JavaScript APIs with no polyfills required.

| Feature | API Used |
|---|---|
| Scroll reveal | `IntersectionObserver` |
| Theme persistence | `localStorage` |
| Smooth scroll | `window.scrollTo` with `behavior: smooth` |
| CSS variables | Custom properties (`--var`) |
| Grid layout | CSS Grid |
| Backdrop blur | `backdrop-filter: blur()` |

Minimum recommended versions: Chrome 88+, Firefox 87+, Safari 14+, Edge 88+.

---

## Deployment

The website is a single self-contained `.html` file. No build process, package manager, or server-side code is required.

**Option 1 — Direct file open**

Open `stackup-seminar.html` directly in any modern browser.

**Option 2 — Static hosting**

Upload `stackup-seminar.html` to any static host:

- GitHub Pages
- Netlify (drag and drop)
- Vercel
- Any shared web hosting (cPanel file manager)

**Option 3 — Rename to index.html**

Rename the file to `index.html` when deploying to a root domain so it serves automatically without specifying the filename in the URL.

---

## Credits

Developed for the **Stack Up: Build the AI-Powered World Before It Builds Without You** seminar organized by:

**College of Computer and Information Sciences**
Polytechnic University of the Philippines
A. Mabini St., Sta. Mesa, Manila

---

*For questions regarding the seminar, contact ccis@pup.edu.ph.*
