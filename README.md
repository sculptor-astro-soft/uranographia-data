# Uranographia data

Star packs for **Uranographia**, the classic star atlas app for Android by
[Sculptor Astro Soft](https://github.com/sculptor-astro-soft).

Uranographia includes every star down to visual magnitude V = 11. Fainter stars
come as optional downloads, one whole-sky pack per magnitude band, which the app
lists and downloads from the releases of this repository. Once downloaded, the
packs work offline.

## Packs (release `packs-v1`)

| File | Band (V) | Stars | Size |
|---|---|---|---|
| `stars_v11-12.uast` | 11 – 12 | 1,395,831 | 7.0 MB |
| `stars_v12-13.uast` | 12 – 13 | 3,242,784 | 16.3 MB |
| `stars_v13-14.uast` | 13 – 14 | 7,135,629 | 35.7 MB |
| `stars_v14-15.uast` | 14 – 15 | 14,993,708 | 75.0 MB |

`manifest.json` lists each pack with its band, number of stars, size and SHA-256
checksum.

## Source

Stars from **Gaia Data Release 3** (ESA/Gaia/DPAC). Visual magnitude V is
computed from Gaia G and BP−RP with the relation of Riello et al. (2021,
A&A 649, A3, Table C.2); stars without colour use V = G.

## Format

Little-endian binary file:

- Header: `UAST`, version (uint16 = 2), cell size in degrees (uint16 = 2),
  lower and upper V limits of the band (float32 each).
- Number of cells (int32; 180 in RA × 90 in Dec), followed by the offset of
  each cell's first star (int32 each, plus one final value with the total).
- Stars: 5 bytes each, sorted by brightness within each cell. RA and Dec are
  stored as uint16 offsets from the cell corner (resolution 0.11″), V as uint8
  in hundredths of a magnitude above the band's lower limit.

## Licence and credit

The packs are derived from Gaia DR3 data and are distributed under the
**Creative Commons Attribution-ShareAlike 3.0 IGO** licence
(CC BY-SA 3.0 IGO), as the Gaia data are.

This work has made use of data from the European Space Agency (ESA) mission
[Gaia](https://www.cosmos.esa.int/gaia), processed by the Gaia Data Processing
and Analysis Consortium
([DPAC](https://www.cosmos.esa.int/web/gaia/dpac/consortium)). Funding for the
DPAC has been provided by national institutions, in particular the institutions
participating in the Gaia Multilateral Agreement.
