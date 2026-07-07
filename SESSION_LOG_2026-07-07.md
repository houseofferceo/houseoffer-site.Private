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
