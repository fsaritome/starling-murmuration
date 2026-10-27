# Starling Murmuration

A live 3D simulation of a starling murmuration in a single HTML file. Open `index.html` in a browser.

Each bird follows only its 7 nearest neighbours: it matches their heading, stays close and keeps a small gap. There is no leader. A falcon hunts the flock now and then, and you can click the sky to send it somewhere. Birds near the falcon get startled, and the startle passes from neighbour to neighbour. That makes the turning waves and folds you see in real murmurations.

## WebGPU and fallback

In browsers with WebGPU (current Chrome and Edge, for example) the simulation runs on the GPU. The nearest-neighbour search, the flocking rules and the drawing all happen in compute and render shaders, so the flock starts at 20,000 birds and goes up to 100,000. A "WebGPU" badge appears next to the bird count.

The CPU version always starts at once, and the GPU version takes over as soon as its shaders have compiled, which can take several seconds on a first visit.

Everywhere else, or if WebGPU fails to start, the page stays on the original CPU version with 500–5,000 birds. Add `?cpu` to the address to force the CPU version.

On a desktop with an AMD RDNA 3 GPU, one simulation step took about 1.6 ms for 20,000 birds on the GPU, compared with 11 ms for 5,000 birds on the CPU.

## Controls

- How many neighbours each bird watches (1–20)
- Flock size
- Reaction speed
- Release falcon, pause, reset
- Falcon hunts on its own
- Show fear wave (WebGPU only): tints startled birds so you can watch the panic spread

A simplified sketch, not a research model.

Live: https://fsaritome.github.io/starling-murmuration/

## Credits

Created by [fsaritome](https://github.com/fsaritome).

## Copyright

© 2026 fsaritome. All rights reserved. See [LICENSE](LICENSE).
