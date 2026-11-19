# Landing brief

Business facts for this page. Claude reads it before writing anything and never invents what is missing.

Short, reusable values (brand, colours, URL, title, headline, CTA, form endpoint, author, verification codes)
live in `site.config.json`, not here: the build puts them into every page. This file holds everything else.

## Design (ustalony – nie zmieniać bez zgody klienta)
- Źródło: zatwierdzona makieta „tomato-studio-final z video.html” (listopad 2026). Układ, kolejność sekcji, kolory, czcionki i CTA mają być jak na makiecie.
- Kolory: tło #FAFAF2, tekst/ciemne pasy #1D180C, akcent (pomidor) #CB422A, jasne pasy #F0F0E3. Tokeny w `src/css/styles.css` (`:root`).
- Czcionki: Outfit (Google Fonts) w treści, Chillax (Fontshare) w dużych tytułach i liczbach (`.mega`, `.chx`, `.page-title`).
- Tylko jasny wygląd (makieta nie ma trybu ciemnego).
- Podstrony: index (strona główna), realizacje, dla-biznesu, o-nas, kontakt, konsultacja (+ polityka prywatności, 404, podziękowanie).

## Identity
- LOGO: src/img/logo.svg (pełne logo), src/img/sygnet.svg (sygnet; favicon to sygnet na kremowym tle)
- Social profiles (become schema.org `sameAs`):
  - https://www.instagram.com/tomatostudio.archi/
  - https://www.facebook.com/tomatostudio.interiordesign
  - https://www.linkedin.com/company/tomato-archi/

## Hosting
- REPO_NAME: tomato-studio
- REPO_OWNER: GKunc
- CUSTOM_DOMAIN: tomatostudio.com.pl (dziś działa tam stara strona na WordPressie – przepięcie domeny dopiero po akceptacji)

## Business
- What is offered: projektowanie wnętrz – od konsultacji i pomiaru, przez układ funkcjonalny, koncepcję z wizualizacjami 3D i projekt wykonawczy, po nadzór i odbiór.
- Target audience: klienci prywatni (domy, mieszkania, apartamenty, lokale inwestycyjne na wynajem) oraz biznes (deweloperzy, hotele, gastronomia, operatorzy PRS/PBSA, biura).
- Main problem solved: wnętrze zaprojektowane tak, żeby dało się je zbudować w budżecie i terminie; zmiana w projekcie jest tańsza niż na budowie.
- Unique selling points: architekci po Politechnice Krakowskiej, niemal dekada doświadczenia, projekty dla sieci hotelowych (m.in. Radisson, Hilton), nadzór na budowie.
- Price / offer: 30 minut bezpłatnej konsultacji; projekt zwykle 6–12% wartości całej inwestycji.
- Location / service area: ul. Pod Fortem 15A/3, Kraków; Małopolska i Podkarpacie na miejscu, cała Polska zdalnie.
- Telefony: +48 696 166 002 (Filip Kieras), +48 512 102 789 (Bartosz Młynarski); e-mail biuro@tomatostudio.com.pl

## Proof (real only)
- Testimonials: opinie Google (bartek, Ewa Blada, Katarzyna Sota, Katarzyna Słupek, Paweł Morawiecki) – treść z makiety.
- Numbers / results: 10Y+ doświadczenia, 70+ koncepcji, 1600 m²+ przestrzeni prywatnych, 10 000 m²+ komercyjnych, 4000+ rysunków i wizualizacji, 10 mln+ wartości realizacji prywatnych (liczby zespołu, także z pracy w pracowni Iliard).
- Client logos: Kraków Airport, Expert Budownictwo, Archiflow AI, Bliskość, CD Locum, Sąsiedzi Development, Browary Tarnowskie, Nago Sushi & Sake.
- Publikacje: Onet, MAGAZIF, Dom Wprost, Domni.pl, Nowy Magazyn (2026).

## FAQ (real questions customers ask; becomes the FAQ section + FAQPage schema)
- Q: Ile kosztuje projekt wnętrz?
  A: Zwykle 6–12% wartości całej inwestycji; dokładna wycena po bezpłatnej konsultacji.
