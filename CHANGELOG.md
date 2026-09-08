# Changelog

> Hashes reference the current (message-rewritten) history. Commit messages for 108 of the 112 commits were improved in a messages-only rewrite in September 2026; trees and diffs are unchanged.

## 2025-12-19 · 222657d · fix: Remove social links from multiple pages for a cleaner footer design
- Deletes the Facebook/Instagram/LinkedIn social blocks from the footers of all eight pages (about, contact, index, properties, and the four property pages), along with their .social-links CSS, the sameAs arrays in the index/about JSON-LD, and the "#" LinkedIn icons on the about-page team cards.
- 386 lines removed, 3 added.

## 2025-12-19 · b7f83fa · style: polish quick-contact email link and remove office hours card
- Adds a CSS block in contact.html styling inline email links inside the .quick-contact card (white bold text, subtle bottom border, hover/focus underline and ring).
- Removes the "Office Hours" contact-item card (Mon-Fri/Sat/Sun hours) from the contact information list.

## 2025-12-19 · dd3662d · feat: Add sitemap.xml for improved SEO and site indexing
- Creates sitemap.xml at the site root with eight URLs (home page, properties hub, the four property detail pages, about, and contact), each with lastmod 2025-12-19, a changefreq of daily/weekly/monthly by page importance, and priorities from 1.00 down to 0.60.
- Home is weighted highest, property pages 0.80, and about/contact 0.60.

## 2025-12-19 · 10f6308 · style: normalize formatting of new email links and JSON
- Formatting-only follow-up to the email-contact commit: re-wraps the new mailto links in contact.html, index.html, and cherry-grove.html footers into Prettier-style multi-line elements, fixes the mis-indented JSON-LD "email" line in contact.html, and collapses blunova-contact.json's link arrays onto single lines (also adding the missing trailing newline).
- No content changes.

## 2025-12-19 · 9d1a5dd · fix: remove placeholder phone/address and standardize on email contact
- Strips the placeholder phone number (615) 555-0123 and the fictitious "123 Main Street, Nashville" address from every page (about, contact, index, properties, and all four property pages) — meta descriptions/keywords, contact:address and contact:phone_number meta tags, JSON-LD telephone/streetAddress/postalCode fields, footer contact blocks, and the contact page's phone card and "Call Now" quick-contact (now email-based).
- blunova-contact.json's contactInfo becomes an email-only blurb, and the form's phone placeholder changes to "Phone (optional)".
- Also silently corrects Chimney Ridge hero stats and Quick Facts to 4 bedrooms / 3 bathrooms.

## 2025-12-19 · a7d5051 · fix: rename listing to Chimney Ridge and correct bed/bath counts
- Renames the property from "Chimney" to "Chimney Ridge" across the page title, meta/OG/Twitter titles, JSON-LD name, breadcrumb, and hero heading in properties/chimney.html.
- Corrects the Chimney Ridge counts: blunova-chimney.json feature list goes from 2 bed/3 bath to 4 bed/4 bath, the hero bathroom stat goes 3 to 4, and the home-page card description changes from "3 individual bedrooms" to "4 individual bedrooms".

## 2025-12-19 · f0e3652 · fix: correct Chimney Ridge bathroom count to 3
- Updates the Chimney Ridge bathroom count to 3 in four places: the feature-list in blunova-chimney.json (was 1), the JSON-LD numberOfBathroomsTotal in properties/chimney.html (was 2), the page hero stat (was 1), and the Quick Facts list (was "1 Bathroom").

## 2025-12-19 · 6b22588 · style: collapse Creekhead Airbnb img tag to one line
- Condenses the multi-line <img src="[image]" alt="[title]" property="image"> element inside the Creekhead Airbnb gallery card from five lines to one.
- Pure formatting change introduced seconds after the previous commit reworked that block.

## 2025-12-19 · 62e61f1 · feat: use real guest reviews and titled Airbnb room listings
- Swaps the three fabricated home-page testimonials (Jennifer M., Robert T., Sarah K.) for six real Airbnb guest reviews (Steven, Zachary, Vinit, Delbert, John) in blunova-home.json.
- Reworks Creekhead's airbnbLinks in blunova-creekhead.json with room titles ("Queen bedroom — Room 1" etc.), new Airbnb room URLs, and real bedroom photos; the creekhead.html gallery markup becomes Mavo-bound ([link], [image], [title]) to render from JSON.
- Comments out Chimney's "Book room on Airbnb" block and applies Prettier re-wrapping.

