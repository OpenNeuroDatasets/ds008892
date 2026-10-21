# CuBiAAD (BIDS EEG and fNIRS)

## Included data

The BIDS raw dataset includes EEG for `sub-01` through `sub-30` and fNIRS for `sub-31` through `sub-40`. The participant table uses demographics reported in Table 1 of the accompanying paper. EEG recordings from one multi-epoch EEGLAB `.set` file were split into separate BIDS sessions, one epoch per matching event table.

The fNIRS runs were converted from the HOMER2 `.nirs` files supplied in `新建文件夹 (7)`. Each participant has one continuous BIDS SNIRF run with all original samples, 150 raw amplitude channels, 24 sources, 16 detectors, and three wavelengths. The three unlabeled HOMER2 stimulus columns are retained as `condition_1` through `condition_3`. The older NIRSPARK binary files from the original database remain unchanged under `sourcedata/nirs-native/` and were not used to generate the SNIRF files.

Available preprocessed EEG is in `derivatives/cubiaad-preproc/`; the separate original `derivatives/preproc/` subset is retained independently. Stimulus audio files are in `stimuli/audio/`.

The source paper reports 32 EEG electrodes, a 500 Hz sampling frequency, 50 Hz power-line frequency, a 10-20 placement scheme, and 69-second speech stimuli. The `.set` metadata was used for sample counts, channel labels, event-marker latencies, and EEGLAB channel coordinates. The `.fdt` signal samples were copied byte-for-byte; the `.set` pointers were updated only so each file opens its BIDS-named `.fdt` partner.

## fNIRS conversion notes

Each participant's original HOMER2 file is one continuous recording, so it is stored as one BIDS `run-01` rather than being cut into 12 artificial recordings. The time series and acquisition time vector were preserved, with time reset to zero at the first sample. All three source stimulus-marker columns are represented in both SNIRF `stim` groups and the associated events table. The 12 source event tables were associated to marker blocks by ascending `ses-XX` order; the marker-condition meanings are not documented, so they remain generic. Confirm the exact task/marker correspondence with the data owner before analysis.

The source supplies identical 2D probe-layout coordinates for all 10 participants, with `SpatialUnit=cm` and z=0. These are recorded as template positions and are not described as individually digitized or anatomically registered coordinates. Raw intensity units and device model are not stated in the HOMER2 files; no unit or manufacturer was inferred.

## Session mapping used

Where one source `.set` contains 12 epochs and 12 event tables are available, epoch order is paired with ascending `ses-XX` order. Where the source contains separate one-trial `.set` files, natural numeric filename order is paired with ascending session order. The database supplies no explicit join key, so this mapping is provisional and must be confirmed with the data owner before scientific analyses. Participant-specific event tables from the accompanying derivatives were used for `sub-02` and `sub-27`, whose raw event folders contained duplicate tables labeled for other participants.

