# Strange Attractors

A zero-dependency, real-time visualizer for chaotic dynamical systems. Thousands of particles are integrated every frame and drawn as glowing trails, so each streak is a real trajectory through the system's state space.

Open `index.html` in any modern browser. Nothing to install, no build step.

## Systems

| System | Type | Notes |
| --- | --- | --- |
| Lorenz | 3D flow (RK4) | Classic butterfly; `σ`, `ρ`, `β` |
| Rössler | 3D flow (RK4) | Folded band; `a`, `b`, `c` |
| Thomas | 3D flow (RK4) | Cyclically symmetric; `b` |
| Clifford | 2D map | Iterated map; `a`, `b`, `c`, `d` |
| De Jong | 2D map | Iterated map; `a`, `b`, `c`, `d` |

Every parameter has a slider. **Randomize** samples new parameters across each system's stable-to-chaotic range, which is where most of the interesting shapes live.

## Controls

- **Drag** to rotate 3D systems. **Scroll** to zoom.
- **Space** pause / play
- **R** randomize parameters
- **E** reseed particles
- **S** save the current frame as PNG
- **H** hide / show the control panel

## How it works

- Flow systems are integrated with classic fourth-order Runge-Kutta. Maps are iterated directly.
- Particles that diverge, collapse to a fixed point, or get randomly refreshed are reseeded, which keeps the image alive indefinitely.
- Color is driven by speed (normalized by an adaptive maximum), depth along the view axis, or particle index. Five palettes are included.
- Trails come from a translucent fade over an additive (`lighter`) composite, so dense regions glow naturally.
- The canvas is HiDPI-aware (capped at 2×).

## Files

- `index.html`: the entire application, with inline CSS and JavaScript.
- `README.md`: this file.

## PC Airflow 3D (`airflow3d.html`)

A live 3D airflow and thermal simulation of a Fractal Pop Air–style mid-tower with an AMD Wraith Stealth cooler and a triple-fan ROG Strix-style GPU. Open the file in a browser; there are no dependencies.

**What is simulated**

- Incompressible Navier–Stokes on a 16 × 35 × 37 staggered grid (1.25 cm cells) using the stable-fluids method: semi-Lagrangian advection, red-black SOR pressure projection, buoyancy, and eddy diffusion to stand in for unresolved turbulence.
- Fans drive face velocities toward their free-air speed, so real back-pressure reduces their airflow. Mesh panels, dust filters and heatsink fins add drag.
- Components exchange heat with the air cells they touch. GPU and CPU heatsinks follow the airflow their own fans push through them; passive parts (SSD, RAM, VRM) follow local air speed. Hot air is carried downstream, so recirculation and preheating show up naturally.
- Case pressure comes from the solver: the flow through vents without a running fan tells you whether the case is positive or negative.

**What you can change**: cooler (stock top-down or dual tower), each fan slot (intake, exhaust, empty), case/GPU/CPU fan speeds, dusty filters, component wattage, room temperature, plus scenarios such as a reversed rear fan. Slices show temperature or speed through any plane.

It is coarse and simplified. Trends and comparisons are meaningful; absolute temperatures are calibrated to typical values, not measured. Component heat-up is time-compressed.
