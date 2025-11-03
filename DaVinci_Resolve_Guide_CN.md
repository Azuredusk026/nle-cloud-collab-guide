# DaVinci Resolve 云协作 省流版新手完整教程

## 什么是 DaVinci Resolve 云协作？
简单说，它是让多人同时访问同一个项目库（Project Library）的功能。  
项目数据（时间线、元数据、标记）保存在数据库，而视频素材（media）在各自电脑本地或云端。  

三种主要模式：
- **Local Database（本地）**：仅自己使用  
- **Network Project Server（局域网共享）**：同一网络多台电脑协作  
- **Blackmagic Cloud Project Library（云端托管）**：跨地区云端协作

---

## 1. 准备工作
1. 安装 **DaVinci Resolve 18 或以上版本**  
2. 注册并登录 **Blackmagic Cloud**：[https://cloud.blackmagicdesign.com](https://cloud.blackmagicdesign.com)  
3. 任选一种存储方式：  
   - 云盘 - Google Drive / Dropbox / OneDrive  
   - NAS 存储 - Synology（群晖）/ QNAP（威联通）  
   - 移动硬盘

---

## 2. 单人使用：跨设备同步项目
### 目标
在家与出差笔电间无缝切换编辑同一项目。  

### 方法一：使用 Blackmagic Cloud
1. 在 Resolve 左上角点击 **Project Manager → Create New Library → Cloud**。  
2. 登录 Blackmagic Cloud，创建一个新的 Project Library（每月约 5 美元）。  
3. 在 A 电脑上创建项目并保存。  
4. 在 B 电脑登录同一账号 → 打开同一 Cloud Library → 项目同步自动完成。  

**优点：** 真正的云同步；不需手动传输文件。  
**缺点：** 仅同步项目数据，不包含素材。  

**素材同步建议：**
- 把视频素材放在 Google Drive 或 NAS 中，同步到两个设备相同路径。  
- 使用 **“Relink Media”** 功能快速重新链接素材。  

### 方法二：使用云盘同步
1. 在 A 电脑进入  
   `C:\Users\<用户名>\AppData\Roaming\Blackmagic Design\DaVinci Resolve\Support\Resolve Disk Database\Resolve Projects`  
   复制整个项目文件夹到你的云盘（例如 Dropbox）。  
2. 在 B 电脑相同路径粘贴并覆盖。  
3. 打开 Resolve，项目即可显示。  

**注意：** 云盘需确保同步完成再关闭软件。  

---

## 3. 团队协作：多人同时剪辑同一项目
### 目标
团队成员在不同地方实时编辑、调色、加特效.

### 方法一：使用 Blackmagic Cloud Project Library（推荐）
1. 管理员登录 [Blackmagic Cloud](https://cloud.blackmagicdesign.com)。  
2. 点击 “Create Library” → 设置名称 → 付费启用。  
3. 在网页端添加协作者的邮箱（需注册 Blackmagic ID）。  
4. 协作者在 Resolve 中登录同一 ID → Project Manager → 看到该 Library。  
5. 创建项目后右键 “Collaborate”。  
6. 进入项目后即可看到：
   - “Locked” 图标（防止两人同时编辑同一区域）  
   - 实时聊天窗口  
   - “Markers” 支持评论与同步  

**协作逻辑：**
- 项目数据在云端实时更新。  
- 媒体素材由各自本地或云盘共享路径解决。  

### 方法二：搭建 Project Server（局域网 / NAS）
1. 安装 **DaVinci Resolve Project Server**（免费）。  
2. 启动并创建数据库 → 设置 “Share” 权限。  
3. 在团队内网或 NAS 上开放端口。  
4. 成员在 Resolve 中点击 **Project Manager → Connect → 输入 IP 地址**。  
5. 登录后即可多人同时编辑。  

**适用场景：**  
同一个办公室或校园局域网；不适合远程使用。  

---

## 4. 混合模式：NAS + 云项目
### 场景
素材体积大，不想放在 Cloud，只希望同步项目版本。  

### 推荐组合
- **Project Library** 放在 Blackmagic Cloud（轻量）  
- **视频素材** 放在 NAS（大容量）  
- **缓存/代理文件** 放在本地（快速）  

**步骤：**
1. 在 Cloud 创建项目。  
2. 在 NAS 建立共享文件夹（例如 `\\NAS\MediaPool`）。  
3. 各成员在 Resolve 的 “Preferences → Media Storage” 中添加相同路径名（路径映射）。  
4. 确保项目设置里勾选“Use Relative Paths”。  
5. 每人只需连接 NAS，即可读取相同素材。  

---

## 5. 单人版本管理
### 版本保存
- Resolve 会自动保存项目历史（Project Backups）。  
- 在 “Project Settings → Project Backups” 勾选自动保存。  
- 可在 Project Manager 右键 → “Project Backups” 查看任意历史版本。  

---

## 6. 不同设备传输与离线编辑
### 场景：出差带笔电剪辑
1. 在主机导出 `.drp` 文件（不含媒体）或 `.drb`（含库结构）。  
2. 用移动硬盘复制媒体。  
3. 在笔电上打开 `.drp` 并 Relink Media。  
4. 回家后再导出最新 `.drp` 覆盖主机项目。  

### 进阶技巧：使用代理（Proxy）文件
1. 在主机生成低分辨率代理。  
2. 上传代理到云盘。  
3. 在笔电上只下载代理文件。  
4. 编辑完成后导出 XML 或 DRP 文件，主机重新链接原始素材导出成品。  

---

## 7. 常见问题 FAQ
**Q: 为什么项目打不开？**  
A: 检查是否所有成员 Resolve 版本一致（建议都用最新稳定版）。  

**Q: 媒体离线？**  
A: 打开 Project Settings → Relink Media → 选择正确路径。  

**Q: 同时编辑冲突怎么办？**  
A: Resolve 会自动锁定 Bin 或 Timeline。可右键“Request Unlock”。  

**Q: 云端项目太多太乱？**  
A: 定期右键 → Archive Project。  

**Q: 网络太慢？**  
A: 改用本地缓存 + Proxy 代理文件，云端只同步项目。  

---

## 结语
开始你的 Resolve 云协作之旅吧！  
不论你是个人创作者，还是跨地区团队项目成员，这套系统都能让协作更稳、更快、更安全。  

**推荐阅读：**
- [Blackmagic Cloud 官方指南](https://www.blackmagicdesign.com/products/davinciresolve/collaboration)  
- *DaVinci Resolve Manual* 第28章 Collaboration  
- [CreativeVideoTips: Cloud Collaboration 教程](https://creativevideotips.com/tutorials/blackmagic-cloud-collaboration-in-davinci-resolve-18)

---

**作者：Azuredusk026**  
**更新时间：2025-11-2**


