# Claude Code Prompt: mypercussionpath.com Homepage

## Context & Goal

You are building the homepage for **mypercussionpath.com** — the primary domain for Spencer Perilloux, an orchestral percussionist and percussion educator based in Michigan. This homepage is a standalone static site (HTML, CSS, vanilla JS or a lightweight framework like Astro or plain HTML/Tailwind) that is **separate** from the existing shop subdomain at `shop.mypercussionpath.com`.

The homepage must:
1. Establish Spencer's identity as a professional orchestral percussionist and educator
2. Funnel visitors toward the shop at `shop.mypercussionpath.com`
3. Capture lesson and performance inquiries via a contact form
4. Present biographical and credential information in a clean, authoritative way
5. Feel cohesive with the shop site's visual identity

Deploy all subagents available to you to accomplish this task in parallel. This prompt is intentionally exhaustive — leave nothing to interpretation.

---

## Design System (Must Match shop.mypercussionpath.com Exactly)

### Color Palette

The shop site uses Tailwind CSS 4 with OKLCH color variables. Replicate these values precisely:

| Token | Value | Usage |
|---|---|---|
| Primary green | `oklch(45% 0.15 145)` | Buttons, links, accents, headings emphasis |
| Primary foreground | `oklch(98% 0 0)` | Text on green backgrounds |
| Background | `oklch(1 0 0)` | Pure white page background |
| Foreground | `oklch(0.235 0.015 65)` | Body text (warm near-black) |
| Muted | `oklch(0.967 0.001 286.375)` | Light gray section backgrounds |
| Muted foreground | `oklch(0.552 0.016 285.938)` | Secondary text, captions |
| Border | `oklch(0.92 0.004 286.32)` | Card borders, dividers |
| Accent green | `oklch(50% 0.15 145)` | Hover states, badges |

In plain hex equivalents for non-Tailwind CSS:
- Primary green: approximately `#2d6a4f` (deep forest green)
- Background: `#ffffff`
- Body text: `#2c2416` (warm dark brown-black)
- Muted bg: `#f5f5f7`
- Muted text: `#6b7280`
- Border: `#e5e5ea`

### Typography

- **Font family:** Use Google Fonts. Load `Inter` (body) and `Playfair Display` (display headings) via CDN link in `<head>`. These are used on the shop site.
- **Heading scale:** `text-4xl` to `text-6xl` for hero H1, `text-3xl` for section H2, `text-xl` for card H3
- **Body:** `text-base` (16px), line-height 1.6
- **Font weight:** 700 for headings, 600 for subheadings, 400 for body

### Spacing & Layout

- Max content width: `1280px`, centered with `auto` margins
- Section padding: `py-16 md:py-24` (64px mobile, 96px desktop)
- Container horizontal padding: `px-4` mobile, `px-6` tablet, `px-8` desktop
- Border radius: `0.65rem` on cards, `0.5rem` on buttons
- Card shadow: `0 1px 3px rgba(0,0,0,0.08), 0 1px 2px rgba(0,0,0,0.04)`

### Component Patterns

- **Primary button:** Green background (`#2d6a4f`), white text, `px-6 py-3`, `border-radius: 0.5rem`, hover darkens 10%
- **Outline button:** White background, green border and text, same sizing, hover fills green
- **Cards:** White background, `border: 1px solid #e5e5ea`, `border-radius: 0.65rem`, subtle shadow
- **Section alternation:** White sections alternate with `#f5f5f7` muted sections
- **Nav:** White background, `border-bottom: 1px solid #e5e5ea`, sticky on scroll, `backdrop-filter: blur(8px)` when scrolled

---

## Site Architecture

This is a **single-page** homepage (`index.html`) with smooth-scroll anchor navigation. No routing needed. Sections in order:

