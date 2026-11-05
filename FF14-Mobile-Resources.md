# 《FF14：水晶世界》手游资源与研究资料总览

> 本文汇总《FF14：水晶世界》手游的资源入口、工具、社区资料和研究结论，方便下载、归档和后续资产研究。
>
> **状态说明**：文中的“已确认”表示该资源曾被调研确认存在，不代表当前链接仍然在线。网盘、论坛附件、镜像站和第三方下载页可能随时失效。

## 1. 项目概况

| 项目 | 信息 |
| --- | --- |
| 游戏名称 | 《FF14：水晶世界》/ Final Fantasy XIV Mobile |
| 开发与发行背景 | 腾讯光子 × Square Enix 授权手游 |
| Android 包名 | `com.tencent.tmgp.fmgame` |
| 引擎 | UE4.25 |
| 主要资源格式 | `.pak`、`.ucas`、`.utoc` |
| 资源处理方向 | UE 资产浏览、模型/贴图/音频导出、静态分析 |
| 停服时间 | 2026-09-30 |
| 推荐版本 | 1.0.22.x，优先 1.0.22.19 全量备份 |

### 1.1 资源分层

从研究用途看，资料可以分为四层：

1. **客户端安装包**：APK 或 IPA，主要用于获得程序入口、原生库和版本信息。
2. **游戏资源包**：`.pak`、`.ucas`、`.utoc` 等，包含模型、贴图、音频、动画和其他 UE 资源。
3. **已整理资产**：社区已经导出的模型、贴图、预览图和 raw data。
4. **代码与运行时研究资料**：`libUE4.so`、DEX、Lua 字节码、映射文件和社区逆向记录。

需要注意：APK 通常不等于完整客户端。完整资源可能需要单独的资源包备份，不能假设仅下载 APK 就能获得全部模型和贴图。

## 2. 推荐获取顺序

### 2.1 最短路径：只看资产

适合只想浏览手游独有外观、模型或贴图的情况：

1. 先获取 **XIV Mobile Rips v1.6** 等已经解包的资产。
2. 参考其预览图、文件夹分类和 raw data，确认资源命名与内容。
3. 需要更多资源时，再下载 Gildor 论坛中的全量备份。
4. 使用 FF14 手游专用 `umodel` 或 FModel 进行浏览和导出。

### 2.2 完整路径：从原始资源包开始

1. 下载并保存 1.0.22.19 全量客户端备份。
2. 保存 Gildor 论坛主帖、专用 `umodel`、quickbms 脚本和相关说明页的离线副本。
3. 按资源包实际格式选择专用 `umodel`、FModel、CUE4Parse、`repak`、`retoc` 或 quickbms。
4. 如资源加密或工具无法读取，按照对应工具说明准备合法取得的本地密钥和脚本。
5. 导出后建立版本、来源、文件哈希和处理工具记录。

### 2.3 代码静态分析路径

1. 获取 APK，并核对包名、版本号和签名信息。
2. 使用 jadx 查看 DEX 中的 Java/Kotlin 层代码。
3. 使用 Ghidra 分析 native 库，例如 `libUE4.so`。
4. 只有在合法授权和本地研究范围内处理加固、符号或运行时信息。
5. 不要收集、复制或使用账号令牌、设备绑定数据、Cookie、私有服务器凭据等敏感信息。

## 3. 核心资源入口

### 3.1 Gildor 论坛主帖

**入口：**

`https://www.gildor.org/smf/index.php?topic=9302.0`

该帖标题为 `[UE4] Final Fantasy XIV Mobile`，是最重要的资源枢纽之一。帖内或关联楼层包含：

| 内容 | 用途 | 状态 |
| --- | --- | --- |
| 1.0.22.19 全量备份 | 获取停服前完整资源包 | URL 已解析，存活需自行确认 |
| FF14 Mobile 专用 `umodel` build | 浏览和提取该游戏 UE 资源 | 已确认存在 |
| quickbms 脚本及说明 | 处理专用工具不支持的资源 | 已确认存在 |
| AES 相关讨论入口 | 为本地资源解包准备必要配置 | 需遵守法律与授权边界 |

