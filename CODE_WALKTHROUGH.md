# Jake Robertson — AI Portfolio: Code Walkthrough

The whole site is one file, `index.html` (418 lines), plus the `assets/` folder
(9 files: the dragon sigil, the dragon peak image and video, and the ABYSS,
GRAVITY and STRATA interface panels and concept artwork). There is no build
step and no separate `.css` or `.js` file: the CSS lives in one `<style>` block
and the JavaScript in two `<script>` blocks, all inside `index.html`. It is
plain HTML, CSS and JavaScript — Java is not used to build the site; Java is
only listed on the page as one of Jake's skills.

## 1. The head — lines 1–10

- `<!doctype html>` and `<html lang="en">` — a standard HTML5 document in English.
- `<meta charset="utf-8"/>` — the character encoding, so symbols like — and · display correctly.
- `<meta name="viewport" ...>` — makes the page scale correctly on phones.
- `<meta name="color-scheme" content="dark"/>` — tells the browser this is a dark site.
- `<link rel="icon" ... href="assets/dragon-sigil.webp"/>` — the dragon sigil as the browser-tab icon.
- `<title>Jake Robertson — AI Engineer | New York, NY</title>` — the text shown in the browser tab and in search results.
- The two Google Fonts links load three fonts: **Chakra Petch** (headings and the logo), **IBM Plex Mono** (labels, dates and kickers) and **IBM Plex Sans** (body text).

## 2. The CSS — lines 11–172

Everything visual is in this one `<style>` block, about 162 lines.

- **`:root` variables (lines 12–18):** the design tokens for the whole site. Backgrounds are near-black (`--bg:#05070a`), text is off-white, muted text is grey-blue, and the accent is electric blue `--blue:#00BFFF` with a lighter `--blue2:#6fdcff` and a deeper `--deep:#0077a8`. Changing `--blue` here would recolour the whole site.
- **Base rules:** `box-sizing:border-box` everywhere; `scroll-behavior:smooth` so anchor links glide instead of jumping; `body` uses IBM Plex Sans at 1.6 line height. `body::before` draws the faint vertical/horizontal grid lines and the blue glow at the top; `body::after` draws the faint dot pattern that fades out down the page.
- **`.wrap`:** the centred content column, max 1160px wide, with 22px side padding.
- **Nav (`header`, `.nav`, `.logo`, `.navlinks`, `.btn`):** the sticky top bar with a blurred dark background, the round dragon-sigil logo mark, the section links, and the pill buttons. `.btn-primary` is the filled blue button. Two media queries hide most nav links on narrow screens.
- **Introduction (`.hero`, `.hero-grid`, `.eyebrow`, `h1`, `.role`, `.lede`, `.hero-ctas`, `.hero-meta`, `.chip`):** a two-column grid (text left, video card right) that collapses to one column under 900px. `h1` uses `clamp()` so the name scales from 44px on phones to 76px on desktop. The eyebrow pill, the glowing blue full stop after ROBERTSON, and the chips (Python, IBM certificates, LAFS May 2027, Lehman Fall 2027, Hickey Dec 2011) all live here.
- **Video card (`.dragon-card`, `.dragon-caption`, `.badge`):** the square video/image card with a dark gradient overlay at the bottom and a caption giving the name and role.
- **Stats (`.stats`, `.stat`):** the four boxes under the introduction — AI Evaluation, 4 Languages, 3 Instruments, 2 IBM Professional Certificates — in four columns, two on small screens.
- **Sections (`.sec-head`, `.kicker`, `.sigil`, `.grid2`, `.grid3`, `.card`):** every section shares the same pattern: a numbered kicker ("01 — About Me") with a small sigil, a big Chakra Petch heading, and a muted paragraph on the right. `.grid2` and `.grid3` are the two- and three-column card layouts, collapsing to one column under 900px.
- **About (`.about-card`, `.tags`, `.tag`):** the highlighted about card with a blue radial glow, and the pill tags for the Top Skills (blue tags) and the other skills.
- **Skills (`.skill-row`, `.bar`):** the skill bars. The filled width is set inline in the HTML (`style="width:72%"` for Python, 78% HTML/CSS, 62% JavaScript, 55% Java, 90% AI Evaluation & Rubrics), and the gradient fill runs from deep blue to light blue with a blue glow.
- **Timeline (`.timeline`):** the Experience & Education list and the Certifications lists. Each row is a two-column grid: a monospace date on the left (e.g. "OCT 2026 —") and the role or certificate on the right.
- **Projects (`.project`, `.project-top`, `.project-num`, `.project-body`, `.mini-list`):** the three project cards, each with a numbered label ("PROJECT — 01 / AI"), a heading, a description, and a bulleted list with blue ▸ markers.
- **Instruments (`.inst`, `.price`, `.presets`, `.ui-shot`, `.ui-cap`, `.art-shot`, `.art-cap`):** the ABYSS, GRAVITY and STRATA cards. Each has a 3px coloured top border — green `#2FA866` for ABYSS (`.inst.green`), blue for GRAVITY, violet `#5B7AFF` for STRATA (`.inst.violet`) — a price line, preset pills, a `.ui-shot` figure showing the actual 812 × 375 Decent Sampler interface, and an `.art-shot` figure showing the concept artwork.
- **Contact (`.cta-band`):** the bordered call-to-action band with a blue radial glow, the "Let's build something reliable." heading, and the contact buttons.
- **Footer:** a top border, the copyright line, and "Jake Robertson — AI Portfolio · Built in HTML / CSS / JavaScript".
- **Chatbot styles (`.chat-fab`, `.chat-panel`, `.chat-head`, `.chat-body`, `.msg`, `.quick`, `.chat-form`, `.typing`):** the fixed blue "Ask Jake's Assistant" button at the bottom right, the chat panel that is hidden until `.open` is added, bot messages on the left in dark panels, user messages on the right in blue, the quick-prompt pills, and the input form.
- **Responsive rules:** the `@media` blocks at 760px, 520px, 900px, 800px, 700px and 560px shrink the nav, the introduction, the stats and the grids for phones, and `@media (prefers-reduced-motion: reduce)` turns off smooth scrolling for people who ask for reduced motion.