1. **Navigation** (sticky header)
2. **Hero** (full-width, with Spencer's photo)
3. **Authority Bar** (orchestras / credentials strip)
4. **About / Bio** (two-column: photo + text)
5. **What I Do** (three-column cards: Perform / Teach / Create)
6. **Shop CTA** (full-width green band linking to shop)
7. **Testimonials** (two verified testimonials)
8. **Contact Form** (lessons + performance inquiries)
9. **Footer**

---

## Section 1: Navigation

**Structure:** Sticky top bar, white background with blur on scroll.

**Left:** Text logo — `Spencer Perilloux` in `font-weight: 700`, followed by a thin vertical divider, then `Percussionist & Educator` in muted text.

**Right nav links (desktop):**
- About
- Teaching
- Shop (links to `https://shop.mypercussionpath.com`, opens in same tab)
- Contact

**Right CTA button:** `Book a Lesson` — primary green button, links to `#contact` anchor.

**Mobile:** Hamburger menu that opens a full-width dropdown with the same links plus the CTA button.

---

## Section 2: Hero

**Layout:** Full-width section, minimum height `600px` desktop / `500px` mobile.

**Background image:** Use `/images/Spencer_Perilloux_Final-02.jpg` — this is a professional headshot/portrait of Spencer. Apply a subtle gradient overlay from left: `linear-gradient(to right, rgba(255,255,255,0.97) 0%, rgba(255,255,255,0.85) 45%, rgba(255,255,255,0.3) 100%)` so the text on the left is readable against the white background and the photo shows through on the right.

**Content (left-aligned, max-width 600px):**

```
Eyebrow text (small caps, green, letter-spacing: 0.1em):
ORCHESTRAL PERCUSSIONIST · EDUCATOR · MICHIGAN

H1 (large, bold, warm near-black):
Precision, Musicality,
and the Systems to
Build Both.

Subheading (muted, 18px):
Spencer Perilloux is an active orchestral percussionist performing with ensembles across Michigan, and an educator whose teaching centers on diagnostic-first problem solving — giving students the tools to become their own teacher.

Two buttons (stacked on mobile, side-by-side on desktop):
[Primary] Explore the Shop  →  links to https://shop.mypercussionpath.com
[Outline] Book a Lesson     →  links to #contact
```

---

## Section 3: Authority Bar

**Layout:** Full-width, `background: #f5f5f7`, `padding: 32px 0`. Single centered row of orchestra names separated by thin vertical dividers (`|`). On mobile, wrap into two lines.

**Content — display these orchestras in this order:**
```
Saginaw Bay Symphony Orchestra  |  Oakland Symphony Orchestra  |  Flint Symphony Orchestra  |  Michigan Sinfonietta Orchestra  |  Rochester Symphony Orchestra  |  West Michigan Symphony
```

**Above the names, centered small label:**
```
Active performer with Michigan orchestras
```

Style: `font-size: 13px`, `letter-spacing: 0.05em`, `color: muted-foreground`, `font-weight: 500`. Orchestra names in `font-weight: 600`, `color: foreground`.

---

## Section 4: About / Bio

**Layout:** Two-column grid on desktop (photo left, text right), single column on mobile (photo on top).

**Left column — photo:**
Use `/images/IMG_3200.jpg` — this is Spencer performing on marimba outdoors, a natural action shot. Display as a tall portrait-ratio image (`aspect-ratio: 3/4`), `border-radius: 0.65rem`, subtle shadow. Do not crop the top of the image.

**Right column — text:**

```
Eyebrow (green, small, uppercase, letter-spacing):
ABOUT SPENCER

H2:
Orchestral Percussionist.
Educator. Michigan.

Body paragraphs (use this exact copy, do not paraphrase):

Spencer Perilloux holds a Master of Music in Percussion Performance from the University of Michigan, where he studied with Dr. Douglas Perkins, Dr. Ian Antonio, and Jeremy Epp (Detroit Symphony Orchestra). He earned his Bachelor of Music in Percussion Performance from Central Michigan University, studying with Tom Sherwood (Cleveland Orchestra).

He performs regularly as a section and substitute percussionist with orchestras throughout Michigan, including the Saginaw Bay Symphony Orchestra, Oakland Symphony Orchestra, Flint Symphony Orchestra, Michigan Sinfonietta Orchestra (Timpanist), Rochester Symphony Orchestra, West Michigan Symphony, Macomb Symphony Orchestra, Warren Symphony Orchestra, and Windsor Symphony Orchestra. He has also performed with the Detroit Community Chorus and participated in the Roundtop Festival Institute in Texas.

His teaching centers on a diagnostic-first philosophy: rather than prescribing exercises, he teaches students to identify the root cause of technical problems so they can solve them independently. This approach is the foundation of his online course, Unlock The Keyboard, and his broader educational work.

CTA link (green, underlined on hover):
→ Explore teaching resources at shop.mypercussionpath.com
```

**Below the two columns:** A row of three credential badges (simple bordered pill tags):
- `M.M. — University of Michigan`
- `B.M. — Central Michigan University`
- `Roundtop Festival Institute`

---

## Section 5: What I Do

**Layout:** Three equal-width cards in a row on desktop, stacked on mobile. White background section.

**Section heading (centered):**
```
H2: What I Do
Subheading (muted): Performance. Education. Resources.
```

**Card 1 — Perform**
- Icon: a simple music note or stage icon (SVG, green)
- Title: `Orchestral Performance`
- Body: `Active section and substitute percussionist with nine Michigan orchestras. Specializing in keyboard percussion, snare drum, and timpani across a full range of orchestral repertoire.`
- No CTA (performance inquiries go to the contact form)

**Card 2 — Teach**
- Icon: a graduation cap or target icon (SVG, green)
- Title: `Private Instruction`
- Body: `Online lessons for percussionists at all levels. Focused on keyboard percussion fluency, audition preparation, and building the diagnostic skills to practice independently.`
- CTA link: `Book a lesson →` links to `#contact`

**Card 3 — Create**
- Icon: a book or document icon (SVG, green)
- Title: `Educational Resources`
- Body: `Online courses, PDF guides, and play-along tracks built around systematic frameworks for keyboard percussion, snare drum, and orchestral preparation.`
- CTA link: `Visit the shop →` links to `https://shop.mypercussionpath.com`

---

## Section 6: Shop CTA Band

**Layout:** Full-width section, `background: oklch(45% 0.15 145)` (the primary green), white text. Centered content. `padding: 80px 32px`.

**Content:**
```
Eyebrow (white, small, uppercase, letter-spacing: 0.1em, opacity: 0.8):
ONLINE RESOURCES

H2 (white, bold, 36px–48px):
Courses, Guides, and Play-Along Tracks
for Serious Percussionists.

Subheading (white, opacity: 0.85, 18px):
From the Unlock The Keyboard course to free PDF guides, everything in the shop is built around the same diagnostic-first framework Spencer uses in private lessons.

Button (white background, green text, hover: light green bg):
Explore the Shop →   links to https://shop.mypercussionpath.com

Below the button, small white text (opacity: 0.7, 13px):
Includes: Unlock The Keyboard Course · Know Where Your Mallets Are Going PDF · Trust Your Roll PDF · Free Guides
```

---

## Section 7: Testimonials

**Layout:** `background: #f5f5f7`. Two cards side-by-side on desktop, stacked on mobile. Section heading centered above.

**Section heading:**
```
H2: What Educators Are Saying
```

**Testimonial 1:**
```
Quote: "Spencer Perilloux's work serves as a tremendous asset to the teaching of percussion for the modern player. Information such as sticking advice, ideas of generating the best tone for each instrument, listening examples from professional players, and gaining an overall sense of phrasing — this should be considered essential to all percussionists in the high school band program."

Attribution:
Name: Chris Chapman
Title: Professor of Music, Director of Bands — Central Michigan University
```

**Testimonial 2:**
```
Quote: "Spencer Perilloux is a highly accomplished performer and pedagogue who has created an invaluable resource for secondary school percussionists. This comprehensive collection of guidance and the accompanying demonstration videos are not only a must-read and watch for any student auditioning for Illinois All-State, but also for any young percussionist who is looking to take the next step in advancing their technique and musicianship."

Attribution:
Name: Jason Fettig
Title: Director of Bands, University of Michigan · Former Director, The President's Own Marine Band
```

**Card styling:** White background, green left border (`border-left: 4px solid #2d6a4f`), `padding: 32px`, `border-radius: 0.65rem`. Opening quotation mark in large green decorative font above the quote text.

---

## Section 8: Contact Form

**Layout:** Two-column on desktop (left: text/context, right: form), single column on mobile. White background.

**Section heading (left column):**
```
Eyebrow (green, uppercase, small):
GET IN TOUCH

H2:
Lessons & Performance Inquiries

Body text:
Whether you're a student looking for private instruction, a director with a performance inquiry, or a colleague with a question — use this form to reach out. Spencer responds to all inquiries personally.

Below the text, three small info rows with icons:
📧  spencer.perilloux@gmail.com
📍  Garden City, MI (lessons via Zoom)
🎓  Currently accepting new students
```

**Right column — the form:**

Build a functional HTML form that submits via `fetch()` to a **Formspree** endpoint. Use Formspree's free tier (`https://formspree.io/f/YOUR_FORM_ID` — leave this as a placeholder `FORMSPREE_ENDPOINT` for Spencer to fill in). This avoids needing a backend.

**Form fields:**
1. First Name (required, `type="text"`, placeholder: "First name")
2. Last Name (required, `type="text"`, placeholder: "Last name")
3. Email (required, `type="email"`, placeholder: "your@email.com")
4. Inquiry Type (required, `<select>`) with options:
   - `-- Select inquiry type --` (disabled default)
   - `Private Lessons`
   - `Performance / Hiring Inquiry`
   - `Educational / Clinic Inquiry`
   - `General Question`
5. Message (required, `<textarea>`, rows: 5, placeholder: "Tell me a bit about what you're looking for...")
6. Submit button: `Send Message` — primary green, full width

**Form behavior:**
- On submit: show a loading state on the button ("Sending...")
- On success: replace the form with a green success card: "Message sent! Spencer will be in touch within 1–2 business days."
- On error: show a red error message below the button: "Something went wrong. Please email spencer.perilloux@gmail.com directly."
- Validate all required fields client-side before submission, highlight invalid fields with a red border

**Styling:** Each label is `font-weight: 500`, `font-size: 14px`, `margin-bottom: 4px`. Inputs have `border: 1px solid #e5e5ea`, `border-radius: 0.5rem`, `padding: 10px 14px`, `font-size: 16px`. Focus state: `border-color: #2d6a4f`, `box-shadow: 0 0 0 3px rgba(45,106,79,0.15)`.

---

## Section 9: Footer

**Layout:** Full-width, `background: oklch(0.235 0.015 65)` (the warm near-black foreground color), white text. `padding: 48px 32px 32px`.

**Three columns on desktop:**

**Column 1 — Branding:**
```
Spencer Perilloux
(in white, font-weight: 700, 18px)

Percussionist & Educator
(muted white, 14px)

Short tagline:
Building reliable technique through diagnostic-first teaching.
(muted white, 13px, max-width: 220px)
```

**Column 2 — Navigation:**
```
Label: NAVIGATE (uppercase, 11px, letter-spacing: 0.1em, muted white)
Links (white, 14px, hover: green):
- About
- Teaching
- Shop  (→ https://shop.mypercussionpath.com)
- Contact
```

**Column 3 — Resources:**
```
Label: RESOURCES (same style as above)
Links (white, 14px, hover: green):
- Unlock The Keyboard Course  (→ https://shop.mypercussionpath.com/unlock-the-keyboard)
- Know Where Your Mallets Are Going  (→ https://shop.mypercussionpath.com/know-where-your-mallets-are-going)
- Trust Your Roll PDF  (→ https://shop.mypercussionpath.com/trust-your-roll)
- Free Guide  (→ https://shop.mypercussionpath.com/free-guide)
```

**Bottom bar (full width, border-top: 1px solid rgba(255,255,255,0.1), padding-top: 24px):**
```
Left: © 2026 Spencer Perilloux. All rights reserved.
Right: spencer.perilloux@gmail.com
```
Both in muted white, `font-size: 13px`.

---

## Image Assets

All images are already hosted on the site and available at these relative paths. Do not use placeholder images — use these exact filenames:

| Path | Description | Use |
|---|---|---|
| `/images/Spencer_Perilloux_Final-02.jpg` | Professional portrait, Spencer in formal attire | Hero background |
| `/images/IMG_3200.jpg` | Spencer performing on marimba outdoors, natural light | About section photo |
| `/images/Spencer_Perilloux_Final-03.jpg` | Alternative professional portrait | Optional: testimonials or footer accent |
| `/images/IMG_3054.jpg` | Performance action shot | Optional: What I Do section background or card accent |
| `/images/CYEDetroitTimpaniShot.jpg` | Spencer on timpani with Civic Youth Ensembles Detroit | Optional: performance credential visual |

For the hero, the image should be positioned `object-position: center top` so Spencer's face is always visible. The gradient overlay must ensure the left-side text is fully legible at all viewport widths.

---

## SEO Requirements

Add the following to `<head>`:

```html
<title>Spencer Perilloux — Orchestral Percussionist & Percussion Educator | Michigan</title>
<meta name="description" content="Spencer Perilloux is an orchestral percussionist performing with Michigan symphonies and a percussion educator specializing in keyboard percussion fluency. Private lessons, online courses, and free resources.">
<meta name="keywords" content="percussion educator, orchestral percussionist, keyboard percussion lessons, marimba lessons online, percussion courses, Michigan percussionist, mallet percussion, Spencer Perilloux">
<meta property="og:title" content="Spencer Perilloux — Orchestral Percussionist & Educator">
<meta property="og:description" content="Active orchestral percussionist with Michigan symphonies. Online percussion lessons and courses built around diagnostic-first teaching.">
<meta property="og:image" content="/images/Spencer_Perilloux_Final-02.jpg">
<meta property="og:url" content="https://mypercussionpath.com">
<meta name="twitter:card" content="summary_large_image">
<link rel="canonical" href="https://mypercussionpath.com">
```

Also add structured data (JSON-LD) for a `Person` schema:

```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Spencer Perilloux",
  "jobTitle": "Orchestral Percussionist and Percussion Educator",
  "url": "https://mypercussionpath.com",
  "email": "spencer.perilloux@gmail.com",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Garden City",
    "addressRegion": "MI",
    "addressCountry": "US"
  },
  "alumniOf": [
    {
      "@type": "EducationalOrganization",
      "name": "University of Michigan"
    },
    {
      "@type": "EducationalOrganization",
      "name": "Central Michigan University"
    }
  ],
  "sameAs": [
    "https://shop.mypercussionpath.com"
  ]
}
```

---

## Technical Requirements

- **No build step required.** Deliver a single `index.html` file with inline `<style>` and `<script>` tags, or a minimal file structure of `index.html` + `style.css` + `main.js`. Do not use React, Vue, or any framework that requires a build process.
- **Tailwind CSS via CDN** is acceptable: `<script src="https://cdn.tailwindcss.com"></script>` with a `tailwind.config` block in the script tag for the custom colors.
- **Google Fonts via CDN:** Load Inter and Playfair Display.
- **Fully responsive:** Must look correct at 320px, 768px, 1024px, and 1440px widths.
- **No external JS dependencies** beyond Tailwind CDN and Google Fonts. The contact form uses native `fetch()`.
- **Smooth scroll:** `html { scroll-behavior: smooth; }` and all anchor links use `#section-id` format.
- **Accessible:** All images have descriptive `alt` text. Form fields have associated `<label>` elements. Color contrast meets WCAG AA (the green on white is approximately 4.8:1).
- **Performance:** Images use `loading="lazy"` except the hero image which uses `loading="eager"`. Add `width` and `height` attributes to all `<img>` tags to prevent layout shift.

---

## What NOT to Do

- Do not use dark backgrounds anywhere. The entire page is white/light gray/green only.
- Do not use generic stock photo placeholders. Use the exact image filenames listed above.
- Do not add sections not listed in this prompt (no blog feed, no social media wall, no pricing table — those are on the shop).
- Do not use emoji in the main content. The contact section info rows may use simple Unicode symbols (✉ ⊙) as an exception.
- Do not make the page look like a generic AI-generated template. The typography hierarchy, the green accent color, the warm near-black body text, and the professional photography should make it feel crafted and specific to Spencer.
- Do not add a cookie banner, GDPR notice, or any legal boilerplate unless specifically requested.
- Do not add social media links — Spencer does not have social profiles to link to on this page.

---

## Formspree Setup Note

Leave the form action as `https://formspree.io/f/FORMSPREE_ENDPOINT` as a literal placeholder string. Add an HTML comment above the form tag:

```html
<!-- SETUP: Replace FORMSPREE_ENDPOINT with your actual Formspree form ID.
     Create a free account at https://formspree.io, create a new form,
     and paste the form ID (e.g., xpwzabcd) in place of FORMSPREE_ENDPOINT. -->
```

---

## Deliverable

Deliver a complete, ready-to-deploy `index.html` file (and optionally a companion `style.css` if you separate styles). The file should be immediately hostable on any static host (IONOS, Netlify, GitHub Pages, etc.) by uploading it to the root of the domain. The only manual step required after delivery is replacing `FORMSPREE_ENDPOINT` with a real Formspree form ID.
