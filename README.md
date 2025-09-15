# EdgesCGALDelaunay2D

Calcule les **arêtes** du 1‑squelette de la **triangulation de Delaunay 2D** à partir d’un `.npy` `(N,2)` et écrit un `.npy` `(M,2)` en `uint64` avec des paires **triées** `(i<j)`.

## Dépendances
```bash
sudo apt-get update
sudo apt-get install -y build-essential cmake libcgal-dev
```

## Build
```bash
cmake -S . -B build
cmake --build build -j
```

## Usage
```bash
./build/EdgesCGALDelaunay2D points.npy out_edges.npy
```

- `points.npy` : `float32`/`float64`, shape `(N,2)`, C‑contigu. Endianness `<`, `=`, `>` supportées (byteswap auto si `>`).
- `out_edges.npy` : `uint64` `(M,2)` trié.

## Perf
- Kernel: `Exact_predicates_inexact_constructions_kernel` (rapide, robuste).
- On itère `finite_edges` (pas de post‑filtrage infini), puis tri + unique pour assurer l’unicité.