# Airbnb Listings — Eight World Cities

**Subtitle:** 288,431 short-term rental listings with prices, hosts, reviews, occupancy estimates and licensing.

---

## 📖 Description

### 288,431 short-term rental listings in 8 cities

Inside Airbnb publishes scraped Airbnb listings for cities worldwide. This dataset collects the
latest snapshot for **8 city feeds** (**8 cities**) and keeps **76 parameters**
per listing.

- **Listing** — id, URL, title, property type, room type, guests, bedrooms, beds, bathrooms and
  amenities.
- **Host** — id, name, join date, response time/rate, acceptance rate, superhost status, listing
  counts, verification methods and identity checks.
- **Location** — neighbourhood, cleansed neighbourhood and neighbourhood group, latitude and
  longitude.
- **Commercial** — price, minimum/maximum nights, availability windows, review counts and scores,
  licence, instant booking, occupancy and revenue estimates.
- **Derived** — numeric price, amenity count, room-type flags, superhost/instant/licence flags,
  mean review score, per-guest ratios, price/occupancy/revenue bands and availability ratio.

**210,155 listings are entire homes** and **112,740 display a licence number** — the core
variables for housing-market, tourism and regulation research.

## 🧾 Columns (76)

`id`, `listing_url`, `name`, `host_id`, `host_name`, `host_since`, `host_location`, `host_response_time`, `host_response_rate`, `host_acceptance_rate`, `host_is_superhost`, `host_listings_count`, `host_total_listings_count`, `host_verifications`, `host_has_profile_pic`, `host_identity_verified`, `neighbourhood`, `neighbourhood_cleansed`, `neighbourhood_group_cleansed`, `latitude`, `longitude`, `property_type`, `room_type`, `accommodates`, `bathrooms`, `bedrooms`, `beds`, `amenities`, `price`, `minimum_nights`, `maximum_nights`, `availability_30`, `availability_60`, `availability_90`, `availability_365`, `number_of_reviews`, `number_of_reviews_ltm`, `number_of_reviews_l30d`, `first_review`, `last_review`, `review_scores_rating`, `review_scores_accuracy`, `review_scores_cleanliness`, `review_scores_checkin`, `review_scores_communication`, `review_scores_location`, `review_scores_value`, `license`, `instant_bookable`, `calculated_host_listings_count`, `calculated_host_listings_count_entire_homes`, `calculated_host_listings_count_private_rooms`, `calculated_host_listings_count_shared_rooms`, `reviews_per_month`, `estimated_occupancy_l365d`, `estimated_revenue_l365d`, `city`, `price_numeric`, `amenities_count`, `is_entire_home`, `is_private_room`, `is_shared_room`, `is_superhost`, `is_instant_bookable`, `has_license`, `has_reviews`, `review_score_mean`, `bedrooms_per_guest`, `beds_per_guest`, `bathrooms_per_bedroom`, `price_band`, `occupancy_band`, `revenue_band`, `availability_ratio`, `reviews_per_month_numeric`, `name_length`

## 💡 Ideas for using this data

1. **Housing pressure** — entire-home share by neighbourhood.
2. **Pricing** — price drivers: size, location, reviews and superhost status.
3. **Regulation** — licence coverage across cities with different rules.
4. **Host concentration** — multi-listing hosts and commercial operators.
5. **Occupancy and revenue** — estimated annual revenue distributions.
6. **Reviews** — score components and review frequency as demand signals.
7. **Amenities** — text mining the amenity lists.
8. **Maps** — price and density maps per city.
9. **Cross-city comparison** — same platform, different regulatory regimes.

## 📁 Files

| File | What it is |
|---|---|
| `airbnb_listings.csv` | 288,431 listings x 76 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`airbnb`, `short-term-rentals`, `housing`, `tourism`, `cities`, `real-estate`

## 🔗 Provenance

- **Source:** **Inside Airbnb** city data downloads
  (`https://data.insideairbnb.com/.../listings.csv.gz`), discovered from the project's data page.
- **Sampling:** the latest available snapshot for 8 cities: amsterdam, barcelona, berlin, london, los-angeles, new-york-city, paris, san-francisco.
- **Processing:** 55 source columns retained; prices, rates and scores parsed to numbers; room,
  host and licence flags plus bands and ratios derived; amenity text truncated.
- **Snapshot date:** 24 November 2026 (feeds dated September 2026).

## 🔄 Update frequency

**Quarterly.** Inside Airbnb refreshes city scrapes every few months.

## ⚠️ Caveats

- Inside Airbnb scrapes public listing pages; the data is a snapshot, not bookings.
- Prices are in local currency per night and are not converted.
- Occupancy and revenue figures are model estimates, not reported figures.
- Coverage and field availability differ by city and date.
- Reviews are only possible after a stay, so new listings look inactive.
- Listing text and amenities are truncated to keep the file manageable.

## 📜 Licence

Inside Airbnb publishes derived data for public-interest research; see insideairbnb.com for terms.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
