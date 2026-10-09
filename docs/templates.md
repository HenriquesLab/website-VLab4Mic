# Templates

VLab4Mic ships with pre-configured templates for common structures, probes, virtual samples, and imaging modalities. These are ready to use in both notebooks and Python scripts.

---

## Structures

Any atomic structure in PDB or CIF format can be used with VLab4Mic. The package
includes YAML templates and example IDs for the structures below; the
corresponding CIF files are downloaded on first use and cached in
`~/.vlab4mic/structures` unless `VLAB4MIC_STRUCTURE_DIR` is set.

| Structure ID | Description | Database | Format |
| --- | --- | --- | --- |
| **1XI5** | Clathrin D6 coat with auxilin J-domain | RCSB | CIF |
| **7R5K** | Human nuclear pore complex (constricted) | RCSB | CIF |
| **3J3Y** | Atomic-level structure of the entire HIV-1 capsid (186 hexamers + 12 pentamers) | RCSB | CIF |
| **8GMO** | Bacteriophage T4 capsid shell | RCSB | CIF |

---

## Probes

Probes are configuration files that model a specific type of fluorescent labelling. Pass the probe name as `probe_template` in `image_vsample`.

### Structure-Independent Probes

These probes work with any atomic structure. Specify your target using `probe_target_type` and `probe_target_value`.

| Probe name | Description | Probe model |
| --- | --- | --- |
| **NHS_ester** | Direct label targeting lysine (LYS) residues | — |
| **Linker** | Indirect label modelled as a rigid spacer | — |
| **Antibody** | Indirect label based on an IGG antibody (anti-HIV-1) | 1HZH |
| **Nanobody** | Indirect label based on a synthetic nanobody | 7MFV |
| **GFP** | Indirect label based on GFP crystal structure | 6YLQ |
| **GFP_w_nanobody** | Indirect label based on a nanobody–eGFP complex | 6XZF |
| **mMaple** | Indirect label based on the mTFP1 fluorescent protein | 2HQK |
| **SNAP-tag** | Indirect label based on SNAP-tag with conjugated fluorophore | 6Y8P |
| **Halo-tag** | Indirect label based on HaloTag with conjugated fluorophore | 5UXZ |

Probe templates set the wobble (`binding.wobble_range.theta`, degrees; 10 for the antibody and nanobody probes) and the mean tilt (`binding.tilt`, degrees; 0 by default). Probe distances (`binding.distance`) are in Å.

### Structure-Specific Probes

Pre-configured probes tuned to particular structures.

| Probe name | Description | Target | Probe model | Structure |
| --- | --- | --- | --- | --- |
| **CCP_heavy_chain_Cterminal** | Direct probe for C-terminal of Clathrin Heavy Chain | `EQATETQ` | — | 1XI5 |
| **NPC_Nup96_Cterminal_direct** | Direct probe for C-terminal of Nup96 in the NPC | `ELAVGSL` | — | 7R5K |
| **HIV_capsid_p24_direct** | Direct probe for HIV-1 Capsid monomer (p24) | `SPRTLNA` | — | 3J3Y |
| **anti-p24_primary_antibody_HIV** | Antibody targeting HIV-1 Capsid monomer (p24) | `SPRTLNA` | 1HZH | 3J3Y |

---

## Virtual Sample Templates

| Template name | Description |
| --- | --- |
| **square1x1um_randomised** | Square field of view with a single particle placed in the centre |

---

## Modalities

| Modality | Description | PSF shape XYZ (nm) | Pixel size (nm) |
| --- | --- | --- | --- |
| **Widefield** | Widefield epifluorescence | 130 × 130 × 400 | 100 |
| **Confocal** | Laser scanning confocal | 100 × 100 × 300 | 70 |
| **AiryScan** | Zeiss AiryScan detector (narrower Gaussian, no pixel reassignment) | 60 × 60 × 230 | 40 |
| **STED** | 2D STED (effective resolution, no depletion physics) | 20 × 20 × 300 | 15 |
| **SMLM** | Single-molecule localisation: localisations (precision 5 nm, 5 per emitter) rendered without PSF convolution | 8 × 8 × 8 (emitters only) | 2 |

The PSF widths are the effective resolution of each method, a user input; set them to the values measured on your instrument with `update_modality`.
| **Reference** | Idealised diffraction-limited reference | 5 × 5 × 5 | 5 |
