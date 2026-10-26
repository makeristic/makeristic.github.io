# Makeristic repository hygiene review

Reviewed on 26 October 2026 using the GitHub CLI, complete repository clones, project history, existing READMEs, KiCad source files and exported documents. All 11 repositories were created between October and November 2020. STUSB4500 Breakout also received a README update in January 2023.

## Blocked on me

Michael authorised source corrections and merging after review. Repository maintenance does not certify these historical designs as ready to manufacture: unresolved electrical, assembly and mechanical findings still require engineering work and physical validation.

Two repositories cannot yet advertise a blanket reuse licence: the upstream MachXO2 hardware design has no identified licence grant, and the collected KiCad library lacks complete per-asset provenance. Clarifying those terms requires upstream/provider evidence; Michael's MIT grant cannot cover other authors' work.

## Changed

- Cloned all 11 public repositories into the workspace and inspected their structure, history, available design/manufacturing files and licence notices.
- Updated each repository's GitHub description and relevant search topics. Metadata and reviewed file corrections are tracked in the individual PRs below.
- Expanded READMEs with concrete project identities, status, source/PDF/BOM/Gerber navigation where present, legacy KiCad setup, library dependencies and contribution guidance.
- Preserved existing photos, renders, project history, attribution and licence grants. Added full licence files or restored the upstream licence where its terms were established.
- Added MIT for Michael Cutler's original material in CurrentSensor, Feather STM32WB55 and this catalogue repository, with third-party exclusions.
- Added minimal ignore rules for generated KiCad state where appropriate, restored required symbol caches and project-local library registration, and retained upstream licence/provenance notices.
- Corrected the badge firmware APIs and malformed zero-length outlines, the shared STM32WL55 ground-pad definition and footprint/model references, the STM32WB55 short and component-reference inconsistencies, and the MachXO2 package/DebugEdge schematic mappings. Individual reports specify exactly what changed and how it was checked.
- Added the [project catalogue](../README.md) and replaced the deployed website placeholder with a static directory linking every project. The existing GitHub Pages publishing configuration is retained.

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

This catalogue repository's PR carries the public directory and this review. Each PR describes its metadata changes, source corrections, evidence, licence scope and validation. Each project also has a `docs/code-audit-report.md` report.

## Found

### Reuse and licensing

The badges already explicitly used CC BY-SA 4.0, and STUSB4500 Breakout already used CC BY 4.0. Both Feather templates derive from arturo182's work in KiCad/kicad-templates PR #23; the source revision supplies CC BY-SA 4.0 with the KiCad library exception. These terms are preserved rather than replaced with MIT.

The MachXO2 repository is a fork of chickadee-tech's design, with Scott Shawcroft and Mark Olsson in its upstream history. Its library submodules have separate CC BY 4.0 and Solderpad 2.1 terms; those do not establish a licence for the top-level design. The Makeristic library credits GitWellBack's KiCad symbol contribution and contains other imported symbols/models without a complete provenance inventory.

### Reproducibility and fabrication

- **CurrentSensor:** schematic-only concept, with unannotated references, unassigned footprints, floating amplifier supply/shutdown pins and unresolved range-switch/controller integration. The restored cache enables loading and ERC; the circuit still has actual errors. No PCB, firmware or measured ranges are supplied.
- **STM32WB55 Feather:** a ground via overlapping the D10 trace was moved and checked against a refilled baseline; the short disappears without new violations or unconnected items. Symbol/footprint recovery and reference corrections improve reproducibility. Historical notes specify a 1 mm board, while both project and PCB settings record 1.6 mm; no physical stackup was guessed. CircuitPython remains a goal, and manufacturing exports are historical.
- **MachXO2:** the invalid `LCMXO2-1200HC-4MG132I` suggestion was corrected to the manufacturer-documented QFN-32 `LCMXO2-1200HC-4SG32I`. DebugEdge schematic connections were repaired to match the existing PCB and connector pinout. The [Lattice datasheet](https://www.latticesemi.com/view_document?document_id=38834) and [migration/pinout data](https://www.latticesemi.com/view_document?document_id=51687) support the package/pin checks. Upstream design licensing and complete hardware validation remain unresolved.
- **HallowBadges:** the original notes describe manufactured boards. The corrected standalone firmware compiles against a pinned MicroCore toolchain, restored caches enable fresh schematic/netlist checks, and malformed outline primitives are removed. BOM resistor/LED values, battery-holder identity and original fuses remain incomplete. H1/H2 have no PCB footprints, local decoupling is absent, and the coin-cell/external supply lacks isolation. The README now requires removing the battery before external/ISP power. Copper artwork clearance needs fabricator review.
- **Feather templates:** unrouted starting layouts, not finished boards. Connector-net partitions match the PCBs. USB-C VBUS and ground are assigned, while CC/data circuitry remains unfinished. Mounting geometry, legacy models and modern DRC findings are documented rather than silently changed.
- **KiCad library:** STM32WL55 exposed VSS now maps to pad 49; six default footprint IDs and ten model references are corrected. Two referenced 3D models remain missing, and one symbol has no supplied footprint. Manufacturer pinout/land-pattern verification and per-asset licence inventory remain incomplete.
- **STUSB4500:** a critical supply issue ties the internal decoupling-only `VREG_2V7` output to the host VCC rail; the RGB indicator also needs a voltage-domain review before operation at higher negotiated voltages. Correcting those requires a reviewed power/routing revision. No new manufacturing release is claimed. Historical fabrication files exist, but no standalone BOM, configuration software or electrical test results are supplied.

### Validation and limits

Validation includes local documentation links/images, Git whitespace/diff review, licence provenance/content, live GitHub metadata and reviewed PR heads. KiCad nightly **10.99.0** parses restored legacy caches and produces ERC, DRC, netlists and temporary renders; its findings are recorded rather than suppressed. Cache-only schematic exports are compared with saved netlists/PCB pin-connectivity groups where annotation permits. An independent check reproduced a nightly discrepancy: registering historical global symbol libraries causes the exporter to omit the STUSB4500/STM32WB55 USB shield pin, while cache-only loading preserves it. The reports specify that limitation; a general modern-import equivalence claim is not made. The exact badge sketch also compiles independently with Arduino CLI **1.5.1**, MicroCore **2.5.2** and AVR GCC **7.3.0**, using 706 bytes flash and 4 bytes static SRAM.

The public directory was checked in a browser at desktop and mobile widths, including keyboard navigation, anchors, contrast and all repository links. No physical boards were available. Electrical/RF performance, manufacturing qualification, complete Gerber equivalence, firmware upload/fuse programming and a supported modern-format migration are not confirmed. Historical fabrication exports are labelled accordingly; source corrections are not presented as a production release.

### Proposed next steps

These remain after the repository corrections and source audit:

1. Add an organisation profile README in a new `.github` repository and pin the most representative projects, using this catalogue as its starting point.
2. Add a photographic gallery and board-specific GitHub social previews; the public project directory is now implemented.
3. Reconstruct known-built revisions with Michael's build notes, exact orderable BOMs, firmware/toolchain settings and test results. Publish versioned manufacturing releases only once their artefacts and revision are verified together.
4. Resolve the STUSB4500 supply/indicator voltage domains, STM32WB55 physical stackup, remaining DRC/assembly findings and the incomplete sensor circuit in validated hardware revisions.
5. Complete the library provenance inventory and obtain a clear upstream licence for the MachXO2 design.

No repositories were renamed or archived, no manufacturing release tags were invented, and no CI jobs were added that would imply hardware verification. No checks or security protections were bypassed when merging reviewed changes.
