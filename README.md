# Makeristic — hobby electronics and KiCad projects

Michael Cutler's collection of electronics projects, started in 2020: microcontroller boards, USB Power Delivery, an FPGA breakout, Halloween LED badges, KiCad templates and a component library.

This catalogue links all 11 public repositories in the [Makeristic organisation](https://github.com/orgs/makeristic/repositories). Each project's own README describes its design status, available manufacturing files and licence. The collection includes unfinished designs and upstream-derived work; a repository's presence here does not imply a tested or production-ready board.

The [repository hygiene review](docs/repository-hygiene.md) records the October 2026 source corrections, known reproducibility gaps and proposed next steps. Each hardware repository also has a source audit report; read it before using historical manufacturing exports.

## Boards and circuits

- **[STUSB4500 Breakout](https://github.com/makeristic/STUSB4500_Breakout)** — USB-C Power Delivery sink breakout with an STUSB4500 controller and STEMMA QT interface. Includes KiCad sources, schematic PDF, board renders and fabrication files. The repository is marked as work in progress.
- **[Feather STM32WB55](https://github.com/makeristic/Feather_STM32WB55)** — work-in-progress STM32WB55 Feather-format wireless microcontroller board. Includes KiCad sources, a BOM, schematic PDF, Gerbers, board images and CubeMX configuration.
- **[STEMMA MachXO2](https://github.com/makeristic/stemma-machxo32)** — STEMMA QT FPGA board design for a Lattice MachXO2 in a 32-pin QFN package. Forked from [chickadee-tech/stemma-machxo32](https://github.com/chickadee-tech/stemma-machxo32); retains its upstream provenance and library submodules.
- **[CurrentSensor](https://github.com/makeristic/CurrentSensor)** — unfinished STM32F042 USB-C current measurement schematic with a MAX4239 analogue front end and an I²C connector labelled STEMMA QT. Includes a schematic and PDF; no PCB layout or firmware.

## HallowBadges

Three ATtiny13A Halloween LED badge designs. Their repositories include KiCad sources, BOMs, schematic PDFs, historical fabrication files, board images and a downloadable Arduino sketch with a pinned compilation configuration. The original project notes describe manufactured boards.

- **[Bat](https://github.com/makeristic/HallowBadges-Bat)** — bat-shaped badge.
- **[Ghost](https://github.com/makeristic/HallowBadges-Ghost)** — ghost-shaped badge, including an assembled-board photo.
- **[Pumpkin](https://github.com/makeristic/HallowBadges-Pumpkin)** — pumpkin-shaped badge.

## KiCad templates and parts

- **[Adafruit Feather template](https://github.com/makeristic/Adafruit_Feather)** — legacy KiCad template for Feather-compatible boards, derived from arturo182's template work.
- **[Adafruit Feather USB-C template](https://github.com/makeristic/Adafruit_Feather_USB-C)** — USB-C variant of the Feather board template, with the same upstream lineage.
- **[Makeristic KiCad Library](https://github.com/makeristic/Makeristic-KiCad-Library)** — collected and customised legacy symbols, footprints and 3D models used by the board projects. Check individual assets' provenance and terms before redistribution.

## This repository

**[makeristic.github.io](https://github.com/makeristic/makeristic.github.io)** holds this catalogue and the [public project directory](https://makeristic.github.io/). GitHub Pages publishes the static [index.html](index.html) from `main` at the repository root. It links every project, works without JavaScript or a build system, and includes search/social metadata, a sitemap and crawler guidance. The [website audit](docs/code-audit-report.md) records the source and browser checks.

```sh
gh repo list makeristic --limit 1000
gh repo clone makeristic/REPOSITORY_NAME
```

Replace `REPOSITORY_NAME` with one of the names above. For the FPGA fork, follow its README's submodule instructions as well.

## Working with the designs

These are legacy KiCad projects from 2020. Start with the schematic PDF and images where available; then read the project's README for the original KiCad version, required libraries and missing files. Work on a copy when importing into a newer KiCad version. Manufacturing exports are historical snapshots and should be checked against the source before ordering boards.

Report design-specific questions in the relevant repository's issues, with the board revision, KiCad version, affected components and useful measurements or screenshots. Use [this repository's issues](https://github.com/makeristic/makeristic.github.io/issues) for catalogue corrections.

## Licences and attribution

There is no single licence for the whole collection:

- The three HallowBadges retain their existing **CC BY-SA 4.0** terms.
- STUSB4500 Breakout retains its existing **CC BY 4.0** terms.
- The Feather templates retain the upstream **CC BY-SA 4.0 with the KiCad library exception** terms and arturo182's attribution.
- Feather STM32WB55 and CurrentSensor use **MIT** for Michael Cutler's original material, with third-party material excluded.
- The MachXO2 fork and collected KiCad library require attention to upstream/individual asset terms; they are not blanket relicensed here.

The original content of **this catalogue repository** is under the [MIT licence](LICENSE). It grants no rights to linked projects, vendor datasheets, imported CAD libraries, trademarks or other third-party material. Read each project's own licence and notices before reuse.
