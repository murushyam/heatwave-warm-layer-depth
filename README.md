# How Deep Does a Heatwave Reach?

## Multi-City Warm-Layer Depth Timing, Heat-Dome Control, and a Physics-Constrained Spatial-Attention Algorithm for 1 km Reconstruction

**Author:** M.S. Shyam Sunder (NIT Rourkela)  
**Status:** Finalized research proposal  
**Date:** 2026-11-21

---

### Abstract

Building on Hotz et al. (2024, 2026), Lhotka & Kyselý (2024), and Lakshman et al. (2025), this study tests whether persistent heat-dome circulation produces deeper surface-connected warm layers whose maximum depth leads or coincides with the surface temperature peak. The analysis covers a balanced set of cities with confirmed high-quality surface, ERA5, and radiosonde data spanning tropical, subtropical, and mid-latitude regimes: Hyderabad and Delhi (India), Austin (Texas), Prague (central Europe), and Seattle (Pacific Northwest). A surface-based event catalogue is constructed first. Warm-layer depth is measured from ERA5 and linked to a reproducible dome screen. On a stratified subset of events a Physics-Constrained Spatial-Attention Network (PC-SAN) is developed and rigorously benchmarked against four baselines. Comprehensive radiosonde, station, and cross-validation protocols support all claims.

### Central Hypothesis

Persistent heat-dome circulation produces deeper surface-connected warm layers whose maximum depth leads or closely coincides with the surface temperature peak. Events lacking persistent ridging remain shallower and more synchronous with the surface peak. This lead–lag relationship and vertical reach differ systematically between tropical and mid-latitude cities, consistent with the climate-zone clusters of Hotz et al. (2026) and the heat-dome dynamics of Lakshman et al. (2025). A physics-constrained spatial-attention network recovers both the vertical structure and intra-city spatial contrasts at 1 km on unseen events better than strong baselines.

### Research Questions

1. Does the warm-layer top reach its greatest depth before, during, or after the hottest surface day, and is this timing controlled by persistent ridging and subsidence?
2. Can a physics-constrained spatial-attention algorithm recover warm-layer depth, its timing, and urban-scale spatial contrasts from coarse ERA5 inputs on fully held-out episodes?

### Objectives

**Objective 1** – Quantify warm-layer depth, its timing relative to the surface peak, and the controlling role of heat-dome circulation across a multi-regime city set.

**Objective 2** – Develop, train, and rigorously benchmark a Physics-Constrained Spatial-Attention Network against strong baselines for 1 km warm-layer reconstruction.

### Study Areas (all with confirmed data availability)

| City              | Regime              | Surface Tmax                  | Radiosonde (IGRA)               | Literature link                  |
|-------------------|---------------------|-------------------------------|---------------------------------|----------------------------------|
| Hyderabad, India  | Tropical Deccan     | IMD/open repositories         | 43128                           | Lakshman et al. (2025)           |
| Delhi, India      | Subtropical / NCI   | IMD/open + GHCN               | New Delhi/Safdarjung (long)     | Lakshman et al. (2025)           |
| Austin, Texas     | Humid subtropical   | NOAA GHCN (Camp Mabry, etc.)  | Nearby IGRA stations            | —                                |
| Prague, Czechia   | Mid-latitude Europe | National open + GHCN/ECA&D    | Praha-Libus (11520)             | Lhotka & Kyselý (2024)           |
| Seattle, USA      | Mid-latitude PNW    | NOAA GHCN                     | Nearby IGRA stations            | Hotz et al. (2024) PNW case      |

ERA5 is global. WRF 1 km targets are generated only for a stratified subset of events. All data are publicly available or generatable.

### Positioning relative to prior work

- Supplies the multi-event lead–lag distributions requested by Hotz et al. (2024), including a PNW site.
- Tests the tropical vs mid-latitude vertical-structure contrast of Hotz et al. (2026) across multiple cities.
- Relates the continuous warm-layer-top metric to the four 3D types of Lhotka & Kyselý (2024) at the European site.
- Extends the Indian heat-dome interpretation of Lakshman et al. (2025) to depth timing and additional climate zones.

### Methodology

#### Objective 1 – Observational analysis

Independent surface-based event catalogue (local 95th-percentile Tmax, ≥3 consecutive days; full sensitivity). Reproducible warm-layer top from ERA5 (contiguous height AGL of local 90th-percentile warmth, with vertical uncertainty interval). Dome screen (≥2 consecutive days of elevated 500 hPa height within 250 km + positive mid-tropospheric ω). Lead–lag analysis stratified by dome class and city/regime. Time–height composites, regional circulation maps, and equal-event-weight statistics.

#### Objective 2 – Algorithm development and benchmarking

**PC-SAN**: multi-level ERA5 encoder + dome indicators + static fields → spatial attention → vertical coherence module (soft hydrostatic/potential-temperature penalty) → multi-task heads (temperature correction + warm-layer-top regression).

**Baselines**: (1) bilinear ERA5, (2) ridge regression, (3) gradient-boosted trees, (4) plain deep-learning model without attention or physics residual.

Identical leave-whole-episode-out and leave-one-year-out splits. Ablations and cross-city transferability tests included.

### Validation (high-impact standard)

- ERA5 warm-layer tops validated against all available IGRA radiosondes during events and controls; bias, MAE, and surface-connected hit rate reported by height and city.
- Surface event catalogues and peak days cross-checked against independent stations and gridded products.
- Every WRF simulation skill-screened against radiosondes and stations before use as a training target.
- PC-SAN and baselines evaluated on warm-layer-top error and lag error (temperature MAE secondary). Residual urban–rural contrasts compared with multi-station differences where available.
- Bootstrap confidence intervals and a pre-specified non-parametric test on the lag difference between dome and non-dome events. Full sensitivity to all thresholds provided. Vertical uncertainty interval carried through all statistics.

### Expected outcomes and novelty

First multi-event, multi-regime distributions of warm-layer depth lead–lag controlled by a dome screen, explicitly spanning the climate zones of Hotz et al. (2026) and the regions of prior case studies. A fully benchmarked, ablated PC-SAN algorithm purpose-built for the vertically integrated diagnostic. Attention maps recovering the same mid-tropospheric features identified observationally.

### Scope control and feasibility

Primary scientific claim remains the observational lead–lag result across the five cities. The algorithm is a supporting methodological contribution. WRF is limited to stratified subsets. All five cities have strong, publicly available surface and radiosonde data, enabling a robust climate-regime comparison without data-quality compromises. With the expanded validation and statistical protocols, the proposal meets the rigor expected by high-impact journals.

---

*This document is the finalized research proposal ready for implementation and manuscript preparation.*
