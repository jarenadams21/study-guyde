# Chernobyl: Disaster to Present — A Physics-Grounded Data Project

This project investigates the Chernobyl Nuclear Power Plant accident of April 26, 1986,
from first principles through the present day. The goal is not a historical summary.
It is a reconstruction of what actually happened, physically, chemically, biologically,
and epidemiologically, using primary and peer-reviewed datasets where they exist and
explicitly flagging where the record is incomplete, suppressed, or contested.

## What this is

The data here covers six distinct layers of the event:

1. Reactor physics — the sequence of events that caused the accident, with timestamped
   power data showing how the RBMK's positive void coefficient drove the excursion.

2. Source term — what was actually released, isotope by isotope, in PBq, with release
   fractions and the daily I-131 release timeline for April 26 through May 5, 1986.

3. Environmental transport — airborne measurements across Europe (Evangeliou 2016
   database; Kashparov 1987 60km survey), ground deposition by country (JRC Cs-137
   Atlas), and long-term soil and groundwater contamination data.

4. Health outcomes — the acute radiation syndrome cases with dose-graded clinical
   outcomes, thyroid cancer incidence in Belarus and Ukraine from 1986 to 2020,
   liquidator dose registries, and the long-term population dose estimates.

5. Health assessment disputes — a direct comparison of the Chernobyl Forum (2005),
   TORCH (2006), UNSCEAR (2008), and Greenpeace (2006) projections. These differ
   by orders of magnitude and the disagreement is methodological, not factual.

6. Present state — current dose rates in the exclusion zone, the 2021 renewed fission
   activity in room 305/2 of the sarcophagus, wildfire resuspension events (2015, 2020),
   and the long-term groundwater contamination picture from 35 years of monitoring.

## What this is not

This is not a cleaned-up version of aggregated hobby datasets. Every data point is
sourced to a peer-reviewed publication or an official government/UN agency report.
The dataset registry (00_dataset_registry.csv) lists DOIs and access URLs for every
primary source so the provenance chain is unbroken.

## Known gaps in the primary record

The first 48 hours of measurements inside the Soviet Union are largely reconstructed,
not directly preserved. Soviet dosimeters at the site had a maximum reading of
3.6 R/h and were saturated by actual conditions. Early official data from Pripyat
and the 30km zone was suppressed or lost. The INSAG-1 (1986) and INSAG-7 (1992)
reports reflect this: the 1986 report blamed operators; the 1992 revision acknowledged
the reactor design was fundamentally unsafe. Any analysis relying solely on Soviet
data from April-May 1986 must account for this.

## Data files

```
data/
  00_dataset_registry.csv       All primary datasets with DOIs and access info
  01_source_term.csv            Radionuclide release inventory by isotope
  02_accident_sequence.csv      Timestamped reactor power and event timeline
  03_european_airborne.csv      Summary of Evangeliou 2016 airborne database
  04_near_zone_soil_1987.csv    Kashparov 60km survey (ESSD 2020)
  05_cez_contamination.csv      Kashparov CEZ spatial datasets (ESSD 2018)
  06_european_deposition.csv    Cs-137 deposition by country (JRC Atlas)
  07_groundwater.csv            35-year CEZ groundwater monitoring data
  08_health_ars.csv             Acute radiation syndrome cases and doses
  09_health_longterm.csv        Thyroid cancer, liquidators, population doses
  10_health_assessments.csv     Chernobyl Forum vs TORCH vs UNSCEAR comparison
  11_modern_status.csv          Current dose rates, 2021 fission event, NSC data
  12_wildfire_resuspension.csv  2015 and 2020 wildfire radionuclide releases
```

## Primary sources

- OECD-NEA: Chernobyl Assessment of Radiological and Health Impact (2002)
- Kashparov et al. (2018): ESSD 10, 339-353. DOI: 10.5194/essd-10-339-2018
- Kashparov et al. (2020): ESSD 12, 1861-1875. DOI: 10.5194/essd-12-1861-2020
- Evangeliou et al. (2016): Environ. Pollut. 216, 408-418. DOI: 10.1016/j.envpol.2016.05.080
- UNSCEAR (2008): Annex D — Health Effects Due to Radiation from Chernobyl
- Chernobyl Forum (2005): WHO/IAEA/UNDP/UNICEF joint report
- TORCH (2006): Ian Fairlie & David Sumner (commissioned by EU Greens)
- Bugai et al. (2022): Scientific Reports. DOI: 10.1038/s41598-022-22842-5
- Evangeliou et al. (2016): Scientific Reports 6, 26062. DOI: 10.1038/srep26062