### 3.2 专用 umodel build

**入口：**

`https://www.gildor.org/smf/index.php?topic=8304.msg42970#msg42970`

使用专用 build 时应注意：

- 应优先使用针对 FF14 手游准备的专用 build。
- 不应默认官方通用 release 能正确解析该游戏的全部资源。
- 某些骨骼网格或材质可能由于游戏自定义实现而无法正常显示，这不一定代表资源损坏。

### 3.3 1.0.22.19 全量备份

**入口：**

`https://pixeldrain.com/l/3cyoZt5X`

用途：获取停服前最终版本完整客户端或资源备份。

注意事项：

- 当前链接是否仍然可下载需要自行核实。
- Pixeldrain 等免费文件服务可能清理长期未访问内容。
- 下载后应至少保留两份本地副本，并记录下载日期、文件大小和 SHA-256 哈希。
- 不要运行来源不明的可执行文件；先进行杀毒和哈希核对。

### 3.4 AES 与 quickbms 相关入口

以下入口可用于查找相关资料：

| 资源 | URL | 说明 |
| --- | --- | --- |
| AES 密钥讨论帖 | `https://cs.rin.ru/forum/viewtopic.php?f=10&t=100672` | 帖内搜索 `Final Fantasy XIV Mobile`；部分内容可能要求注册 |
| Gildor 密钥索引 | `https://www.gildor.org/smf/index.php?topic=7304.0` | UE4/UE5 密钥索引或镜像入口 |
| quickbms 脚本说明 | `https://cs.rin.ru/forum/viewtopic.php?p=3355306#p3355306` | 新版资源包处理说明 |

这些入口只用于合法取得的本地资源研究。本文不提供、复制或传播任何账号凭据、运行时令牌或未经授权的敏感数据。

## 4. 已解包资产与 Mod 资料

### 4.1 XIV Mobile Rips v1.6

**入口：**

`https://www.xivmodarchive.com/modid/150972`

这是重要的已解包成品资源之一，包含：

- 手游独有发型、装备、坐骑等资产。
- 已整理的文件夹结构和预览图。
- 男性与女性角色资源，例如 `c0101` 和 `c0201`。
- raw data，可作为自己解包结果的对照样本。
- Kaitou_XIV 的导出教程或相关说明。

使用建议：

1. 先阅读资源页的授权和传播要求。
2. 下载后保留原始压缩包，不要只保存导出结果。
3. 将成品资产作为验证样本，而不是默认代表全量资源。
4. 按作者要求免费使用和传播，不要将其放入未经许可的付费墙。

### 4.2 其他手游移植资产

| 内容 | URL | 说明 |
| --- | --- | --- |
| Penguin Suit | `https://www.xivmodarchive.com/modid/150851` | 手游企鹅玩偶服移植资产 |
| Street Graffiti Set | `https://www.xivmodarchive.com/modid/151093` | 街头涂鸦套装移植，附 Blender 相关工具链 |
| Blender 顶点组转换 addon | `https://www.xivmodarchive.com/modid/151067` | 将模型顶点组转换为 FF14 骨骼命名或结构 |
| Wolf's Tail 版本一 | `https://www.xivmodarchive.com/modid/155488` | 狼尾装饰移植 |
| Wolf's Tail 版本二 | `https://www.xivmodarchive.com/modid/155522` | 另一角色体型或版本的狼尾移植 |
| Heliosphere | `https://heliosphere.app/` | XivModArchive 的替代前端或镜像入口 |

这些资源适合作为模型结构、材质命名、骨骼权重和导出流程的参考。具体下载条件、作者许可和当前可用性应以页面现状为准。

## 5. APK 获取入口

以下第三方页面曾提供相关 APK：

