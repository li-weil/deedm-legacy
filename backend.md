# Legacy Deemd 后端处理逻辑代码

本文档详细列出了 `/home/admin-unix/Deedm/legacy` 目录下所有后端处理逻辑代码，这些代码包含核心算法、数据结构和业务逻辑，适合被Service层调用。

## 核心数学逻辑处理层

### 命题逻辑核心模块

#### 公式构建和解析
- **`src/proplogic/FormulaBuilder.java`** - 公式构建器，支持符号和LaTeX格式字符串解析
  - `buildFromSymbolFormulaString()` - 从符号字符串构建公式
  - `buildFromLaTexFormulaString()` - 从LaTeX字符串构建公式
  - **Service调用点**：公式解析和构建的核心服务

#### 真值计算和赋值
- **`src/proplogic/TruthAssignment.java`** - 真值赋值管理
  - 管理命题变量的真值分配
  - **Service调用点**：真值计算服务的基础数据结构

- **`src/proplogic/TruthAssignmentFunction.java`** - 真值赋值函数
  - 实现真值赋值的函数化处理
  - **Service调用点**：真值计算的函数式接口

#### 真值表生成
- **`src/proplogic/FormulaTruthTable.java`** - 公式真值表生成器
  - 生成任意公式的完整真值表
  - **Service调用点**：真值表生成服务的核心算法

#### 公式替换操作
- **`src/proplogic/Substitution.java`** - 公式替换操作
  - 实现公式中的变量替换
  - **Service调用点**：公式变换服务

### 公式抽象语法树

#### 基础公式类
- **`src/proplogic/formula/Formula.java`** - 抽象公式基类
  - 定义公式的基本结构和操作
  - **Service调用点**：所有公式操作的抽象基类

#### 具体公式类型
- **`src/proplogic/formula/AtomicFormula.java`** - 原子公式（命题变量）
- **`src/proplogic/formula/NegFormula.java`** - 否定公式
- **`src/proplogic/formula/AndFormula.java`** - 合取公式
- **`src/proplogic/formula/OrFormula.java`** - 析取公式
- **`src/proplogic/formula/ImpFormula.java`** - 蕴含公式
- **`src/proplogic/formula/BiImpFormula.java`** - 双蕴含公式
- **`src/proplogic/formula/Symbol.java`** - 符号类

#### 抽象语法树可视化
- **`src/proplogic/formula/ASTGraph/FormulaASTGraph.java`** - 公式AST图
- **`src/proplogic/formula/ASTGraph/FormulaASTNode.java`** - AST节点
- **`src/proplogic/formula/ASTGraph/FormulaASTEdge.java`** - AST边

### 逻辑推理系统

#### 推理引擎
- **`src/proplogic/reason/LogicReasoning.java`** - 逻辑推理引擎
  - 管理前提和结论的推理过程
  - `isPremise()` - 检查公式是否为前提
  - `getConjunctiveFormulaForAllPremises()` - 获取所有前提的合取式
  - **Service调用点**：逻辑推理服务的核心引擎

#### 推理验证器
- **`src/proplogic/reason/ReasonArgumentChecker.java`** - 推理参数检查器
  - 验证推理步骤的正确性
  - **Service调用点**：推理验证服务

#### 推理记录器
- **`src/proplogic/reason/ReasonArgumentRecorder.java`** - 推理过程记录器
- **`src/proplogic/reason/ReasonArgumentStep.java`** - 推理步骤
- **`src/proplogic/reason/ReasonArgumentCheckStep.java`** - 推理检查步骤

### 等价演算系统

#### 等价检查器
- **`src/proplogic/equiv/EquivCalculusChecker.java`** - 等价演算检查器
  - 验证等价演算步骤的正确性
  - **Service调用点**：等价验证服务

#### 等价记录器
- **`src/proplogic/equiv/EquivCalculusRecorder.java`** - 等价演算记录器
- **`src/proplogic/equiv/EquivCalculusStep.java`** - 等价演算步骤

### 范式转换系统

#### 范式计算器
- **`src/proplogic/normalFormula/NormalFormulaCalculator.java`** - 范式计算器
  - 将公式转换为不同范式
  - **Service调用点**：范式转换服务

