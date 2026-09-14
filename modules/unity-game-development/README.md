# Unity 游戏开发

> [← 返回作品集](../../README.md)

覆盖战斗 AI、群体导航、性能优化、玩法系统与完整游戏原型。

## Fire（2026.07）

**技术栈：** Unity、C#、URP、Compute Shader、AI Navigation、Input System

一款低多边形 FPS 丧尸波次生存游戏。项目基于第三方 FPS 框架完成角色和武器基础能力，并在此基础上实现敌人 AI、群体导航、波次、成长、对象池、技能和移动端输入适配。

- 实现敌人 `Birth / Chase / Attack / Dead` 状态机，以及基于 BFS 的共享 FlowField 群体导航
- 使用 SpatialGrid 支撑邻居查询、局部避让和刷怪合法性检查，并支持 FlowField 局部重建
- 通过 AI LOD、导航分批更新、对象池和 NonAlloc API 降低大量敌人同时更新时的 CPU 与 GC 压力
- 接入 Compute Shader GPU Skinning 路径与标准渲染回退，并以 ScriptableObject 分离波次、Buff、敌人和地图配置
- 独立实现经验升级、随机 Buff、自动技能及移动端触控输入适配

**链接：** [源码](https://github.com/chnnasn/Fire)

## Cat_Coffee（2025.02）

**技术栈：** Unity、C#、等距网格、DOTween、UGUI

一个 Unity 等距视角网格建造原型，重点验证设施放置、时间推进与 UI 面板切换之间的完整交互链路，适合展示 Unity 系统拆分和玩法原型实现能力。

- 使用泛型 `Grid<T>` 生成等距网格 Mesh，统一处理坐标映射、格子值和占用状态
- 通过事件与委托驱动建筑选择、放置状态、鼠标交互和物体描边
- 时间系统支持秒、分、时、日、月、季节推进，并可响应游戏暂停状态
- 使用 Singleton、BasePanel 和 UIManager 组织面板层级及 DOTween 动效

**链接：** [源码](https://github.com/chnnasn/Cat_Coffee)

## Light（2024.10）

**技术栈：** Unity、C#、2D Physics、URP、Input System、AssetBundle

一款围绕光线、镜面与激光交互展开的 2D 平台解谜游戏。玩家需要在不同角色模式与镜面状态间切换，利用激光反射、镜面搬运和传送能力完成多章节关卡。

- 实现包含 Idle、Move、Jump、Dash、Mirror Mode、Hold/Control Mirror、Transfer 和 Death 等状态的玩家有限状态机
- 实现激光反射、镜面联动、敌对激光与敌人 AI
- 提供多章节关卡、关卡进度保存、场景切换与结算流程
- 搭建事件中心、资源/AssetBundle 管理、对象池、计时器、UI、音乐和移动端摇杆等通用框架
- 同时适配桌面与移动端输入，并使用 Sprite Shape 和自定义 Shader 表现部分交互效果

**链接：** [源码](https://github.com/chnnasn/Light)

## Reverse Loop / TencentGameJam（2024.09）

**技术栈：** Unity、C#、URP、2D Physics、Line Renderer、UGUI

一款 Game Jam 时间回溯解谜平台游戏。玩家移动时系统会持续记录轨迹，回溯结束后生成沿历史路径行动的敌对影子，玩家需要规划路线避开“过去的自己”并抵达终点。

- 使用 `Before / StartRecall / Recall / After` 状态机拆分完整时间回溯流程
- 实时采样玩家位置并绘制轨迹，通过逆序读取记录点完成回溯播放
- 实现历史影子系统，使敌人复用玩家轨迹、自动转向并在重演结束后回收
- 编写 2D 移动、多射线地面检测、跳跃、重力、暂停、异步场景加载和越界重置
- 接入相机震动、轨迹遮罩、动画、音频与 UI 反馈

**链接：** [源码](https://github.com/chnnasn/TencentGameJam)

## Shelter（2024.09）

**技术栈：** Unity、C#、QFramework、UGUI、Tilemap、Particle System

一款 2D 生存策略游戏。玩家需要在风暴到来前派遣居民探索、收集资源、建设避难所，并在逐渐增强的资源与防御压力下维持人口生存。

- 设计资源、人口、探索、建造和风暴结算构成的核心玩法循环
- 使用网格坐标映射、占用字典和建造状态管理实现设施放置
- 实现居民派遣、食物消耗、探索收益、人员损耗和新增人口结算
- 通过阶段倒计时、每日消耗、周期性风暴和递进式难度形成生存压力
- 使用 QFramework 拆分关卡、建筑、物品和探索数据模型，并接入 UGUI 与粒子反馈

**链接：** [源码](https://github.com/chnnasn/Shelter)

---

[← 返回作品集](../../README.md)