# World Map (India boundary variant)

This repository provides GeoJSON and TopoJSON files of the world with country boundaries depicting India including territories claimed by it. This is useful for projects that require an India-aligned boundary depiction, including publication contexts in India; users should verify applicable requirements for their organisation and jurisdiction.

The repo includes:

- `world_map_india.zip` — containing full-resolution GeoJSON (larger file) as well as the TopoJSON files
- `world_with_india_claimed_simplified.geojson` — TopoJSON version of the map
- `world_map_india_compressed.geojson` - A compressed version of the original GeoJSON file. 


## Data sources

This map was derived from **Natural Earth** vector datasets:

- Admin 0 – Countries (polygons)
- Admin 0 – Breakaway and Disputed Areas (polygons)

Natural Earth is a public domain dataset. Please see Natural Earth’s website for details and updates.

---

## How the dataset was created

The workflow was performed in **QGIS**:

1. Load Natural Earth **Admin 0 – Countries** and **Admin 0 – Breakaway/Disputed Areas**.
2. Extract the **India** polygon from the countries layer.
3. From the disputed/breakaway layer, select polygons whose notes indicate India is a claimant and/or the polygon is administered by India (based on the layer’s attribute fields).
4. Dissolve and fix geometries for:
   - India base polygon
   - Selected disputed polygons
5. Union these to create a single **India (claimed)** polygon.
6. Remove India from the world layer and insert the new India polygon.
7. Remove overlaps before merging to keep the output topologically clean.
8. Export final as GeoJSON.

---

## Joining data (ISO codes / names)

Depending on how you plan to join your data, use one of the following properties (check the GeoJSON properties panel in your GIS/editor):

- `ADM0_A3` / `ISO_A3` (ISO3-style codes)
- `SOVEREIGNT` / `NAME` (country names)

If you need a guaranteed join key, consider using `ADM0_A3` and keep that field in the simplified version as well.

---

## Caveats

- **Disputed territories are complex.** Different datasets and institutions encode disputes differently (de facto vs de jure vs claimant views). This dataset follows the selection logic described above using Natural Earth’s disputed areas layer.
- **Not legal advice.** If you are publishing maps in jurisdictions with specific legal requirements around boundary depiction, consult the relevant official guidance and your organisation’s policies.

---

## License

- CC0-1.0
- Natural Earth source data is public domain; this repo mainly packages a derived boundary variant and the processing output.

---

## Citation / attribution

If you use this dataset, please attribute as:

- “Sreedev Krishnakumar (World Map – India boundary variant), derived from Natural Earth.”


---
