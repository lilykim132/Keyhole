# Keyhole

**Know your landlord before you sign.** Keyhole shows landlord scores from past student tenants near Carnegie Mellon and Pitt. Scores cover repairs, getting the deposit back, communication and fair pricing.

This is the MVP for 70-415 (Section B, Fall 2026), built by Benedict Nematadzira, Arnav Arora, Doug Darling, Lily Kim, Saamarth Sethi and Arjun Vasudevan.

> **Sample data:** all landlords, listings and starting reviews are made up for testing. Neighborhood outlines are real.

## What's in it

- **Find a place:** listings with filters for neighborhood, budget, beds and commute, sorted by landlord score, next to a real map of Pittsburgh.
- **Landlord pages:** the overall score, a score for each category, "would rent again," reviews and open listings.
- **Neighborhood match:** set a budget, a max commute and up to 3 priorities to see which neighborhoods match best on the map.
- **Write a review:** an anonymous form with a 1–5 rating for each category.
- **CMU / Pitt switch:** changes all commute times at once.

## Project structure

```
index.html                         the whole app (HTML, CSS, JS)
favicon.svg
data/pittsburgh-neighborhoods.json neighborhood outlines and rivers
vendor/leaflet/                    Leaflet 1.9.4 map library (BSD-2 license)
vercel.json                        static hosting settings
```

There's no build step and nothing to install. It's a plain static site.

## Run it locally

From this folder:

```
python3 -m http.server 8000
```

Then open http://localhost:8000. Opening `index.html` directly won't load the map, because browsers block loading the map data file from a `file://` page.

## Deploy on Vercel

1. Push this folder to a GitHub repo, with `index.html` at the top level of the repo.
2. On vercel.com, choose **Add New → Project** and import the repo.
3. Set **Framework Preset** to **Other**. Leave Build Command empty, and set Output Directory to `.` or leave it as is.
4. Click **Deploy**. Every push to `main` redeploys automatically.

## Known limits

- **Reviews are saved per browser.** In this version, a submitted review is stored in that visitor's browser (`localStorage`). Other students don't see it. Sharing reviews between visitors needs a database, such as Supabase or Vercel's storage options.
- **Team insights** (`/#insights`) need that same database, so the page shows a placeholder for now.
- **Parks are approximate.** The Schenley and Frick Park shapes are hand-drawn approximations.

## Credits

- Neighborhood boundaries: City of Pittsburgh (via the Western Pennsylvania Regional Data Center)
- Map library: [Leaflet](https://leafletjs.com) © Volodymyr Agafonkin, BSD-2-Clause (see `vendor/leaflet/LICENSE`)
- Fonts: Inter and Inter Tight from Google Fonts
