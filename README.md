# On Public Good — Retrofit-To-Order Map

An interactive map of Singapore's HDB blocks, built for an AA Fourth Year Media Studies project on policies that incentivise waste. This repository holds **Part 3: Retrofit-To-Order**. The scrollytelling story that comes before it (Parts 1–2) will be added later. The map works across four scales: **Singapore → Town → Precinct → Block**. The **left panel** shows the same sections at every scale and counts only what is selected: a scale indicator, the total embodied carbon, a **Map mode** switch (VERS status or Block type, which also scrolls to that list), the VERS status and Block type checkbox lists (both always filter the map), and a ranking list of the next level down. Outside the selected town or precinct, blocks turn grey. The **right panel** opens with a preview navigator (the white box is what the map is showing), then a summary card, a block typology bar, the share VERS-eligible within 20 years and an **At risk** section; at precinct scale it adds the neighbourhood's history and its facilities within walking-distance bands every 500 m. At **block scale** a card rises at the bottom centre with flat details, embodied carbon and **Apply for RTO**, which slides the voting form up from the bottom. A present resident chooses to cash out under VERS or join RTO; a new applicant joins RTO. Anyone who joins RTO then votes to adapt or harvest the block.

## Run it locally (offline backup for the crit)

```bash
cd on-public-good
python3 -m http.server
```

Then open <http://localhost:8000>. A local server is needed because the page loads `map.json` by a relative path, which browsers block when `index.html` is opened directly from disk. Deep links work locally too, for example <http://localhost:8000/#site-1>.

**Note:** the page loads Leaflet from cdnjs and its fonts from Google Fonts. The map needs an internet connection even when served locally; without one the fonts fall back to system fonts, but the map itself will not draw.

## Editing the map's styling

Click **Style** at the top right of the map, or press **S**, to open the style editor. It controls the colours, line weights, opacities, fonts and sizes of every map element:
- interface colours and fonts;
- the dark and light base maps;
- VERS band and typology colours;
- block outlines and hover outlines;
- RTO site outlines;
- walking-distance bands (spacing and number);
- material-recovery lines, parks and amenity icons;
- which overlays are shown.

Changes show live and are saved in your browser only.

To make a style permanent for every visitor: click **Download** (or **Copy JSON**) in the editor, replace `style.json` in this repo with the new file, and commit it. The page loads its colours in this order: built-in defaults, then `style.json`, then any edits saved in the visitor's browser. **Reset** in the editor returns to the `style.json` version. You can hide the Style button for a crit from the editor ("Show on map"); press **S** to bring it back.

## Editing the code

`index.html` opens with a short guide (an HTML comment at the very top) that says what is where and which function to search for. For example, `panelLeft` and `panelRight` hold the two side panels, `renderBlockCard` the block card, `renderForm` the RTO form, and `describe` the hover tooltips. Colours, fonts and sizes don't need code: use the Style editor or `style.json`.

## Data sources

- HDB, URA, LTA, MOE, ECDA, NEA, MOH and NParks datasets via [data.gov.sg](https://data.gov.sg), used under the [Singapore Open Data Licence](https://data.gov.sg/open-data-licence).
- Block type, embodied carbon and gross internal area come from the QGIS project **"261118 RTO Interface"** (layer `hdb_block_type_full`, every block). Lease start B, the 4 RTO sites and the MP2019 subzone base map come from **"261116_Singapore Cleaned"**. Years till VERS-eligible = lease start + 70 − 2026; bands follow the eligible year (0–10 yrs = 2027–2036).
- Precincts outside the RTO sites are a stand-in: blocks grouped by distance (about 14 per precinct) until real precinct boundaries are added.

## About the RTO votes

The RTO voting form is a simulation. The starting applicant numbers and vote splits are made up for the demonstration. A visitor's own vote is stored only in their own browser (`localStorage`); nothing is sent to a server, and no one else sees it.
