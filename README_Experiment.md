[AIFM 8.1.2]  |  [fig7-8]

验证 AIFM 在 DataFrame 应用程序上即使只有少量的本地内存也能达到近乎最佳的性能。通过调整 cache_size（本地缓存大小）观察性能变化趋势。

# Intro

- Table-structured in-memory structure [表结构的内存数据结构]
- Expose slicing, filtering and aggregation ops [支持切片、过滤、聚合操作]

# Dataset & Setting

- NYC taxi trip：NYC_Taxi.zip(31GB)

![img](https://jianmucloud.feishu.cn/space/api/box/stream/download/asynccode/?code=N2I3ZTZmYzYzOTljNzRiNjRmNTVmMmZkOGM0MzMzMzVfWm9VSVpWMjdDOE9ucE5OYjVqZTJIalU1cTR0cGFWT1dfVG9rZW46Tmh4eGJRd3ZJb0Fjc0R4emIxa2M3NmZubjljXzE3NTQ4OTE1NzM6MTc1NDg5NTE3M19WNA)

工作负载的完整内存工作集为31GB，实验中需要将可用本地内存的大小在1GB和31GB之间变化。

- cache_sizes=(1 3 5 7 9 11 13 15 17 19 21 23 25 27 29 31)

# Benchmark & Procedure

Benchmark：[dataframe_performance.cc](https://github.com/hosseinmoein/DataFrame/blob/master/benchmarks/dataframe_performance.cc)

```Shell
cd AIFM_Fork/aifm/exp/fig7 # 或 AIFM
./setup_input.sh # 下载数据集到 /mnt 文件夹
# 运行每个子文件夹的 run.sh 
# log.X 文件倒数第二行显示总执行时间（μs）
```

# AIFM

## API

- std::vector → AIFM-enabled
- Support [low compute intensity but high memory access frequency] key ops offload

![img](https://jianmucloud.feishu.cn/space/api/box/stream/download/asynccode/?code=MmM4M2U3OGQ1ZGMwMjRjOTUyMzVmNWM4NTZkYTNhMmRfT3dUcFBjZXFnajhqVmxnTFM5UUh0d09qZ1hkT2Rwc1dfVG9rZW46TmRVaGJFNHFFb1ZnNUh4dVhTdmNPR3JLblBmXzE3NTQ4OTE1NzM6MTc1NDg5NTE3M19WNA)

## Problems

运行 setup_input.sh  所有下载返回 403 Forbidden 错误，数据集链接失效。

![img](https://jianmucloud.feishu.cn/space/api/box/stream/download/asynccode/?code=YTllMjA0NGZlNGRiZDExZDlmMzI2NTA4YTM2MzQ1NDZfUTNWYk5FbEE5bGQzWDZnWXViU3A3NGd3d3A0V2l0QkJfVG9rZW46QXhZZmIya0F2b1lqajN4QzYzOWNYMURRbkpoXzE3NTQ4OTE1NzM6MTc1NDg5NTE3M19WNA)

把数据集放到 /mnt 文件夹，重新执行即可。

## Result

实验数据存在问题，待重测

![img](https://jianmucloud.feishu.cn/space/api/box/stream/download/asynccode/?code=NmRjMDczNTNiMWU1NDNhMmVhNjUxNmNlYzRkOGFkNzRfVE5aYUNQSVNiYWYwUUtEc3ZUc2s3MXdoUU1jdWpvNHZfVG9rZW46UFpSeWJzY0JYb0UwcG54TGVnQmNUSk1jbkFiXzE3NTQ4OTE1NzM6MTc1NDg5NTE3M19WNA)