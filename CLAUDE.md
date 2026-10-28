# Mark Taylor #82 website

Static site (HTML + CSS + one inline script, no build step) for motorcycle racer Mark Taylor, built and maintained by Rob Dessoy. Live at https://marktaylor82.com. The customer is happy with the current design.

NOTE: every file in this repo is served publicly by GitHub Pages. Do not put emails, account numbers or other private details in this file or the README.

## Layout
- `index.html` – the whole site: nav, hero, About, Achievements by year, Calendar, Sponsors, Contact, footer. Head holds SEO tags (title, description, canonical, Open Graph, JSON-LD Person).
- `styles.css` – all styling. Mobile breakpoints at 860px and 560px.
- `assets/` – logos and photos. `mt82-logo.png` (header), `mt82-share.png` (social sharing image), `taylor82-logo.png` (hero), sponsor logos, and the five About-section photos (`mark-norton-team.jpg` as a wide 3:2 tile on top, then `mark-portrait.jpg`, `mark-norton-82.jpg`, `mark-goodwood.jpg`, `mark-trophy.jpg` as a 2x2 grid of square cover-cropped tiles).
- `favicon.ico`, `apple-touch-icon.png` – supplied by the customer (MT82, Kawasaki green). A new logo is planned; when it arrives replace the header logo, favicon, apple-touch icon and share image together.
- `robots.txt`, `sitemap.xml`, `CNAME` (marktaylor82.com – keep it).

## Deploy
- Hosted on GitHub Pages from branch `main` of `rdessoy-art/Website_Taylor82` (legacy build, HTTPS enforced).
- `main` is the only branch. Work directly on `main`, then `git push origin main`; pushing publishes within about a minute.
- Only commit, push and deploy when Rob asks.
- Check a deploy by fetching the live page, e.g. `curl -s https://marktaylor82.com/ | grep <new text>`.

## Content rules and decisions
- Mark is a "Ten-time" club champion (not sixteen). Race number 82. From Ashingdon, Essex. Racing the 2027 BMW F900 Cup at British Superbike level; Norton classics for Oakdene Classic Racing.
- No plain-text email addresses anywhere (scraper protection). The "Email Mark" button builds its mailto link in JavaScript on hover, focus, touch or click. Keep it that way; do not add visible addresses.
- Sponsor links carry UTM tags: `utm_source=mark-taylor-racing&utm_medium=sponsor-link&utm_campaign=mt82-sponsorship&utm_content=<sponsor-slug>`.
- Sponsors, in order: All Clear Services Ltd, Oakdene Classic Racing, Melbray London, Mark Walker Coaching, Dessoy Racing, Eastern Garage Racing. Logos all sit in a uniform white panel, so supply or convert logos dark-on-white. Oakdene has no link yet; its and Melbray's descriptions are placeholders until the customer supplies text.
- Calendar rows show the round number only (header says "Round"); the "Official Test" rows keep their label. The 2027 dates come from the customer's screenshot of the official BSB/BMW F900 R Cup calendar and differ from an earlier document, so confirm if in doubt.
- Footer credit reads "Website designed & built by www.DessoyRacing.com".
- News section and the stats strip (race number / championships / ambition) were deliberately removed.

## Gotchas
- Global `img { height: auto }` is required. Without it, the width/height attributes on images stretch them.
- After any CSS edit, check braces balance (`{` count equals `}` count). A deleted closing brace once silently broke every rule after it.
- When scripting edits to `index.html`, assert the target text exists and slice from the right occurrence. There are two `<script>` tags (JSON-LD in the head, behaviour at the bottom).
- Mobile menu closes on link tap, Escape or outside tap; hover colours are wrapped in `@media (hover: hover)` so touch screens do not keep links highlighted.
- Headless Chrome check: `"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu --hide-scrollbars --window-size=1280,900 --screenshot=out.png file://$PWD/index.html`. The minimum window width is about 500px, so true 390px phones cannot be simulated.

## Still to do
- Google Analytics 4: needs the customer's Measurement ID, then add the snippet.
- Google Search Console: add the domain property and submit `https://marktaylor82.com/sitemap.xml`.
- Optionally add links and descriptions for Oakdene and Melbray.
- Replace branding assets when the new logo is delivered.