## 3. The navigation bar — lines 174–182

A sticky `<header>` with the logo (dragon sigil + "JAKE ROBERTSON" + "AI Engineer — NYC") linking to `#top`, and nav links to `#about`, `#skills`, `#certifications`, `#projects`, `#hobbies` and `#contact`, plus an "Ask the Assistant" button that calls `toggleChat(true)` to open the chatbot.

## 4. The introduction — lines 184–217

- **Eyebrow pill:** "Jake Robertson — AI Portfolio" with a small sigil.
- **`h1`:** "JAKE ROBERTSON." in huge Chakra Petch type, with the full stop in glowing blue.
- **Role and location:** "AI Engineer" and "📍 New York, NY · Data Specialist / AI Trainer".
- **`.lede`:** the introduction, written as if speaking to an interviewer — an applied AI engineer based in New York who evaluates AI systems, designs the training tasks that improve them, and builds toward engineering reliable, human-centred AI products.
- **Call-to-action buttons:** "View Projects →" (jumps to `#projects`), "Ask My Assistant" (opens the chatbot), "Resume & Skills" (jumps to `#skills`).
- **Chips:** Python · HTML/CSS · JavaScript · Java; IBM Professional Certificates in progress; Music Production Bachelor's May 2027; Lehman B.S. CS Fall 2027; Graphic Design Associates Degree, Hickey College, Dec 2011.
- **Video card:** a `<video>` (autoplay, muted, loop, playsinline, with `assets/dragon-peak.webp` as the poster and fallback image), with a caption giving the name and role.
- **Stats row:** the four stat boxes described in the CSS section above.

## 5. About — lines 220–243

Section `id="about"`, kicker "01 — About Me", heading "Evaluation, architecture, and engineering." Two cards: the about card with the full introduction (applied AI engineer and AI domain task architect, token-level model mechanics, context engineering, Ground Truth, multi-agent comparison, Mercor work) and the Top Skills tags; and a "What I bring to a team" card listing evaluator + architect + engineer, creative technologist, detail-obsessed, and the clear path (IBM certificates, LAFS May 2027, Hickey, Lehman Fall 2027).

## 6. Skills and resume — lines 246–281

Section `id="skills"`, kicker "02 — Resume / Skills". Left card: Technical Skills with the five skill bars, the Top Skills tags, the other skill tags (Data Annotation, Content QA, PII Redaction, SFT/RLHF Rubrics, Multi-Turn Tool Use, Multimodal Synthetic Data, Decent Sampler, UI Design), Languages (Haitian Creole — Elementary), and Graphic Design — SyEn3rgy GraphiX with its 15 design-skill tags and a link to `@syen3rgygraphix_official`. Right card: Experience & Education as a timeline — Mercor AI Domain Task Architect (Oct 2026–Present), Mercor AI Evaluation Specialist, Project Horn (Nov 2026–Nov 17, 2026, concluded), SyEn3rgy GraphiX founder (2019–), the two IBM Professional Certificates in progress, LAFS Bachelor's (May 2, 2027), Lehman B.S. CS (Fall 2027), CTU coursework toward a B.S. in Business Administration (Feb 2023–Mar 2024, not completed), and the Hickey Graphic Design Associates Degree (Dec 2011).

## 7. Certifications — lines 284–309

