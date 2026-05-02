# Changelog

## v1.0.0-alpha02

### Added
- Premium mobile and tablet UI refresh across the authenticated app shell and core screens.
- GitHub release update check in Account using the public Releases API.
- Release-safe debug logging wrapper to keep scanner and auth diagnostics out of release logging paths.
- No-flash device handling in Lens with a clear warning when torch is unavailable.
- Expanded manual record entry fields for older or barcode-free vinyl releases.

### Changed
- Barcode scan enrichment now sanitizes digits, tries UPC/EAN variants, fetches MusicBrainz release detail, and supplements missing metadata through the server-side catalog lookup path.
- OCR scan handling now filters packaging/legal text more aggressively and requires review instead of silently saving weak OCR-only candidates.
- Scanner duplicate protection now uses stronger fuzzy matching against existing local collection records.
- Record detail release metadata now uses cached release-detail hydration and clearer low-estimate wording for valuation.
- Release build hardening now enables minify/resource shrinking and tighter ProGuard/R8 rules.
- Supabase client-key validation now rejects service-role style JWT keys in app config.

### Security
- Prepared a Supabase email allowlist migration for:
  - `aloleng88@gmail.com`
  - `rickyabarquez@live.com`
- Hardened inactive AI edge-function responses so request payloads are not echoed back.
- Removed local CLI token content from `.env.example`.

### Known limitations
- OCR is best-effort and may still require manual review for stylized covers, glare, spines, or older releases without strong identifiers.
- First MusicBrainz release-detail fetch can take a few seconds; subsequent opens are faster once cached locally.
- GitHub in-app update checking requires the public `Iricksta/VinylVault` release repo and a published release to exist.
- Supabase email allowlist migration is prepared but not applied live yet.
