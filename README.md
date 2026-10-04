# SMPCore

Custom plugin for a DonutSMP-style server: **Orders**, **Shards + Shard Shop**, **AFK zone**, **Bounties**.

Requires: Paper 1.21+, Java 21, **Vault** and an economy plugin (**EssentialsX**). PlaceholderAPI is optional.

## Build the .jar

**Option A – IntelliJ IDEA (easiest)**
1. File → Open → select this folder (it's a Maven project).
2. Open the Maven panel on the right → Lifecycle → double-click `package`.
3. The jar is in `target/SMPCore-1.0.0.jar`.

**Option B – command line**
Install JDK 21 and Maven, then run `mvn package` in this folder.

**Option C – GitHub (no setup)**
Push this folder to a GitHub repo. The included workflow builds it automatically;
download the jar from the repo's **Actions** tab → latest run → Artifacts.

Then drop the jar into your server's `plugins/` folder and restart.

## Commands

| Command | What it does |
|---|---|
| `/orders` | Browse all buy orders. Click one to deliver items and get paid. |
| `/orders create <amount> <price-each>` | Order the item in your hand. Money is taken up front. Example: `/orders create 640 5` |
| `/orders mine` | Your orders. Left-click collects items, shift-click cancels (refunds the rest). |
| `/orders collect` | Collect all delivered items. |
| `/shards` / `/shards <player>` | Check shards. |
| `/shards pay <player> <amount>` | Send shards. |
| `/shardshop` | Spend shards (items set in config.yml). |
| `/afk` | Teleport to the AFK zone. Standing inside earns shards. |
| `/bounty <player> <amount>` | Put money on someone's head. Killer gets it. |
| `/bounty`, `/bounty check <player>` | Top bounties / one player's bounty. |

Amounts accept `1.5k`, `2m`, `3b`.

### Admin (`smpcore.admin`, ops by default)
| Command | |
|---|---|
| `/afkzone pos1` / `pos2` | Set the AFK zone corners where you stand. |
| `/afkzone setspawn` | Where `/afk` teleports. |
| `/afkzone info` | Show the zone and whether you're inside. |
| `/shards give/take/set <player> <amount>` | Manage shards. |
| `/smpcore reload` / `save` | Reload config / force save. |

## Placeholders (PlaceholderAPI)
`%smpcore_shards%`, `%smpcore_shards_formatted%`, `%smpcore_bounty%`, `%smpcore_bounty_raw%`, `%smpcore_orders%`

Use them in TAB (scoreboard) and ajLeaderboards, e.g. `/ajlb add %smpcore_shards%` for a shards leaderboard.

## AFK zone setup
1. Build a small closed room (or use a separate world).
2. Stand in one corner: `/afkzone pos1`. Opposite corner (include height): `/afkzone pos2`.
3. Stand where players should arrive: `/afkzone setspawn`.
4. Protect it with WorldGuard (no PvP, no building).

## Data
Saved in `plugins/SMPCore/` (`shards.yml`, `orders.yml`, `bounties.yml`), autosaved every 5 minutes and on shutdown.