- Q: Odbieram mieszkanie od dewelopera. Kiedy się zgłosić?
  A: Przed terminem zmian lokatorskich.
- Q: Czy pracujecie poza Krakowem?
  A: Małopolska i Podkarpacie na miejscu, cała Polska zdalnie.
- Q: Czy muszę mieć rzut mieszkania?
  A: Nie, projekt robimy na podstawie własnego pomiaru.
- Czekają na odpowiedź klienta (w makiecie były puste): „Ile trwa projekt mieszkania?”, „Czy pomagacie wybrać ekipę?”

## Author (for blog posts and E-E-A-T; name and URL go into site.config.json)
- AUTHOR_BIO: (brak)

## Voice
- Tone: bezpośredni, ciepły, konkretny; do klientów prywatnych na „Ty”, do biznesu na „Państwo”.
- Words to use / avoid: metafora pomidora („dobry projekt musi dojrzeć”).

## SEO
- Primary keyword: projektowanie wnętrz Kraków
- Secondary keywords: architekt wnętrz Kraków, projekt mieszkania, projekt domu, wnętrza komercyjne, projekt wnętrz hotelu/restauracji
- Competitors / reference sites:

## Forms, analytics, compliance
- Contact form: form worker with autoreply (dwa formularze: konsultacja.html i dla-biznesu.html; dodatkowe pola trafiają do treści wiadomości przez js/site.js)
- Who receives enquiries: biuro@tomatostudio.com.pl
- Reply promise for the autoreply: oddzwonimy w ciągu 24 godzin w dni robocze (konsultacja); biznes: w ciągu jednego dnia roboczego
- Named person to sign the autoreply:
- Analytics wanted: (do ustalenia)
- AI_CRAWLERS: allow-all

## Facts Claude must not invent
- Nazwa firmy do polityki prywatności (forma prawna, NIP) – na razie tylko „Tomato Studio”.
- Czas trwania projektu, liczba dni na wycenę, referencje inwestorów biznesowych – nie podawać, dopóki klient ich nie przekaże.

## site.config.json cheat sheet
| Key | What to put |
| --- | --- |
| BRAND, BRAND_INITIAL | name; one letter for the generated favicon |
| THEME_COLOR | brand accent as 6-digit #hex |
| LANG, LOCALE | e.g. `pl` and `pl_PL` |
| LEGAL_ENTITY, CONTACT_EMAIL | who is responsible for the site (privacy policy) |
| SITE_URL | (auto, publish skill) https URL without trailing slash |
| INDEXNOW_KEY | (auto) `openssl rand -hex 16` |
| PAGE_TITLE | 30-60 chars incl. brand, primary keyword first |
| H1_HEADLINE, SUBHEADLINE, CTA_LABEL | hero copy and button label |
| META_DESCRIPTION | 120-155 chars, with a reason to click |
| LLMS_SUMMARY | 2-4 plain sentences: what the business is, for whom, where |
| BLOG_TITLE, BLOG_DESCRIPTION | needed from the first post on |
| AUTHOR_NAME, AUTHOR_URL | blog author (LinkedIn or about page) |
| FORM_ENDPOINT | (auto with the form worker: `node tools/form-worker.mjs deploy`) or the external form service URL |
| FORM_PROVIDER | who processes the form, for the privacy policy ("Cloudflare and Resend" with the worker) |
| EMAIL_FROM | sender of the autoreply; domain verified in Resend |
| FORM_NOTIFY_TO | who gets enquiries (empty = CONTACT_EMAIL) |
| TURNSTILE_SITE_KEY | Cloudflare Turnstile site key (anti-bot check, needed for the autoreply) |
| FORM_ACCESS_KEY | only for services that need a key in the form (e.g. Web3Forms) |
| ANALYTICS, ANALYTICS_ID | `none`, `plausible` (id = domain, may stay empty), `goatcounter` (site code), `cloudflare` (token), `ga4` (G-…) |
| PRIVACY_UPDATED | YYYY-MM-DD |
| GOOGLE_SITE_VERIFICATION, BING_SITE_VERIFICATION | filled after launch (`node tools/google.mjs verification-token`) |
