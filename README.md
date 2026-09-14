# 作品集

> 游戏引擎 / C++ 系统与图形 / Unity 游戏开发 / 桌面工具

本作品集按技术方向划分为 3 个模块；每个模块中的项目按 GitHub **创建时间从新到旧** 排列。

## C++ 引擎与基础库

聚焦引擎架构、底层系统、物理仿真与 ECS 基础设施。

### Butter（2026.08）

**技术栈：** C++20、CMake、物理引擎、GJK/EPA、PBD

一个强调流畅 API 与零开销抽象的现代 C++20 头文件物理引擎。项目同时提供 3D 核心 API 和独立 2D 物理模块，覆盖刚体、碰撞、约束、查询、触发器及求解器。

- 实现球体、盒体、胶囊体、凸包和索引三角网格碰撞，包含 SAT、GJK/EPA 等窄相检测
- 支持冲量求解器与 PBD 求解模式、摩擦、位置修正、睡眠、碰撞过滤和关节
- 使用空间哈希宽相、AABB 查询、Raycast 和进入/退出触发器
- 提供 2D/3D 示例、基准与 9 组测试目标，并包含动态断裂和爆炸堆叠演示

**链接：** [源码](https://github.com/chnnasn/Butter)

### ekit（2026.08）

**技术栈：** C++20、ECS、Sparse Set、Thread Pool、CMake

一个面向游戏引擎的头文件式 C++20 ECS 库，结合 Sparse Set 存储与接近 C# LINQ / Unity DOTS 的流式 API，重点改善 ECS 查询的可读性和编译期诊断。

- 使用强类型、带 generation 的实体句柄，避免悬空实体和裸 `uint32_t` 标识
- 同时支持 dense archetype SoA 组件和按类型存储的 Sparse Set 组件
- 查询链支持 `Where`、`With`、`Without`、`Optional`、`ForEach` 和 `Count`，无需类型擦除或逐实体虚调用
- 提供线程池并行查询、数据依赖 DAG 调度器、事件系统和可运行示例

**链接：** [源码](https://github.com/chnnasn/ekit) · [v0.1.0](https://github.com/chnnasn/ekit/releases/tag/v0.1.0)

### TomCat_Engine（2025.09）

**技术栈：** C++20、OpenGL 4.6、Dear ImGui、Box2D、.NET 10、CMake/Premake

一套面向 2D 游戏开发的完整引擎、编辑器和项目管理 Hub，覆盖渲染、ECS、物理、资源管线、脚本、UI、音频、场景、预制体和独立 Player 打包流程。

- 实现 OpenGL 批量精灵渲染、Scene/Game 双视图、实体拾取、图集子资源和 Animator 状态机
- 构建稳定 `AssetHandle`、`.tcmeta` v2、SHA-256 产物缓存、依赖追踪和后台导入协调机制
- 集成固定 60 Hz Box2D 物理、编辑器碰撞体工具、Tag/Layer 与碰撞矩阵
- 支持 .NET 10 C# 脚本编译、可回收 Play 域、Inspector 序列化字段和完整游戏 API
- 提供 Unity 风格的 Hierarchy/Inspector/Project 工作流、撤销重做、自动保存、Prefab、输入、UI 和音频系统
- 通过 `.tcpak` v6、独立 Player 模板和私有 .NET 运行时完成一键构建与发布，并配置 CI 回归与打包工作流

**链接：** [源码](https://github.com/chnnasn/TomCat_Engine) · [v0.1.0](https://github.com/chnnasn/TomCat_Engine/releases/tag/v0.1.0)

## Unity 游戏开发

覆盖战斗 AI、群体导航、性能优化、玩法系统与完整游戏原型。

### Fire（2026.07）

**技术栈：** Unity、C#、URP、Compute Shader、AI Navigation、Input System

一款低多边形 FPS 丧尸波次生存游戏。项目基于第三方 FPS 框架完成角色和武器基础能力，并在此基础上实现敌人 AI、群体导航、波次、成长、对象池、技能和移动端输入适配。

- 实现敌人 `Birth / Chase / Attack / Dead` 状态机，以及基于 BFS 的共享 FlowField 群体导航
- 使用 SpatialGrid 支撑邻居查询、局部避让和刷怪合法性检查，并支持 FlowField 局部重建
- 通过 AI LOD、导航分批更新、对象池和 NonAlloc API 降低大量敌人同时更新时的 CPU 与 GC 压力
- 接入 Compute Shader GPU Skinning 路径与标准渲染回退，并以 ScriptableObject 分离波次、Buff、敌人和地图配置
- 独立实现经验升级、随机 Buff、自动技能及移动端触控输入适配

**链接：** [源码](https://github.com/chnnasn/Fire)

### Cat_Coffee（2025.02）

**技术栈：** Unity、C#、等距网格、DOTween、UGUI

一个 Unity 等距视角网格建造原型，重点验证设施放置、时间推进与 UI 面板切换之间的完整交互链路，适合展示 Unity 系统拆分和玩法原型实现能力。

- 使用泛型 `Grid<T>` 生成等距网格 Mesh，统一处理坐标映射、格子值和占用状态
- 通过事件与委托驱动建筑选择、放置状态、鼠标交互和物体描边
- 时间系统支持秒、分、时、日、月、季节推进，并可响应游戏暂停状态
- 使用 Singleton、BasePanel 和 UIManager 组织面板层级及 DOTween 动效

**链接：** [源码](https://github.com/chnnasn/Cat_Coffee)

### Light（2024.10）

**技术栈：** Unity、C#、2D Physics、URP、Input System、AssetBundle

一款围绕光线、镜面与激光交互展开的 2D 平台解谜游戏。玩家需要在不同角色模式与镜面状态间切换，利用激光反射、镜面搬运和传送能力完成多章节关卡。

- 实现包含 Idle、Move、Jump、Dash、Mirror Mode、Hold/Control Mirror、Transfer 和 Death 等状态的玩家有限状态机
- 实现激光反射、镜面联动、敌对激光与敌人 AI
- 提供多章节关卡、关卡进度保存、场景切换与结算流程
- 搭建事件中心、资源/AssetBundle 管理、对象池、计时器、UI、音乐和移动端摇杆等通用框架
- 同时适配桌面与移动端输入，并使用 Sprite Shape 和自定义 Shader 表现部分交互效果

**链接：** [源码](https://github.com/chnnasn/Light)

### Reverse Loop / TencentGameJam（2024.09）

**技术栈：** Unity、C#、URP、2D Physics、Line Renderer、UGUI

一款 Game Jam 时间回溯解谜平台游戏。玩家移动时系统会持续记录轨迹，回溯结束后生成沿历史路径行动的敌对影子，玩家需要规划路线避开“过去的自己”并抵达终点。

- 使用 `Before / StartRecall / Recall / After` 状态机拆分完整时间回溯流程
- 实时采样玩家位置并绘制轨迹，通过逆序读取记录点完成回溯播放
- 实现历史影子系统，使敌人复用玩家轨迹、自动转向并在重演结束后回收
- 编写 2D 移动、多射线地面检测、跳跃、重力、暂停、异步场景加载和越界重置
- 接入相机震动、轨迹遮罩、动画、音频与 UI 反馈

**链接：** [源码](https://github.com/chnnasn/TencentGameJam)

### Shelter（2024.09）

**技术栈：** Unity、C#、QFramework、UGUI、Tilemap、Particle System

一款 2D 生存策略游戏。玩家需要在风暴到来前派遣居民探索、收集资源、建设避难所，并在逐渐增强的资源与防御压力下维持人口生存。

- 设计资源、人口、探索、建造和风暴结算构成的核心玩法循环
- 使用网格坐标映射、占用字典和建造状态管理实现设施放置
- 实现居民派遣、食物消耗、探索收益、人员损耗和新增人口结算
- 通过阶段倒计时、每日消耗、周期性风暴和递进式难度形成生存压力
- 使用 QFramework 拆分关卡、建筑、物品和探索数据模型，并接入 UGUI 与粒子反馈

**链接：** [源码](https://github.com/chnnasn/Shelter)

---

更多代码与更新请见 [GitHub @chnnasn](https://github.com/chnnasn)。

## 桌面工具与工程化

围绕 Electron、Node.js、自动打包与持续发布，展示桌面产品交付能力。

### DeepSeek-Harness-Desktop（2026.08）

**技术栈：** Electron、Node.js、PowerShell、NSIS、GitHub Actions

将开源 DeepSeek Harness 封装为 Windows 桌面应用，用户无需单独安装 Node.js、DeepSeek Harness 或 Microsoft Edge，下载安装包即可使用。项目已获得 100+ GitHub Stars。

- 使用 Electron 自带 Node 启动和管理 `dsh` 服务，实现单实例锁、关窗停服与服务进程树清理
- 内置插件商城、插件启停、主题色和背景图自定义，并预装常用 Web UI 扩展
- 通过运行时裁剪移除多平台二进制、调试文件、类型声明和文档，将安装包从约 150 MB 降至约 99 MB
- GitHub Actions 每日跟踪上游版本、自动打包并发布 NSIS 安装包

**链接：** [源码](https://github.com/chnnasn/DeepSeek-Harness-Desktop) · [最新版本](https://github.com/chnnasn/DeepSeek-Harness-Desktop/releases/tag/v0.1.5-rc.1)

---

更多代码与更新请见 [GitHub @chnnasn](https://github.com/chnnasn)。