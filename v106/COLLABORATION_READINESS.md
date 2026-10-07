# The Phandalin 5 1/2 — v90 Shared Supabase Beta

v90 connects the PWA to the managed Supabase project for authenticated shared campaign data.

## Shared in Supabase
- Inventory and Funds
- Item ordering
- Containers and Characters
- Campaign Reference and Trash
- Session Notes and Trash
- Player/DM membership roles
- Item artwork in private Storage

## Local per-device preferences
- Image/List/Compact inventory view
- Campaign Reference Cards/List view
- Collapsed Session Note state

## Security
- The former Player/DM selector is now locked to the authenticated campaign role.
- Row Level Security remains the authority for campaign access and DM Storage visibility.
- Only the publishable browser key is included. No service-role key or database password is present.

## Migration
The v88 localStorage keys are preserved so existing browser data can be migrated without changing the user-facing data model. Test v90 with the DM and Test Player accounts before replacing the live production copy.


## v99
Private item artwork is loaded through Supabase Storage's authenticated object endpoint. The temporary v98 diagnostic UI has been removed.


## v101 diagnostic
Temporary artwork authentication diagnostic reports the session user ID, JWT subject, campaign membership API response, and private Storage response for Potion Test 5.


V102
- Removed temporary v101 artwork/auth diagnostics.
- Retains authenticated private artwork retrieval.
- Artwork access depends on corrected storage.objects SELECT RLS policy using storage.foldername(storage.objects.name).
- Next validation: shared artwork -> DM Storage -> shared, including Player visibility.

## v104 realtime collaboration
- Restores Supabase Realtime subscriptions for items, containers, characters, Campaign Reference, and Session Notes.
- Incoming events trigger a safe re-fetch through the existing RLS-protected REST queries.
- Adds a lightweight 3-second visibility reconciliation so rows that become hidden by RLS (for example, an item moved into DM Storage) disappear from Player views without manual refresh.
- Realtime does not bypass RLS and never directly injects DM-only payloads into Player state.


## v104
- Open inventory item/Treasury viewer refreshes in place after realtime cloud reloads.
- If an open item becomes inaccessible or is deleted, the viewer closes automatically.


## v105 Concurrent Edit Protection
- Detects when an item, Treasury, Campaign Reference entry, or Session Note changed after an editor was opened.
- Presents a review dialog instead of silently applying last-write-wins.
- Merge Changes preserves newer remote values on fields the current editor did not change, while applying the current editor’s changes.
- Overwrite Anyway intentionally applies the current editor values.
- Cancel leaves the editor open without saving.


## v106 session longevity
- Proactively refreshes the Supabase access token before expiry.
- Updates Realtime authentication after token refresh.
- Retries an API request once when Supabase reports an expired JWT.
- Keeps the refresh token/session persisted locally so long-running campaign sessions do not require sign-out/sign-in.
