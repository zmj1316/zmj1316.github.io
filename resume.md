---
layout: resume
title: Key Zhang 的简历
---

# Key Zhang

## 个人信息

* 性别： 男
* 邮箱： [zmj1316@gmail.com](mailto:zmj1316@gmail.com)
* 联系电话： `hide`
* 出生日期： 1995-04-19
* github：[https://github.com/zmj1316](https://github.com/zmj1316)
* 主页：[https://zmj1316.github.io](https://zmj1316.github.io)

## 教育经历

`2013/07 - 2017/07`

__浙江大学，计算机科学与技术，本科，GPA top 5%__

`2017/09 - 2020/03`

__浙江大学，计算机技术，硕士__


## 技能方向

### 语言

C++ > Python > JavaScript, MaxScript, Shell

### 技能

游戏开发, 图形学, 动画系统, 物理系统, 并行计算, 操作系统

### 工具

Visual Studio, VTune, RenderDoc, 3DS MAX, Docker, WinDbg, SSH

## 项目经历

### 正式项目

`2018/12 - 至今`

__Virtual Texture__

* 基于 Virtual Texture 的高效大世界细节地表渲染
* 离线加载\实时生成 Texture Page
* 基于四叉树的二级页表查找，实现超大规模（一级页表放不下的）VT的快速更新和索引; 参考 far cry4 的 Adaptive Procedure Virtual Texture 实现的改进方案，far cry 的那个太不直观了，应该算是独创的了。
* TODO 贴图实时压缩


`2018/01 - 2018/10`


__荒野行动 Plus 端游引擎__

* *游戏场景 PhysX 物理材质系统的集成和相应美术制作流程工具链的实现*，实现了高效的美术资源规范检查和导出流程
* 游戏客户端打包与发布流程优化
* 反外挂代码混淆
* 游戏引擎崩溃、卡顿与日常维护处理


`2017/06 - 2018`

__*端游客户端资源发布流程优化*__

* 通过 Docker 容器简化工具环境部署
* 通过 Jenkins 搭建自动化工具交互平台
* 通过增加类似持续集成的流程，将最终发布阶段的工作提前，从而分摊了工作量，减少客户端版本发布和部署所需的时间，加快测试和发布流程

性能提升：由原来 `30分钟 - 2个小时` 的打包发布时间，降到 `2 - 30分钟` 。
提升主要依赖于对整个打包流程的优化：
1. 将原来基于本地文件修改时间和md5的判断增量更新方法，改为通过比较 svn 更新记录，大幅度减少磁盘 IO 的开销 （约减少 30 分钟）
2. 将原先在打包时进行的贴图转换压缩过程，通过 CI 的方式在资源上传的时候提前完成，将 CPU 开销分摊到平时 （约减少 30 分钟），提前压缩还可以减少打包时从网络下载的文件大小。
3. 利用 btrfs 的 COW 功能，减少生成 diff 时文件复制的 IO 和磁盘空间开销（优化3 - 10 分钟）
4. 接入 Jenkins 作为用户交互前端，轻松接入各个自动化流程



`2017/03 - 2017/08`

__骨骼动画 IK 系统__

* 实现了基于 FABRIK 算法的全身动画 IK 计算模块，后续已经集成到端游引擎中

`2016/09 - 2017/02`

__Unity 资源加载管理框架__

* 在打包时记录并拆分 Unity 资源间的依赖关系，减少包体冗余
* 运行时根据记录动态重建资源依赖，从而控制资源加载的内存占用

### 业余|课程项目

`2018/10 - 至今`

__GPU 粒子系统__

* 基于 D3D12 Compute Shader 实现 GPU 发射、模拟、渲染的高性能高效果的粒子系统


`2018/02 - 2018/03`

__GPU based path tracer__

* 基于 D3D11 Compute Shader 实现的光线追踪 path tracer。
* 实现了 BVH 加速结构、重要性采样、轮盘等算法
* 项目地址: [https://github.com/zmj1316/path-tracer](https://github.com/zmj1316/path-tracer)

`2016/03 - 2016/05`

__课程设计 Blipay__

* 软件工程团队课程设计
* 前端基于 React，后端基于 Express
* 实时聊天基于 socket.io
* 项目地址: [https://github.com/magicae/Blipay](https://github.com/magicae/Blipay)

## 职业经历

`2019/01 - 至今`

__手游引擎开发实习生__

网易游戏雷火工作室


`2016/07 - 2018/12`


__引擎开发实习生__

网易游戏盘古工作室