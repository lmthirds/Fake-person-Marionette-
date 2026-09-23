# 🎮 Minecraft Server Keep-Alive & Marionette Configuration

本项目记录了在 **Minekeep** 平台上部署 **Paper 1.21.10** Minecraft 服务器时，通过 **Marionette** 假人插件实现服务器 24 小时挂机保活、防止无人在线导致自动关机的完整教程与配置指南。

---

## 🔗 相关项目与下载地址

| 项目名称 | 说明 | 官方下载 / 项目链接 |
| :--- | :--- | :--- |
| **Marionette** | 核心假人插件（零前置依赖，推荐） | [SpigotMC 下载页](https://www.spigotmc.org/resources/marionette-fake-players.136068/) / [GitHub 仓库](https://github.com/synthet1cc/Marionette) |

---

## 🛠️ 安装与配置步骤

### 第一步：部署 Marionette 插件
由于旧版的 `fakeplayer` 插件与 `CommandAPI` 存在版本接口不兼容，可能会导致服务器启动报错崩溃。请先进入服务器的 `plugins/` 目录删除以下冲突包：
- 🗑️ `CommandAPI-*.jar`
- 🗑️ `fakeplayer-*.jar`
1. 前往 [SpigotMC Marionette 下载页](https://www.spigotmc.org/resources/marionette-fake-players.136068/) 点击右上角 **Download Now** 下载 `.jar` 文件。
2. 将下载好的 `Marionette-x.x.x.jar` 文件上传至服务器的 **`plugins/`** 目录中。

### 第二步：检查插件正常加载
在面板点击 **Restart** 重启服务器。检查 Console（控制台）日志，确认看到以下提示即表示插件正常加载：
```text
[INFO] Enabling Marionette v0.1.1
[INFO] Marionette-datasource - Start completed.

```
### 第三步：控制台命令生成假人
服务器完全启动（控制台输出 Done!）后，直接在 网页控制台 (Console) 输入以下命令并回车（注：控制台输入命令不需要加斜杠 /）：
```
marionette spawn bot1 world 0 100 0
```

游戏内使用：若玩家已进入游戏，亦可输入：/marionette spawn bot1
保活原理：执行后服务器在线人数将常态化保持为 1/20，Minekeep 面板检测到持续有玩家在线，即可彻底防止服务器因为无人在线而触发自动暂停/关机机制。
