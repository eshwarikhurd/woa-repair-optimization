# WOA Repair Optimization for Geo-Distributed Storage
### EECS 247: Information Storage | University of California, Irvine

A comparative study of metaheuristic algorithms (WOA, PSO, GA) for 
multi-objective erasure code repair optimization in geo-distributed 
data centers.

> Replicating and extending: Xu et al. (2026), *Journal of Cloud 
> Computing*, 15(3). https://doi.org/10.1186/s13677-025-00807-z

---

## What This Project Does

When a node fails in a geo-distributed storage system, recovering 
erasure-coded data requires retrieving fragments from multiple 
data centers — generating network traffic, latency, and load 
imbalance. This project implements a **repair tree optimization 
framework** that jointly minimizes all three, and benchmarks three 
metaheuristic solvers (WOA, PSO, GA) on the same problem to 
empirically validate which performs best.

## Repository Structure

```

├── preliminary_woa.py        # Parts 1–5: graph, Dijkstra, repair
│                             # tree, objective functions, WOA loop
├── preliminary_results.png   # WOA convergence plot
├── proposal/
│   ├── main.tex              # ACM-format proposal (LaTeX)
│   └── Khurd_EECS247_ProjectProposal.docx
└── README.md

```

## How to Run

```bash
pip install matplotlib
python preliminary_woa.py
```

## Preliminary Results

WOA on an 8-node test network (RS (6,4) code, 20 whales, 30 
iterations):

| Metric | Random Init | WOA Optimized |
|--------|-------------|---------------|
| Combined fitness | 1.1146 | **0.2832** |
| fmerge | — | 0.5000 |
| fnet-load | — | 0.0663 |

Converges by iteration 10. 

## Progress

- [x] Graph construction, Dijkstra, loop removal
- [x] Repair tree encoding (leaf-to-root paths)
- [x] Objective functions: fmerge (Eq. 5), fnet-load (Eq. 6)
- [x] WOA main loop (contraction, random search, spiral update)
- [ ] PSO and GA implementations
- [ ] Baseline stubs: AggreTree, ORT, SRPT, ERT
- [ ] Experiments I, II, III (n,k / bandwidth / block size)
- [ ] Final report and presentation

## Tech Stack

Python 3.11 · NetworkX · NumPy · Matplotlib

## References

1. Xu et al. (2026). *Journal of Cloud Computing*, 15(3).
2. Nadimi-Shahraki et al. (2023). *Arch. Comput. Methods Eng.*, 30(7).
3. Zhang et al. (2017). *IEEE Trans. Parallel Distrib. Syst.*, 28(6).