# On Public Good — Retrofit-To-Order Map

An interactive map of Singapore's HDB blocks, built for an AA Fourth Year Media Studies project on policies that incentivise waste. This repository holds **Part 3: Retrofit-To-Order**. The scrollytelling story that comes before it (Parts 1–2) will be added later. The map works across three scales. **City (Site Finder):** every HDB block is coloured by years until it becomes eligible for the Voluntary Early Redevelopment Scheme (VERS), with filters for VERS band, town, block type and SERS status; click a town to zoom in. **Precinct (Residential Value):** click a precinct, or one of the four red RTO sites, to see its history and maturity, block typology, embodied carbon, and nearby transport, schools, food centres, clinics and parks within 400 m and 800 m. **Project (Retrofit-To-Order):** click a block to see its lease clock, flat details, embodied carbon and possible material-recovery links to neighbouring blocks. From there, "Apply for RTO" opens a voting form. A present resident chooses to cash out under VERS or join RTO; a new applicant joins RTO. Anyone who joins RTO then votes to adapt or harvest the block.

## Run it locally (offline backup for the crit)

```bash
cd on-public-good
python3 -m http.server
```

Then open <http://localhost:8000>. A local server is needed because the page loads `map.json` by a relative path, which browsers block when `index.html` is opened directly from disk. Deep links work locally too, for example <http://localhost:8000/#site-1>.

**Note:** the page loads Leaflet from cdnjs and its fonts from Google Fonts. The map needs an internet connection even when served locally; without one the fonts fall back to system fonts, but the map itself will not draw.

## Editing the map's styling

Click **🎨 Style** at the top right of the map, or press **S**, to open the style editor. It controls the colours, line weights, opacities, fonts and sizes of every map element:
- interface colours and fonts;
- the dark and light base maps;
- VERS band and typology colours;
- block outlines and hover outlines;
- RTO site outlines;
- walking-ring radii;
- material-recovery lines, parks and amenity icons;
- which overlays are shown.

Changes show live and are saved in your browser only.

To make a style permanent for every visitor: click **Download** (or **Copy JSON**) in the editor, replace `style.json` in this repo with the new file, and commit it. The page loads its colours in this order: built-in defaults, then `style.json`, then any edits saved in the visitor's browser. **Reset** in the editor returns to the `style.json` version. You can hide the Style button for a crit from the editor ("Show on map"); press **S** to bring it back.

## Data sources

- HDB, URA, LTA, MOE, ECDA, NEA, MOH and NParks datasets via [data.gov.sg](https://data.gov.sg), used under the [Singapore Open Data Licence](https://data.gov.sg/open-data-licence).
- Layers, styles and the 4 RTO sites come from the QGIS project **"261116_Singapore Cleaned"**: HDB VERs Eligibility (lease start B, counted from 2027), HDB typology metrics with embodied carbon (983 blocks with under 50 years left), 261030 5 Sites, and MP2019 subzones as the base map.
- Precincts outside the RTO sites are a stand-in: blocks grouped by distance (about 14 per precinct) until real precinct boundaries are added.

## About the RTO votes

The RTO voting form is a simulation. The starting applicant numbers and vote splits are made up for the demonstration. A visitor's own vote is stored only in their own browser (`localStorage`); nothing is sent to a server, and no one else sees it.
