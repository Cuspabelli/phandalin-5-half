# The Phandalin 5 1/2 — Collaboration-Ready v88

No hosted backend has been selected or connected. v88 continues using localStorage.

Prepared for migration:
- Stable UUIDs for inventory/Funds.
- createdAt, updatedAt, and revision metadata on inventory/Funds.
- Stable item ordering by item ID; migration snapshot exposes sortOrder.
- A buildCollaborationSnapshot() helper for later migration.
- Current visual behavior and PWA experience preserved.

Recommended eventual roles:
DM/Admin: all player abilities plus DM Storage, container/character management, and permanent deletion.
Player: shared inventory add/edit/reorder, Funds editing, Campaign Reference and Session Notes editing, and Used/Sold removal.

The current Player/DM selector is only a UI preview and is not security. A shared deployment should replace it with authenticated roles enforced by the backend.

Keep local per-user: Image/List/Compact choice, Campaign Reference view choice, collapsed Session Note state, and other visual preferences.

Move to shared backend later: inventory/Funds/order, containers, characters, Campaign Reference + Trash, Session Notes + Trash, and user roles.

Backend safeguards to add when a provider is selected: server-side permissions, createdBy/updatedBy, revision-based stale-edit detection, soft deletion before permanent deletion, and realtime refresh.
