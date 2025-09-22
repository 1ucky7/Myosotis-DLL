# Myosotis DLL劫持生成器

## 项目简介

Myosotis DLL劫持生成器是一个用于生成DLL劫持相关代码和项目的工具，旨在帮助开发者快速创建和生成DLL劫持项目。集成多种加载方式和多种加密模式，可进行链式加密提升加密复杂度，本工具提供测试模式和利用模式两种主要功能，可以满足不同场景的需求。

与之前发布的免杀框架相同，由于使用了链式加密可以变化出几乎无法穷尽的加密链条，在静态方面几乎永远不会被监测。

<img width="2877" height="1433" alt="图片" src="https://github.com/user-attachments/assets/42f1f481-cf14-4eb0-96b2-2955d7785edc" />


## 主要功能

### 测试模式

通过自动识别导出函数，生成弹窗代码确认白程序调用的函数。

- **导出函数自动测试**：自动弹窗显示被调用的导出函数
- **快速验证**：帮助开发者快速验证DLL劫持的可行性

### 利用模式

自动识别`dll`导出函数，架构位数，支持一键进行链式加密shellcode，组装各个模板实现一键免杀`dll`项目生成。

- **加密链支持**：
  - 集成多种加密算法
  - 支持自定义加密链组合
  - 灵活的加密策略配置
  - 可自定义加密模板

- **多样化加载方式**：
  - 支持多种shellcode加载技术
  - 可自定义加载器模板

- **功能函数定制**：
  - 支持自定义功能函数
  - 提供多种预置功能模板
  - 灵活的功能扩展机制

## 使用说明

### 环境配置

需要完整rust编译环境，具体安装教程自行搜索教程

```
rustc 1.88.0 (6b00bc388 2025-06-23)
Visual Studio 2022
```

 **添加 x86编译链接器**

```
rustup target add i686-pc-windows-msvc
```

### 使用教程

项目支持转发模式，即在需要时调用原`dll`功能，这里仅用非转发模式测试。

挖掘到可进行`dll`劫持的项目后，利用测试模式生成`dll`项目，勾选自动编译后会生成项目并自动编译。

<img width="2879" height="1471" alt="图片" src="https://github.com/user-attachments/assets/d2d8ef45-2482-457f-84e9-e13672c1b19f" />


生成的`dll`直接运行白程序，可以发现成功弹窗显示当前调用函数，记录会被调用的函数后续在利用模式中进行利用。

  <img width="993" height="401" alt="图片" src="https://github.com/user-attachments/assets/a521b538-ef13-4738-bf87-93e58e74994b" />


​		如下图选择利用函数`dllmain`，选择利用模式，选择导出函数，加载器以及加密链条和功能函数，配置需要加载的shellcode的bin文件，即可生成利用模式下`dll`。

注意如果`dll`调用了`dllmain`，需要使用进程注入模式以避免死锁。

<img width="2879" height="1645" alt="图片" src="https://github.com/user-attachments/assets/512aaf20-cb24-4104-9473-60aa0c60c7b1" />


直接复制生成`dll`到白程序目录，成功加载shellcode
<img width="1017" height="241" alt="图片" src="https://github.com/user-attachments/assets/9969f9e9-2667-45f0-b8df-f699b8d04bc1" />


## 免杀测试

<img width="2023" height="339" alt="图片" src="https://github.com/user-attachments/assets/71ce5d9b-469d-443e-9108-a18ec8b2c786" />


<img width="2071" height="305" alt="图片" src="https://github.com/user-attachments/assets/9ae9fca9-4ab3-4481-9240-11a55e5783a6" />


<img width="1881" height="677" alt="图片" src="https://github.com/user-attachments/assets/d7d0e5eb-6869-4556-89e4-5d5000d782fd" />


成功上线
<img width="2879" height="101" alt="图片" src="https://github.com/user-attachments/assets/d5a6af3f-2729-447c-ad17-739268a116bd" />


### 模板编写

项目支持自己编写脚本，形成自己的模块，进一步提升免杀能力，具体编写规则见`模板编写指南.md`

### 更新

202509
转发模板存在bug导致无法转发，知识星球已更新


## 知识星球

由于免杀性能考虑，公开版仅支持几种简单加密和加载，完整版在我的知识星球获取，同时也是增加门槛防止滥用。

目前已更新两种一键免杀工具

`Myosotis-免杀框架-1.1.1`

`Myosotis-dll-劫持生成器 v0.0.5-beta`

如下为加载模板和加密模板，后续会持续更新维护。

<img width="1153" height="557" alt="图片" src="https://github.com/user-attachments/assets/7cfe40cb-48b3-4df1-9fb0-c51810607d10" />


<img width="1075" height="619" alt="图片" src="https://github.com/user-attachments/assets/4914b834-d9cf-4064-8bb1-6e35ac6c95cb" />


<img width="750" height="412" alt="图片" src="https://github.com/user-attachments/assets/cbb54653-707a-46d6-9fb0-36533cd446fc" />
