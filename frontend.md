git 添加测试3
# Legacy Deemd 前端设计代码

本文档记录了在 `/home/admin-unix/Deedm/legacy` 目录下找到的所有前端设计和UI相关代码。

## 概述

Legacy Deedm项目是一个基于Java Swing的桌面应用程序，专注于数学和逻辑推理。前端由Java Swing GUI组件和用于可视化数学概念的动画系统组成。

## 主要GUI框架

### 核心Swing框架
- **`src/guiManager/MainSwingFrame.java`** - 主Swing应用程序框架和窗口管理
- **`src/guiManager/MainGUIManager.java`** - 中央GUI管理协调器
- **`src/util/Configuration.java`** - 应用程序配置和设置

### 数理逻辑的GUI组件

#### 公式和逻辑管理
- **`src/guiManager/logic/FormulaTruthValueUIManager.java`** - 真值计算UI
- **`src/guiManager/logic/FormulaTruthTableUIManager.java`** - 真值表生成和显示
- **`src/guiManager/logic/ReasonArgumentCheckUIManager.java`** - 逻辑参数验证界面
- **`src/guiManager/logic/EquivCalculusCheckUIManager.java`** - 等价演算检查UI
- **`src/guiManager/logic/NormalFormulaCalculationUIManager.java`** - 范式计算
- **`src/guiManager/logic/NormalFormulaExpansionUIManager.java`** - 公式展开操作
- **`src/guiManager/logic/FormulaSyntaxUIManager.java`** - 公式语法验证和高亮

### 集合论和关系的GUI组件

#### 集合操作
- **`src/guiManager/setrelfun/SetOperationUIManager.java`** - 集合操作界面
- **`src/guiManager/setrelfun/SetExprOperationUIManager.java`** - 集合表达式操作
- **`src/guiManager/setrelfun/FunctionUIManager.java`** - 函数管理界面

#### 关系管理
- **`src/guiManager/setrelfun/RelationOperationUIManager.java`** - 关系操作
- **`src/guiManager/setrelfun/RelationPropertyUIManager.java`** - 关系属性显示
- **`src/guiManager/setrelfun/RelationClosureUIManager.java`** - 关系闭包计算
- **`src/guiManager/setrelfun/PartialOrderUIManager.java`** - 偏序可视化
- **`src/guiManager/setrelfun/EquivalenceUIManager.java`** - 等价关系界面

### 计数和代数的GUI组件

#### 计数操作
- **`src/guiManager/count/ExprCalculatorUIManager.java`** - 表达式计算器界面

### 动画和可视化框架

#### 核心动画系统
- **`src/graphicAnimation/Animation.java`** - 基础动画类
- **`src/graphicAnimation/Animator.java`** - 动画控制器
- **`src/graphicAnimation/AnimationDriver.java`** - 动画执行引擎
- **`src/graphicAnimation/AnimationArea.java`** - 动画渲染区域
- **`src/graphicAnimation/AnimationPath.java`** - 动画路径计算
- **`src/graphicAnimation/AnimationView.java`** - 抽象动画视图接口
- **`src/graphicAnimation/PainterHelper.java`** - 图形绘制工具

#### 文本动画视图
- **`src/graphicAnimation/textAnimationView/TextDocumentAnimationView.java`** - 文本文档动画
- **`src/graphicAnimation/textAnimationView/TextLineAnimationView.java`** - 基于行的文本动画
- **`src/graphicAnimation/textAnimationView/PlainStringAnimationView.java`** - 纯字符串动画
- **`src/graphicAnimation/textAnimationView/LaTeXStringAnimationView.java`** - LaTeX数学符号动画
- **`src/graphicAnimation/textAnimationView/LaTeXStringImageCreator.java`** - LaTeX到图像转换器

#### 图形动画视图
- **`src/graphicAnimation/graphAnimationView/ImageFileAnimationView.java`** - 图像文件动画
- **`src/graphicAnimation/LineAnimationView.java`** - 线条和形状动画

### 文本和UI工具
- **`src/guiManager/PlainTextAreaManager.java`** - 纯文本区域管理
- **`src/guiManager/ImagedTextAreaAnimator.java`** - 带图像的动画文本区域

## 主要特性

### 数学可视化
- 真值表生成和显示
- 公式语法高亮和验证
- 逻辑参数验证
- 集合论可视化
- 关系属性显示

### 动画系统
- LaTeX数学符号渲染
- 基于文本的分步推理动画
- 视觉演示的图形动画
- 自定义动画路径和时间

### 用户界面
- 基于Swing的桌面界面
- 针对不同数学领域的模块化UI管理器
- 可配置的外观
- 屏幕分辨率感知

## 技术架构

前端使用传统的Swing架构，具有：
- **模型-视图分离**，UI管理器处理不同领域
- **动画框架**，具有可扩展的视图类
- **LaTeX集成**，用于数学符号
- **模块化设计**，支持特定领域的UI组件

## 文件结构

```
legacy/
├── src/guiManager/           # 主要GUI管理
│   ├── MainSwingFrame.java   # 核心应用程序框架
│   ├── MainGUIManager.java   # 中央协调器
│   ├── logic/               # 逻辑和公式UI
│   ├── setrelfun/           # 集合和关系UI
│   └── count/               # 计数操作UI
├── src/graphicAnimation/    # 动画系统
│   ├── Animation.java       # 基础类
│   ├── textAnimationView/   # 文本动画
│   └── graphAnimationView/  # 图形动画
└── src/util/               # 工具和配置
```

## 使用说明

这个遗留代码代表了一个具有Swing界面的综合数学推理工具。UI管理器为不同的数学领域提供专门的界面，而动画系统实现了数学概念和推理步骤的动态可视化。