<!-- markdownlint-disable MD007 -- Unordered list indentation -->
<!-- markdownlint-disable MD010 -- No hard tabs -->
<!-- markdownlint-disable MD024 -- No duplicate headings [OK with no TOC] -->
<!-- markdownlint-disable MD033 -- No inline html -->
<!-- markdownlint-disable MD041 -- First line in a file should be a top-level heading -->
<!-- markdownlint-disable MD055 -- Table pipe style [Expected: leading_and_trailing; Actual: leading_only; Missing trailing pipe] -->
# Changelog

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## v1.0.5 (unreleased) - 2026-05-03

### Other work

- Minor edits to this file to make it more "changelog idiomatic".

## v1.0.4 (unreleased) - 2026-05-03

### Other work

- Borrowed and lightly edited a copy of v2's more concise `base-definitions.sh`
- Updated some paths in `cicd.sh`, broke, fixed.
- Updated `test.sh`.
- Minor clarifications to `README.md`.
- Moved a line in `convert-base-v1b`.
- Removed `alias-definitions.sh` (moved contents into `base-definitions.sh`)

## v1.0.2 - 2026-04-26

### Changed

- Minor change to the way `--version` and `--about` are shown.

### Other work

- Minor additions and clarifications to README.md.

## v1.0.1 - 2026-04-26

### Notes

`v1.0.1`, as the semantic version would suggest, is 100% backwards-compatible with `v1.0.0`. Nothing from the former interface or input/output has changed, only a bugfix and new option aliases added.

### Added

- Added option `--from` as an alias to `--ibase`.

- Added optional flag `--obase` (and alias `--to`), as an alternative to specifying the base as a positional argument.

### Changed

- Bug fix: `--help` produced an error. It was trying to call non-existent function `fPrint_Help()`, rather than `fHelp()`

### Other work

- Updated inline help, and README.md, to reflect additional interfaces.
- Updated testing to also test new flags.

## v1.0.0 - 2026-04-25

### Notes

This contains changes made through v1.0.0-beta1 and to release v1.0.0.

### Added

- More base aliases.

### Changed

- While older aliases still work, the advertised base names have been more streamlined and rationalized.

- Fixed numerous minor bugs found in fuzz testing.

- Improved help; now sorts by base #, rather than grouping them in category chunks. Added a column of whether its a standard base, pseudostandard, published, or custom (rather than aforementioned groups).

### Other work

- Added scripting for exhaustive fuzz testing, including of base names and aliases (caught many edge-case bugs).

- Added scripting for exhaustive fuzz testing against v2. Even in beta, v2 can accurately handle _inputs_ of all the bases, whereas testing against self is limited to the input bases this version supports. In this way, v1b can be tested against all the bases it supports.

- Polished CI/CD/Dogfood scripts.

- Updated README.md with better and accurate examples.

## `convert-base-v1b` v1.0.0-beta1 (unreleased) - 2026-04-23

### Notes

This is a breaking update over the previous version. As such, the exe suffix is renamed from `v1` to `v1b`. (`v2` is already being worked on.)

This rename is independent of the internal standard semantic versioning, and was intended for this reason from the start.

The rationale behind the minor but necessary breaking changes, and the version in the name, are explained in the `README.md`.

### Added

- Base: 45email
- Base: 64hex. Unlike the RFC variants, sorts in code point order, hex-style. (Like 32hex.)
- Base: 48j1w. Replaces 48j1, with a different symbol set. Now accurately extends 32w.
- Base: 64j1w. Replaces 64j1uw, with a different symbol set. Extends 32w and 48j1w.
- Base: 128j1. Is now redefined as a left-most subset of 256j1 (and 288j1), for consistency. Extends base-62.
- Base: 128j1w. Replaces what used to be 128j1. Extends 48j1w and 64j1w (all now consistent with 32w), but is now different than the old removed 128j1.
- Alias: 64j1u -> 64j1.

### Changed

- Renamed base 64j1u -> 64j1 for consistency with other bases.
- 38username -> 39username. (Added an extra, valid username character.)

### Removed

- Base: 48j1. Was too inconsistent with 32w as a "word-safe" base.
- Base: 64j1uw. Was too inconsistent with 32w as a "word-safe" base.
- Base: 128j1. Was too inconsistent with 32w as a "word-safe" base, and different than 256j1 and 288j1.
- Removed all unadorned large custom base numbers (e.g. "128") as aliases for bases that don't have well-defined standards.

### Other work

- Added optional testing and CI/CD scripts.

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