# Makeristic directory source audit

26 October 2026. Scope: the complete static website, catalogue, crawler files, repository metadata and cross-repository review links. Individual hardware audits live in the linked project repositories; this website is a directory, not a hardware-validation service.

## Blocked on me

No blocker to publishing the directory. Several linked designs still require electrical/mechanical completion, manufacturing review or clearer third-party licensing. The [repository review](repository-hygiene.md) records those limits; a merged correction is not a production-readiness certificate.

## Changed

- Replaced the deployed `Hello World` placeholder with a semantic HTML directory linking all 11 organisation repositories. The catalogue uses the existing GitHub Pages setup; no framework, JavaScript, analytics, external font or build dependency is added.
- Added document language, charset, viewport, a descriptive title, canonical URL, description and Open Graph metadata.
- Added skip navigation, named landmarks, grouped project links, visible keyboard focus, responsive layout and light/dark colour tokens.
- Added `robots.txt` and `sitemap.xml` for the actual published root URL.
- Corrected the README's stale placeholder description and linked the public directory and source audits.

## Found

### Verification

- Parsed the HTML and checked unique IDs, one H1, valid internal anchors, `lang="en"`, UTF-8, metadata and the canonical URL.
- Compared GitHub repository links with the live 11-repository CLI inventory; every repository is linked, including this website's source repository.
- Parsed the sitemap XML and checked that its root URL and the robots sitemap directive agree with the canonical URL.
- Inspected the page in the collaborative browser at 1280, 1440 and 390 CSS pixels. Full-page desktop/mobile screenshots show the complete directory, with no horizontal overflow. The skip link becomes visible on keyboard focus, its outline is present, and section navigation reaches the intended anchor.
- Computed WCAG text contrast for every foreground/link/muted token against its light/dark background: the lowest ratio is **6.33:1**. No console errors were observed.
- An independent finish reviewer inspected the source and all three screenshot sizes. Its sole required fix was the stale README description; its follow-up verdict scored that fix resolved and returned **ship**. No layout recapture was requested.
- The design detector's ten row-padding warnings were checked against the browser: actual top/bottom padding is 24 px. They arise from the detector not accounting for `padding-block`, so no spacing change was needed.
- Reviewed the diff and ran Git whitespace and local-link checks. Deployment is verified after merge against the public URL and Pages build result.

### Limits and future work

No claim is made about search-engine indexing, rankings, every browser or assistive-technology combination, or the electrical correctness of linked hardware. There is no dynamic application, authentication, storage or third-party script to audit here. Source-specific hardware validation and licence evidence remain in the individual reports.

An organisation profile/pinned repositories, social-preview images and a photographic gallery would be separate discoverability improvements. This correction supplies a useful public directory without adding those systems.
