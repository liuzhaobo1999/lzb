# 单元测试

## 为什么项目中要编写单元测试

先理解下**单元测试**，编写、运行单元测试本质上核心就只有一个，为了准确保证代码运行的结果与我们开发者期望的返回值保持一致。同时单元测试属于 `CI / CD` 的核心流程之一，正是因为有了**单元测试**、**Docker**等，才能让**DevOps** 落地于实践、自动化所有流程。

回归正题、为什么要编写单元测试？旨在

- 提高软件程序的质量

- 尽可能避免、甚至规避 `bug` 出现

- 较少重复性的开发工作与时间，比如测试调试

- 让开发者更加有信心地、安全地重构代码

编写单元测试更是对自己代码负责人的体现。



## 单元测试的特点与要求

- 单元测试必须遵循 `AIR` 原则，即遵循自动化( `Automatic ` )、独立性( `Independent` )、可重复( `Repeatable` )三大原则

- 单元测试必须全流程自动执行、不需要人工干预，即非交互式

- 单元测试必须保持独立性

  即单元测试用例之间禁止互相调用，也不能依赖执行的先后顺序。

- 单元测试必须可重读执行，并且不受外部环境影响

  单元测试的测试用例是会在持续集成环境中运行的，假设是对外界有强依赖的关系，那么会造成持续集成机制不可用。

- 单元测试目录规划

  遵循 `Laravel` 框架的架构规范，单元测试的目录位于 `/tests`

- 项目核心部分务必编写、通过单元测试

  核心部分包括核心业务、核心底层封装模块、核心应用等

- 单元测试必须遵循质量交付 `BCDE` 原则

  `Border`  : 边界值测试

  `Correct` : 正确的输入，并得到预期的结果

  `Design` : 与设计文档相结合，来编写单元测试

  `Error` : 强制错误信息输入，并得到预期的结果