| participant | BIDS session | source recording / epoch |
|---|---:|---|
| sub-01 | ses-01 | `1-.set` |
| sub-01 | ses-02 | `2-.set` |
| sub-01 | ses-03 | `3-.set` |
| sub-01 | ses-04 | `4-.set` |
| sub-01 | ses-05 | `5-.set` |
| sub-01 | ses-06 | `7-.set` |
| sub-01 | ses-07 | `8-.set` |
| sub-01 | ses-08 | `9-.set` |
| sub-01 | ses-09 | `11-.set` |
| sub-01 | ses-10 | `12-.set` |
| sub-01 | ses-11 | `14-.set` |
| sub-01 | ses-12 | `15-.set` |
| sub-02 | ses-01 | `all.set [epoch 1]` |
| sub-02 | ses-02 | `all.set [epoch 2]` |
| sub-02 | ses-03 | `all.set [epoch 3]` |
| sub-02 | ses-04 | `all.set [epoch 4]` |
| sub-02 | ses-05 | `all.set [epoch 5]` |
| sub-02 | ses-06 | `all.set [epoch 6]` |
| sub-02 | ses-07 | `all.set [epoch 7]` |
| sub-02 | ses-08 | `all.set [epoch 8]` |
| sub-02 | ses-09 | `all.set [epoch 9]` |
| sub-02 | ses-10 | `all.set [epoch 10]` |
| sub-02 | ses-11 | `all.set [epoch 11]` |
| sub-02 | ses-12 | `all.set [epoch 12]` |
| sub-03 | ses-01 | `all.set [epoch 1]` |
| sub-03 | ses-02 | `all.set [epoch 2]` |
| sub-03 | ses-03 | `all.set [epoch 3]` |
| sub-03 | ses-04 | `all.set [epoch 4]` |
| sub-03 | ses-05 | `all.set [epoch 5]` |
| sub-03 | ses-06 | `all.set [epoch 6]` |
| sub-03 | ses-07 | `all.set [epoch 7]` |
| sub-03 | ses-08 | `all.set [epoch 8]` |
| sub-03 | ses-09 | `all.set [epoch 9]` |
| sub-03 | ses-10 | `all.set [epoch 10]` |
| sub-03 | ses-11 | `all.set [epoch 11]` |
| sub-03 | ses-12 | `all.set [epoch 12]` |
| sub-04 | ses-01 | `all.set [epoch 1]` |
| sub-04 | ses-02 | `all.set [epoch 2]` |
| sub-04 | ses-03 | `all.set [epoch 3]` |
| sub-04 | ses-04 | `all.set [epoch 4]` |
| sub-04 | ses-05 | `all.set [epoch 5]` |
| sub-04 | ses-06 | `all.set [epoch 6]` |
| sub-04 | ses-07 | `all.set [epoch 7]` |
| sub-04 | ses-08 | `all.set [epoch 8]` |
| sub-04 | ses-09 | `all.set [epoch 9]` |
| sub-04 | ses-10 | `all.set [epoch 10]` |
| sub-04 | ses-11 | `all.set [epoch 11]` |
| sub-04 | ses-12 | `all.set [epoch 12]` |
| sub-05 | ses-01 | `all.set [epoch 1]` |
| sub-05 | ses-02 | `all.set [epoch 2]` |
| sub-05 | ses-03 | `all.set [epoch 3]` |
| sub-05 | ses-04 | `all.set [epoch 4]` |
| sub-05 | ses-05 | `all.set [epoch 5]` |
| sub-05 | ses-06 | `all.set [epoch 6]` |
| sub-05 | ses-07 | `all.set [epoch 7]` |
| sub-05 | ses-08 | `all.set [epoch 8]` |
| sub-05 | ses-09 | `all.set [epoch 9]` |
| sub-05 | ses-10 | `all.set [epoch 10]` |
| sub-05 | ses-11 | `all.set [epoch 11]` |
| sub-05 | ses-12 | `all.set [epoch 12]` |
| sub-06 | ses-01 | `all.set [epoch 1]` |
| sub-06 | ses-02 | `all.set [epoch 2]` |
| sub-06 | ses-03 | `all.set [epoch 3]` |
| sub-06 | ses-04 | `all.set [epoch 4]` |
| sub-06 | ses-05 | `all.set [epoch 5]` |
| sub-06 | ses-06 | `all.set [epoch 6]` |
| sub-06 | ses-07 | `all.set [epoch 7]` |
| sub-06 | ses-08 | `all.set [epoch 8]` |
| sub-06 | ses-09 | `all.set [epoch 9]` |
| sub-06 | ses-10 | `all.set [epoch 10]` |
| sub-06 | ses-11 | `all.set [epoch 11]` |
| sub-06 | ses-12 | `all.set [epoch 12]` |
| sub-07 | ses-01 | `all.set [epoch 1]` |
| sub-07 | ses-02 | `all.set [epoch 2]` |
| sub-07 | ses-03 | `all.set [epoch 3]` |
| sub-07 | ses-04 | `all.set [epoch 4]` |
| sub-07 | ses-05 | `all.set [epoch 5]` |
| sub-07 | ses-06 | `all.set [epoch 6]` |
| sub-07 | ses-07 | `all.set [epoch 7]` |
| sub-07 | ses-08 | `all.set [epoch 8]` |
| sub-07 | ses-09 | `all.set [epoch 9]` |
| sub-07 | ses-10 | `all.set [epoch 10]` |
| sub-07 | ses-11 | `all.set [epoch 11]` |
| sub-07 | ses-12 | `all.set [epoch 12]` |
| sub-08 | ses-01 | `all.set [epoch 1]` |
| sub-08 | ses-02 | `all.set [epoch 2]` |
| sub-08 | ses-03 | `all.set [epoch 3]` |
| sub-08 | ses-04 | `all.set [epoch 4]` |
| sub-08 | ses-05 | `all.set [epoch 5]` |
| sub-08 | ses-06 | `all.set [epoch 6]` |
| sub-08 | ses-07 | `all.set [epoch 7]` |
| sub-08 | ses-08 | `all.set [epoch 8]` |
| sub-08 | ses-09 | `all.set [epoch 9]` |
| sub-08 | ses-10 | `all.set [epoch 10]` |
| sub-08 | ses-11 | `all.set [epoch 11]` |
| sub-08 | ses-12 | `all.set [epoch 12]` |
| sub-09 | ses-01 | `all.set [epoch 1]` |
| sub-09 | ses-02 | `all.set [epoch 2]` |
| sub-09 | ses-03 | `all.set [epoch 3]` |
| sub-09 | ses-04 | `all.set [epoch 4]` |
| sub-09 | ses-05 | `all.set [epoch 5]` |
| sub-09 | ses-06 | `all.set [epoch 6]` |
| sub-09 | ses-07 | `all.set [epoch 7]` |
| sub-09 | ses-08 | `all.set [epoch 8]` |
| sub-09 | ses-09 | `all.set [epoch 9]` |
| sub-09 | ses-10 | `all.set [epoch 10]` |
| sub-09 | ses-11 | `all.set [epoch 11]` |
| sub-09 | ses-12 | `all.set [epoch 12]` |
| sub-10 | ses-01 | `all.set [epoch 1]` |
| sub-10 | ses-02 | `all.set [epoch 2]` |
| sub-10 | ses-03 | `all.set [epoch 3]` |
| sub-10 | ses-04 | `all.set [epoch 4]` |
| sub-10 | ses-05 | `all.set [epoch 5]` |
| sub-10 | ses-06 | `all.set [epoch 6]` |
| sub-10 | ses-07 | `all.set [epoch 7]` |
| sub-10 | ses-08 | `all.set [epoch 8]` |
| sub-10 | ses-09 | `all.set [epoch 9]` |
| sub-10 | ses-10 | `all.set [epoch 10]` |
| sub-10 | ses-11 | `all.set [epoch 11]` |
| sub-10 | ses-12 | `all.set [epoch 12]` |
| sub-11 | ses-01 | `all.set [epoch 1]` |
| sub-11 | ses-02 | `all.set [epoch 2]` |
| sub-11 | ses-03 | `all.set [epoch 3]` |
| sub-11 | ses-04 | `all.set [epoch 4]` |
| sub-11 | ses-05 | `all.set [epoch 5]` |
| sub-11 | ses-06 | `all.set [epoch 6]` |
| sub-11 | ses-07 | `all.set [epoch 7]` |
| sub-11 | ses-08 | `all.set [epoch 8]` |
| sub-11 | ses-09 | `all.set [epoch 9]` |
| sub-11 | ses-10 | `all.set [epoch 10]` |
| sub-11 | ses-11 | `all.set [epoch 11]` |
| sub-11 | ses-12 | `all.set [epoch 12]` |
| sub-12 | ses-01 | `all.set [epoch 1]` |
| sub-12 | ses-02 | `all.set [epoch 2]` |
| sub-12 | ses-03 | `all.set [epoch 3]` |
| sub-12 | ses-04 | `all.set [epoch 4]` |
| sub-12 | ses-05 | `all.set [epoch 5]` |
| sub-12 | ses-06 | `all.set [epoch 6]` |
| sub-12 | ses-07 | `all.set [epoch 7]` |
| sub-12 | ses-08 | `all.set [epoch 8]` |
| sub-12 | ses-09 | `all.set [epoch 9]` |
| sub-12 | ses-10 | `all.set [epoch 10]` |
| sub-12 | ses-11 | `all.set [epoch 11]` |
| sub-12 | ses-12 | `all.set [epoch 12]` |
| sub-13 | ses-01 | `all.set [epoch 1]` |
| sub-13 | ses-02 | `all.set [epoch 2]` |
| sub-13 | ses-03 | `all.set [epoch 3]` |
| sub-13 | ses-04 | `all.set [epoch 4]` |
| sub-13 | ses-05 | `all.set [epoch 5]` |
| sub-13 | ses-06 | `all.set [epoch 6]` |
| sub-13 | ses-07 | `all.set [epoch 7]` |
| sub-13 | ses-08 | `all.set [epoch 8]` |
| sub-13 | ses-09 | `all.set [epoch 9]` |
| sub-13 | ses-10 | `all.set [epoch 10]` |
| sub-13 | ses-11 | `all.set [epoch 11]` |
| sub-13 | ses-12 | `all.set [epoch 12]` |
| sub-14 | ses-01 | `all.set [epoch 1]` |
| sub-14 | ses-02 | `all.set [epoch 2]` |
| sub-14 | ses-03 | `all.set [epoch 3]` |
| sub-14 | ses-04 | `all.set [epoch 4]` |
| sub-14 | ses-05 | `all.set [epoch 5]` |
| sub-14 | ses-06 | `all.set [epoch 6]` |
| sub-14 | ses-07 | `all.set [epoch 7]` |
| sub-14 | ses-08 | `all.set [epoch 8]` |
| sub-14 | ses-09 | `all.set [epoch 9]` |
| sub-14 | ses-10 | `all.set [epoch 10]` |
| sub-14 | ses-11 | `all.set [epoch 11]` |
| sub-14 | ses-12 | `all.set [epoch 12]` |
| sub-15 | ses-01 | `all.set [epoch 1]` |
| sub-15 | ses-02 | `all.set [epoch 2]` |
| sub-15 | ses-03 | `all.set [epoch 3]` |
| sub-15 | ses-04 | `all.set [epoch 4]` |
| sub-15 | ses-05 | `all.set [epoch 5]` |
| sub-15 | ses-06 | `all.set [epoch 6]` |
| sub-15 | ses-07 | `all.set [epoch 7]` |
| sub-15 | ses-08 | `all.set [epoch 8]` |
| sub-15 | ses-09 | `all.set [epoch 9]` |
| sub-15 | ses-10 | `all.set [epoch 10]` |
| sub-15 | ses-11 | `all.set [epoch 11]` |
| sub-15 | ses-12 | `all.set [epoch 12]` |
| sub-16 | ses-01 | `all.set [epoch 1]` |
| sub-16 | ses-02 | `all.set [epoch 2]` |
| sub-16 | ses-03 | `all.set [epoch 3]` |
| sub-16 | ses-04 | `all.set [epoch 4]` |
| sub-16 | ses-05 | `all.set [epoch 5]` |
| sub-16 | ses-06 | `all.set [epoch 6]` |
| sub-16 | ses-07 | `all.set [epoch 7]` |
| sub-16 | ses-08 | `all.set [epoch 8]` |
| sub-16 | ses-09 | `all.set [epoch 9]` |
| sub-16 | ses-10 | `all.set [epoch 10]` |
| sub-16 | ses-11 | `all.set [epoch 11]` |
| sub-16 | ses-12 | `all.set [epoch 12]` |
| sub-17 | ses-01 | `all.set [epoch 1]` |
| sub-17 | ses-02 | `all.set [epoch 2]` |
| sub-17 | ses-03 | `all.set [epoch 3]` |
| sub-17 | ses-04 | `all.set [epoch 4]` |
| sub-17 | ses-05 | `all.set [epoch 5]` |
| sub-17 | ses-06 | `all.set [epoch 6]` |
| sub-17 | ses-07 | `all.set [epoch 7]` |
| sub-17 | ses-08 | `all.set [epoch 8]` |
| sub-17 | ses-09 | `all.set [epoch 9]` |
| sub-17 | ses-10 | `all.set [epoch 10]` |
| sub-17 | ses-11 | `all.set [epoch 11]` |
| sub-17 | ses-12 | `all.set [epoch 12]` |
| sub-18 | ses-01 | `all.set [epoch 1]` |
| sub-18 | ses-02 | `all.set [epoch 2]` |
| sub-18 | ses-03 | `all.set [epoch 3]` |
| sub-18 | ses-04 | `all.set [epoch 4]` |
| sub-18 | ses-05 | `all.set [epoch 5]` |
| sub-18 | ses-06 | `all.set [epoch 6]` |
| sub-18 | ses-07 | `all.set [epoch 7]` |
| sub-18 | ses-08 | `all.set [epoch 8]` |
| sub-18 | ses-09 | `all.set [epoch 9]` |
| sub-18 | ses-10 | `all.set [epoch 10]` |
| sub-18 | ses-11 | `all.set [epoch 11]` |
| sub-18 | ses-12 | `all.set [epoch 12]` |
| sub-19 | ses-01 | `all.set [epoch 1]` |
| sub-19 | ses-02 | `all.set [epoch 2]` |
| sub-19 | ses-03 | `all.set [epoch 3]` |
| sub-19 | ses-04 | `all.set [epoch 4]` |
| sub-19 | ses-05 | `all.set [epoch 5]` |
| sub-19 | ses-06 | `all.set [epoch 6]` |
| sub-19 | ses-07 | `all.set [epoch 7]` |
| sub-19 | ses-08 | `all.set [epoch 8]` |
| sub-19 | ses-09 | `all.set [epoch 9]` |
| sub-19 | ses-10 | `all.set [epoch 10]` |
| sub-19 | ses-11 | `all.set [epoch 11]` |
| sub-19 | ses-12 | `all.set [epoch 12]` |
| sub-20 | ses-01 | `all.set [epoch 1]` |
| sub-20 | ses-02 | `all.set [epoch 2]` |
| sub-20 | ses-03 | `all.set [epoch 3]` |
| sub-20 | ses-04 | `all.set [epoch 4]` |
| sub-20 | ses-05 | `all.set [epoch 5]` |
| sub-20 | ses-06 | `all.set [epoch 6]` |
| sub-20 | ses-07 | `all.set [epoch 7]` |
| sub-20 | ses-08 | `all.set [epoch 8]` |
| sub-20 | ses-09 | `all.set [epoch 9]` |
| sub-20 | ses-10 | `all.set [epoch 10]` |
| sub-20 | ses-11 | `all.set [epoch 11]` |
| sub-20 | ses-12 | `all.set [epoch 12]` |
| sub-21 | ses-01 | `all.set [epoch 1]` |
| sub-21 | ses-02 | `all.set [epoch 2]` |
| sub-21 | ses-03 | `all.set [epoch 3]` |
| sub-21 | ses-04 | `all.set [epoch 4]` |
| sub-21 | ses-05 | `all.set [epoch 5]` |
| sub-21 | ses-06 | `all.set [epoch 6]` |
| sub-21 | ses-07 | `all.set [epoch 7]` |
| sub-21 | ses-08 | `all.set [epoch 8]` |
| sub-21 | ses-09 | `all.set [epoch 9]` |
| sub-21 | ses-10 | `all.set [epoch 10]` |
| sub-21 | ses-11 | `all.set [epoch 11]` |
| sub-21 | ses-12 | `all.set [epoch 12]` |
| sub-22 | ses-01 | `all.set [epoch 1]` |
| sub-22 | ses-02 | `all.set [epoch 2]` |
| sub-22 | ses-03 | `all.set [epoch 3]` |
| sub-22 | ses-04 | `all.set [epoch 4]` |
| sub-22 | ses-05 | `all.set [epoch 5]` |
| sub-22 | ses-06 | `all.set [epoch 6]` |
| sub-22 | ses-07 | `all.set [epoch 7]` |
| sub-22 | ses-08 | `all.set [epoch 8]` |
| sub-22 | ses-09 | `all.set [epoch 9]` |
| sub-22 | ses-10 | `all.set [epoch 10]` |
| sub-22 | ses-11 | `all.set [epoch 11]` |
| sub-22 | ses-12 | `all.set [epoch 12]` |
| sub-23 | ses-01 | `all.set [epoch 1]` |
| sub-23 | ses-02 | `all.set [epoch 2]` |
| sub-23 | ses-03 | `all.set [epoch 3]` |
| sub-23 | ses-04 | `all.set [epoch 4]` |
| sub-23 | ses-05 | `all.set [epoch 5]` |
| sub-23 | ses-06 | `all.set [epoch 6]` |
| sub-23 | ses-07 | `all.set [epoch 7]` |
| sub-23 | ses-08 | `all.set [epoch 8]` |
| sub-23 | ses-09 | `all.set [epoch 9]` |
| sub-23 | ses-10 | `all.set [epoch 10]` |
| sub-23 | ses-11 | `all.set [epoch 11]` |
| sub-23 | ses-12 | `all.set [epoch 12]` |
| sub-24 | ses-01 | `all.set [epoch 1]` |
| sub-24 | ses-02 | `all.set [epoch 2]` |
| sub-24 | ses-03 | `all.set [epoch 3]` |
| sub-24 | ses-04 | `all.set [epoch 4]` |
| sub-24 | ses-05 | `all.set [epoch 5]` |
| sub-24 | ses-06 | `all.set [epoch 6]` |
| sub-24 | ses-07 | `all.set [epoch 7]` |
| sub-24 | ses-08 | `all.set [epoch 8]` |
| sub-24 | ses-09 | `all.set [epoch 9]` |
| sub-24 | ses-10 | `all.set [epoch 10]` |
| sub-24 | ses-11 | `all.set [epoch 11]` |
| sub-24 | ses-12 | `all.set [epoch 12]` |
| sub-25 | ses-01 | `all.set [epoch 1]` |
| sub-25 | ses-02 | `all.set [epoch 2]` |
| sub-25 | ses-03 | `all.set [epoch 3]` |
| sub-25 | ses-04 | `all.set [epoch 4]` |
| sub-25 | ses-05 | `all.set [epoch 5]` |
| sub-25 | ses-06 | `all.set [epoch 6]` |
| sub-25 | ses-07 | `all.set [epoch 7]` |
| sub-25 | ses-08 | `all.set [epoch 8]` |
| sub-25 | ses-09 | `all.set [epoch 9]` |
| sub-25 | ses-10 | `all.set [epoch 10]` |
| sub-25 | ses-11 | `all.set [epoch 11]` |
| sub-25 | ses-12 | `all.set [epoch 12]` |
| sub-26 | ses-01 | `all.set [epoch 1]` |
| sub-26 | ses-02 | `all.set [epoch 2]` |
| sub-26 | ses-03 | `all.set [epoch 3]` |
| sub-26 | ses-04 | `all.set [epoch 4]` |
| sub-26 | ses-05 | `all.set [epoch 5]` |
| sub-26 | ses-06 | `all.set [epoch 6]` |
| sub-26 | ses-07 | `all.set [epoch 7]` |
| sub-26 | ses-08 | `all.set [epoch 8]` |
| sub-26 | ses-09 | `all.set [epoch 9]` |
| sub-26 | ses-10 | `all.set [epoch 10]` |
| sub-26 | ses-11 | `all.set [epoch 11]` |
| sub-26 | ses-12 | `all.set [epoch 12]` |
| sub-27 | ses-01 | `all.set [epoch 1]` |
| sub-27 | ses-02 | `all.set [epoch 2]` |
| sub-27 | ses-03 | `all.set [epoch 3]` |
| sub-27 | ses-04 | `all.set [epoch 4]` |
| sub-27 | ses-05 | `all.set [epoch 5]` |
| sub-27 | ses-06 | `all.set [epoch 6]` |
| sub-27 | ses-07 | `all.set [epoch 7]` |
| sub-27 | ses-08 | `all.set [epoch 8]` |
| sub-27 | ses-09 | `all.set [epoch 9]` |
| sub-27 | ses-10 | `all.set [epoch 10]` |
| sub-27 | ses-11 | `all.set [epoch 11]` |
| sub-27 | ses-12 | `all.set [epoch 12]` |
| sub-28 | ses-01 | `all.set [epoch 1]` |
| sub-28 | ses-02 | `all.set [epoch 2]` |
| sub-28 | ses-03 | `all.set [epoch 3]` |
| sub-28 | ses-04 | `all.set [epoch 4]` |
| sub-28 | ses-05 | `all.set [epoch 5]` |
| sub-28 | ses-06 | `all.set [epoch 6]` |
| sub-28 | ses-07 | `all.set [epoch 7]` |
| sub-28 | ses-08 | `all.set [epoch 8]` |
| sub-28 | ses-09 | `all.set [epoch 9]` |
| sub-28 | ses-10 | `all.set [epoch 10]` |
| sub-28 | ses-11 | `all.set [epoch 11]` |
| sub-28 | ses-12 | `all.set [epoch 12]` |
| sub-29 | ses-01 | `all.set [epoch 1]` |
| sub-29 | ses-02 | `all.set [epoch 2]` |
| sub-29 | ses-03 | `all.set [epoch 3]` |
| sub-29 | ses-04 | `all.set [epoch 4]` |
| sub-29 | ses-05 | `all.set [epoch 5]` |
| sub-29 | ses-06 | `all.set [epoch 6]` |
| sub-29 | ses-07 | `all.set [epoch 7]` |
| sub-29 | ses-08 | `all.set [epoch 8]` |
| sub-29 | ses-09 | `all.set [epoch 9]` |
| sub-29 | ses-10 | `all.set [epoch 10]` |
| sub-29 | ses-11 | `all.set [epoch 11]` |
| sub-29 | ses-12 | `all.set [epoch 12]` |
| sub-30 | ses-01 | `all.set [epoch 1]` |
| sub-30 | ses-02 | `all.set [epoch 2]` |
| sub-30 | ses-03 | `all.set [epoch 3]` |
| sub-30 | ses-04 | `all.set [epoch 4]` |
| sub-30 | ses-05 | `all.set [epoch 5]` |
| sub-30 | ses-06 | `all.set [epoch 6]` |
| sub-30 | ses-07 | `all.set [epoch 7]` |
| sub-30 | ses-08 | `all.set [epoch 8]` |
| sub-30 | ses-09 | `all.set [epoch 9]` |
| sub-30 | ses-10 | `all.set [epoch 10]` |
| sub-30 | ses-11 | `all.set [epoch 11]` |
| sub-30 | ses-12 | `all.set [epoch 12]` |

