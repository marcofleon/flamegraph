## Steps to generate flamegraph:

```bash
git clone https://github.com/brendangregg/Flamegraph.git

FUZZ=utxo_snapshot perf record -g --call-graph dwarf ./src/test/fuzz/fuzz -runs=10000

perf script > out.perf

cd Flamegraph
stackcollapse-perf.pl ../out.perf | flamegraph.pl > flamegraph.svg

open flamegraph.svg
```
