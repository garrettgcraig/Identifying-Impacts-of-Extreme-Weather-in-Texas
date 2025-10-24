# Identifying Impacts of Extreme Weather

## Overview

This repository contains a geospatial analysis examining the impact of the February 2021 Texas winter storms on Houston area power outages. Using remotely-sensed night lights data from NASA's VIIRS instrument, OpenStreetMap building data, and US Census socioeconomic data, this analysis estimates which homes lost power and explores potential environmental justice implications.

## Assignment Goals

- **Estimate power outage impacts**: Use satellite night lights data to identify areas that experienced blackouts during the 2021 Texas winter storms
- **Map affected residential areas**: Combine geospatial datasets to determine which homes lost power
- **Analyze socioeconomic patterns**: Investigate whether certain census tracts were disproportionately affected based on median household income
- **Develop reproducible workflow**: Create a professional, well-documented Quarto analysis that follows best practices for geospatial data science

## Repository Structure

```
EDS223-HW3/
├── README.md                    # This file
├── EDS223-HW3.qmd              # Main analysis document (Quarto)
├── EDS223-HW3.html             # Rendered HTML output
├── .gitignore                  # Git ignore file (excludes data/)
├── data/                       # Data directory (not tracked by git)
│   ├── VNP46A1.zip            # VIIRS night lights data
│   ├── gis_osm_buildings_a_free_1.gpkg.zip  # OSM buildings
│   ├── gis_osm_roads_free_1.gpkg.zip        # OSM roads
│   └── ACS_2019_5YR_TRACT_48_TEXAS.gdb.zip  # Census data
└── EDS223-HW3.Rproj            # R Project file
```

## Data Sources

1. **VIIRS Night Lights (VNP46A1)**
   - Daily satellite imagery showing nighttime light intensity
   - Dates: February 7, 2021 (pre-storm) and February 16, 2021 (during storm)
   - Source: NASA Earth Observations

2. **OpenStreetMap (OSM) Data**
   - Building footprints and road network for Houston metropolitan area
   - Source: Geofabrik's download sites

3. **US Census Bureau ACS Data**
   - American Community Survey 2019 5-year estimates
   - Census tract-level demographic and socioeconomic variables
   - Focus: Median household income

## Methodology

1. **Create blackout mask** from changes in night lights intensity between pre-storm and during-storm dates
2. **Exclude highway areas** to reduce false positives from reduced traffic
3. **Identify affected residential buildings** through spatial joins with OSM data
4. **Analyze socioeconomic impacts** by linking affected areas to census tract income data
5. **Visualize results** through maps and statistical comparisons

## Key Deliverables

- Maps comparing night lights before and after the storms
- Map of Houston residential buildings that lost power
- Estimate of total homes affected
- Census tract-level analysis of blackout events
- Income distribution comparison between affected and unaffected areas
- Discussion of findings and analytical limitations

## Requirements

- R (≥ 4.0)
- Key packages: `tidyverse`, `sf`, `stars`, `tmap`, `patchwork`
- Quarto for rendering

## Usage

1. Clone this repository
2. Download and unzip data files to the `data/` directory
3. Open `EDS223-HW3.Rproj` in RStudio
4. Render `EDS223-HW3.qmd` to generate the HTML report

## Author

Garrett Craig
Master of Environmental Data Science (MEDS)
Bren School of Environmental Science & Management, UC Santa Barbara

## Acknowledgments

Assignment developed for EDS 223: Geospatial Analysis & Remote Sensing
Data sources: NASA, OpenStreetMap, US Census Bureau
