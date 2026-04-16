# Acoustics

Pipeline for note analysis:

- compute power spectrum on a sustain window (attack/decay excluded),
- estimate fundamental frequency robustly (autocorrelation + harmonic consistency),
- extract overtone amplitudes,
- classify notes by overtone profile with K-means clustering.

## Setup

Use Python 3.10+ and install dependencies:

```bash
pip install numpy scikit-learn
```

## Run

From the project root:

```bash
python analyze_notes.py --data-dir data --clusters 4 --harmonics 8 --out-csv analysis_results.csv
```

## Output

The script creates `analysis_results.csv` with:

- `f0_hz`: estimated fundamental frequency,
- `f0_autocorr_hz`: raw autocorrelation estimate,
- `h1_rel_db ... hN_rel_db`: harmonic amplitudes in dB relative to the first harmonic,
- `cluster`: K-means class from overtone relative amplitudes.

Tip: if clusters look unstable, try a different number of clusters (`--clusters`) or harmonics (`--harmonics`).