#### 具体范式类型
- **`src/proplogic/normalFormula/ConjunctiveNormalFormula.java`** - 合取范式
- **`src/proplogic/normalFormula/DisjunctiveNormalFormula.java`** - 析取范式
- **`src/proplogic/normalFormula/PCNFormula.java`** - 主合取范式
- **`src/proplogic/normalFormula/PDNFormula.java`** - 主析取范式
- **`src/proplogic/normalFormula/SimpleConjunctiveFormula.java`** - 简单合取范式
- **`src/proplogic/normalFormula/SimpleDisjunctiveFormula.java`** - 简单析取范式

#### 范式展开
- **`src/proplogic/normalFormula/ExpandNFRecorder.java`** - 范式展开记录器
- **`src/proplogic/normalFormula/ExpandNFStep.java`** - 范式展开步骤

#### 归结原理求解器
- **`src/proplogic/normalFormula/ResolutionSolver.java`** - 归结求解器
  - 使用归结原理进行定理证明
  - **Service调用点**：自动定理证明服务

#### 文字和归结式
- **`src/proplogic/normalFormula/Literal.java`** - 文字类
- **`src/proplogic/normalFormula/Resolvent.java`** - 归结式

## 集合论和关系处理层

### 集合运算核心

#### 集合基础类
- **`src/setrelfun/Set.java`** - 集合基础类
  - 实现集合的基本操作：并、交、差、补等
  - `inSet()` - 元素属于判断
  - `length()` - 集合大小
  - **Service调用点**：集合运算服务的核心数据结构

#### 集合表达式
- **`src/setrelfun/SetExpr.java`** - 集合表达式
  - 处理复杂的集合表达式
  - **Service调用点**：集合表达式解析和计算服务

### 关系运算核心

#### 关系基础类
- **`src/setrelfun/Relation.java`** - 关系基础类
  - 实现关系的基本操作和性质判断
  - **Service调用点**：关系运算服务的核心数据结构

#### 特殊关系类型
- **`src/setrelfun/EquivalenceRelation.java`** - 等价关系
- **`src/setrelfun/PartialOrder.java`** - 偏序关系

#### 关系闭包计算
- **`src/setrelfun/TestRelation.java`** - 关系测试和验证
  - 包含关系闭包计算算法
  - **Service调用点**：关系闭包计算服务

### 函数处理

#### 函数基础类
- **`src/setrelfun/Function.java`** - 函数基础类
  - 实现函数的定义域、值域和映射关系
  - **Service调用点**：函数运算服务的核心数据结构

#### 序对和矩阵
- **`src/setrelfun/OrderedPair.java`** - 有序对
- **`src/setrelfun/Matrix.java`** - 矩阵运算
  - **Service调用点**：关系矩阵表示服务

### 工具类

#### 集合论工具
- **`src/setrelfun/SetrelfunUtil.java`** - 集合论工具类
  - 提供集合和关系的辅助计算方法
  - **Service调用点**：集合论计算工具服务

#### 示例求解器
- **`src/setrelfun/SetrelfunExampleSolver.java`** - 集合论示例求解器
  - 解决集合论相关的标准问题
  - **Service调用点**：集合论问题求解服务

## 组合计数处理层

### 计数核心算法

#### 组合计算器
- **`src/counting/CombCalculator.java`** - 组合计算器
  - 实现排列组合的基础计算
  - **Service调用点**：组合数学计算服务

#### 方程求解计数器
- **`src/counting/EquationSolverCounter.java`** - 方程求解计数器
  - 计算满足条件的整数解的数量
  - 使用生成器模式进行遍历计数
  - **Service调用点**：方程求解计数服务

#### 表达式计算器
- **`src/counting/ExprCalculator.java`** - 表达式计算器
  - 计算数学表达式的值
  - **Service调用点**：表达式计算服务

#### 递推关系计算器
- **`src/counting/RecuExpressionCalculator.java`** - 递推表达式计算器
- **`src/counting/RecurrenceRelationChecker.java`** - 递推关系检查器

#### 字符串计数器
- **`src/counting/StringCounter.java`** - 字符串计数器
  - 计算满足特定条件的字符串数量
  - **Service调用点**：字符串计数服务

### 示例和练习求解器

#### 示例求解器
- **`src/counting/CountingExampleSolver.java`** - 计数示例求解器
  - 提供标准计数问题的解决方案
  - **Service调用点**：计数问题示例服务

#### 练习求解器
- **`src/counting/CountingExerciseSolver.java`** - 计数练习求解器
  - 自动解决计数练习题
  - **Service调用点**：计数练习自动求解服务

