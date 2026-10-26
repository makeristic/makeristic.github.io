# Makeristic repository hygiene review

Reviewed on 26 October 2026 using the GitHub CLI, complete repository clones, project history, existing READMEs, KiCad source files and exported documents. All 11 repositories were created between October and November 2020. STUSB4500 Breakout also received a README update in January 2023.

## Blocked on me

No blocker prevents the documentation and metadata updates. The PRs need Michael's review and merge.

Two repositories cannot yet advertise a blanket reuse licence: the upstream MachXO2 hardware design has no identified licence grant, and the collected KiCad library lacks complete per-asset provenance. Clarifying those terms requires upstream/provider evidence; Michael's MIT grant cannot cover other authors' work.

## Changed

- Cloned all 11 public repositories into the workspace and inspected their structure, history, available design/manufacturing files and licence notices.
- Updated each repository's GitHub description and relevant search topics. These metadata changes are live; file changes remain in the individual PRs below.
- Expanded READMEs with concrete project identities, status, source/PDF/BOM/Gerber navigation where present, legacy KiCad setup, library dependencies and contribution guidance.
- Preserved existing photos, renders, project history, attribution and licence grants. Added full licence files or restored the upstream licence where its terms were established.
- Added MIT for Michael Cutler's original material in CurrentSensor, Feather STM32WB55 and this catalogue repository, with third-party exclusions.
- Added minimal ignore rules for generated KiCad state where appropriate. Board, schematic, BOM, model and fabrication data are unchanged.
- Added the [project catalogue](../README.md), which lists every repository and its purpose. The original website entry point is preserved.

### Pull requests

- [CurrentSensor #1](https://github.com/makeristic/CurrentSensor/pull/1)
- [HallowBadges Bat #1](https://github.com/makeristic/HallowBadges-Bat/pull/1)
- [HallowBadges Ghost #1](https://github.com/makeristic/HallowBadges-Ghost/pull/1)
- [HallowBadges Pumpkin #1](https://github.com/makeristic/HallowBadges-Pumpkin/pull/1)
- [Adafruit Feather template #1](https://github.com/makeristic/Adafruit_Feather/pull/1)
- [Adafruit Feather USB-C template #1](https://github.com/makeristic/Adafruit_Feather_USB-C/pull/1)
- [Makeristic KiCad Library #1](https://github.com/makeristic/Makeristic-KiCad-Library/pull/1)
- [STUSB4500 Breakout #1](https://github.com/makeristic/STUSB4500_Breakout/pull/1)
- [Feather STM32WB55 #1](https://github.com/makeristic/Feather_STM32WB55/pull/1)
- [STEMMA MachXO2 #1](https://github.com/makeristic/stemma-machxo32/pull/1)

This catalogue repository's PR carries the directory and this review. Each PR describes its metadata changes, evidence, licence scope and validation.

## Found

### Reuse and licensing

The badges already explicitly used CC BY-SA 4.0, and STUSB4500 Breakout already used CC BY 4.0. Both Feather templates derive from arturo182's work in KiCad/kicad-templates PR #23; the source revision supplies CC BY-SA 4.0 with the KiCad library exception. These terms are preserved rather than replaced with MIT.

The MachXO2 repository is a fork of chickadee-tech's design, with Scott Shawcroft and Mark Olsson in its upstream history. Its library submodules have separate CC BY 4.0 and Solderpad 2.1 terms; those do not establish a licence for the top-level design. The Makeristic library credits GitWellBack's KiCad symbol contribution and contains other imported symbols/models without a complete provenance inventory.

### Reproducibility and fabrication

- **CurrentSensor:** schematic-only concept, with unannotated references, unassigned footprints and unresolved range-switch/controller integration. No PCB, firmware or measured ranges are supplied.
- **STM32WB55 Feather:** historical notes specify a 1 mm board, while the PCB records 1.6 mm. The external STM32 symbol/footprint library is absent, and CircuitPython remains a goal rather than a supplied port.
- **MachXO2:** the schematic's suggested `LCMXO2-1200HC-4MG132I` part is a 132-lead csBGA, while its symbol/footprint and PCB use QFN-32. The mismatch needs an electrical/design review before procurement. The [Lattice datasheet](https://www.latticesemi.com/-/media/LatticeSemi/Documents/DataSheets/MachXO23/FPGA-DS-02056-4-6-MachXO2-Family-Data-Sheet.ashx?document_id=38834) identifies the part's package.
- **HallowBadges:** the original READMEs describe manufactured boards, but BOM resistor/LED entries are generic and the README-only firmware example has no recorded Arduino core version or fuse settings.
- **Feather templates:** starting layouts with no routed tracks. The USB-C template still needs VBUS/data/CC circuitry.
- **KiCad library:** two referenced 3D models are missing, and several paths depend on `eec.models`. Imported symbols also need explicit footprint assignment.
- **STUSB4500:** historical fabrication files are present, but no standalone BOM, configuration software or confirmed electrical test results are supplied.

### Validation and limits

Validation covers 102 local Markdown links/images across the repositories, Git whitespace checks, diff review, licence provenance/content, live GitHub metadata and clean/pushed PR branches. KiCad is not installed in the workspace, and no physical boards were available. Current electrical performance, current KiCad migration, ERC/DRC, RF performance, manufacturing export consistency and firmware builds were not confirmed. The source files, PDFs, existing notes and available configuration were inspected for what they establish.

### Proposed next steps

These require separate work and are not part of this documentation update:

1. Add an organisation profile README in a new `.github` repository and pin the most representative projects, using this catalogue as its starting point.
2. Replace the website's “Hello World” page with a public project gallery and add board photos as GitHub social previews.
3. Reconstruct known-built revisions with Michael's build notes, exact orderable BOMs, firmware/toolchain settings and test results. Publish versioned manufacturing releases only once their artefacts and revision are verified together.
4. Resolve the FPGA package and STM32WB55 stackup discrepancies in design-focused PRs.
5. Complete the library provenance inventory and obtain a clear upstream licence for the MachXO2 design.

No repositories were renamed or archived, no release tags were invented, and no CI jobs were added that would imply hardware verification.
