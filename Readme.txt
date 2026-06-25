# GFSW Downloader

Python downloader for GFS Wave forecast files and NOAA sea ice analysis files. The repository contains separate scripts for sea ice concentration and global wave model GRIB2 downloads.

## Objective

Automate downloads for ocean-related NOAA products:

- Sea ice analysis at 5-minute resolution.
- GFS Wave global forecast fields at 0.25 degree resolution.

## Repository Structure

```text
GFSW_Downloader/
├── Readme.txt
└── Descarga/
    ├── Descarga_AUTO_GFS_Sea_Ice_0083.py
    ├── Descarga_AUTO_GFS_Sea_Waves_025.py
    ├── Archivo de hielo/
    │   └── seaice.t00z.5min.grb.grib2
    └── Archivos/
        └── gfswave.t00z.global.0p25.f000.grib2
```

## Scripts

### `Descarga_AUTO_GFS_Sea_Ice_0083.py`

Downloads the daily NOAA sea ice analysis file:

```text
seaice.t00z.5min.grb.grib2
```

The script:

- Uses the current UTC date.
- Deletes previous `.grib2` files from `Descarga/Archivo de hielo/`.
- Downloads the current `t00z` sea ice analysis file.

### `Descarga_AUTO_GFS_Sea_Waves_025.py`

Downloads global GFS Wave forecast files:

- Forecast cycle: current UTC `00Z` or `12Z`.
- Forecast lead times: `f000` through `f078`.
- Resolution: global `0p25`.
- Format: GRIB2.

The script clears previous wave files from `Descarga/Archivos/` before downloading the new set.

## Data Sources

Sea ice analysis:

```text
https://nomads.ncep.noaa.gov/pub/data/nccf/com/seaice_analysis/prod/
```

GFS Wave:

```text
https://nomads.ncep.noaa.gov/pub/data/nccf/com/gfs/prod/
```

## Technologies Used

- Python 3
- requests

## Installation

Clone the repository:

```bash
git clone https://github.com/fabriciolopretto/GFSW_Downloader.git
cd GFSW_Downloader/Descarga
```

Install dependencies:

```bash
pip install requests
```

## Usage

Download sea ice analysis:

```bash
python Descarga_AUTO_GFS_Sea_Ice_0083.py
```

Download GFS Wave forecast files:

```bash
python Descarga_AUTO_GFS_Sea_Waves_025.py
```

## Output

Sea ice files are saved to:

```text
Descarga/Archivo de hielo/
```

Wave files are saved to:

```text
Descarga/Archivos/
```

## Notes

Both scripts remove previous files from their output folders before downloading the current product.

Availability depends on NOAA/NCEP publication timing. If a selected run has not been published yet, some files may be missing or empty.