## 2025-12-19 · fc45572 · fix: standardize bathroom counts to 2.5 and remove Airbnb links
- Corrects bathroom counts to 2.5 across Cherry Grove and Creekhead listings (JSON feature lists, HTML hero stats, quick facts, and Creekhead's JSON-LD numberOfBathroomsTotal).
- Removes the Airbnb unit-booking block (airbnbLinks array and "Book unit on Airbnb" gallery markup) from the Luttrell JSON and page, with the gallery copy now pointing to photos/contact instead of Airbnb.
- Creekhead also receives extensive Prettier-style attribute and paragraph re-wrapping.

## 2025-12-19 · 2d14cc7 · fix: remove Luttrell amenities grid and align listing copy
- Deletes the entire "What this place offers" amenities section (~146 lines) from properties/luttrell.html, leaving amenity details to the overview and quick facts.
- Updates blunova-luttrel.json so the JSON description matches the corrected two 1-bedroom unit mix, renames the gallery heading from "Rooms" to "Units" with clearer Airbnb click-through copy, and fixes the page meta description from "at least two 1-bedroom" to "two 1-bedroom units".

## 2025-12-19 · a8ba65c · fix: correct Luttrell unit mix to two 1-bedroom apartments
- Follow-up to the Luttrell rewrite that fixes the unit mix in three places: the feature-list in blunova-luttrel.json, the meta description and JSON-LD description in properties/luttrell.html, and the on-page overview paragraph now state two 2-bedroom and two 1-bedroom apartments instead of "one 1-bedroom".
- Also fixes the grammar of "two 1-bedroom apartment" to plural.

## 2025-12-19 · 6b89356 · fix: correct Luttrell 4-plex listing details and property metadata
- Rewrites the Luttrell listing across blunova-luttrel.json and properties/luttrell.html to accurately describe it as a 4-plex with two 2-bedroom and 1-bedroom apartments rented whole (not by room), with a 1-year lease, no on-site internet, no washer/dryer, and no self check-in; JSON-LD type changes from House to ApartmentComplex with numberOfUnits replacing room/bath counts.
- Fixes Cherry Grove's bathroom count from 1.5 to 2.5 in its structured data.
- Home-page card copy is clarified to "individual bedrooms" and the hero description is trimmed.

## 2025-12-19 · 4c28faf · feat: add images and links to home-page property cards
- Rewrites blunova-home.json so each propertyCard entry gains an "image" (local path or blunovainc.com URL) and a "link" to the per-property detail page.
- Card descriptions are cleaned up ("4-bedroom for rent in single-family rental" becomes "4 bedrooms for rent in a single-family home", apartment phrasing fixed for Luttrell and 3rd).
- The file is also re-indented from tabs to 2 spaces and gains a trailing newline.

## 2025-12-19 · d954a74 · chore: Mavo save updating feature copy and card descriptions
- Auto-generated Mavo save of blunova-home.json.
- Replaces the "Tenant-First Approach" feature description ("We treat every tenant like family...") with the shorter "We give you space and freedom within reason." and inserts "for rent in" into all four property card descriptions (e.g., "4-bedroom for rent in single-family rental in Knoxville..."), leaving awkward grammar and a double space in one entry.

## 2025-12-19 · 890af8e · chore: Mavo save of hero copy; drop propertyCard fields
- Auto-generated Mavo save of blunova-home.json ("Updated blunova-home.json" is Mavo's default commit message).
- Substantive changes: heroDescription reworded from "carefully maintained single-family homes" to "carefully maintained rooms in single-family homes and appartments" (with typo) and the em-dash swapped for an &mdash; entity; the whole file reindented from spaces to tabs.
- Notably, all four propertyCard entries lose their "image" and "link" fields, which starves the homepage card template of its image src and detail-page link.

## 2025-12-18 · d3c7e0b · feat: block SEO-scam spam submissions on contact form
- Adds a capture-phase submit handler on the contact form that checks the message field against a list of ~15 spam keywords ("pay per click", "seo", "google's 1st page", etc.) and calls preventDefault/stopImmediatePropagation to block submission when a match is found.
- Also includes minor Prettier-style reformatting of the contact:address meta tag and the Properties nav link.

## 2025-12-18 · 13431a0 · fix: repair malformed meta tags, rebrand keywords
- Repairs the malformed head in contact.html left by an earlier reflow (nested meta tag inside the keywords attribute and stray "/>"), rewrites the keywords meta from Nashville to Knoxville terms while dropping street-address/phone keyword spam, changes contact:address to Knoxville TN 37902, and adds an author meta.
- Also corrects the FAQ Mavo structure by moving mv-list="faqItem" to the wrapper and mv-list-item onto the article so list items bind properly.

## 2025-12-18 · 47e6b8b · feat: swap About nav link for Properties anchor across all pages
- Changes the second nav item from an About link to a Properties link pointing at index.html#properties (with a building icon) across all eight pages — index, about, contact, properties listing, and the four property detail pages — consistently using the correct relative path per directory depth.

## 2025-12-18 · f2cb9c4 · feat: init pages from local JSON and templatize homepage sections
- Adds <link rel="preload" as="fetch"> for each page's Mavo JSON (home, about, contact, all four property pages) and sets mv-init on their Mavo bodies so data loads from the local JSON files instead of only GitHub storage.
- Converts index.html's hero badge/title/description, trust badges, features, and testimonials sections from hardcoded markup to Mavo-bound templates (mv-list/mv-list-item with [icon] interpolation), collapsing ~100 lines into repeating templates fed by blunova-home.json.
- Restructures contact.html's contact info into icon/detail items, converts its FAQ to an mv-list, enables the importhtml plugin, updates blunova-contact.json with hero/FAQ/links data, and removes the commented-out Google Maps embed; also reflows (and leaves malformed) the contact meta tags in its head.

## 2025-12-18 · c1027c3 · docs: add editability guide and enrich homepage JSON data
- Adds "Mavo Editability Guide.md", a reference explaining how property, mv-list, and mv-list-item attributes bind HTML to JSON for no-code editing.
- Expands blunova-home.json with new hero badge/title/description, four trustBadges, four features, three testimonials, and CTA fields; also swaps property card images from jsdelivr CDN pins to blunovainc.com URLs and normalizes card links from absolute to relative ./properties/ paths.

## 2025-12-18 · 14dd57f · fix: correct hero, og/twitter, and JSON-LD image paths
- Adds a heroImage entry to blunova-luttrel.json and updates the luttrell.html hero <img>, og:image, twitter:image, and JSON-LD images from the old luttrell-images/Front.jpg to the real organized photo tree (628 Luttrell St_Exterior_White_House.jpg / 510 3rd Ave_Exterior_Stone_House.jpg).
- Also fixes og/twitter image URLs on chimney.html and creekhead.html to include the /properties/ prefix and percent-encode spaces in paths.

## 2025-12-18 · 33ed24c · feat: add lightbox galleries, amenities, Knoxville SEO
- Applied the Luttrell-style upgrades across all four property pages (cherry-grove, chimney, creekhead, luttrell): card-grid galleries with a full lightbox (keyboard/swipe navigation), img-based hero backgrounds replacing fixed CSS backgrounds, and a new Airbnb-style "What this place offers" amenities section with categorized lists.
- Rewrote SEO meta/JSON-LD from Nashville to Knoxville (correct geo coordinates, removal of fake contact metadata; Cherry Grove corrected to 1.5 baths and no pets) and reformatted much of the HTML.

## 2025-12-18 · fc10a91 · refactor: rebrand metadata to Knoxville, cards from JSON
- On index.html, rewrites Nashville-era meta/OG/Twitter/JSON-LD content to Knoxville (dropping the fake 123 Main Street address, phone, and office hours, and updating geo coordinates), expands the ItemList schema from one to four properties, and converts the hardcoded Cherry Grove card into a generic Mavo-templated card driven by blunova-home.json ([image]/[title]/[description] placeholders).
- On properties/luttrell.html, replaces the CSS background-image hero with a bound <img class="hero-background" property="heroImage"> element and adjusts z-index layering.

## 2025-12-18 · fcbbd6a · feat: add lightbox gallery to Luttrell page
- Replaces the Luttrell page's simple click-to-fullscreen gallery with a full lightbox (prev/next buttons, image counter, Escape/arrow keyboard navigation, touch swipe, scroll lock) plus restyled gallery grid with hover overlays and zoom icon; renames the "Individual Rooms" heading to "Book room on Airbnb" and drops a duplicate Front_2.jpg image.
- In properties.html, restores the title/meta tags broken by the previous commit, rewrites meta descriptions/keywords/JSON-LD from Nashville placeholder content to Knoxville with all four listings, and removes fake contact metadata (123 Main Street, phone, office hours).

## 2025-12-18 · 8d0a993 · style: restyle price badge as centered gradient pill
- Restyles .property-price on index.html and properties.html from a right-corner box to a centered pill with gradient background, larger radius, shadow, and adjusted typography; widens the index main container from 1400px to 1600px; and removes a trailing comma after the location span in index.html.
- Inadvertently replaces the <title>/<meta name="title"> content in properties.html's head with a stray property-location paragraph, producing broken markup in that section.

## 2025-12-18 · 621ae9f · docs: rewrite hero copy and property card text
- Rewrites blunova-home.json's sectionContent with richer SEO-oriented Knoxville rental copy, upgrades all four property card descriptions from generic "N rooms for rent" to specific benefit-driven text (Cherry Grove, Creekhead Cove, Chimney Ridge, Luttrell and 3rd), and reformats the file from tabs to spaces while adding properties.html to the links array.
- Also removes the "Available Now" badge from the Cherry Grove card in index.html and changes its itemprop-like attribute from name to title.

## 2025-12-18 · 9550f1a · fix: rename Luttrell image dirs to fix gallery URLs
- Renames 21 property images out of directories containing '#' ('628 #1', '628 #2', '510 #2') into '628-1', '628-2', '510-2' and updates the matching paths in blunova-luttrel.json's gallery entries.
- Also removes a misplaced footer block (about/contact/quick-links markup) that had been pasted inside a value-card in about.html, cutting 31 lines.
- No file contents changed (all renames are R100).

## 2025-12-18 · cbda005 · fix: map property JSON configs to their own image sets
- Updates the four Mavo JSON configs (blunova-luttrel.json, blunova-chimney.json, blunova-creekhead.json, blunova-cherryGrove.json) to reference the reorganized descriptive images under ./images/<address>/ instead of generic cherry-grove-images paths — each page previously showed Cherry Grove photos.
- The Luttrell config also gets a corrected hero ("Luttrell Street"), multi-unit feature list, expanded gallery copy, and three renamed/moved unit photos (laundry, mini kitchen, living room).

## 2025-12-18 · d3a2ff4 · chore: rename property photos to descriptive address_room filenames
- Pure rename of all 60 property photos from per-address subdirectories (added in 891b2e6, moved in 691b6a1) into a flat properties/images/ layout with descriptive names like "2413 Chimney Ridge Road_Bedroom_1.jpg" (address + room/view).
- No content changes to any file bytes.

## 2025-12-18 · 587d26f · fix: correct Luttrell page images/SEO and reorganize property photos
- Moves all property photos added in 891b2e6 one level deeper under properties/images/ (per-address directories) and rewrites properties/luttrell.html to use real local image sets (./luttrell-images/), a correct canonical/OG/Twitter image, an Airbnb listing link, and clarified property copy — it previously displayed Cherry Grove images.
- Also tweaks index.html layout: 4-column grids, wider max-widths, and responsive breakpoints for features/property grids, plus trims the footer about/contact section.

## 2025-12-18 · 3f21d17 · chore: add property photo sets for all four rentals
- Bulk-adds 60 binary images under properties/ for Chimney Ridge Road, 5454 Creekhead Cove Lane, 628 Luttrell St & 510 3rd Ave (units #1 and #2), and 6914 Cherry Grove Road — exteriors, rooms, kitchens, bathrooms, laundry, and aerial shots.
- No code or markup changes; pure asset import.

## 2025-12-18 · 77179b2 · feat: apply SEO redesign to property pages, add logo and OG image
- Continues the SEO/redesign effort from 7de74f4 across properties.html and the four property detail pages (cherry-grove, chimney, creekhead, luttrell): adds canonical/OG meta, Schema.org JSON-LD with amenityFeature, gallery sections, neighborhood copy, filtering UI on properties.html, and restructured footers.
- Also adds branding assets logo.png (~2.6 MB) and og-image.jpg (638 KB), deletes the test image images/healing.jpeg, and applies smaller follow-up edits to index/about/contact.

## 2025-12-18 · f5e8ece · feat: add SEO metadata and redesign home, about, contact pages
- Massive work-in-progress rewrite (~4,100 insertions across index.html, about.html, contact.html) that adds SEO infrastructure (canonical URLs, Open Graph/Twitter meta, keywords, geo tags, multiple Schema.org JSON-LD blocks incl.
- LocalBusiness and property listings, microdata) plus Font Awesome, favicon variants, responsive clamp()-based typography, hero badges/stats/CTA groups, "Why Rent with Blunova" feature grid, testimonials section, FAQ (contact), restructured footer, and Knoxville-focused copy.
- Mavo data-binding is retained.

## 2024-08-24 · 0d31cab · feat: make about.html editable via Mavo with GitHub storage
- Integrates the Mavo CMS framework into about.html: loads mavo.min.css/js, adds mv-app/mv-storage/mv-bar attributes pointing at the hsingh23/blunova GitHub repo, annotates headings, nav, timeline items, team members, and footer with property/mv-list attributes (with the TinyMCE plugin for rich text), and moves all prior static content into an embedded #initial JSON seed.
- Static markup for timeline and team is replaced by Mavo list templates, so content now renders from the JSON data.

## 2024-08-20 · 9b08b3e · chore: empty commit, no file changes
- Empty commit — tree is identical to parent (ee425e3), no diff, no body.
- The message claims an update to blunova-cherryGrove.json but nothing changed.
- Likely an accidental save/publish from the CMS-like editing tool.

## 2024-08-20 · 5adbf89 · chore: remove healing.jpeg test card from home page config
- Removes the placeholder property card ("Hello"/"World" using healing.jpeg) that was added in fec591d from blunova-home.json.
- Everything else in the file stays as-is.
- This was a 13-second-later cleanup, confirming the prior commit was a CDN/image test.

## 2024-08-20 · 3886f34 · feat: add healing.jpeg placeholder card to home page config
- Rewrites blunova-home.json (also reformatting from spaces to tabs).
- Content changes: the hero heading becomes "Exclusive Properties in Knoxville, TN" with "comfortable"/"welcoming" bolded, and a new placeholder property card is inserted using the just-uploaded healing.jpeg via a jsDelivr CDN URL pinned to commit 34e330c, with dummy title "Hello", location "World", description "Something", linking to the Luttrell page.

## 2024-08-20 · 8d46e3e · chore: add healing.jpeg image asset
- Adds a new binary image, images/healing.jpeg (~204 KB), to the repository.
- No code or markup references are added in this commit.
- Likely uploaded via a web-based file manager given the generic message.

## 2024-08-19 · 61c2dfe · chore: empty commit, no file changes
- Another empty commit (identical tree to parent) in the same series of "Updated blunova-contact.json" commits, created about 10 minutes after the previous ones.
- It contains no diff and no body.
- Like its predecessors, it looks like a stray re-publish from an external tool.

## 2024-08-19 · 0af369d · chore: empty commit, no file changes
- An empty commit with an identical tree to its parent (0a74cc9); it changes nothing.
- It was created 19 seconds after the prior commit with the same message, likely an accidental re-save/re-publish from a tool.
- The only "content" is the repeated message "Updated blunova-contact.json".

## 2024-08-19 · a235d79 · chore: update contact form ID in blunova-contact.json
- Changes the "formId" value in blunova-contact.json from "blunova-c061e4" to "blunova-contact-bca8a0".
- The file embeds contact info HTML and a form identifier, presumably consumed elsewhere to render or link the contact form.
- No other files are touched.

## 2024-08-19 · ea50939 · chore: empty commit (no changes to blunova-cherryGrove.json)
- Second consecutive no-op commit by blunovainc: diff-tree reports no modified paths and the tree matches its parent (fc94f63).
- The message "Updated blunova-cherryGrove.json" again describes a change that did not occur.

## 2024-08-19 · 0eb2939 · chore: empty commit (no changes to blunova-cherryGrove.json)
- No-op commit by the blunovainc account: diff-tree reports no modified paths and the tree is identical to its parent.
- Despite the message "Updated blunova-cherryGrove.json" (a file that does exist in the tree), no content changed.

## 2024-08-19 · 936ef05 · feat: bind contact form-wrapper ID to Mavo formId property
- Changes the form-wrapper element's data-form-id from the hardcoded "Emails-134e76" to the Mavo expression "[formId]", adds a hidden span bound to the formId property, and adds CSS so the .editingOnly span displays only in Mavo edit mode.
- This lets the form ID be managed from the blunova-contact.json data file.

## 2024-08-19 · 950b400 · chore: empty commit (no changes to blunova-contact.json)
- Fourth consecutive no-op commit touching nothing: diff-tree reports no modified paths and the tree equals its parent (78a4bfb).
- "Updated blunova-contact.json" again describes a change that did not happen.

## 2024-08-19 · b3c2c44 · chore: empty commit (no changes to blunova-contact.json)
- Another empty commit five seconds after the previous one: diff-tree reports no modified paths and the tree matches its parent (efb78d5).
- The message "Updated blunova-contact.json" does not correspond to any content change.

## 2024-08-19 · 646c6f6 · chore: empty commit (no changes to blunova-contact.json)
- A third no-op commit: diff-tree reports no modified paths and the tree is identical to its parent (4aedfb3).
- Despite the message "Updated blunova-contact.json", no file content changed.

## 2024-08-19 · c962b7e · feat: add formId to blunova-contact.json
- Adds a new "formId": "blunova-c061e4" key to blunova-contact.json alongside the existing contactInfo HTML.
- This supplies the form identifier consumed by the Mavo/form-wrapper-powered contact page introduced in commit 8df7f47.

## 2024-08-19 · 5500118 · feat: make contact page Mavo-editable and expand property data
- Reworks contact.html into a Mavo-powered editable page: adds Mavo CSS/JS and a form-wrapper script, sets mv-app="blunova-contact" with GitHub storage and tinymce plugin, binds the contact-info div to the contactInfo property, replaces the old GET form with a form-wrapper element (removing the Cloudflare email-decode script and map placeholder).
- Expands blunova-chimney.json and blunova-creekhead.json with cleaned HTML, three more Airbnb room links each, and ~20 gallery pictures each.
- Deletes the stale blunova-home.json2.

## 2024-08-19 · 52f4b62 · chore: empty commit (no changes to blunova-contact.json)
- Another no-op commit: diff-tree reports no modified paths and the tree matches its parent (d3ca619).
- Despite the message "Updated blunova-contact.json", the file content is unchanged across this commit.

## 2024-08-19 · eb43131 · feat: add blunova-contact.json contact page content
- Creates blunova-contact.json with a single contactInfo key holding HTML for a contact section: address (123 Main Street, Nashville, TN), phone number, and office hours (Mon–Fri 9–6, Sat 10–4, Sun closed).
- Values appear to be placeholder contact details.

## 2024-08-19 · eeb3488 · chore: empty commit (no changes to blunova-chimney.json)
- This commit contains no changes at all — its tree is identical to its parent (d6a08a3), and diff-tree reports no modified paths.
- Despite the message "Updated blunova-chimney.json", blunova-chimney.json is byte-identical before and after.

## 2024-08-19 · dddf47b · feat: add blunova-luttrel.json property content file
- Creates blunova-luttrel.json for a third property page.
- Blob-identical to blunova-chimney.json and blunova-creekhead.json added moments earlier (same blob hash 2f6df78), containing Cherry Grove placeholder content (hero, description, amenities, feature list, Airbnb link, pictures).

## 2024-08-19 · 875bbae · feat: add blunova-creekhead.json property content file
- Creates blunova-creekhead.json with property page content.
- The content is currently an identical copy of blunova-chimney.json (Cherry Grove, Knoxville hero, description, amenities, feature list, Airbnb link, and picture), presumably a starting template to be customized for the Creekhead property later.

## 2024-08-19 · ea5e86f · feat: add blunova-chimney.json with Cherry Grove property content
- Creates blunova-chimney.json containing structured content for a rental property site, including hero content ("Cherry Grove, Knoxville, TN"), property description with amenities, a feature list (4 bedrooms, 1.5 bathrooms, no pets), gallery descriptions, an Airbnb room link with image, and a picture list.
- The JSON holds HTML fragments keyed by page section.

## 2024-08-19 · 0ee06f8 · fix: Give new property pages unique Mavo apps and working fullscreen
- Applies the same gallery fullscreen fix from 8e32896 (run once on "mv-load", selector ".gallery>div>img") to chimney.html, creekhead.html, and luttrell.html, and replaces the copied Cherry Grove Mavo identity on each page: mv-app becomes blunova-chimney / blunova-creekhead / blunova-luttrel and mv-upload-path becomes pictures/chimney / pictures/creekhead / pictures/luttrel.
- Page content is still the uncustomized Cherry Grove template.

## 2024-08-19 · 63886fb · feat: Fix gallery fullscreen after Mavo render; add property pages
- Reworks the cherry-grove fullscreen-image script to run once on Mavo's "mv-load" event (instead of DOMContentLoaded, which fired before Mavo rendered the lists) and updates its selector from ".gallery>img" to ".gallery>div>img" to match the new mv-list-item wrapper divs.
- Adds properties/chimney.html, creekhead.html, and luttrell.html as byte-identical copies of the pre-change cherry-grove.html (still containing Cherry Grove titles, data, and mv-app config) and deletes the stale cherry-grove2.html copy.

## 2024-08-19 · 73728ac · chore: Empty Mavo save of blunova-cherryGrove.json
- Third empty Mavo auto-commit in this series: the message claims the storage JSON was updated but diff-tree shows no file changes at all.
- Committed 10 seconds after 49ef0a2.

## 2024-08-19 · 1fbf640 · chore: Update rooms intro text in cherry-grove Mavo storage
- The only content change in this Mavo save is the "gallery-desc" rooms introduction: it now bolds just "airbnb", adds the sentence "Please check availability by clicking each picture.", and gains &nbsp; spacer paragraphs.
- Everything else is re-serialization noise — indentation flipped from 2 spaces back to tabs and the trailing newline was dropped, which is why the diff spans all 162 lines.

## 2024-08-19 · f2659f0 · style: Update property card class names for consistency
- Renames the CSS classes on the home page's featured-properties section (property-list → propertyList, property-card → propertyCard, property-image → propertyImage, property-details → propertyDetails) in both the stylesheet and markup, aligning class names with the camelCase Mavo property naming adopted in 6ed38aa.
- Also drops the overflow: hidden declaration from the card rule.

## 2024-08-19 · ebeb174 · refactor: Rename Mavo properties to camelCase and sync markup
- Renames Mavo property names from kebab-case to camelCase across data and markup ("airbnb-links" → "airbnbLinks" in cherry-grove.html and its JSON; "property-card" → "propertyCard" in blunova-home.json and the index.html featured-properties list, which also gains an explicit property binding).
- Adds mv-autoedit, mv-logged-in, and mv-no-add flags to the cherry-grove body, updates its static fallback HTML to match the stored content (emoji amenities, &nbsp; spacers), reformats both JSON files to 2-space indent with compact link arrays, and self-closes the favicon link tag on index.html.

## 2024-08-19 · c4d1870 · chore: Empty Mavo save of blunova-cherryGrove.json
- Auto-generated Mavo commit with the usual "Updated blunova-cherryGrove.json" message but no file changes whatsoever (diff-tree empty).
- Committed 24 minutes after the mv-list markup refactor, it only adds noise to history.

## 2024-08-19 · 869ff6e · refactor: Use explicit mv-list/mv-list-item markup for galleries
- Restructures both Mavo galleries in cherry-grove.html from the shorthand mv-multiple section to explicit mv-list sections with mv-list-item wrapper divs around each airbnb-links entry and each pictures image.
- Data bindings and rendered content are unchanged; only the collection markup pattern differs.

## 2024-08-19 · c7b263b · style: Reformat blunova-cherryGrove.json to tab indentation
- Pure serialization/formatting change to the Mavo storage file: switches from 2-space to tab indentation, expands the compact one-line "pictures" entries to one object per line, and drops the trailing newline.
- All content values (hero, description, feature list, airbnb-links, pictures) are byte-identical.

## 2024-08-19 · e4268f0 · refactor: Move cherry-grove galleries into Mavo storage
- Converts the page's hardcoded galleries to Mavo data binding: the rooms gallery now renders from the "airbnb-links" collection (restoring the three room links that were commented out in c726efd, now as data), and the House gallery becomes an mv-multiple "pictures" collection seeded with all 17 cherry-grove images.
- The hardcoded <img>/<a> tags are replaced by single template elements with property="image"/"link", the stale "gallery" collection is dropped from the JSON, and the storage JSON is reformatted to 2-space indentation.

## 2024-08-19 · 713508f · chore: Add airbnb-links collection to cherry-grove Mavo storage
- Mavo data commit appending a new "airbnb-links" collection to blunova-cherryGrove.json containing a single entry (the Airbnb room link and rooms/3.webp image already used in the gallery).
- No HTML change accompanies it in this commit.

## 2024-08-19 · 9c4f615 · chore: Skip empty Mavo save of blunova-cherryGrove.json
- Despite the message, this commit contains no file changes at all (diff-tree is empty); it was committed 39 seconds after ba94c12 with the identical auto-generated "Updated blunova-cherryGrove.json" message.
- It is an artifact of the Mavo GitHub-storage save flow producing a redundant commit.

## 2024-08-19 · cdc881c · chore: Update Cherry Grove content in Mavo storage JSON
- Mavo data commit for the cherry-grove page's GitHub storage: the property-description HTML was re-minified into paragraph form with &nbsp; spacers, the amenities list was converted to emoji-prefixed paragraphs (🍳 kitchen, 🛏️ bedroom, 💻 Wi-Fi, 📺 TV, 🧺 washer/dryer, 🚗 parking, ❄️ HVAC), and the feature-list was re-wrapped in a proper <ul>.
- These are content edits made through the Mavo/TinyMCE in-browser editor added in c726efd.

## 2024-08-19 · 504c37b · feat: Add Mavo.js for dynamic content editing and uploading images
- Loads Mavo (mavo.min.css/js) on properties/cherry-grove.html and configures the body as a Mavo app (mv-app "blunova-cherryGrove") storing to the GitHub repo with tinymce/importhtml plugins, a 3-second autosave, and image upload path pictures/cherry-grove.
- Marks the hero content, description, feature list, and rooms intro as editable via tinymce/property attributes, converts the rooms gallery into an mv-multiple collection with editable link/image properties, and comments out the now-redundant hardcoded room anchors.
- Also adds autosave="3" to the Mavo app on index.html.

## 2024-08-19 · 30c4693 · feat: add Cherry Grove Mavo data file for property detail page
- Created blunova-cherryGrove.json, a new Mavo storage file for the Cherry Grove property detail page.
- It defines hero content (name + location), a property overview with amenities and location description (tinymce HTML), a feature list (4 bedrooms, 1.5 shared baths, no pets), and a gallery whose single entry links a room image (rooms/3.webp) to its Airbnb listing for availability and pricing.

## 2024-08-18 · a223fdb · feat: link favicon.ico in homepage head
- One-line addition to index.html's <head>: <link rel="icon" href="./favicon.ico" type="image/x-icon">, explicitly wiring in the favicon uploaded in the preceding commit (e5ba56a).
- Edited via GitHub's web interface.

## 2024-08-18 · 58208b7 · chore: add favicon.ico
- Added favicon.ico (44 KB binary) at the repository root through GitHub's "Add files via upload" web interface.
- Gives the site a browser tab icon; no markup change references it explicitly, though browsers request /favicon.ico by convention.

## 2024-08-18 · cb4ca5c · chore: add spacing paragraph under hero heading in home data
- Single-line Mavo data edit to the homepage hero's sectionContent HTML: inserted an extra empty paragraph (&nbsp;) between the h1 heading and the intro text, adding vertical spacing below the headline.
- Saved via the Mavo editor's GitHub storage integration.

## 2024-08-18 · c604c0e · fix: use uploaded photos for Chimney Ridge and Luttrell cards
- Replaced the remaining Unsplash placeholder images in blunova-home.json with jsDelivr CDN URLs for the newly uploaded photos: Chimney Ridge now uses 2413 Chimney Ridge_House.jpg (pinned to commit 1ff56fd) and Luttrell and 3rd uses 628 House.jpg (pinned to commit c8cdce7, the re-uploaded smaller version).
- All four homepage property cards now show real photos.

## 2024-08-18 · 9c3ea89 · chore: replace 628 House.jpg with smaller re-upload
- Replaced images/628 House.jpg with a new version, shrinking the binary from 982 KB to 494 KB (roughly half).
- Same file path, so any existing references remain valid; likely a re-upload of a resized or corrected photo via the Mavo editor.

## 2024-08-18 · d0635b4 · chore: add 628 House property photo
- Added binary file images/628 House.jpg (959 KB), a property photograph (likely the Luttrell/628 property) uploaded through the Mavo editor and auto-committed by its GitHub storage integration.
- No markup or data changes accompany it.

## 2024-08-18 · 6bac588 · chore: add Chimney Ridge house exterior photo
- Added binary file images/2413 Chimney Ridge_House.jpg (129 KB), an exterior house photograph for the Chimney Ridge property uploaded through the Mavo editor and auto-committed by its GitHub storage integration.
- No markup or data changes accompany it.

## 2024-08-18 · 469278d · chore: add Chimney Ridge living room photo
- Added binary file images/2413 Chimney Ridge_Living Room.jpg (74 KB), a Chimney Ridge living-room photograph uploaded through the Mavo editor and auto-committed by its GitHub storage integration.
- No markup or data changes accompany it.

## 2024-08-18 · 5044eeb · chore: use uploaded Front Image.jpg for Creekhead Cove card
- Single-line Mavo data update replacing the Creekhead Cove card's Unsplash placeholder image with a jsDelivr CDN URL referencing the just-uploaded images/Front Image.jpg (pinned to commit 6d112cd).
- This wires the photo uploaded in the preceding commit into the homepage property card.

## 2024-08-18 · 81c5b3f · chore: add uploaded property photo images/Front Image.jpg
- Added binary file images/Front Image.jpg (153 KB), a property front-view photograph uploaded through the Mavo editor and auto-committed by its GitHub storage integration.
- No markup or data changes are included in this commit.

## 2024-08-18 · 375678a · chore: add uploaded property photo images/20220922_133915.jpg
- Added binary file images/20220922_133915.jpg (3.6 MB), a property photograph uploaded through the Mavo editor's image upload feature (mv-upload-path="pictures" / images directory).
- No code or markup changes accompany it in this commit.

## 2024-08-18 · 484f89b · fix: correct property card links and Chimney Ridge typo in home data
- Mavo auto-saved blunova-home.json with corrected property links: Creekhead Cove now points to /properties/creekhead.html, Chimney Ridge to /properties/chimney.html, and Luttrell and 3rd to /properties/luttrell.html, replacing placeholder suburban-home.html and riverfront-condo.html targets.
- Also corrected the "Chimmney Ridge" misspelling to "Chimney Ridge" and reformatted the file with tabs (Mavo's serialization style), adding a newline-at-EOF regression.

## 2024-08-18 · b36e2f6 · refactor: flatten Mavo schema, restore GitHub storage
- Restructured blunova-home.json by removing nested "detail" objects and duplicate title/description fields, renaming "price" to "location", and dropping unused top-level content/title/description keys.
- In index.html, switched the Mavo app storage from local back to the GitHub repo (hsingh23/blunova), bound the hero section to the "sectionContent" property with the tinymce plugin, and removed custom --mv-property CSS annotations in favor of class-based bindings.
- Also changed the header from position:fixed to position:sticky with top:0 and lowered z-index from 1000 to 2.

## 2024-08-18 · c09d7c1 · chore: record empty Mavo save of blunova-home.json
- Another empty commit: its tree matches parent d7614e9 exactly and no file changed, despite the message claiming blunova-home.json was updated.
- Third no-op commit in this Mavo experimentation series.

## 2024-08-18 · 2f3d629 · chore: persist sectionContent hero HTML via Mavo save
- Added a top-level "sectionContent" key to blunova-home.json containing the homepage hero HTML (h1, intro paragraph, and a &nbsp; placeholder paragraph) alongside the existing title/description keys, and a trailing comma fix.
- This is Mavo persisting a rich-text section property during the local editing experiments.

## 2024-08-18 · b4ad2b8 · chore: record empty Mavo save of blunova-home.json
- Second consecutive empty commit: its tree is identical to parent b4edeab, with no file modified despite the message claiming blunova-home.json was updated.
- Consistent with repeated no-op saves from the Mavo GitHub-storage integration or accidental empty commits.

## 2024-08-18 · b6ae530 · chore: record empty Mavo save of blunova-home.json
- This commit contains no changes at all — its tree is identical to parent cdd9257.
- It was likely created by committing with nothing staged (or via an --allow-empty / tooling artifact such as a Mavo GitHub-storage save that produced no diff).
- The message claims blunova-home.json was updated, but no file differs.

## 2024-08-18 · 430e798 · chore: persist page title and description via Mavo save
- Added top-level "title": "Exclusive Properties in Knoxville" and "description" keys to blunova-home.json.
- The description carries the homepage intro paragraph with its original HTML indentation preserved, indicating Mavo re-saved the page heading and paragraph as individual named properties alongside the existing data.

## 2024-08-18 · 2bd7774 · chore: save Mavo edit adding detail.title to Creekhead Cove
- Set the previously empty "detail" object of the Creekhead Cove property card to {"title": "Hello"}, the only change in the file.
- This is another artifact of testing the Mavo in-browser editor's nested-property saving against local storage.

## 2024-08-18 · 46034c2 · chore: check in Mavo-saved blunova-home.json from editing test
- Replaced blunova-home.json with the version produced by an in-browser Mavo editing session: file reformatted with tabs and no trailing newline, "content" overwritten with the test string "hello", a populated nested "detail" object added to the Cherry Grove card and empty "detail": {} objects to the other three, plus a new duplicate top-level "link" array mirroring the nav hrefs.
- Property card data itself is otherwise unchanged.

## 2024-08-18 · 3fb60d8 · refactor: switch Mavo bindings to HTML attributes and local storage
- Migrated the homepage from Mavo CSS custom properties to HTML attributes: commented out --mv-list/--mv-property on .property-list and added mv-list/mv-list-item attributes to the markup, plus new per-element bindings for detail, description, and link.
- Renamed the JSON key "properties" to "property-card" and each item's "details_link" to "link", renamed .property-price to .property-location (bound to location), and switched mv-storage from the GitHub remote to "local" (old body tag left commented out).
- Also deleted the unused images/vegan-4809593_1280.jpg.

## 2024-08-17 · 5d24d54 · refactor: restore property listings and drop Mavo nav attributes
- Re-populated the empty "properties": [] array in blunova-home.json with the four property listings (Cherry Grove, Creekhead Cove, Chimmney Ridge, Luttrell and 3rd), restoring data removed earlier.
- Removed the experimental Mavo CSS custom properties (--mv-property: links, --mv-list: true) from the .nav-links rule in index.html, reverting the nav to plain static HTML; also introduced a stray space inside the About link's opening tag.

## 2024-08-17 · 3a5fff8 · refactor: wrap links in a link object again in blunova-home.json
- Changed "links" in blunova-home.json from the flat array back into the nested object {"link": ["./about.html", "./contact.html"]}, reintroducing the exact wrapping that was reverted in the previous commit.
- No other keys were touched; content, properties, and footer stay as-is.

## 2024-08-17 · e64f66f · refactor: flatten links back to an array in blunova-home.json
- Reverted the "links" field in blunova-home.json back from the nested {"link": [...]} object to a flat array of hrefs, undoing the wrapping introduced two commits earlier.
- Also replaced the blank line with an explicit empty "properties": [] placeholder.
- The file now has links, content, properties, and footer keys.

## 2024-08-17 · 6de933c · fix: use --mv-list for nav links and trim stored properties
- Changed the .nav-links Mavo CSS custom property in index.html from --mv-multiple: true to --mv-list: true, and removed the entire "properties" array (all four property listings) from blunova-home.json, leaving only links, content, and footer.
- The two edits together adjust how the Mavo-backed homepage binds and stores its data.

## 2024-08-17 · 6bf88ae · refactor: wrap blunova-home.json links in a link object
- Changed the "links" field in blunova-home.json from a flat array to a nested object of the form {"link": [...]}, while all other sections stayed unchanged.
- Also added blunova-home.json2, a verbatim backup copy of the pre-change flat version of the file.
- The commit message only mentions the links restructure and omits the backup file entirely.

## 2024-08-17 · 9e00773 · refactor: flatten blunova-home.json to a single object schema
- Rewrote blunova-home.json from an array of single-key wrapper objects ([{links:...},{content:...},{properties:...},{footer:...}]) into a single flat object with top-level keys links, content, properties, and footer (footer also simplified from array-of-objects to a plain string).
- All property data (Cherry Grove, Creekhead Cove, Chimmney Ridge, Luttrell and 3rd) is preserved unchanged.
- Despite the message mentioning index.html, only blunova-home.json was modified.

## 2024-08-17 · 16ac117 · chore: store Mavo app data as JSON instead of YAML
- Replaces blunova-home.yaml with an equivalent blunova-home.json (same links, hero HTML, four Knoxville property records, and footer text, expanded to full object-per-item JSON) and removes the "yaml" entry from the mv-plugins attribute on index.html's body tag, keeping tinymce and importhtml.

## 2024-08-17 · 2c20f44 · feat: drive homepage from Mavo CMS with blunova-home.yaml
- Converts index.html into a Mavo.io app (mv-app="blunova-home", mv-storage pointing at hsingh23/blunova on GitHub, tinymce/importhtml/yaml plugins) whose hero, links, property cards, and footer bind to data via --mv-property custom properties, and replaces blunova-home.json with a structured blunova-home.yaml containing the four Knoxville listings.
- Adds properties/cherry-grove2.html, a new web-components-based property page reviving the previously reverted custom elements.
- Also converts all remaining /portfolio/blunova1/ absolute links to relative paths across about/contact/index/properties, changes the title to "Comfortable Rentals", reflows formatting, and removes the "Apply Now" button from cherry-grove.html.

## 2024-08-16 · 0c757ed · feat: populate blunova-home.json with property listing data
- Fills the previously empty "properties" array in blunova-home.json with one record containing parallel arrays for image, title, and price covering the four Knoxville listings (Cherry Grove, Creekhead Cove, Chimmney Ridge, Luttrell and 3rd).
- The single image entry points at the vegan-4809593_1280.jpg added in 34b9aaa via a jsdelivr CDN URL pinned to that commit, with null placeholders for the other three.

## 2024-08-16 · 6767bd2 · chore: add vegan stock photo to images/
- Adds a single binary asset, images/vegan-4809593_1280.jpg (235 KB, a Pixabay stock photo by the ID).
- No code or markup references it in this commit.

## 2024-08-16 · b7405a1 · chore: set blunova-home.json footer placeholder to "Hello"
- One-line change to blunova-home.json replacing the whitespace-only "footer" value with the string "Hello      ".
- Another manual placeholder edit to the JSON scaffold, minutes after the content edit.

## 2024-08-16 · ed4b1dd · chore: set blunova-home.json content placeholder to "hi"
- One-line change to blunova-home.json replacing the whitespace-only "content" value with the string "hi".
- Looks like a manual test of editing the JSON scaffold.

## 2024-08-16 · d2270d6 · chore: add blunova-home.json page scaffold
- Adds an 11-line blunova-home.json with a links object (about.html, contact.html), empty content/properties/footer fields, and no trailing newline.
- The structure looks like a page-content scaffold, but nothing in the repo references it.

## 2024-07-07 · 18906e8 · revert: rebuild Cherry Grove page with web components
- Exact revert of commit 0981de0: restores properties/cherry-grove.html to its pre-web-components state (identical to the tree at 857c512), bringing back the plain header/hero/details/gallery markup, the page-level fullscreen-image script, and the Google Analytics gtag snippet, and dropping the four custom elements and their shadow-DOM styles.

## 2024-07-07 · 93b14a3 · refactor: rebuild Cherry Grove page with web components
- Refactors properties/cherry-grove.html to replace plain HTML sections with four custom elements defined in an inline ES module: <app-header>, <property-hero> (title/location/background-image attributes), <property-details> (named slots for description/features), and <image-gallery> (default slot with a showFullscreenImage lightbox method in connectedCallback).
- Global page CSS shrinks to CSS variables and footer styles since each component carries its own scoped styles.
- Also removes the Google Analytics gtag snippet and the old querySelector-based fullscreen script.

## 2024-07-07 · 03237b7 · style: polish Cherry Grove rooms section
- Small polish to properties/cherry-grove.html: fixes a missing space in the Bathrooms feature text, replaces the property-details class on the Rooms section with an inline 40px margin, and bolds the note that each room links to Airbnb for availability and pricing.

## 2024-07-07 · a86e36b · chore: rebrand BluNova to Blunova and drop base href on remaining pages
- Applies the same treatment as the previous commits to the remaining top-level pages: removes the <base href="/portfolio/blunova1/..."> tags from about.html, contact.html, and properties.html, rebrands all "BluNova" text to "Blunova" (titles, hero headings, story/mission copy, footer), and reformats the HTML with consistent Prettier-style indentation.
- No new sections or functionality are added; properties.html still lists the old placeholder listings.

## 2024-07-07 · 097a8df · fix: use relative paths for navigation and property links
- Fixes broken navigation and property links by removing the <base href="/portfolio/blunova1/"> tag from index.html and converting all nav, property-card, and hero links to relative paths (./properties.html, ./properties/cherry-grove.html, /index.html).
- Also swaps the Cherry Grove hero and card background images from Unsplash URLs to the local ./cherry-grove-images/Front.jpg photo.

## 2024-07-07 · 3afeba8 · feat: add Cherry Grove property page and real listing content
- Adds properties/cherry-grove.html (adapted from the downtown-loft template) along with ~20 real photos under properties/cherry-grove-images/ and properties/rooms/.
- Rewrites the index.html featured-properties section with four real Knoxville listings (Cherry Grove, Creekhead Cove, Chimmney Ridge, Luttrell and 3rd), rebrands "BluNova" to "Blunova", updates hero copy from statewide luxury to personally-managed Knoxville rentals, reformats the HTML with Prettier-style formatting, and deletes the duplicate property/downtown-loft.html.

## 2024-07-07 · 433ae72 · feat: add initial static site for BluNova Properties
- Initial commit establishing a static multi-page real-estate website for BluNova Properties (luxury rentals in Tennessee).
- Adds index, about, contact, properties listing pages, a property detail page (downtown-loft, duplicated in both /properties/ and /property/ directories), plus .gitignore and config.yml.
- Pages are self-contained HTML with embedded CSS (Montserrat/Playfair Display fonts, Unsplash imagery) and a base href pointing at /portfolio/blunova1/.
