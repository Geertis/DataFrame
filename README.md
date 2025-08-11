[AIFM 8.1.2]  |  [fig7-8]

验证 AIFM 在 DataFrame 应用程序上即使只有少量的本地内存也能达到近乎最佳的性能。通过调整 cache_size（本地缓存大小）观察性能变化趋势。

# Intro

- Table-structured in-memory structure [表结构的内存数据结构]
- Expose slicing, filtering and aggregation ops [支持切片、过滤、聚合操作]

# Dataset & Setting

- NYC taxi trip：NYC_Taxi.zip(31GB)

​	通过网盘分享的文件：dataset
​	链接: https://pan.baidu.com/s/1Rq_dIPJkADYcbdnkM9_ouQ?pwd=esai 提取码: esai 
​	--来自百度网盘超级会员v6的分享

![image-20250811214344571](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20250811214344571.png)

- cache_sizes=(1 3 5 7 9 11 13 15 17 19 21 23 25 27 29 31)

​	工作负载的完整内存工作集为31GB，实验中需要将可用本地内存的大小在1GB和31GB之间变化。

# Benchmark & Procedure

Benchmark：[dataframe_performance.cc](https://github.com/hosseinmoein/DataFrame/blob/master/benchmarks/dataframe_performance.cc)

Proceduce：参考原README

# AIFM

## API

## Problems

运行 setup_input.sh  所有下载返回 403 Forbidden 错误，数据集链接失效。

![image-20250811214744640](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20250811214744640.png)

把数据集放到 /mnt 文件夹，重新执行即可。

## Result

实验数据存在问题，待重测
