# WellWatch: early warnings for desert wells (Breaking Bytes, Water & Climate AI)

**Who:** a village council and herders who rely on a handful of wells.
**What:** warns ~3 weeks before a well runs dry, in plain SMS (English + Arabic) with an action: ration, and which well to move to.

## Chain: data → prediction → warning
1. **Data (simulated, shaped like CHIRPS rainfall + Sentinel-2 NDVI + well-level sensors).** 90 days, 3 wells.
2. **Prediction:** 30-day regression on water level; outputs days-to-dry with an 80% range, and probability of running dry within 21 days (prediction-interval based).
3. **Warning:** tiered OK / WATCH / WARN, rendered as two short SMS on a basic phone.

## Desert rules
- **Sensor dies:** model extrapolates from the last good reading; uncertainty band visibly widens.
- **Cloudy satellite:** vegetation signal is dropped and flagged, not guessed.
- **Both down:** confidence drops to "Low" and the SMS asks herders for a report; a herder "water is low" SMS is fused in by inverse-variance weighting.
- **False alarm vs missed alarm:** one threshold slider; WATCH tier at half the threshold.
- **Cost / connectivity:** SMS only, no app, no data plan; static page, no server.

## Run
Open `index.html`. No build step, no dependencies.

## Honest limits
Data is simulated. Next step: swap in CHIRPS/Sentinel-2 via Google Earth Engine and real sensor logs; backtest the threshold on historical well failures.
