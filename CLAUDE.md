# pit stop school

Single file web app (index.html) plus bundled assets. No build, no framework, no package.json. Serve the folder statically to run it.

## Structure of index.html
- `<style>`: brand tokens on :root (navy, cream, gold, teal, rust; Inter Tight display, Geist Mono labels). Single dark theme by design.
- Markup: header with lesson tabs, `#stage` (three.js canvas) and `<aside>` with the step card and nav.
- Script, in order: renderer/scene setup, tween engine (`tween`, `tweenV3`, `flyTo`), props (`buildProps`, `buildEngineBay`), model loading (`loadModel` rebuilds a GLB from the JSON and calls `GLTFLoader.parse`), camera presets (`cam`), the `lessons` object, the lesson runner (`goStep`, `renderCard`, `showQuiz`), tap handling (`handleTap`), frame loop.

## Conventions
- Copy is lowercase, closed with a period, in the voice b style. No em dashes, no semicolons in copy.
- Positions use `at(side, length, height)` so the code does not care which axis the model calls front. `geo` holds what was measured off the model at load.
- Anything bolted to the car goes in the `car` group (so it lifts with the jack). Floor things go in `props`.
- The engine lid is clipped out of the body with `clipPlanes` and rebuilt as `P.lid`. Keep `renderer.localClippingEnabled = true`.
- `THREE.ColorManagement.legacyMode = false` is required. Without it every hex color renders washed out.
- Three.js is r147 (UMD, globals). Addons are the examples/js versions. Do not upgrade past r147 without moving to ES modules.

## Testing
Open in a browser, tap through both lessons, confirm each `task` can be completed and `Next` unlocks. Check phone width (under 900px switches to the stacked layout).
