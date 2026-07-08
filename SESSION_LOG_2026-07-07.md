# HouseOffer — Session Log
Date: 2026-07-07
Scope: homepage REORDER + TRIM pass per CEO brief (9-section target sequence).
Frontend repo only (houseoffer-site.Private → Netlify). NOT merged, NOT deployed.

Branch: `claude/houseoffer-homepage-refresh-port-e2uvqf` (restarted from main
after the previous refresh-port branch was merged; same designated branch name).

Also in this session, before this restructure (separate commits, already
merged to main with sign-off): white-paper £99/ten-method accuracy pass,
backend /track redirect → houseoffer.uk, site-wide favicon.

═══════════════════════════════════════════════════════════════════════
# WHAT CHANGED (by brief item)
═══════════════════════════════════════════════════════════════════════

1. **Hero lightened.** Badge, H1, confidence sub-headline, two-field form and
   single CTA kept. The three "What you get in your free report" preview
   cards under the form: REMOVED. New microcopy under the CTA button:
   "Free report in minutes · No account needed." Hero mock card: the
   "Open £355,000 · Target £360,000 · Walk away £368,000" banner REMOVED —
   the card now shows free-tier content only (address, valuation + range,
   confidence badge, stats). The offer trio lives in section 3, badged £29.

2. **Data trust strip** — untouched, still directly under the hero.

