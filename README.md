
# TerraLunaMars – Planetary Analogue Atlas
**NASA Space Apps Challenge 2026**

## Problem
Choosing where to land or build on the Moon or Mars requires knowing slope, surface texture, rock type and thermal extremes. Field study is impossible before a mission, and orbital data is hard to interpret without a familiar reference.

## Solution
We compare each Moon/Mars target with a geologically similar site on Earth, so terrain and thermal behaviour can be examined on the ground, not only from orbit. This is a screening and interpretation model: it narrows where to look and does not replace mission data.

## Site pairs
| Target | Earth analogue | Why this pair |
|---|---|---|
| Flaugergues Crater, Mars | Lut Desert, Iran | Hyper-arid, wind-worked surfaces under extreme solar heating (sandblasting, yardangs, evaporite crusts) |
| Gruithuisen Domes, Moon | Sugarloaf Dome, Arizona | Steep-sided, silica-rich rhyolite–dacite domes; Gruithuisen is the Lunar-VISE landing target (2027) |

## Method
1. Select comparable sites on Earth, Moon and Mars.
2. Assemble open NASA, ESA and USGS layers (MOLA, LOLA, Copernicus DEM GLO-30).
3. Clip, reproject and resample both sites to one grid and one analysis window.
4. Compute relief, slope, detrended roughness and elevation scatter in Python, then compare using S = 100 × (1 − |a − b| / max(|a|, |b|)).

## Key results
| Metric | Mars vs Lut | Moon vs Sugarloaf |
|---|---|---|
| Topographic match (computed) | 86.3% | 74.1% |
| Mineralogy match (literature) | 72.5% | 72.5% |
| Thermal match (literature) | 31.3% | 13.8% |
| Overall (equal weights) | 63.4% | 53.5% |

Lut is best framed as a hyper-arid aeolian/geomorphological analogue, not a thermal one. Gruithuisen vs Sugarloaf is a partial analogue, strongest in silicic composition and dome morphology.

## Limitations
- 68.4% of the Mars (MOLA) window is interpolated, not directly measured.
- Results depend on window size; the Moon analysis uses a 30 km window larger than the domes themselves.
- Rows tagged "Literature" are estimates from published values, not computed by the code.
- An analogue narrows hypotheses; it does not prove equivalence. Gravity, atmosphere, radiation and time scales differ.

## Files
- `Planetary_Analogue_Report_Revised__1_.pdf` – scientific report
- `DOC-20261114-WA0100.pdf` – project atlas (slides)
- Code and result files – reproducible analysis

## Sources
- https://science.nasa.gov/earth/earth-observatory/san-francisco-peaks-volcano-field-6585/
- https://science.nasa.gov/photojournal/gruithuisen-domes-constellation-region-of-interest/
- https://science.nasa.gov/photojournal/flaugergues-crater-false-color/
- NASA PDS Geosciences Node (MOLA MEGDR, LRO LOLA), ESA Copernicus DEM GLO-30, USGS Astrogeology, NASA Earth Observatory
