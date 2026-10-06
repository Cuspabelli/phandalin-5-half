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