| 来源 | URL | 页面记录 |
| --- | --- | --- |
| 游侠手游 | `https://m.ali213.net/aznew/687387.html` | v1.0.2，约 143.5 MB |
| 多特软件站 | `https://m.duote.com/android/1178174.html` | 页面记录为 v4.8.7 |
| 游戏鸟 | `https://m.youxiniao.com/game/jbbixy/` | v1.0.2，页面包含签名或 MD5 信息 |
| 奇珀网 | `https://m.7po.com/downlist/31395.html` | v1.0.2 页面 |
| 当游网 | `https://m.3h3.com/az/385966.html` | v1.0.2 页面 |

### 5.1 APK 安全检查清单

下载第三方 APK 后，至少检查：

- 包名是否为 `com.tencent.tmgp.fmgame`。
- 版本号是否与页面描述一致。
- 文件大小是否与页面描述大致一致。
- 页面提供的 SHA-256、MD5 或签名信息是否匹配。
- APK 是否被重新签名、篡改或捆绑额外权限。
- 不在主力设备或包含真实账号的设备上直接安装未知 APK。

### 5.2 APK 的用途边界

APK 更适合作为：

- DEX 和 AndroidManifest 静态分析入口。
- `libUE4.so`、原生库和版本信息来源。
- 包名、资源路径和加载逻辑确认材料。

APK 不应被视为完整资源包。完整 `.pak` 等资源需要另行获取，尤其是在原 CDN 已停止服务的情况下。

## 6. 通用资源处理工具

| 工具 | 官方或主要入口 | 主要用途 |
| --- | --- | --- |
| FModel | `https://github.com/4sval/FModel/releases` | 图形化浏览和导出 UE 资源 |
| CUE4Parse | `https://github.com/FabianFG/CUE4Parse` | FModel 使用的 C# 解析库，也可用于程序化处理 |
| repak | `https://github.com/trumank/repak` | 命令行处理 `.pak` |
| retoc | `https://github.com/trumank/retoc` | 命令行处理 IoStore 相关 `.utoc`/`.ucas` |
| quickbms | `https://aluigi.altervista.org/quickbms.htm` | 运行 BMS 脚本，处理特殊或不兼容格式 |
| UEViewer / umodel 源码 | `https://github.com/gildor2/UEViewer` | UE 资源浏览器源码；本游戏优先使用专用 build |
| jadx | `https://github.com/skylot/jadx` | DEX 转 Java 代码并浏览 Android 层逻辑 |
| Ghidra | `https://github.com/NationalSecurityAgency/ghidra` | native 库静态分析 |

### 6.1 工具选择建议

- **优先验证资源**：使用包含游戏适配的专用 `umodel`。
- **快速浏览和批量导出**：使用 FModel。
- **IoStore 资源**：尝试 CUE4Parse、`retoc` 或 FModel 的对应支持。
- **特殊封装或自定义处理**：按照来源说明使用 quickbms。
- **代码静态分析**：jadx 负责 DEX，Ghidra 负责 ELF/native 库。

不要同时修改多个工具的输入文件。建议每一步输出到独立目录，以便定位是资源包、密钥配置还是工具版本造成的问题。

## 7. FModel Mappings 结论

目前没有找到该游戏现成的 `usmap`、`GNames` 或 `GObjects` 文件。Gildor 专用 `umodel` 路线可能不要求这些 mappings，但如果使用 FModel 并希望显示更可读的类名，可能需要自己生成。

### 7.1 可参考工具

| 工具 | URL | 适用方向 |
| --- | --- | --- |
| UE4Dumper | `https://github.com/kp7742/UE4Dumper` | Android 端 UE4 数据提取参考 |
| UnrealDumper-4.25 | `https://github.com/guttir14/UnrealDumper-4.25` | 与 UE4.25 版本对应 |
| UnrealMappingsDumper | `https://github.com/OutTheShade/UnrealMappingsDumper` | 生成 `.usmap` 的参考工具 |
| Dumper-7 | `https://github.com/Encryqed/Dumper-7` | 社区常用的 UE 数据导出参考 |
| UnrealFinderTool | `https://www.unknowncheats.me/forum/unreal-engine-4-a/338695.html` | GObjects/GNames 定位参考 |

### 7.2 现实限制

