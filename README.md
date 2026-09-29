# AGHRI-to-nuScenes-Style Dataset Release

This repository provides the **AGHRI dataset converted to a nuScenes-style structure** for camera, LiDAR, and multimodal perception workflows.

It contains:

- AGHRI metadata represented in a nuScenes-style structure;
- synchronization metadata for the 65 converted AGHRI scenes; and
- nine pre-generated information PKLs for full-camera, ZED–LiDAR, and fisheye–LiDAR configurations.

The large camera and LiDAR sensor files are distributed separately as **18 ZIP archives**. These archives contain the sensor data required to construct the `samples/` and `sweeps/` directories of the AGHRI-to-nuScenes-style release.

The code used for **AGHRI-to-nuScenes-style format conversion**, dataset splitting, and PKL generation is maintained separately in the **AGHRI-nuScenes-tools** repository.

## Resources

| Resource | Link |
|---|---|
| AGHRI paper preprint | [SSRN preprint](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7360013) |
| Original AGHRI dataset | [University of Lincoln Research Repository](https://doi.org/10.24385/lincoln.32982638) |
| Converted AGHRI-to-nuScenes-style metadata and PKLs | [AGHRI-nuScenes-release](https://github.com/Prabuddhi-05/AGHRI-nuScenes-release) |
| Sensor payload ZIP archives (`samples` and `sweeps`) | Link to be added |
| AGHRI-to-nuScenes conversion and PKL-generation tools | [AGHRI-nuScenes-tools](https://github.com/Prabuddhi-05/AGHRI-nuScenes-tools) |
| BEVFusion adaptation for AGHRI | [AGHRI-BEVFusion](https://github.com/Prabuddhi-05/AGHRI-BEVFusion) |

> **Important:** The camera and LiDAR payloads are distributed separately from this Git repository. Download all sensor payload ZIP archives and extract them as described below to assemble the complete AGHRI-to-nuScenes-style dataset.

---

## Repository Contents

The repository is organised as follows:

```text
AGHRI-nuScenes-release/
├── README.md
├── dataset/
│   ├── v1.0-aghri/                # AGHRI metadata in nuScenes-style tables
│   ├── metadata/
│   │   ├── synchronization/       # per-scene sensor associations
│   │   └── scene_name_map.csv     # public scene names and AGHRI recording names
│   ├── samples/                   # created by extracting the samples ZIP archives
│   └── sweeps/                    # created by extracting the sweeps ZIP archives
└── pkls/
    ├── full/
    │   └── pkls/
    ├── zed_lidar/
    │   └── pkls/
    ├── fisheye_lidar/
    │   └── pkls/
    └── RELEASE_PKL_PROVENANCE.json
```

The `dataset/v1.0-aghri/` directory contains AGHRI scene, sample, sensor, calibration, ego-pose, annotation, and related metadata represented using a nuScenes-style table structure.

The `dataset/metadata/synchronization/` directory contains the camera–LiDAR associations used during the **AGHRI-to-nuScenes-style conversion**.

The `samples/` and `sweeps/` directories are created by extracting the separately distributed sensor payload archives.

The `pkls/` directory contains the pre-generated information files for the three supported AGHRI sensor configurations and their train, validation, and test splits.

---

## Sensor Payload ZIP Archives

The sensor payload for the AGHRI-to-nuScenes-style release is distributed as:

- **8 `samples` ZIP archives**
- **10 `sweeps` ZIP archives**

Each archive is an **independent ZIP file**, rather than one segment of a multi-volume ZIP.

The archives are divided by complete AGHRI scene ranges and preserve paths beginning with:

```text
samples/
```

or:

```text
sweeps/
```

### Samples

| ZIP filename | Scenes | Files | Approx. payload size |
|---|---:|---:|---:|
| `AGHRI_nuScenes_samples_part01.zip` | 0001–0011 | 8,052 | 3.57 GB |
| `AGHRI_nuScenes_samples_part02.zip` | 0012–0020 | 9,053 | 3.48 GB |
| `AGHRI_nuScenes_samples_part03.zip` | 0021–0026 | 8,677 | 3.77 GB |
| `AGHRI_nuScenes_samples_part04.zip` | 0027–0033 | 7,853 | 3.53 GB |
| `AGHRI_nuScenes_samples_part05.zip` | 0034–0041 | 7,203 | 3.26 GB |
| `AGHRI_nuScenes_samples_part06.zip` | 0042–0049 | 8,772 | 3.63 GB |
| `AGHRI_nuScenes_samples_part07.zip` | 0050–0057 | 8,675 | 3.67 GB |
| `AGHRI_nuScenes_samples_part08.zip` | 0058–0065 | 8,188 | 3.49 GB |
| **Samples total** | | **66,473** | **28.40 GB** |

### Sweeps

| ZIP filename | Scenes | Files | Approx. payload size |
|---|---:|---:|---:|
| `AGHRI_nuScenes_sweeps_part01.zip` | 0001–0009 | 6,395 | 3.11 GB |
| `AGHRI_nuScenes_sweeps_part02.zip` | 0010–0017 | 8,406 | 3.79 GB |
| `AGHRI_nuScenes_sweeps_part03.zip` | 0018–0022 | 8,647 | 3.78 GB |
| `AGHRI_nuScenes_sweeps_part04.zip` | 0023–0029 | 7,433 | 3.57 GB |
| `AGHRI_nuScenes_sweeps_part05.zip` | 0030–0034 | 6,807 | 3.56 GB |
| `AGHRI_nuScenes_sweeps_part06.zip` | 0035–0041 | 7,289 | 3.40 GB |
| `AGHRI_nuScenes_sweeps_part07.zip` | 0042–0047 | 8,161 | 3.67 GB |
| `AGHRI_nuScenes_sweeps_part08.zip` | 0048–0052 | 7,498 | 3.35 GB |
| `AGHRI_nuScenes_sweeps_part09.zip` | 0053–0059 | 7,095 | 3.40 GB |
| `AGHRI_nuScenes_sweeps_part10.zip` | 0060–0065 | 7,101 | 3.36 GB |
| **Sweeps total** | | **74,832** | **34.98 GB** |

---

## Assemble the Complete Dataset

Download:

- all eight `AGHRI_nuScenes_samples_part*.zip` files; and
- all ten `AGHRI_nuScenes_sweeps_part*.zip` files.

The ZIP archives are provided separately from this Git repository.

Place the downloaded ZIP files in a directory of your choice. They do not need to be manually separated into `samples` and `sweeps` directories before extraction.

From the root of this repository, run:

```bash
cd /path/to/AGHRI-nuScenes-release

PARTS_DIR=/path/to/downloaded-zip-parts

shopt -s nullglob

samples=("$PARTS_DIR"/AGHRI_nuScenes_samples_part*.zip)
sweeps=("$PARTS_DIR"/AGHRI_nuScenes_sweeps_part*.zip)

if (( ${#samples[@]} == 8 && ${#sweeps[@]} == 10 )); then
    for archive in "${samples[@]}" "${sweeps[@]}"; do
        unzip -q "$archive" -d dataset/
    done
else
    printf 'Expected 8 samples ZIPs and 10 sweeps ZIPs; found %s and %s.\n' \
        "${#samples[@]}" "${#sweeps[@]}"
fi
```

Each archive already contains the appropriate `samples/` or `sweeps/` path prefix, so all archives should be extracted directly into:

```text
dataset/
```

After extraction, the complete **AGHRI-to-nuScenes-style dataset** should have the following structure:

```text
dataset/
├── samples/
│   ├── lidar/
│   ├── cam_zed_rgb/
│   ├── cam_fish_front/
│   ├── cam_fish_left/
│   └── cam_fish_right/
│
├── sweeps/
│   ├── cam_zed_rgb/
│   ├── cam_fish_front/
│   ├── cam_fish_left/
│   └── cam_fish_right/
│
├── v1.0-aghri/
└── metadata/
    ├── synchronization/
    └── scene_name_map.csv
```

### Check the Extracted Files

The complete `samples/` directory should contain:

```bash
find dataset/samples -type f | wc -l
```

```text
66473
```

The complete `sweeps/` directory should contain:

```bash
find dataset/sweeps -type f | wc -l
```

```text
74832
```

---

## PKL Variants

Nine information PKLs are provided for three AGHRI sensor configurations.

The **Train**, **Validation**, and **Test** columns below show the number of AGHRI LiDAR-anchored samples retained in each split after requiring the camera associations needed by that sensor configuration.

| Variant | Cameras used | Train samples | Validation samples | Test samples |
|---|---|---:|---:|---:|
| `full` | ZED RGB + front, left, and right fisheye | 10,468 | 1,155 | 1,260 |
| `zed_lidar` | ZED RGB | 10,780 | 1,156 | 1,264 |
| `fisheye_lidar` | front, left, and right fisheye | 10,706 | 1,183 | 1,280 |

The files are organised as:

```text
pkls/
├── full/
│   └── pkls/
│       ├── aghri_full_infos_train.pkl
│       ├── aghri_full_infos_val.pkl
│       └── aghri_full_infos_test.pkl
│
├── zed_lidar/
│   └── pkls/
│       ├── aghri_zed_lidar_infos_train.pkl
│       ├── aghri_zed_lidar_infos_val.pkl
│       └── aghri_zed_lidar_infos_test.pkl
│
└── fisheye_lidar/
    └── pkls/
        ├── aghri_fisheye_lidar_infos_train.pkl
        ├── aghri_fisheye_lidar_infos_val.pkl
        └── aghri_fisheye_lidar_infos_test.pkl
```

The PKLs use relative `lidar_path` and camera `data_path` values referring to the corresponding sensor files in the assembled AGHRI-to-nuScenes-style dataset.

For downstream use, set the dataset root to:

```text
AGHRI-nuScenes-release/dataset/
```

The assembled AGHRI-to-nuScenes-style dataset can therefore be moved or downloaded to another location without regenerating the PKLs, provided that the relative directory structure is preserved.

`pkls/RELEASE_PKL_PROVENANCE.json` records the release information and checksums for the distributed PKL files.

---

## Dataset Metadata

The **AGHRI-to-nuScenes-style conversion** contains **65 scenes** and uses a fixed sequence-level train, validation, and test split.

The `v1.0-aghri/` directory contains the AGHRI metadata represented using the following nuScenes-style table organisation:

```text
category.json
attribute.json
visibility.json
sensor.json
calibrated_sensor.json
ego_pose.json
log.json
scene.json
sample.json
sample_data.json
instance.json
sample_annotation.json
map.json
splits.json
camera_model.json
```

The synchronization directory contains one sensor-association file for each AGHRI scene included in the conversion:

```text
metadata/
└── synchronization/
    ├── aghri-scene-0001_sync.json
    ├── aghri-scene-0002_sync.json
    └── ...
```

`scene_name_map.csv` maps each public `aghri-scene-XXXX` identifier used in the AGHRI-to-nuScenes-style release to its corresponding original AGHRI recording name.

---

## Using the Converted Dataset

After extracting all sensor ZIP archives, use:

```text
AGHRI-nuScenes-release/dataset/
```

as the dataset root.

The assembled release then contains the **AGHRI data represented in a nuScenes-style dataset structure**, including the metadata, synchronized camera and LiDAR sensor data, and supporting metadata referenced by the provided PKLs.

For **AGHRI-to-nuScenes-style format conversion**, PKL generation, dataset splits, and detailed format documentation, use:

[AGHRI-nuScenes-tools](https://github.com/Prabuddhi-05/AGHRI-nuScenes-tools.git)

The converted AGHRI metadata and pre-generated PKLs are maintained in:

[AGHRI-nuScenes-release](https://github.com/Prabuddhi-05/AGHRI-nuScenes-release.git)

---

## AGHRI Dataset and Citation

This **AGHRI-to-nuScenes-style release** is derived from:

**AGHRI: A dataset for multimodal robot perception of humans in agricultural and off-road environments**

- **Original dataset:** [University of Lincoln Research Repository](https://doi.org/10.24385/lincoln.32982638)
- **Submitted manuscript / preprint:** [SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7360013)

The original AGHRI release provides the camera, LiDAR, calibration, pose, metadata, and annotation data used to prepare this **AGHRI-to-nuScenes-style representation**.

When using this release, please cite the original AGHRI dataset and the associated manuscript where appropriate. Use the dataset and manuscript pages for the current author list, dataset version, and preferred citation information.
