# 热更新服务端文件（上传到 https://peyt.org/peytchat-android-update/）

本目录是**已生成、可直接上传**的热更新文件：

| 文件 | 说明 |
| --- | --- |
| `update.json` | 更新清单（模块 shell v1.0.1） |
| `shell_1.0.1.dex` | 示例补丁（源码见 `patch-sample/`） |

## 部署

把这两个文件上传到服务器目录 `peytchat-android-update/` 下，即：

```
https://peyt.org/peytchat-android-update/update.json
https://peyt.org/peytchat-android-update/shell_1.0.1.dex
```

上传完成后 App 设置 → 检查更新（默认地址已是上面这个 `update.json`）→ 立即检查即可。

## 以后发新版补丁

1. 修改/新增 `patch-sample/` 里的补丁类，按 `patch-sample/README.md` 打成 dex
   （命名 `<module>_<version>.dex`，版本号递增，如 `shell_1.0.2.dex`）；
2. 重新生成清单（脚本自动算 md5、拼 url）：

   ```bash
   OUT=updates/update.json ./scripts/gen-update-manifest.sh \
       https://peyt.org/peytchat-android-update/ \
       updates/shell_1.0.2.dex
   ```

3. 把新 dex 和新的 `update.json` 一起上传覆盖。