Section `id="certifications"`, kicker "02b — Certifications". Two cards: "AI & Generative AI" with seven timeline entries (Mastering Model Mechanics, GenAI for Executives & Business Leaders, Python for Data Science, AI & Development, Introduction to Agents, Generative AI Essentials, Generative AI: Prompt Engineering Basics, AI Foundations) and "Other" with two (Honored Listee — Marquis Who's Who, An Insider's Guide to Today's Music Biz), plus a note that the two IBM Professional Certificates are in progress.

## 8. Projects — lines 312–320

Section `id="projects"`, kicker "03 — Projects", heading "Selected Work". Three cards in a three-column grid: AI Evaluation Practice (Mercor rubric scoring, QA, PII), Virtual Instrument Family (ABYSS, GRAVITY, STRATA for Decent Sampler), and This Portfolio & Chatbot (hand-built in HTML, CSS and JavaScript, with the chatbot that answers only from this page, and an "Open the Chatbot →" button).

## 9. Hobbies and instruments — lines 323–336

Section `id="hobbies"`, kicker "04 — Hobbies & Music", heading "Instruments & Sound". Three instrument cards: **ABYSS** (dark ambient drone, green accent, presets Dark, Deep, Ethereal, Abyssal, Void), **GRAVITY** (bass synth, blue accent, presets Round, Loam, Smoke, Magma, Bedrock) and **STRATA** (cinematic pads, violet accent, proposed presets Dawn, Horizon, Ember, Dusk, Aurora). Each shows the actual Decent Sampler interface panel (812 × 375) and the concept artwork. Below them is the SyEn3rgy Music card, with a "Learn More" button whose link is still a placeholder (`href="#"`) — Jake is to set the final URL later.

## 10. Contact — lines 339–345

Section `id="contact"`, the `.cta-band`: "Let's build something reliable." with the note that Jake is interested in AI Trainer / Evaluator, AI Data and junior AI Engineer roles, and collaborations in AI + music technology. The buttons are "Ask Jake’s Assistant" (opens the chatbot), GitHub — @Xado-TheDarkEngineer, LinkedIn — Jay Robertson, "Review Projects" and "Back to Top ↑". No phone number or email is published on the page.

## 11. Footer — line 347

"© 2026 Jake Robertson — AI Engineer, New York, NY" on the left, and "Jake Robertson — AI Portfolio · Built in HTML / CSS / JavaScript" on the right.

## 12. The chatbot HTML — lines 350–356

- A fixed floating button (`.chat-fab`, `id="chatFab"`) — "Ask Jake's Assistant" — that calls `toggleChat()`.
- The hidden chat panel (`.chat-panel`, `id="chatPanel"`, `role="dialog"`): a header with "Jake’s Assistant — Answers from this page only · No made-up claims", an empty `.chat-body` (`id="chatBody"`) that JavaScript fills with messages, a `.quick` row (`id="quickPrompts"`) that JavaScript fills with quick-prompt buttons, and a form (`.chat-form`, `id="chatForm"`) with the input (`id="chatInput"`, placeholder "Ask about skills, projects, education…") and a Send button.

## 13. The JavaScript, part 1 — the video — lines 358–370

A small immediately-invoked function that finds the video (`.dragon-video` in the code), forces it muted, and respects `prefers-reduced-motion`: if the visitor asked for reduced motion, it removes autoplay and pauses the video; otherwise it plays it, swallowing any autoplay error. It also listens for the setting changing while the page is open.

## 14. The JavaScript, part 2 — the chatbot — lines 372–418

- **`KB` (the knowledge base):** an array of 14 entries. Each entry has `k`, a list of keywords, and `a`, the answer. The topics are graphic design, skills, Mercor work, certifications, projects, ABYSS, GRAVITY, STRATA, instruments/music, education, location, contact, who Jake is, and greetings. Every answer is written from the content on the page itself — the chatbot never invents facts.
- **`FALLBACK`:** the reply when no keywords match — "I can only answer from what's on this page", followed by suggested topics.
- **`toggleChat(force)`:** opens or closes the panel, hides the floating button while the panel is open, and on first open sends the greeting message ("Hi — I'm Jake's assistant…") and focuses the input.
- **`addMsg(text, who)`:** creates a message bubble (`.msg bot` or `.msg user`), adds it to the chat body, and scrolls to the bottom.
- **`answer(q)`:** lowercases the question, then scores every KB entry — a matched keyword longer than 4 characters scores 2, a shorter one scores 1 — and returns the highest-scoring entry's answer, or the FALLBACK if nothing matched.
- **Form submit handler:** on submit it stops the page reloading, reads and clears the input, adds the question as a user message, adds a temporary "Thinking…" message, and after 420 milliseconds replaces it with the answer.
- **Quick prompts:** six buttons are built from a list — "What are Jake's skills?", "Tell me about GRAVITY", "What does Jake do at Mercor?", "What's his education path?", "What instruments has he built?", "What graphic design does Jake do?" — and clicking one fills the input and submits the form.

## How to change things

- **Text content:** edit the HTML in the matching section (introduction, about, skills, certifications, projects, hobbies, contact).
- **Colours:** edit the `--blue`, `--blue2` and `--deep` variables in `:root` at the top of the `<style>` block.
- **Chatbot answers:** edit the `a` strings in the `KB` array, or add a new entry with its own `k` keyword list.
- **The "Learn More" button:** replace `href="#"` in the SyEn3rgy Music card with the final URL.
- **Publishing:** commit and push to GitHub; GitHub Pages serves the `master` branch, so the live site updates automatically. Live site: https://xado-thedarkengineer.github.io/electric-blue-dragon-portfolio/
