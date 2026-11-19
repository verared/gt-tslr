# TSLR Specification — True Local Solar Time (EXPERIMENTAL)

- **Status: EXPERIMENTAL** — separate from the normative core ·
  **Version:** 1.0.0 · **Baseline:** GUS v3.1.1
- **Consolidated edition:** [`../en/gus-3.0.0.md`](../en/gus-3.0.0.md) (§9.6, Layer 3)
- **License:** CC-BY-4.0 · Maintained by: verared contributors

> **This profile is NOT part of the calendar conformance guarantee nor of
> the canonical stamp.** There is no reference implementation in this
> repository; the specification declares the contract for future
> implementations (e.g. a `gerarion-tslr` satellite repository).

## 1. Scope

Optional astronomical verification (Layer 3) for Level-3 forensic
evidence: solar position computed with ephemerides, a master-nodes
quorum, and a log-integrity profile.

## 2. Planned rules

1. Solar position (altitude/azimuth) computed from ephemerides (DE440)
   with a **mandatory `ephemeris_hash`**: a future ephemeris update
   never retro-invalidate a previous signature.
2. **3-of-4 Master Nodes quorum** (Jerusalem 31.7683°N/35.2137°E,
   Sèvres (BIPM) 48.8292°N/2.2203°E, Santiago 33.4489°S/70.6693°W,
   Sydney 33.8688°S/151.2093°E): no single point of verification
   failure.
3. **Polar protocol** (|φ| > 66.5°): altitude/azimuth computation is
   degenerate in polar nights or days; the verifier downgrades the stamp
   to Level 2 and records the condition.
4. **Integrity invariants:** monotonic `tai_seconds`,
   cycle/observer-hour consistency, weekday consistency (I-1),
   year↔TAI consistency, and verifiability of the declared ephemeris;
   hash-chained logs and double sealing (`gero_canonical` +
   `tai_seconds`) on critical events.

## 3. Sources of truth

None yet: the specification is the source. Any future implementation
must publish its own CC0 vectors and reproducible test suite.

## 4. Applicable vectors

None in this repository yet.

## 5. Maturity and limits

- **Experimental.** Not part of the conformance guarantee.
- GUS does not replace operating-system security controls, hardware
  isolation, or network mitigations: it covers around them, never in
  their place.
- TSLR verification provides **deterministic tamper detection** and
  traceability; it makes no unforgeability claims.

## 6. References

- Section 9.6 of the consolidated edition; `docs/en/threat-model.md`.