- 工具版本必须和目标 UE 版本、平台及编译方式匹配。
- Android ELF 与 PC 进程环境不同，PC 教程不能直接照搬。
- 目前未找到针对 `fmgame` 的专用 mappings 提取脚本。
- 运行时分析必须在自己拥有或明确获准分析的环境中进行。

## 8. Lua 脚本层资料

目前没有找到该游戏专用的 Lua 导出脚本，只有通用参考：

| 资源 | URL | 用途 |
| --- | --- | --- |
| Tencent sluaunreal | `https://github.com/Tencent/sluaunreal` | 了解腾讯 UE 手游 Lua 集成方式 |
| unluac | 通用项目，可通过代码托管平台搜索 | 尝试反编译标准 Lua 字节码 |

注意：腾讯或游戏自身可能对 Lua 字节码进行魔改、压缩、加密或二次封装。不能假设标准 `unluac` 能直接处理目标文件。

## 9. 中文社区与内容索引

### 9.1 B 站展示视频

这些内容主要适合作为外观和资产存在性的对照，不一定包含完整解包教程。

| BV号或短链 | 内容 |
| --- | --- |
| `BV1bB3MzUEAG` | 手游原创炎火套，涉及发型、脚印特效或时装 |
| `BV1nHFhzzEhF` | 双丸子辫、狼尾辫等手游独有发型 |
| `BV1TJ75zmErp` | 兜兜企鹅坐骑 |
| `BV1r9HbzsEU5` | 魔科学滑板及紫菱配色 |
| `https://b23.tv/zMesO7W` | 弈后棋域套，可能是稀缺且未正式上线的套装 |

### 9.2 NGA

| 主题 | URL 或主题号 | 用途 |
| --- | --- | --- |
| 关服前讨论 | `tid=47642904` | 讨论解包中存在但未发售的外观 |
| 停运公告 | `tid=47201677` | 停服信息参考 |
| iOS 脱壳讨论 | `tid=44402434` | iOS IPA 研究线索；第三方站点安全性需自行判断 |

### 9.3 微博整理帖

| 内容 | URL |
| --- | --- |
| 全外观与全发型文字清单 | `https://m.weibo.cn/detail/5349239410657426` |
| 发型细目 | `https://m.weibo.cn/detail/5349224935328131` |

相关外观关键词包括豆柴睡衣、君临棋域、弈后棋域、东方祥云、东方锦裙、街头涂鸦、滑雪、机能、炎火、花漾礼裙、降神节狮子和企鹅玩偶服等。该清单更适合用于资产命名和展示内容的交叉核对，不应直接视为资源文件目录。

### 9.4 中文通用教程

| 教程 | URL | 方向 |
| --- | --- | --- |
| PinkD UE4 加密资源教程 | `https://blog.pinkd.moe/others/2021/11/22/unpack-encrypated-ue4-game-resource` | UE AES 与资源解包流程 |
| BearChild FModel 教程 | `https://www.bearchild.top/2024/08/30/游戏开发/逆向/[UE]FModel资源解包流程/` | FModel 与 AES 工具使用参考 |
| AWAKE Wiki | `https://awakewiki.org/reversing/frameworks/unreal-engine/` | 从 native 库分析 UE 资源、IoStore 处理思路 |

### 9.5 已知空白区域

在 52pojie、看雪、知乎和贴吧中，目前没有发现针对 `com.tencent.tmgp.fmgame` 的专门公开教程，也没有确认到公开百度网盘资源。因此，中文社区更适合作为展示、外观清单和线索补充渠道，而不是主要原始资源来源。

## 10. 协议、私服与端游资料的边界

目前没有发现该手游的公开私服、协议文档或完整服务器实现。以下端游项目只能用于理解概念，不能当作手游服务端：

- Sapphire：`https://github.com/SapphireServer/Sapphire`
- Project Meteor、Garlemald Server
- meteor-decomp
- Deucalion、ffxivmon、Velcro、xiv.dev
- TexTools 及相关端游资源教程

必须区分：

- 端游协议和手游协议不是同一套实现。
- 端游私服项目不能直接作为手游服务端。
- 没有公开协议成果时，网上下载资源无法自动解决服务器模拟问题。
- 不应尝试访问、重放或利用真实用户的账号、Token、服务器接口或私有数据。

