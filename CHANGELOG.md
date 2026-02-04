# Changelog

All notable changes to the **HTML implementation** will be documented in this file.

Protocol/spec changes belong in the canonical repo:
- [schiavinato-sharing](https://github.com/GRIFORTIS/schiavinato-sharing)

## Unreleased

- (no changes)

## 0.4.0 - 2026-01-31

This repo begins at **v0.4.0**. Earlier history for the HTML reference implementation lived in the canonical repo under `reference-implementation/`.

### Added
- Repo reorg: migrated the single-file HTML implementation and Playwright test suite into `schiavinato-sharing-html/`.
- DevSecOps automation: CI, CodeQL, and signed release workflows.

### Changed
- Implemented dual-path checksum validation and explicit path mismatch surfacing (implementation behavior; see canonical changelog for the normative spec notes).
- Implemented Global Integrity Check (GIC) binding to share number `x` (printed GIC = sum + x mod 2053).
- Terminology alignment: "Global Checksum" → "Global Integrity Check (GIC)".