3. **£29 report showcase** replaces the free-report walkthrough ("The real
   report, piece by piece" section deleted per brief). New section keeps
   id="report" so anchors stay stable. Contents: "£29 Offer Report" teal
   badge + "Inside the full report" eyebrow, H2 "Walk into the negotiation
   prepared", the football-field card MOVED here from the methodology
   section (unchanged: shipped method labels, fictional 14 Maple Close,
   red asking line, methods footnote), offer trio directly beneath as three
   stat cards (Open with / Target / Walk away above), four supporting
   feature cards (Offer Frontier, Seller signal score, Full comparables
   table, Personalised to your buying position), and the closing free-tier
   line ("Start with the free report — valuation, confidence score and
   verdict. Upgrade only when you're ready to offer.").

4. **Methodology shortened** to the credibility block: "We show our working"
   header + six data-source/method cards + "Read our full methodology →".
   Football field no longer duplicated here. Moved above pricing.

5. **Pricing** — content untouched, position now after methodology.

6. **FAQ** — untouched, all seven entries + "Read all questions" link.

7. **CTA band** — now directly after FAQ (Explore section that sat between
   them removed).

8. **Crowd voting** — the old two-column section (previously between How-it-
   works and Pricing) and the hero/walkthrough crowd mentions are gone.
   Crowd voting now appears exactly once: a compact centered lavender strip
   AFTER the CTA band — eyebrow "One more thing", "Get their verdict too.",
   one line of copy, and four vote chips (Dad £338k / You £350k / Mum £365k
   lavender, Data £360k teal).

9. **Footer** — the Buyer guides column already carried all six SEO links
   (Property Value, Offer Strategy, Negotiation, Buying Hub, White Paper,
   FAQ), so the standalone Explore section was deleted without content loss.

Deletions confirmed: How-it-works section (whole), Explore section, hero
preview cards, walkthrough crowd card (with the walkthrough), hero mock
offer-trio row.

Anchors: `#how` no longer exists — nav and footer links relabelled
"Inside the report" → `#report`. All other anchors (#pricing, #faq,
#hero-form, #get-started) unchanged. focusHeroForm() behaviour verified
from nav CTA, free pricing card, and CTA band.

═══════════════════════════════════════════════════════════════════════
# JUDGMENT CALLS
═══════════════════════════════════════════════════════════════════════

- **Vote-chip names/values.** Brief example was "Mum £355k / Dave £325k /
  Data £318k". Kept the previously approved, page-consistent demo family
  (Dad £338k / You £350k / Mum £365k) and Data at £360k — the page's single
  fictional property has a £360k midpoint, and the example-numbers-stay-
  self-consistent rule was an approved decision from the 19-item pass. The
  brief's values were prefixed "e.g." so I read them as illustrative, not
  prescriptive. Trivial to swap if you want the exact chips.
- **Nav label.** "How it works" pointed at a deleted section; relabelled
  "Inside the report" → #report (nav + footer). Label choice was mine.
- **Free-report walkthrough content** (verdict card, DOM card, anchoring
  card, comps mini-table) is fully deleted with its section per "replaces".
  The free tier remains represented by the hero mock card, the free pricing
  card, and the section-3 closing line.
- **Showcase feature cards** reuse the methodology-card visual pattern
  (white card, icon chip, existing palette tints) — no new colours.
- The offer-trio values shown unblurred: fictional example, clearly badged
  £29 and labelled fictional in the chart card (sample-report page keeps
  its blur pattern — untouched).

# Verification
- Section order asserted programmatically: hero → trust → report →
  methodology → pricing → faq → cta-band → crowd → footer. Tag balance
  checked. Zero `#how` references.
- Headless Chromium at 1440px and 390px: nav-anchor scroll, hero-form focus
  from all three CTAs, £29/£99 /track links, /sample-report/ link, no JS
  errors. Before/after screenshots delivered in chat (before = pre-
  restructure state of the same sections).

# NOT done / notes
- No backend, template, or other-page changes in this pass.
- Old `.neg-banner`, `.crowd-grid`, `.steps` etc. CSS now partially unused;
  left in place deliberately (small, zero risk to shipped markup).
- NOT merged, NOT deployed — awaiting CEO review.

═══════════════════════════════════════════════════════════════════════
# ADDENDUM — showcase v2: full-report mock (same day, after CEO review)
═══════════════════════════════════════════════════════════════════════

CEO correction to item 3: the showcase should mock the ENTIRE £29 report,
including the free-report visuals. Iterated as a standalone draft in chat,
approved ("apply it"), then swapped into index.html.

Final showcase structure (each block chip-tagged Free or £29):
  header + £29 badge → offer trio (moved ABOVE the chart per CEO) →
  football field → valuation card [Free] + verdict card [Free] →
  negotiation approach [£29] + seller signal STRONG [£29] →
  days-on-market [Free, with the 3–7% discount strip chipped £29 inside] +
  comparables table [3 free / all 12 £29] →
  Offer Frontier full-width [£29]: risk-vs-discount curve (adapted from
  /sample-report/) plus three priced positions → free-tier closing line.

The abstract four-feature-card row from v1 is gone — those features now
appear as actual report pieces. New CSS: .tier-chip, .pos-*, .approach-list.

Judgment calls:
- Frontier position prices set to Secure £365k / Balanced £360k /
  Aggressive £355k so no position exceeds the £368k walk-away.
  FLAG: /sample-report/ has Secure at £372,000 (blurred) — above its own
  walk-away and contradicting its own footnote. Not fixed; awaiting CEO.
- Crowd-voting and anchoring cards remain excluded from the showcase
  (crowd/instinct content lives only in the post-CTA strip per the reorder
  brief). The real paid report's "Their number vs the market" section is
  therefore not mocked. CEO can overrule.
- Verified: anchors, hero-form focus from all three CTAs, track links,
  DOM-level checks (no neg-banner, one crowd section, 11 tier chips),
  1440px + 390px screenshots.


═══════════════════════════════════════════════════════════════════════
# ADDENDUM 2 — post-deploy CEO tweaks (fresh branch off merged main)
═══════════════════════════════════════════════════════════════════════

Showcase v2 was merged/deployed. These four tweaks restart the branch
from main and are NOT yet merged.

1. Hero sub-headline rewritten (CEO verbatim): "Everyone in the deal works
   for the seller. We work for you. Paste a Rightmove link and get the
   buyer's side of the table: what similar homes actually sold for, a
   defensible offer range, a deliberate opening position and your walk-away
   number — with a confidence score on every report so you know exactly how
   far to trust it." NOTE: reintroduces the word "exactly" that the 19-item
   pass had scrubbed from the hero — kept because it's CEO-supplied copy and
   refers to trust calibration (the confidence score), not the banned
   "exactly what to offer/say" framing.
2. Offer trio colours now escalate teal → amber → red (Open with / Target /
   Walk away above), all solid-filled white-text, style-guide vars only.
3. Seller signal card gained a motivation gauge: white track, teal fill to
   ~80% with a knob, "Not motivated" → "Highly motivated". Style-guide
   colours only.
4. Offer Frontier: "time on market shifts the curve" arrow + label moved
   right (arrow x1 330→392, x2 416→478; text x 373→435) so they no longer
   overlap the green curve.

Verified: functional checks pass (anchors, hero-form focus ×3, track links,
no JS errors); desktop + mobile screenshots of all four.


═══════════════════════════════════════════════════════════════════════
# ADDENDUM 3 — "One offer, two lenses" reconciliation (frontend half)
═══════════════════════════════════════════════════════════════════════

Phase 1 framing CEO-approved; Phase 2 on this branch (restarted from main).
Backend half (report_paid.html, FRONTIER_METHODOLOGY.md v1.1 §13,
tools/demo_two_lenses.py) is on the same-named branch in houseoffer-backend,
logged in its SESSION_LOG_2026-07-07.md. No calculation changes anywhere —
backend `git diff app.py` is empty.

## Generated, not authored
All trio/frontier/method figures on homepage, /sample-report/ and the white
paper worked example now come from tools/demo_two_lenses.py, which executes
the REAL trio source and _offer_frontier. Real output for the demo property:
trio £357,000 / £360,000 / £368,000; Frontier anchor 5.2% — Secure
£366,000–£368,000 (2.5–5%), Balanced £354,000–£366,000 (5–8%), Aggressive
£352,000–£354,000 (8–10.5%). This fixes the two audit findings: the
impossible Secure £372,000 on /sample-report/ (above its own walk-away) and
the hand-written £355,000 open (the real calc emits £357,000).

## Surfaces changed
- Homepage showcase: VALUE LENS header → trio (£357k open) → football field
  (bars redrawn to the harness inputs so the weighted 352–368k actually
  follows from the displayed bars under the real formula — it never did
  before) → PRESSURE LENS header → Offer Frontier (real ranges + %) →
  "Where the lenses meet" strip (overpriced-convergence narrative) →
  evidence grid → free-tier close. New CSS: .lens-chip/.lens-head/.lens-meet.
- /sample-report/: frontier section retitled "One offer, two lenses" with
  the intro + value/pressure panels and meet strip (mirrors the paid
  template, static, blur pattern kept); trio → £357,000 with recomputed
  honesty percentages (7.3% below asking / 0.8% below comps); position
  cards → real ranges; football-field rows regenerated on one clean linear
  scale (the old bars were eyeballed and internally inconsistent); method
  table midpoints → harness midpoints.
- /white-paper/: "Calculating the offer" replaced by "Two lenses on one
  offer" — concept only, coefficients explicitly withheld ("this paper
  describes the logic, not the coefficients"); method list + figure bars +
  both chart markers updated to the generated numbers; Case Study A opens
  at £357,000. Valuation methodology (ten methods, sources, confidence)
  already published in full from the earlier pass; not-advice/not-RICS
  disclaimer already present.

## Judgment calls
- Demo method inputs were CHOSEN so the real calc lands on the established
  example range (352–368k/360k/£385k asking): preserves every downstream
  example number. The visible cost: per-method bars changed on all three
  surfaces (they now sum correctly under the real weighted-mean formula).
- Homepage layout: value lens (trio+chart) and pressure lens (frontier)
  are now adjacent, with the evidence cards AFTER the meet strip under
  their own small header ("The evidence behind both, piece by piece") —
  keeps the two lenses reading as one story.
- The DOM card's "3–7% below asking" discount strip is a separate report
  feature (not trio/frontier) and was left as-is.
- Frontier position cards on marketing surfaces now show RANGES because
  that is what the live product renders (price_label) — the single prices
  were another mock artifact.

## Four-surface consistency check (one-sentence description each)
Canonical: "The value lens (open · target · walk-away) tells you where to
land inside what the home is worth; the pressure lens (Secure · Balanced ·
Aggressive) tells you how hard the seller's position lets you push — two
readings of one offer, and neither ever points past your walk-away."
1. Homepage (teaser): "It answers two different questions — what the home is
   actually worth, and how hard the seller's position lets you push —
   because one number can't answer both." (+ meet strip: "neither ever
   points past your walk-away" via floor/ceiling line.)
2. Paid report (full view): lens-intro — "Your offer answers two different
   questions. What is this home actually worth? And how hard will the
   seller's position let you push? … one number can't answer both." Panels
   name the lenses; meet strip carries the shared floor/ceiling.
3. White paper (public concept): "the pressure lens tells you how hard to
   push and the value lens tells you when to stop: however weak the seller
   looks, no Frontier position is ever shown below the valuation floor or
   above the walk-away."
4. Dev doc (internal spec): FRONTIER_METHODOLOGY.md §13.3 quotes the
   canonical sentence verbatim, plus both formulae and the convergence note.
All four describe the same relationship: two intentionally distinct
calculations, complementary lenses, sharing only the floor/ceiling bounds.

## Verification
- Homepage functional checks all pass (anchors, form focus ×3, track links,
  no JS errors); tag balance checked on homepage + sample-report.
- Sweeps: no £372,000 remains; no "gut"; "Calculating the offer" gone;
  £357,000 present on all three surfaces.
- Screenshots delivered in chat: homepage showcase (desktop), sample-report
  two-lens frontier, white-paper figure.
- NOT merged, NOT deployed — awaiting CEO review (both repos).

═══════════════════════════════════════════════════════════════════════
# ADDENDUM 4 — homepage chart IS the real report chart
═══════════════════════════════════════════════════════════════════════
CEO: make the homepage £29 example match the actual paid-report football
field, add Target + Walk away lines, keep the method table for the full
report only (not the website), land walk-away on a clean £368k, widen the
gutter. Applied:

- index.html: the bespoke hand-built SVG football field is REPLACED by the
  genuine report_paid.html ff-card, rendered statically. Same markup, chart
  maths, styling and the new Open/Target/Walk away/Asking lines a paying
  customer sees. Ported the 8 .ff-* CSS rules (no class collisions).
- CHART ONLY on the homepage — no method table (that stays in the paid
  report, per CEO). Chart header reads "9 methods" (the weighted set); the
  card sub now reads "Two further context-only methods complete the ten in
  the full report" and the trio caption drops its "ten methods below"
  table reference — nothing on the page points at a table that isn't there.
- Trio unchanged (£357k / £360k / £368k); walk-away line sits on £368k.

Demo numbers are GENERATED, not authored — real trio + _offer_frontier math
on a code-faithful full-data property (bedroom present, so raw comparable
is the one context row; adjusted comparable demoted 2→1, bedroom-matched
w2 — per app.py:2735-2738). Nine weighted method bars:
  Comparable sales (HPI-adjusted) 353-372k, HPI-adjusted last sale 355-370k
  (x2), Bedroom-matched local price 354-369k (x2), Price per m² 355-366k,
  Area price trend 347-371k, Automated valuation 350-369k, Est. lender
  range (modelled) 350-359k, Rental yield implied value 349-361k,
  Asking-to-sold discount 351-369k → weighted 352,091-367,727 → open
  357,000 / target 360,000 / walk 368,000 (real formula). Reproduce by
  rendering report_paid.html's ff-card with this context.

FINDING corrected in-thread: "full data → all ten bars" is false. The
engine weights ~8-9 methods; some are always context (raw-vs-bedroom
demotion, national-fallback asking-to-sold, scoring-only matched-sold).
"Ten methods" is the full menu shown in the paid report's TABLE; the chart
plots the weighted subset. Homepage now states this honestly.

Companion backend change (Target/Walk away lines + widen) is on the same
branch in houseoffer-backend (Addendum 2 there). Verified: functional
checks pass, tag balance OK, desktop + mobile screenshots. NOT merged.

═══════════════════════════════════════════════════════════════════════
# ADDENDUM 5 — /sample-report/ football field = the real report card
═══════════════════════════════════════════════════════════════════════
CEO-approved (option 1: keep numbers blurred). The sample report's bespoke
div-based football field is replaced by the genuine report_paid.html ff-card
(same as homepage + paid report), with the Open/Target/Walk away/Asking
lines and the widened gutter. Its £ figures stay BLURRED to preserve the
paywall look — CSS classes namespaced rff-* so they don't collide with the
sample page's own .ff-* system; numeric SVG labels wrapped in .rff-blur.
The two context methods (rental yield, asking-to-sold) drop off the CHART
(weighted set = 9 bars) and remain in the method TABLE below, exactly as
the real paid report presents them. Frontier positions unchanged and
in-range (Secure £366,000–£368,000).

Note (verified, not a defect): the sample page is a FICTIONAL static demo,
so its blurred numbers being present in page source is harmless — nothing
real is exposed. The real free→paid gate (report_free.html) is genuinely
server-side: paid offer numbers are never sent to the browser and the
football field's paid-tier bars are fake placeholders, so the blur there
covers decoys, not the answer.

Verified: real card renders (19 svg rects), method table intact with all
ten methods, frontier in-range, zero JS page errors.
