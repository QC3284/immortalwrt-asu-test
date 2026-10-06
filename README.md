# immortalwrt-asu-test

第三方 ASU（Attended Sysupgrade）服务器的构建后端原型。

用 GitHub Actions 跑 ImmortalWrt ImageBuilder，为固件选择器 / ASU 客户端提供按需构建。

## 状态

原型验证阶段。asu-build workflow 接受 workflow_dispatch，产出镜像 artifact。

## 触发方式

gh workflow run asu-build.yml -f request_hash=test001 -f version=24.10.0 -f target=x86/64 -f profile=generic -f packages=""

## 设计要点

- run-name 设为 asu-<request_hash>，便于 dispatch 后按 displayTitle 定位 run_id（workflow_dispatch 返回 204 无 body）
- 产物用 upload-artifact；生产环境应改为上传 OSS/R2 以便国内分发
