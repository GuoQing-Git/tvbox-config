# TVBox 配置文件

TVBox 自动更新的视频源配置文件，包含多个可用的影视资源站点。

## 配置地址

复制以下地址到 TVBox 中使用：

**推荐地址（国内 CDN，速度快）：**
```
https://cdn.jsdelivr.net/gh/GuoQing-Git/tvbox-config@main/tvbox_config.json
```

**备用地址：**
```
https://raw.githubusercontent.com/GuoQing-Git/tvbox-config/main/tvbox_config.json
```

## 使用方法

1. 打开 TVBox 应用
2. 进入 **设置** → **配置地址**
3. 粘贴上面的地址
4. 点击 **确定**，等待加载完成

## 包含内容

### 视频站点（11个）

| 站点 | 类型 | 搜索 |
|------|------|------|
| 采集资源 | 标准采集站 | 支持 |
| 暴风资源 | 标准采集站 | 支持 |
| 量子资源 | 标准采集站 | 支持 |
| 快看资源 | 标准采集站 | 支持 |
| 闪电资源 | 标准采集站 | - |
| 光速资源 | 标准采集站 | 支持 |
| 超快资源 | 标准采集站 | 支持 |
| 极速资源 | 标准采集站 | - |
| 红牛资源 | 标准采集站 | 支持 |
| 360资源 | 标准采集站 | 支持 |
| 非凡资源 | 标准采集站 | 支持 |

### 直播源（2个）

- 央视频道
- 地方频道

### 解析接口（4个）

- 聚合解析
- 夜幕解析
- 虾米解析
- CK解析

## 自动更新

本配置文件通过脚本自动更新，定期搜索并验证可用站点。

### 更新命令

```bash
cd D:/test/tvbox/tools
python auto_update.py
```

脚本会自动：
1. 搜索最新的可用站点
2. 验证站点是否可用
3. 生成新的配置文件
4. 推送到 GitHub

### 手动更新

```bash
# 1. 拉取最新代码
cd D:/test/tvbox/tvbox-config
git pull

# 2. 运行更新脚本
cd D:/test/tvbox/tools
python cli.py auto

# 3. 生成配置
python cli.py generate -o D:/test/tvbox/tvbox-config/tvbox_config.json

# 4. 推送到 GitHub
cd D:/test/tvbox/tvbox-config
git add tvbox_config.json
git commit -m "更新配置"
git push origin main
```

## 项目结构

```
tvbox-config/
├── tvbox_config.json    # TVBox 配置文件
└── README.md            # 说明文档
```

## 常见问题

### Q: 配置加载失败？
A: 检查地址是否正确，确保网络可以访问 GitHub 或 jsdelivr CDN。

### Q: 视频无法播放？
A: 部分站点可能失效，等待下次自动更新或手动运行更新脚本。

### Q: 如何添加自定义源？
A: 编辑 `tvbox_config.json`，在 `sites` 数组中添加新站点。

### Q: 如何设置自动定时更新？
A: 使用 Windows 任务计划程序或 Linux crontab：

**Windows：**
```powershell
# 创建定时任务，每天凌晨3点执行
schtasks /create /tn "TVBox更新" /tr "python D:\test\tvbox\tools\auto_update.py" /sc daily /st 03:00
```

**Linux/Mac：**
```bash
# 编辑 crontab
crontab -e

# 添加以下行（每天凌晨3点执行）
0 3 * * * cd /path/to/tools && python auto_update.py
```

## 相关项目

- [TVBox](https://github.com/CatVod/CatVodOpen) - TVBox 开源版本

## 免责声明

本项目仅供学习交流使用，不存储任何视频资源。所有视频均来自第三方站点，请遵守相关法律法规。
