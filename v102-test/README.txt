PARTY SHARED INVENTORY PWA — v14

NEW IN v14
- Global Party Funds header removed.
- Optional Treasury entries can be added to any container or character.
- Players and DM can add/edit Treasury entries.
- Treasury entries always sort to the top of their location.
- Tracks platinum, gold, silver, copper, plus a formatted Jewels & Valuables list.
- Multiple Treasuries are allowed; none are required.
- DM can permanently delete a Treasury.
- Existing items/data remain compatible.

V99
- Fixes private Supabase Storage artwork retrieval by using the authenticated object endpoint.
- Removes the temporary v98 artwork diagnostic.
- No Supabase policy changes required.


V102
- Clean production-candidate build after resolving private artwork reads.
- Removes all temporary artwork/auth diagnostic UI and code.
- Retains authenticated private Storage artwork loading.
- Requires the corrected Storage SELECT policy from query 14.
- Service-worker cache bumped to v102.
