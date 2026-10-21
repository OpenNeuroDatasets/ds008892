# Native fNIRS source files (not BIDS-NIRS)

These files are preserved byte-for-byte from the supplied database. Although
their source filenames end in `.tsv`, their contents are NIRSPARK device data,
not tab-separated text and not SNIRF. They are therefore kept under `sourcedata`
and are not presented as converted BIDS fNIRS recordings. Export the recordings
from the vendor software to valid SNIRF (`.snirf`) files, with the required
optode/channel metadata, to complete BIDS-NIRS conversion. `source_manifest.tsv`
records the original filename, byte size, and SHA-256 checksum.


These older native NIRSPARK files are retained for provenance only. The BIDS-NIRS runs for sub-31 through sub-40 were converted from the separate HOMER2 `.nirs` files under `sourcedata/homer2-nirs/`.
