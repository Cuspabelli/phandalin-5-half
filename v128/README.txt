THE PHANDALIN 5 1/2 — v128

Shared campaign journal PWA hosted on GitHub Pages with Supabase as the cloud data source.

CURRENT SYSTEMS
- Shared Inventory and Treasury
- Containers and character inventories
- Campaign Reference
- Collaborative Session Notes
- Private item artwork in Supabase Storage
- DM/player permissions through Supabase Row Level Security
- Realtime shared-data refresh and concurrent-edit protection
- Full JSON backup plus readable DOCX/PDF exports

PERSISTENCE
- Shared campaign data is stored in Supabase.
- Browser localStorage is used only for authentication/session state and lightweight per-browser UI preferences.
- Legacy campaign-data localStorage keys are cleared after a successful cloud load.

DEPLOYMENT
- Static client files are hosted on GitHub Pages.
- The browser contains only the Supabase publishable key; no service-role key or database password belongs in this package.
- Private artwork is stored in the item-artwork Supabase Storage bucket and read through authenticated requests governed by RLS.

VERSION 128 CLEANUP
- Removed obsolete browser-to-Supabase migration functions.
- Consolidated legacy localStorage cleanup into an explicit one-way compatibility list.
- Updated PWA manifest naming to The Phandalin 5 1/2.
- Corrected full-backup app version metadata to v128.
- Updated project documentation to describe the current GitHub Pages + Supabase architecture.
- No database schema, RLS, collaboration, or item-sync behavior was intentionally changed.