#### 语句计数示例
- **`src/counting/StatementCountingExample.java`** - 语句计数示例

### 过滤器系统

#### 基础过滤器
- **`src/counting/filter/IntegerFilter.java`** - 整数过滤器
- **`src/counting/filter/StringFilter.java`** - 字符串过滤器
- **`src/counting/filter/EquationSolverFilter.java`** - 方程求解过滤器

#### 组合过滤器
- **`src/counting/filter/AndGroupIntegerFilter.java`** - 整数与组合过滤器
- **`src/counting/filter/OrGroupIntegerFilter.java`** - 整数或组合过滤器
- **`src/counting/filter/AndGroupStringFilter.java`** - 字符串与组合过滤器
- **`src/counting/filter/OrGroupStringFilter.java`** - 字符串或组合过滤器

#### 专用过滤器
- **`src/counting/filter/IntegerDivisionFilter.java`** - 整数除法过滤器
- **`src/counting/filter/StringLocationFilter.java`** - 字符串位置过滤器
- **`src/counting/filter/StringRepetitionFilter.java`** - 字符串重复过滤器
- **`src/counting/filter/StringSubstringFilter.java`** - 字符串子串过滤器
- **`src/counting/filter/EquationSolverRangeFilter.java`** - 方程求解范围过滤器

### 生成器系统

#### 组合生成器
- **`src/counting/generator/CombinationGenerator.java`** - 组合生成器
  - 生成所有可能的组合
  - **Service调用点**：组合生成服务

#### 排列生成器
- **`src/counting/generator/PermutationGenerator.java`** - 排列生成器
  - 生成所有可能的排列
  - **Service调用点**：排列生成服务

#### 重复组合生成器
- **`src/counting/generator/RepetitionCombinationGenerator.java`** - 重复组合生成器

#### 方程求解生成器
- **`src/counting/generator/EquationSolverGenerator.java`** - 方程求解生成器
  - 生成方程的整数解
  - **Service调用点**：方程解生成服务

#### 函数生成器
- **`src/counting/generator/FunctionGenerator.java`** - 函数生成器
  - 生成特定条件的函数
  - **Service调用点**：函数生成服务

#### 字符串生成器
- **`src/counting/generator/StringGenerator.java`** - 字符串生成器
  - 生成满足条件的字符串
  - **Service调用点**：字符串生成服务

## 代数结构处理层

### 代数结构核心

#### 群论基础
- **`src/algebra/Group.java`** - 群基础类
  - 实现群的代数结构和运算
  - `getOrder()` - 计算元素阶数
  - `isAbelGroup()` - 判断阿贝尔群
  - **Service调用点**：群论计算服务的核心数据结构

#### 特殊群类型
- **`src/algebra/GroupPermutation.java`** - 置换群
- **`src/algebra/GroupUnitModulo.java`** - 模群
- **`src/algebra/GroupModPoly.java`** - 多项式模群

#### 代数运算符
- **`src/algebra/BinaryOperator.java`** - 二元运算符
  - 定义代数结构的二元运算
  - **Service调用点**：代数运算服务的基础接口

#### 特殊代数结构
- **`src/algebra/FiniteRing.java`** - 有限环
- **`src/algebra/Lattice.java`** - 格
- **`src/algebra/ModNumber.java`** - 模数
- **`src/algebra/SVModPoly.java`** - 单变量多项式模

#### 复数和高斯整数
- **`src/algebra/GaussComplex.java`** - 高斯复数

### 代数求解器

#### 示例求解器
- **`src/algebra/AlgebraExampleSolver.java`** - 代数示例求解器
  - 解决代数结构相关的标准问题
  - **Service调用点**：代数问题求解服务

#### 练习求解器
- **`src/algebra/AlgebraExerciseSolver.java`** - 代数练习求解器
  - 自动解决代数练习题
  - **Service调用点**：代数练习自动求解服务

## 图论处理层

### 图结构基础

#### 抽象图类
- **`src/graph/AbstractGraph.java`** - 抽象图基类
  - 定义图的基本结构和操作接口
  - **Service调用点**：图论服务的抽象基类

#### 具体图实现
- **`src/graph/DefaultGraph.java`** - 默认图实现
- **`src/graph/WeightedGraph.java`** - 加权图