## 11. 建议的本地目录结构

```text
FF14-Mobile-Research/
├─ 00-docs/              # 原始链接、说明、下载记录
├─ 01-apk/               # APK/IPA，只读保存
├─ 02-client-backup/     # 1.0.22.19 等原始备份
├─ 03-tools/              # umodel、FModel、quickbms 等工具
├─ 04-keys-config/        # 合法取得的本地配置，不提交到公开仓库
├─ 05-unpacked/           # 原始解包输出
├─ 06-exported/           # glTF、PNG、WAV 等导出结果
├─ 07-mappings/           # usmap、GNames、GObjects 等本地结果
├─ 08-community-reference/ # 视频、外观清单、截图和对照资料
└─ hashes.txt             # 文件哈希与版本记录
```

### 11.1 下载与归档记录模板

每个文件建议记录：

| 字段 | 示例 |
| --- | --- |
| 资源名称 | `FF14Mobile_1.0.22.19_backup` |
| 来源 URL | 原始下载地址 |
| 下载日期 | `YYYY-MM-DD` |
| 文件大小 | 下载后的实际大小 |
| SHA-256 | 本地计算值 |
| 版本 | `1.0.22.19` |
| 文件类型 | APK、PAK、UCAS、UTOC、ZIP 等 |
| 处理工具 | 工具名和版本 |
| 状态 | 原始、已解包、已导出、损坏、待验证 |
| 备注 | 密钥配置、错误信息、特殊参数等 |

## 12. 风险、版权与安全边界

### 12.1 下载安全

- 优先使用项目官方仓库、原作者页面和可追溯的社区入口。
- 不要运行未经验证的破解工具、所谓“一键解包器”或带捆绑安装器的程序。
- 对 APK、压缩包和可执行文件计算哈希并进行安全扫描。
- 使用隔离目录或虚拟机处理不信任文件。
- 对需要注册的论坛，使用专门的研究账号，不要重复使用重要账号密码。

### 12.2 隐私安全

- 不要导出或分享真实账号 Token、Cookie、设备标识、支付信息或私有服务器地址。
- `data/data`、`shared_prefs` 和数据库中可能包含账号绑定、缓存和运行时信息；本文不建议为了资源研究收集这些数据。
- 研究时只使用公开下载资源或自己有明确权限处理的文件。

### 12.3 版权与传播

- 仅在当地法律、游戏授权和资源作者许可范围内使用。
- 不要将原始商业资源重新打包为付费内容。
- 对社区作者提供的导出资产，保留作者署名和原始许可说明。
- 公开发布前确认是否涉及未公开内容、第三方版权或平台条款。

## 13. 当前结论

当前最有价值的公开资源组合是：

1. **Gildor 全家桶**：主帖、FF14 手游专用 `umodel`、quickbms 说明和 1.0.22.19 全量备份。
2. **XIV Mobile Rips v1.6**：已经整理好的手游独有模型、装备、发型、坐骑和 raw data。
3. **通用 UE 工具链**：FModel、CUE4Parse、`repak`、`retoc`、quickbms、jadx 和 Ghidra。
4. **中文索引资料**：B 站展示、NGA 讨论、微博外观清单和通用 UE 解包教程。
5. **明确空白**：没有确认到公开的手游专用 mappings、Lua 导出工具、协议文档或私服实现。

### 最终建议

如果目标是保存网上资源，优先级应为：

1. 先确认并下载 1.0.22.19 全量备份。
2. 同步保存 Gildor 主帖、专用 build 和工具说明。
3. 下载 XIV Mobile Rips v1.6 作为已解包对照样本。
4. 再补齐 FModel、CUE4Parse、`repak`、`retoc` 和 quickbms。
5. 最后整理 APK、社区视频、外观清单和哈希记录。

如果目标只是查看或导出资产，不必优先研究协议、私服、账号运行时数据或本地私有目录；这些方向目前没有现成公开成果，而且存在更高的隐私、授权和安全风险。
