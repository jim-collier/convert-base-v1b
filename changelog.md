<!-- markdownlint-disable MD007 -- Unordered list indentation -->
<!-- markdownlint-disable MD010 -- No hard tabs -->
<!-- markdownlint-disable MD024 -- No duplicate headings [OK with no TOC] -->
<!-- markdownlint-disable MD033 -- No inline html -->
<!-- markdownlint-disable MD041 -- First line in a file should be a top-level heading -->
<!-- markdownlint-disable MD055 -- Table pipe style [Expected: leading_and_trailing; Actual: leading_only; Missing trailing pipe] -->
# Changelog

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## v1.0.3 (unreleased) - WIP

### Other work

- Borrowed and lightly edited a copy of v2's more concise `base-definitions.sh`. [20250503]
- Updated some paths in `cicd.sh`, broke, fixed. [20250503]
- Updated `test.sh`. [20250503]
- Minor clarifications to `README.md`. [20250503]
- Moved a line in `convert-base-v1b`. [20250503]
- Removed `alias-definitions.sh` (moved contents into `base-definitions.sh`) [20250503]
- Minor edits to this file to make it more "changelog idiomatic". [20250503]

## v1.0.2 - 2026-04-26

### Added

- Added option `--from` as an alias to `--ibase`. [20260426]
- Added optional flag `--obase` (and alias `--to`), as an alternative to specifying the base as a positional argument. [20260426]

### Changed

- Minor change to the way `--version` and `--about` are shown. [20260426]
- Bug fix: `--help` produced an error. It was trying to call non-existent function `fPrint_Help()`, rather than `fHelp()` [20260426]

### Other work

- Minor additions and clarifications to README.md. [20260426]
- Updated inline help, and README.md, to reflect additional interfaces. [20260426]
- Updated testing to also test new flags. [20260426]

## `convert-base-v1b` v1.0.0 - 2026-04-25

### Notes

This is a breaking update over the previous version. As such, the exe suffix is renamed from `v1` to `v1b`. (`v2` is already being worked on.)

This rename is independent of the internal standard semantic versioning, and was intended for this reason from the start.

The rationale behind the minor but necessary breaking changes, and the version in the name, are explained in the `README.md`.

### Added

- Added bases: [20260423]
	- Base: 45email
	- Base: 64hex. Unlike the RFC variants, sorts in code point order, hex-style. (Like 32hex.)
	- Base: 48j1w. Replaces 48j1, with a different symbol set. Now accurately extends 32w.
	- Base: 64j1w. Replaces 64j1uw, with a different symbol set. Extends 32w and 48j1w.
	- Base: 128j1. Is now redefined as a left-most subset of 256j1 (and 288j1), for consistency. Extends base-62.
	- Base: 128j1w. Replaces what used to be 128j1. Extends 48j1w and 64j1w (all now consistent with 32w), but is now different than the old removed 128j1.
	- Alias: 64j1u -> 64j1.
- More base aliases. [20260425]

### Changed

- Renamed base 64j1u -> 64j1 for consistency with other bases. [20260423]
- 38username -> 39username. (Added an extra, valid username character.) [20260423]
- While older aliases still work, the advertised base names have been more streamlined and rationalized. [20260425]
- Fixed numerous minor bugs found in fuzz testing. [20260425]
- Improved help; now sorts by base #, rather than grouping them in category chunks. Added a column of whether its a standard base, pseudostandard, published, or custom (rather than aforementioned groups). [20260425]

### Removed

- Base: 48j1. Was too inconsistent with 32w as a "word-safe" base. [20260423]
- Base: 64j1uw. Was too inconsistent with 32w as a "word-safe" base. [20260423]
- Base: 128j1. Was too inconsistent with 32w as a "word-safe" base, and different than 256j1 and 288j1. [20260423]
- Removed all unadorned large custom base numbers (e.g. "128") as aliases for bases that don't have well-defined standards. [20260423]

### Other work

- Added scripting for exhaustive fuzz testing, including of base names and aliases (caught many edge-case bugs). [20260425]
- Added scripting for exhaustive fuzz testing against v2. Even in beta, v2 can accurately handle _inputs_ of all the bases, whereas testing against self is limited to the input bases this version supports. In this way, v1b can be tested against all the bases it supports. [20260425]
- Polished CI/CD/Dogfood scripts. [20260425]
- Updated README.md with better and accurate examples. [20260425]

## `convert-base-v1` v1.0.0-beta1 (unreleased) - 2026-04-17

### Changed

- Changed license from GPLv3 to GPLv2.
- Changed name from `x9convertbase1` to `convert-base-v1`.
	- This convention: `x9convertbase1` would get confusing for v2. `x9convertbase2`??

### Removed

- Removed all unused script boilerplate
- Removed base94ascii. It was causing a bug.

### Other work

- Updates to README.md.

## `x9convertbase1` v1.0.0 - 2023-10-09

### Added

- Dropped in functional, in-production script.

### Other work

- Set up basic github repo structure.

<!--
## NEXT VERSION

### Notes

### Added

### Changed

### Removed

### Other work
-->