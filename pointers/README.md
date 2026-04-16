# Freight lane pointers

`freight_lanes.json` is the **stable registry** consumed by tools such as the TrueSight DAO
[Shipping Planner](https://dapp.truesight.me/shipping_planner.html).

Stable raw URL (default branch `main`):

https://raw.githubusercontent.com/TrueSightDAO/agroverse-freight-audit/main/pointers/freight_lanes.json

When you publish a new quotation snapshot for a lane, update that lane’s
`latest_snapshot_url` (and `snapshot_path_in_repo`) to point at the new immutable snapshot
file under `snapshots/`.
