# Four Search Algorithms, One Transit Network

**Artificial Intelligence Search Algorithms for the Johnson City Transit Network**  
Md. Zobaer Ahammad · East Tennessee State University · CSCI 5260 · November 2026

## Overview

This course research project compares four classic graph-search methods on the real Johnson City Transit (JCT) network:

- Breadth-First Search (BFS)
- Uniform-Cost Search (UCS)
- Greedy Best-First Search
- A* Search

A directed, weighted graph was built from publicly available static GTFS schedule information. The experiment compared **route distance**, **nodes expanded**, and **execution time** on the same **25 reachable origin–destination pairs**.

## Data and experiment

| Measure | Value |
|---|---:|
| Transit stops (graph nodes) | 389 |
| Unique directed graph edges | 431 |
| Transit routes | 12 |
| Scheduled trips | 333 |
| Stop-time records | 9,360 |
| Selected origin–destination pairs | 25 |
| Total algorithm–pair evaluations | 100 |

The four GTFS source files were `stops.txt`, `routes.txt`, `trips.txt`, and `stop_times.txt`. Geographic edge distances and heuristic distances were computed using the Haversine formula. Pairs were sampled across five straight-line-distance groups using a fixed random seed of 42.

## Results

| Algorithm | Average route distance (km) | Average nodes expanded | Average execution time (ms) |
|---|---:|---:|---:|
| A* | 11.6590 | 84.80 | 0.3273 |
| BFS | 12.1280 | 185.00 | 0.1844 |
| Greedy | 12.4947 | 74.68 | 0.2876 |
| UCS | 11.6590 | 159.16 | 0.2494 |

**Key findings:** A* and UCS returned matching minimum geometric route distances for all 25 tested pairs. A* expanded about **46.7% fewer nodes** than UCS. Greedy expanded the fewest nodes on average but returned longer distances on some pairs. BFS was fastest in the reported implementation, despite expanding the most nodes on average.

These are results for a **simplified static geometric graph**; the route costs are not actual road distances or schedule-feasible passenger travel times. Runtimes are small and depend on implementation and hardware.

## Figures

![Mean path distance](figures/average_path_distance.png)

![Mean nodes expanded](figures/average_nodes_expanded.png)

![Mean execution time](figures/average_execution_time.png)

![Nodes by distance group](figures/nodes_by_distance_group.png)

## Repository contents

- [`report/`](report/) — research report, proposal, and methodology document
- [`presentation/`](presentation/) — CSCI 5260 project presentation
- [`results/`](results/) — individual test results and selected origin–destination pairs in CSV format
- [`figures/`](figures/) — summary plots

**Reproducibility note:** The original Python implementation and GTFS input feed were not included in the supplied materials. This repository preserves the supplied results and documentation but is not yet a runnable code release. Add your original `.py` or `.ipynb` files to reproduce the analysis.

## Sources

- [Johnson City Transit GTFS feed](https://www.johnsoncitytransit.org/google_transit.zip)
- [GTFS Schedule reference](https://gtfs.org/documentation/schedule/reference/)

## Presentation video

A presentation recording exists separately. Because it is large (~80 MB), it is **not included in this upload bundle**. If adding it to GitHub, consider an external video link or Git LFS.
