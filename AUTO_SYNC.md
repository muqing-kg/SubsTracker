# 自动同步说明

本仓库自动镜像上游：

- 上游：https://github.com/wangwangit/SubsTracker
- 同步分支：`master`
- 频率：每 6 小时（UTC）+ Actions 手动 `Run workflow`
- 策略：每次把 `master` 重置为上游 `master`，再写回：
  - `.github/workflows/auto-sync-upstream.yml`
  - `wrangler.toml`（本 fork 的 Worker 名 / KV ID / 定时）
  - `AUTO_SYNC.md`

冲突处理：不手解冲突，以上游代码为准重建，只保留部署配置。

注意：

- 不要在 `master` 上堆长期业务私改；会被下次同步覆盖
- 若要改部署身份，只改 `wrangler.toml` 后推到 `master`（同步脚本会保留它）