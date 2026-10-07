# The Phandalin 5 1/2 — Current Collaboration Architecture (v128)

## Hosting and source of truth
The PWA is served as static files from GitHub Pages. Supabase is the source of truth for shared campaign data. The production app does not rely on browser localStorage for campaign records.

## Shared in Supabase
- Inventory and Treasury
- Item ordering
- Containers and Characters
- Campaign Reference and Trash
- Session Notes and Trash
- Collaborative Session Note updates
- Player/DM campaign membership roles
- Item artwork in private Storage

## Local per-browser state
- Supabase login/session token
- Image/List/Compact Inventory view
- Campaign Reference Cards/List view
- Collapsed Session Note state

Legacy campaign-data localStorage keys are deleted after a successful cloud load. They are not used as a persistence layer.

## Security
- Authenticated campaign membership determines access.
- Supabase Row Level Security is the authority for campaign rows and DM-only visibility/actions.
- Item artwork is private and retrieved with authenticated requests subject to Storage RLS.
- The browser package contains the Supabase publishable key only. It must never contain a service-role key or database password.

## Collaboration
- Supabase Realtime watches shared campaign tables and triggers safe cloud reloads.
- A reconciliation check handles visibility changes caused by RLS, such as moving an item into DM Storage.
- Open item viewers refresh after cloud changes and close if the item becomes inaccessible.
- Concurrent edits compare revisions and prompt only when both editors changed the same field.
- Session Note bodies use Yjs updates stored in `session_note_updates`; metadata retains revision-based conflict handling.

## Backups and exports
- DM Full Backup exports a JSON recovery snapshot including campaign rows and artwork data.
- Campaign Notes can be exported to DOCX.
- Inventory can be exported to PDF.
- The backup payload records the current application version.

## Known architectural follow-up (not a v128 change)
Item synchronization still uses the established bulk-upsert workflow. It is protected by the current revision/conflict system and is intentionally left unchanged in v128. A future refactor may move to targeted row-level writes after separate testing.
