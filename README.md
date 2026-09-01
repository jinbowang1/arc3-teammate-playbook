# ARC-AGI-3 队友作战手册（独立参赛期）

> 给：并肩作战但（暂时）没组队的队友。10 月组队截止前我们各干各的，每人每天 1 发提交，等于我们合计每天 2 发。

## 一、合规红线（先读这个，比跑分重要）

1. 组队之前，你我之间**不能私下传任何代码、数据、提交文件**——Kaggle 抓到算 private sharing，封号级处罚。
2. 本手册里让你跑的**全部是公开材料**（第 5 名 Son Pham 自己公开的完整包），全网谁都能跑，你跑它完全合法。
3. 互相通报**分数**、聊思路没问题；交换文件不行。这个仓库里只有这份手册，没有代码。

## 二、你要跑什么（按优先级）

**任务 1（首选）：原样复刻第 5 名的公开包（他榜上 3.58）**

- 为什么值得：这是当前全网可复现的最高分配置；而且你跑出来的分数 + 我们跑出来的分数 = 同配置两个独立样本，能测出这套配置的真实方差——这个数据对两边都值钱。
- 预期：3 分上下（他的 3.58 可能含选择运气）。

**任务 2（任务 1 顺利后、第二天）：再原样跑一遍**，拿方差的第二个样本；或者试他配置里保守关掉的开关（比如把 MTP 投机解码打开），看是他多虑还是真有坑。

## 三、怎么搭 notebook（只用公开材料，一步步来）

1. Kaggle 上打开比赛 arc-prize-2026-arc-agi-3，新建 Notebook；
2. 右侧 Settings：Accelerator 选 **RTX Pro 6000**，Internet **关**，Persistence 默认；
3. Add Input 挂 4 个公开数据集（搜 sonphamorg）：
   - `sonphamorg/arc3-flashnext-serving-part-a-v1`
   - `sonphamorg/arc3-flashnext-serving-part-b-v1`
   - `sonphamorg/arc3-flashnext-serving-part-c-v1`
   - `sonphamorg/arc3-flashnext-gcp-runtime-exact-v1`
4. notebook 的代码**不用自己写**：Part A 数据集里自带官方分享版跑分 notebook（路径 `source-bundle/src/tufa-arc-agi-framework/src/taaf/kaggle/taaf_kaggle_run_share.ipynb`），把它的 cells 原样搬进你的 notebook。它会自己找到源码捆绑、装环境、起模型、跑 25 局、产出 submission.parquet；
5. Save Version（选 Save & Run All），等约 3.5 小时跑完；
6. 检查跑分健康：Output 里有 `submission.parquet`；日志里有 25 行 `[finished]`、无 `crashed`。

## 四、怎么提交

- 网页：打开你跑完的 notebook 版本 → Output 页 → submission.parquet 右侧 **Submit to Competition**；
- 或命令行：`kaggle competitions submit arc-prize-2026-arc-agi-3 -k <你的notebook引用> -v <版本号> -f submission.parquet -m "flashnext public replica"`
- 名额：每天 1 发，**北京时间早 8 点刷新**；提交后官方连夜重跑隐藏题库，第二天早上出分。
- GPU 额度：每周 30 小时，**周五早 8 点刷新**；一次跑分约 3.5 小时。

## 五、通报

跑完把「隐藏集分数 + 公开集日志里的 mean score + 有没有崩溃」发群里就行。就这三个数，别发文件。

祝顺利。有坑随时群里喊。
