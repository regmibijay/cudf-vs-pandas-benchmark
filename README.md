# cudf-vs-pandas-benchmark
Benchmarking for CUDF12 vs Pandas in general operations

Source file for benchmarking was: https://colab.research.google.com/drive/12tCzP94zFG2BRduACucn5Q_OcX1TUKY3

## Hardware
This benchmark was ran with: 

- CPU: Intel i7 11700K @3.60GHz
- GPU: NVIDIA RTX 3060TI (8GB VRAM + 16GB Shared DRAM)
- RAM: 32GB DDR4
- SSD: Samsung NVMe SSD

## Software
- NVIDIA Toolkits
    - Driver Version: 546.01
    - CUDA Version: 12.3

- cuDF: 23.10.01

## Results
Raw data is present in included file `rapids_cudf_pandas_accelerator_mode.ipynb`
| Operation | native Pandas | cuDF |
|-----------|---------------|------|
|read, group, sort index | CPU: 7.42s, Wall: 5.31s | CPU: 695ms, Wall: 781ms|
|group, aggregate, rename, sort | CPU: 1.44s, Wall: 1.43s | CPU: 37.8ms, Wall: 43.4ms|
|dtype change, map dtype, groupby | CPU:2.3s, Wall: 2.29s | CPU: 173ms, Wall: 239ms|

## Conclusion
cuDF provides blazing fast operation interface for pandas by bootstraping dtypes which leverage GPU while performing operations rather than CPU like native pandas. This speed can be achieved by almost no code change. However this speed requires supported NVIDIA Graphics Unit.