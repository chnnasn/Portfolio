# C++ 引擎与基础库

> [← 返回作品集](../../README.md)

聚焦引擎架构、底层系统、物理仿真与 ECS 基础设施。

## Butter（2026.08）

**技术栈：** C++20、CMake、物理引擎、GJK/EPA、PBD

一个强调流畅 API 与零开销抽象的现代 C++20 头文件物理引擎。项目同时提供 3D 核心 API 和独立 2D 物理模块，覆盖刚体、碰撞、约束、查询、触发器及求解器。

- 实现球体、盒体、胶囊体、凸包和索引三角网格碰撞，包含 SAT、GJK/EPA 等窄相检测
- 支持冲量求解器与 PBD 求解模式、摩擦、位置修正、睡眠、碰撞过滤和关节
- 使用空间哈希宽相、AABB 查询、Raycast 和进入/退出触发器
- 提供 2D/3D 示例、基准与 9 组测试目标，并包含动态断裂和爆炸堆叠演示

**链接：** [源码](https://github.com/chnnasn/Butter)

## ekit（2026.08）

**技术栈：** C++20、ECS、Sparse Set、Thread Pool、CMake

一个面向游戏引擎的头文件式 C++20 ECS 库，结合 Sparse Set 存储与接近 C# LINQ / Unity DOTS 的流式 API，重点改善 ECS 查询的可读性和编译期诊断。

- 使用强类型、带 generation 的实体句柄，避免悬空实体和裸 `uint32_t` 标识
- 同时支持 dense archetype SoA 组件和按类型存储的 Sparse Set 组件
- 查询链支持 `Where`、`With`、`Without`、`Optional`、`ForEach` 和 `Count`，无需类型擦除或逐实体虚调用
- 提供线程池并行查询、数据依赖 DAG 调度器、事件系统和可运行示例

**链接：** [源码](https://github.com/chnnasn/ekit) · [v0.1.0](https://github.com/chnnasn/ekit/releases/tag/v0.1.0)

## TomCat_Engine（2025.09）

**技术栈：** C++20、OpenGL 4.6、Dear ImGui、Box2D、.NET 10、CMake/Premake

一套面向 2D 游戏开发的完整引擎、编辑器和项目管理 Hub，覆盖渲染、ECS、物理、资源管线、脚本、UI、音频、场景、预制体和独立 Player 打包流程。

- 实现 OpenGL 批量精灵渲染、Scene/Game 双视图、实体拾取、图集子资源和 Animator 状态机
- 构建稳定 `AssetHandle`、`.tcmeta` v2、SHA-256 产物缓存、依赖追踪和后台导入协调机制
- 集成固定 60 Hz Box2D 物理、编辑器碰撞体工具、Tag/Layer 与碰撞矩阵
- 支持 .NET 10 C# 脚本编译、可回收 Play 域、Inspector 序列化字段和完整游戏 API
- 提供 Unity 风格的 Hierarchy/Inspector/Project 工作流、撤销重做、自动保存、Prefab、输入、UI 和音频系统
- 通过 `.tcpak` v6、独立 Player 模板和私有 .NET 运行时完成一键构建与发布，并配置 CI 回归与打包工作流

**链接：** [源码](https://github.com/chnnasn/TomCat_Engine) · [v0.1.0](https://github.com/chnnasn/TomCat_Engine/releases/tag/v0.1.0)

---

[← 返回作品集](../../README.md)