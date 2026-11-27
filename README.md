# GeoLite2 Country (mmdb)

每周自动构建 [MaxMind GeoLite2-Country](https://dev.maxmind.com/geoip/geolite2-free-geolocation-data) 数据库，输出可直接使用的 `.mmdb` 单文件。

MaxMind 官方只提供 `.tar.gz` 压缩包，多数客户端（如 Quantumult X）无法解压，因此这里做了一层转换。

## 订阅地址

```
https://github.com/raddystar1/geoip-mmdb-CN/releases/download/geoip/Country.mmdb
```

> 把 `USER/REPO` 换成你的用户名和仓库名。该地址固定不变，每次更新会覆盖同名附件。

## 特性

- **自动更新**：每周三 03:00 UTC 由 GitHub Actions 拉取最新数据
- **格式精简**：只输出 `GeoLite2-Country`，约 3 MB，不含体积庞大的 City 数据
- **地址稳定**：固定 tag `geoip` + `--clobber` 覆盖，订阅地址永不变更
- **完整性校验**：构建时检查文件大小，异常响应不会发布

## 使用方式

### Quantumult X

「设置 → 其他设置 → GeoLite2」：

1. **来源** 填入上方订阅地址
2. 开启 **自动更新**
3. 点「更新」

加载成功后，`geoip, cn, direct` 这类 IP 归属地规则即可正常工作，节点列表也会显示正确的国家标识。

### 手动触发一次构建

Actions → **GeoLite2 Country** → **Run workflow**。

## 构建原理

1. 用 `MAXMIND_LICENSE_KEY` Secret 调用官方下载接口
2. 解压 `GeoLite2-Country_YYYYMMDD.tar.gz`
3. 取出 `GeoLite2-Country.mmdb`，重命名为 `Country.mmdb`
4. 上传到 Release（同名覆盖）

## 关于许可

数据库版权归 MaxMind 所有，使用须遵循 [GeoLite2 EULA](https://www.maxmind.com/en/geolite2/eula)。其中要求：新版本发布后 30 天内应停止使用并删除旧版本数据 —— 本仓库的每周自动更新恰好满足这一条。

## 免责声明

本仓库仅做格式转换与分发，不对数据的准确性与可用性作任何保证。
