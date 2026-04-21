data_dict = """# Data dictionary — NM OCD well data

## Source
NM Oil Conservation Division (OCD)
URL: https://ocd-hub-nm-emnrd.hub.arcgis.com/datasets/387f397ebf164c7aa6a752aac7d22b17_0
Downloaded: 2026-04-21
Access method: ArcGIS REST API (paginated, batch=2000)

## Files produced
| File | Description | Rows | CRS |
|------|-------------|------|-----|
| nm_ocd_disposal_wells.geojson | SWD + Injection wells | 7,892 | EPSG:4326 |
| nm_ocd_oil_wells.geojson | Oil production wells (cross-validation) | 81,371 | EPSG:4326 |
| nm_swd_per_county.geojson | County polygons with SWD well counts | 33 | EPSG:4326 |
| nm_swd_summary.csv | County × disposal type breakdown | — | — |

## Well type classification
| OCD type string | Count | Included as |
|----------------|-------|-------------|
| Oil | 81,371 | Oil wells (cross-validation only) |
| Gas | 47,512 | Excluded |
| Injection | 6,104 | Disposal well (included in swd_wells) |
| Salt Water Disposal | 1,788 | Disposal well (included in swd_wells) |
| CO2 | 977 | Excluded |
| Miscellaneous | 383 | Excluded |
| Water | 144 | Excluded — water supply, not disposal |
| CO2 (duplicate) | 56 | Excluded |

## Decisions and assumptions
- "Injection" wells included because they serve the same disposal
  function as SWD wells in the NM regulatory context.
- "Water" wells excluded — these are water supply wells,
  not saltwater disposal infrastructure.
- No volume data available in this dataset (locations only).
  Volume data comes from the separate NM produced water dataset.
"""

with open(f"{WORK_DIR}/docs/data_dictionary.md", "a") as f:
    f.write(data_dict)
print("Data dictionary updated.")