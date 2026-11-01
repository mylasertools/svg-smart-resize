# Contributing

Small, dependable geometry tools are the goal. Bug reports with a minimal SVG, requested dimensions, and expected hole/slot measurements are especially useful.

1. Use Node.js 20 or newer and run `npm ci`.
2. Add a small regression fixture for geometry changes.
3. Run `npm run check`, `npm run test:package`, and `npm run format:check`.
4. For demo changes, run `npm run demo` and inspect desktop and mobile layouts.
5. If example behavior changes, run `npm run assets`.

Runtime dependencies need a strong reason. The complete ESM bundle has a 13,000-byte gzip budget. Preserve Bézier curves and arcs in exported SVG; approximation is for analysis only.

Changes should document unsupported input explicitly. Don't silently drop geometry or claim fabrication correctness from a bounding-box check.

## Commands

```sh
npm ci
npm run check
npm run demo         # local demo; SVG files stay in the browser
npm run assets       # regenerate the README illustrations
npm run format       # format source and docs
npm run test:package # test the installable tarball in an isolated consumer
```

## Project layout

- `src/xml.ts`, `svg.ts`: constrained SVG reading and physical units.
- `src/path.ts`, `matrix.ts`, `geometry.ts`: path geometry and affine transforms.
- `src/analyze.ts`: contour nesting and feature detection.
- `src/index.ts`: preservation policies, export, and conflict reporting.
- `demo/`: a framework-free consumer of the built npm entry point.
- `test/`: Node's built-in test runner; no test framework dependency.
- `scripts/assets.mjs`: actual-output illustrations for the README.

## Releasing

See [docs/RELEASING.md](docs/RELEASING.md).