#### 图的组成元素
- **`src/graph/GraphNode.java`** - 图节点接口
- **`src/graph/DefaultGraphNode.java`** - 默认图节点
- **`src/graph/GraphEdge.java`** - 图边接口
- **`src/graph/DefaultGraphEdge.java`** - 默认图边
- **`src/graph/WeightedGraphEdge.java`** - 加权边
- **`src/graph/GraphPath.java`** - 图路径
- **`src/graph/WeightedGraphPath.java`** - 加权路径

### 特殊图结构

#### 树结构
- **`src/graph/RootedTree.java`** - 有根树
- **`src/graph/RootedTreeNode.java`** - 有根树节点
- **`src/graph/RootedForest.java`** - 有根森林
- **`src/graph/WeightedTreeNode.java`** - 加权树节点

#### 特殊算法
- **`src/graph/HuffmanTree.java`** - 哈夫曼树
  - 实现哈夫曼编码算法
  - **Service调用点**：哈夫曼编码服务

### 图算法工具

#### 图算法工具类
- **`src/graph/GraphUtil.java`** - 图算法工具类
  - 提供各种图算法的实现
  - `createGraphUsingAdjacencyMatrix()` - 从邻接矩阵创建图
  - `createCompleteGraph()` - 创建完全图
  - **Service调用点**：图算法服务的核心工具类

#### 图矩阵表示
- **`src/graph/DoubleMatrix.java`** - 双精度矩阵
  - 用于图的矩阵运算
  - **Service调用点**：图矩阵运算服务

#### 图示例求解器
- **`src/graph/GraphExampleSolver.java`** - 图论示例求解器
  - 解决图论相关的标准问题
  - **Service调用点**：图论问题求解服务

## 数据表处理层

### 数据表管理

#### 数据表管理器
- **`src/dataTable/DataTableManager.java`** - 数据表管理器
  - 管理结构化数据的存储和检索
  - **Service调用点**：数据管理服务的核心类

#### 数据表工具
- **`src/dataTable/DataTableUtil.java`** - 数据表工具类
  - 提供数据表操作的辅助方法
  - **Service调用点**：数据表操作工具服务

## 离散数学算法

### 离散数学求解器

#### 综合求解器
- **`src/disbook/MathSolver.java`** - 数学求解器
  - 提供各种离散数学问题的统一求解接口
  - **Service调用点**：离散数学求解服务的统一入口

#### 章节算法
- **`src/disbook/Chapter01Algorithm.java`** - 第1章算法
- **`src/disbook/Chapter04Algorithm.java`** - 第4章算法
- **`src/disbook/Chapter07Algorithm.java`** - 第7章算法
- **`src/disbook/Chapter08Algorithm.java`** - 第8章算法
  - **Service调用点**：各章节专项算法服务

## 通用工具和配置

### 配置管理

#### 配置类
- **`src/util/Configuration.java`** - 配置管理类
  - 管理应用程序的全局配置
  - **Service调用点**：配置管理服务

### 调试工具

#### 调试类
- **`src/util/Debug.java`** - 调试工具类
  - 提供调试输出和日志功能
  - **Service调用点**：调试服务

### 数据结构

#### 栈实现
- **`src/util/Stack.java`** - 栈数据结构
  - 实现基本的栈操作
  - **Service调用点**：栈数据结构服务

## Service层集成建议

### 核心服务接口

1. **命题逻辑服务**
   - 依赖：FormulaBuilder, LogicReasoning, FormulaTruthTable
   - 功能：公式解析、逻辑推理、真值计算

2. **集合论服务**
   - 依赖：Set, Relation, Function, SetrelfunUtil
   - 功能：集合运算、关系分析、函数处理

3. **组合数学服务**
   - 依赖：CombCalculator, EquationSolverCounter, 各种生成器
   - 功能：组合计算、排列生成、计数问题求解

4. **代数结构服务**
   - 依赖：Group, BinaryOperator, AlgebraExampleSolver
   - 功能：群论计算、代数结构分析

5. **图论服务**
   - 依赖：GraphUtil, AbstractGraph, GraphExampleSolver
   - 功能：图算法、路径分析、特殊图处理

### 集成模式

这些后端代码适合通过以下方式集成到Service层：

1. **直接调用**：核心算法类可以直接被Service层调用
2. **代理模式**：为复杂算法创建代理接口
3. **工厂模式**：使用工厂创建不同类型的数学对象
4. **策略模式**：根据问题类型选择不同的求解策略

所有这些代码都是纯后端逻辑，不包含任何UI依赖，非常适合作为微服务或企业级应用的后端计算引擎。
