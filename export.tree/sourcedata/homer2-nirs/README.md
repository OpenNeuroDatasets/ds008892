# HOMER2 fNIRS source and conversion provenance

The supplied `sub-31` through `sub-40` `.nirs` files are MATLAB/HOMER2 continuous-wave recordings. The original `.nirs` files and their 12 event TSVs per subject are copied unchanged here. The BIDS SNIRF runs under each participant's `nirs/` directory preserve the complete continuous recording; no time samples were trimmed. `source_manifest.tsv` records source sizes and SHA-256 checksums.

The three HOMER2 stimulus columns were unlabeled in the source and are therefore named `condition_1` through `condition_3`, without guessing their meanings. The 12 per-session source tables are associated to each condition's markers by ascending session order; check that mapping with the data owner before scientific interpretation.