The BIDS `onset` values are derived from the EEGLAB event-marker latencies relative to each extracted epoch (MATLAB one-based samples converted to zero-based seconds). The task `duration` is 69 seconds, using the stimulus duration reported in the paper by default. The event tables preserve the original timestamp and audio filenames. `Target f/m` is interpreted as target speaker gender and `Target l/r` as target location; the source event-description JSON described those columns in reverse.

## Metadata limits

- The source `.set` files report `ref = common`; the exact reference-electrode location is not identified. The output records this value in `EEGReference`.
- The supplied raw-file history does not document software filters, so `SoftwareFilters` is `n/a`. The paper's 0.4-32 Hz filtering and average re-reference describe its preprocessed data, and were not applied here.
- The physical EEG signal units are not stated in the supplied files. `channels.tsv` therefore uses `n/a` instead of guessing a voltage unit.
- Electrode coordinates are the normalized EEGLAB template locations in the `.set` files, not participant-specific digitized measurements; their coordinate units are marked `n/a`.
- Preprocessed derivative metadata reports average re-reference and 0.4-32 Hz filtering; filter implementation details are not supplied.
- fNIRS raw-intensity units were not specified in the source, so `channels.tsv` uses `n/a`. The optode positions are the shared planar template coordinates stored in HOMER2 and were not registered to individual anatomy.

## Re-running the conversion

Install `numpy`, `scipy`, and `h5py`. First convert the EEG dataset, then append the HOMER2 fNIRS recordings:

```bash
python "新建文本文档 (2).py" "C:/Users/fengjunkai/Desktop/CuBiAAD" "C:/Users/fengjunkai/Desktop/CuBiAAD_BIDS"
python "新建文本文档 (2).py" "C:/Users/fengjunkai/Desktop/CuBiAAD" "C:/Users/fengjunkai/Desktop/CuBiAAD_BIDS" --append-nirs-source "C:/Users/fengjunkai/Desktop/新建文件夹 (7)"
```

The original database is read-only during conversion; output is written to a separate directory.
