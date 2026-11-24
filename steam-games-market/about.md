Steam Games Market

### The Steam catalogue as a market dataset

SteamSpy publishes an estimate of every game on Steam: ownership bands, review counts, playtime,
price and concurrency. This snapshot covers **2,488 games** with **41 parameters** per title.

Columns cover:
- **Identity** — app id, title, developer, publisher, and how many titles in the file that
  developer and publisher have.
- **Reviews** — positive, negative and total review counts, the positive ratio, a review band,
  user score and SteamSpy's score rank.
- **Audience** — estimated owner range with its bounds and midpoint, plus review and concurrency
  rates per estimated owner.
- **Engagement** — average and median lifetime playtime (minutes and hours), two-week playtime,
  the median/average ratio and playtime per owner.
- **Commerce** — current and initial price, discount percentage and amount, a price band,
  free-to-play and discount flags, peak concurrent users.
- **Title features** — length, word count, sequel heuristic, leading "The".

**304 titles (12.2%)** are free to play. Owner figures are SteamSpy's own
interval estimates, not Valve disclosures, which makes the dataset a good exercise in working with
banded, uncertain quantities.

41 columns; one row per Steam game.
