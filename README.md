# World of Ato — Embroidery Digitizing Case Study

This repository documents a focused KSuite production problem: converting a small, layered **World of Ato** character mark into a sewable Brother PES design without losing the visual relationships that make the artwork recognizable.

## The problem

Small artwork is unforgiving. A preview can look correct while the stitch plan introduces dense blobs, closes intentional gaps, loses toes or facial details, or creates unsafe exposed travel. The target was a deterministic, machine-aware design for a Brother SE700 hoop.

## Approach

1. Normalize artwork into physical 0.1 mm geometry.
2. Preserve alpha and layer semantics instead of inventing a global base fill.
3. Generate typed stitch, move, trim, tie-on, tie-off, stop, color-change, and end commands.
4. Protect small details during density retries and travel optimization.
5. Validate hoop fit, stitch budgets, relocations, and PES read-back.
6. Compare successive regressions by stitch topology and production metrics, not preview appearance alone.

## Included evidence

- `evidence/world-ato-layered.png` — layered design preview.
- `evidence/world-ato-layered-4x4.png` — 4x4 hoop-oriented preview.
- `evidence/world-ato-fine-guard.png` — detail-preservation regression.
- `evidence/world-ato-toe-regression.png` — topology regression focused on small features.

The source engine and acceptance rules live in [KSuite](https://github.com/jt-wilkinson/ksuite). The binary PES files are intentionally not mirrored here; the case study keeps the repository reviewable and avoids treating generated machine output as source.

## What changed

The key lesson was to make production constraints explicit in the intermediate representation. That allowed the optimizer to reduce wasteful travel and density without silently changing the artwork's topology.

## Reproducibility

Run the KSuite validation tools against the original artwork and the documented machine profile. A real sew-out remains the final authority for production quality.

## License

Documentation and evidence in this repository are released under the MIT License. Artwork remains the property of its respective rights holders.
