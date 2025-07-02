# 🎯 CSGO Betterbot 指南

---
## 🚀 1. Server 搭建教程
### ✅ 服务器注意事项
- 至少配置：**2核4G**, 硬盘空间 **50G 起**
- 带宽建议：**5M 可支持约 10 人竞技**
### 🐧 Linux 端搭建
- **参考教程：**  
  - https://www.bilibili.com/read/cv17211032/?from=search&opus_fallback=1
  - https://www.bilibili.com/opus/417487734754630292/?from=readlist
- **注意事项：**
  - Linux 非常适合运行 **满十竞技、僵尸、KZ、娱乐模式**
  - 但是针对此模组，可能存在编译Betterbot插件中**botmimic拓展依赖出错**等一系列框架问题，如下所示：
	-  `个人不建议使用linux搭建此Betterbot服务器
```
Errors: 
bot_inventory.smx (BOT Inventory): Error detected in plugin startup (see error logs) 
csgo_weaponstickers.smx ([CS:GO] Weapon Stickers): Native not found: eItems_GetWeaponNumByDefIndex 
eitems.smx (eItems): Native "HTTPRequest.HTTPRequest" was not found 
bot_stuff.smx (BOT Stuff): Native "eItems_GetWeaponSlotByWeapon" was not found 
botmimic.smx (Bot Mimic): Native "eItems_GetWeaponSlotByClassName" was not found 
botmimic_menu.smx (Bot Mimic Menu): Could not find required plugin "botmimic"
```


### Windows 平台搭建
……


---

## 🎮 2. Client 连接教程

### 📦 前提条件
- 空间需求：约 **90G**

### 🔻 2.1 下载游戏文件
1. 在 Steam 中下载 **CS2**
2. 右键 CS2 → 属性 → **测试版** → 选择 **csgo_legacy_version**
   ![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702164850.png)
3. 下载完成后，右键 CS2 → **管理 → 浏览本地文件**
   ![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702165335.png)

- **游戏目录说明：**
  - CS2 根目录：`Counter-Strike Global Offense`
  - CSGO 根目录：**小写的 `csgo`**
  ![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702165258.png)

### 🔧 2.2 安装 MOD

#### 📁 MOD 组成
- 插件框架：Metamod + Sourcemod  
- 机器人插件：Betterbot

#### 🔗 下载地址
- [📥 Betterbot 插件包 - 123 网盘（高速下载）](https://www.123684.com/s/8C4RTd-6mE63)

#### 📂 插件目录结构如下：
![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702165934.png)

#### 📌 安装步骤
- 解压后将插件目录 **全部复制并替换** 到 `csgo` 根目录下  
  示例路径：  
  `Steam\steamapps\common\Counter-Strike Global Offensive\csgo\`
- 替换后的目录示意：
![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702170137.png)


---

### ▶️ 2.3 启动游戏

#### 🖥️ 2.3.1 服务器模式

##### 📌 创建服务器
编辑 `start.bat` 文件，写入以下启动项：
```bash
srcds_run.exe -game csgo -tickrate 128 -maxplayers_override 10 +ip 0.0.0.0 -usercon map de_dust2 +game_type 0 +game_mode 0
```

参数说明：
- `tickrate`: 每秒更新次数（CSGO 默认 64）
- `game_type` & `game_mode`: 游戏模式  
  - [游戏模式参考文档](https://developer.valvesoftware.com/wiki/CS:GO_Game_Modes)  
  - +game_type 0 +game_mode 0 → 休闲模式  
  - +game_type 0 +game_mode 1 → 竞技模式
- `maxplayers_override`: 最大玩家数
- `port`: 游戏端口

双击 `start.bat` 即可运行服务器：  
![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702173635.png)

##### 🎯 玩家连接服务器

1. 启动时选择 **csgo_legacy_version**
   ![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702171933.png)
2. 启动后进入设置 → **启用开发者控制台**
   ![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702172158.png)
3. 游戏主界面按 `~` 打开控制台 → 输入：  
   ```bash
   connect xxx.xxx.xxx.xxx
   ```
   ![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702174035.png)

---

### 🌐 2.4 局域网模式

#### 🔧 插件启动设置
查看插件目录内：  
`【1】每次更新必看！更新日志！.txt` 文件

示例命令如下：
```bash
开启插件：启动项加入 -insecure -tickrate 128 -worldwide -maxplayers_override 10
关闭插件：启动项删除 -insecure -tickrate 128 -worldwide -maxplayers_override 10
```

#### 🛠 启动参数设置
- CS2 → 属性 → 通用 → 启动选项：
```bash
-insecure -tickrate 128 -worldwide -maxplayers_override 10
```
![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702171703.png)

- 启动时选择 **csgo_legacy_version**
- 启用开发者控制台


#### 🖥️ 局域网主机建立服务器
主机进入：**机器人练习赛**  
![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702172313.png)

进入后按 `~` 打开控制台，输入控制命令。

常用命令如下（可参考根目录的 `2 必须学会的指令.txt`）：

```bash
# 添加队伍
team astralis ct
team g2 t

# 控制机器人
bot_stop 1    # 机器人静止
bot_stop 0    # 机器人恢复移动

# 更改阵营名
mp_teamname_1 XXX
mp_teamname_2 XXX

# 设置游戏参数
mp_freezetime X             # 开局禁止时间 X 秒
mp_halftime_duration X      # 中场换边时间 X 秒
mp_restartgame 1            # 一秒后重置对局

# 聊天框命令（英文输入法下的 !）
!dao          # 更换匕首
!pf           # 更改皮肤
!st           # 更改手套
!music        # 更改音乐盒
!s / !tz      # 更改贴纸
!s xxx        # 搜索指定贴纸
```

#### 👥 局域网玩家连接主机
进入游戏 → 控制台输入：  
```bash
connect 192.168.xxx.xxx
```
![](https://techla-img.oss-cn-hangzhou.aliyuncs.com/CODE/WEB/20250702174035.png)

即可进入游戏。
