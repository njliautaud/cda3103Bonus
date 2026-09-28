# CDA 3103 Bonus: Cache Simulator

A small C program written for the bonus assignment of CDA 3103 (Computer Organization). It simulates a CPU cache on a trace of memory addresses and reports the number of hits and misses.

## What it does

- Models a cache with configurable total size, block size and associativity: `sets = size / (associativity × block size)`.
- Splits each address into a set index and a tag, and checks every way in the set for a valid matching tag.
- On a miss, fills an invalid way first, then evicts using either a simplified LRU policy or random replacement.
- Reads 16 addresses from `traces.txt` and prints `Hits`, `Misses` and `Total`.

The configuration in `main()` is a 32-byte, direct-mapped cache with 4-byte blocks (8 sets) using LRU. Change `cache.size`, `cache.sizeBlock` and the arguments to `startCache(&cache, associativity, policy)` to try other layouts (`policy` 0 = LRU, 1 = random).

## Build and run

The source is the single file `finalCDA` (C, no extension):

```bash
gcc -x c finalCDA -o cache
./cache            # expects traces.txt (one address per line) in the working directory
```

## Notes

Coursework submitted in April 2023. The trace reader and the LRU bookkeeping are intentionally minimal. For example, the loop reads a fixed 16 addresses, and the trace line is scanned with `%d` before being parsed as hex. Treat it as a learning exercise rather than a general-purpose simulator.
