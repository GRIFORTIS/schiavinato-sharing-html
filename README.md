# Schiavinato Sharing (HTML)

[![Security: Experimental](https://img.shields.io/badge/Security-⚠️%20Experimental-red)](https://github.com/GRIFORTIS/schiavinato-sharing/blob/main/SECURITY.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen)](https://nodejs.org/)

> ## ⚠️ EXPERIMENTAL - NOT AUDITED - DO NOT USE FOR REAL FUNDS
> 
> This specification has NOT been audited. Use only for testing, learning, and experimentation. **We invite cryptographers and developers to review the spec and contribute.**
> 
> **[See Security Status](https://github.com/GRIFORTIS/schiavinato-sharing/blob/main/SECURITY.md) for details.**

**Single-file, air-gapped HTML implementation of Schiavinato Sharing**

Human-executable secret sharing for BIP39 mnemonics using GF(2053). Runs entirely offline in any modern browser with no installation or network connection required.

---

## What is this?

A self-contained HTML/JavaScript application implementing the Schiavinato Sharing scheme. Designed for offline/air-gapped environments where computational convenience is preferred over manual math, but network access or software dependencies are unavailable or untrusted.

**Key properties:**
- Single file (all CSS/JS inline)
- No external dependencies at runtime
- Offline-capable by design
- Manual-fallback compatible

---

## Links

- **Canonical protocol + specs**: [schiavinato-sharing](https://github.com/GRIFORTIS/schiavinato-sharing)
- **Whitepaper**: [PDF](https://github.com/GRIFORTIS/schiavinato-sharing/releases/latest/download/WHITEPAPER.pdf) | [LaTeX source](https://github.com/GRIFORTIS/schiavinato-sharing/blob/main/WHITEPAPER.tex)
- **Test Vectors**: [TEST_VECTORS.md](https://github.com/GRIFORTIS/schiavinato-sharing/blob/main/TEST_VECTORS.md)
- **JavaScript library**: [schiavinato-sharing-js](https://github.com/GRIFORTIS/schiavinato-sharing-js)
- **Python library**: [schiavinato-sharing-py](https://github.com/GRIFORTIS/schiavinato-sharing-py)

---

## Security

This tool implements well-established cryptographic principles but has **NOT** been professionally audited.

**Use only for**: testing, learning, experimentation.

**Canonical security posture**: [schiavinato-sharing/SECURITY.md](https://github.com/GRIFORTIS/schiavinato-sharing/blob/main/SECURITY.md)

---

## Verify Before Use (Required)

**CRITICAL**: Before using with real crypto seeds, verify the HTML file hasn't been tampered with.

### 1. Import GRIFORTIS Public Key (One-Time)

```bash
curl -fsSL https://raw.githubusercontent.com/GRIFORTIS/schiavinato-sharing/main/GRIFORTIS-PGP-PUBLIC-KEY.asc | gpg --import
```

**Verify fingerprint:**
```bash
gpg --fingerprint security@grifortis.com
```

**Expected**: `7921 FD56 9450 8DA4 020E  671F 4CFE 6248 C57F 15DF`

### 2. Download Release Files

```bash
# Replace VERSION with actual release (e.g., v0.4.0)
VERSION="v0.4.0"
curl -fsSL -O "https://github.com/GRIFORTIS/schiavinato-sharing-html/releases/download/${VERSION}/schiavinato_sharing.html"
curl -fsSL -O "https://github.com/GRIFORTIS/schiavinato-sharing-html/releases/download/${VERSION}/schiavinato_sharing.html.asc"
```

### 3. Verify GPG Signature

```bash
gpg --verify schiavinato_sharing.html.asc schiavinato_sharing.html
```

**Expected output**: `Good signature from "GRIFORTIS <security@grifortis.com>"`

### 4. Verify Checksum (Optional but Recommended)

```bash
curl -fsSL -O "https://github.com/GRIFORTIS/schiavinato-sharing-html/releases/download/${VERSION}/CHECKSUMS.txt"
curl -fsSL -O "https://github.com/GRIFORTIS/schiavinato-sharing-html/releases/download/${VERSION}/CHECKSUMS.txt.asc"
gpg --verify CHECKSUMS.txt.asc CHECKSUMS.txt
sha256sum --check CHECKSUMS.txt --ignore-missing
```

---

## Usage

1. Open `schiavinato_sharing.html` in any modern browser (Chrome, Firefox, Safari, Edge)
2. Follow on-screen instructions to split or recover mnemonics
3. **Use offline only** — disconnect from all networks before proceeding

**No installation, no dependencies, no network connection required.**

---

## For Developers

### Running Tests

```bash
# Install test dependencies
npm ci

# Install Playwright browser
npx playwright install chromium

# Run all tests
npm test

# Run with UI
npm run test:ui

# Run linter
npm run lint
```

### Test Coverage

Comprehensive Playwright test suite covering:
- Happy path (split/recover for 2-of-3, 3-of-5 schemes)
- Edge cases (invalid inputs, corrupted checksums, boundary conditions)
- Validation (BIP39 checksum, input constraints, error handling)
- GIC binding (share number validation)
- Path mismatch detection (dual-path checksum validation)

---

## Conformance Validation

This implementation is validated against canonical test vectors:
- [TEST_VECTORS.md](https://github.com/GRIFORTIS/schiavinato-sharing/blob/main/TEST_VECTORS.md)

Tests run automatically in CI on every push/PR.

---

## Compatibility

- **Spec version**: v0.4.0
- **BIP39 word counts**: 12, 24
- **Threshold schemes**: 2-of-3, 2-of-4, 3-of-5 (extensible to any k-of-n where k ≥ 2, n < 2053)
- **Browser requirements**: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+

---

## Contributing

See [CONTRIBUTING.md](https://github.com/GRIFORTIS/schiavinato-sharing/blob/main/CONTRIBUTING.md) in the canonical repo.

When contributing:
- Maintain single-file, self-contained design
- Add/update tests for any behavioral changes
- Run full test suite before submitting PR

---

## License

[MIT License](LICENSE)

---

**Made by [GRIFORTIS](https://github.com/GRIFORTIS)** — Open-source tools for sovereign crypto self-custody
