# Git提交规范

## 前言


咱们在协作开发时，针对 **git commit** 规范是十分必须的，每一次提交都务必带上说明信息，同时说明信息亦要有格式规范。目的是制定统一的标准，使得提交历史信息条理清晰，更是为了项目有条不紊地迭代以及提高开发者的效率。

> **[info] 不知道想写什么，反正要写点东西**
>
> 统一团队 git commit 日志标准，便于后续代码 review ，版本发布以及日志自动化生成等等。

## 规范

#### 提交格式

```shell
git commit -m [type](:scope):[subject]
```

#### 示例

```shell
git commit -m "feature:user_center:login 增加微信第三方登录"
```

#### 提交类别 | type

- `feature`: 新功能

- `fixed` : 修复bug

- `update` : 更新

- `docs` : 文档改变

- `style` : 代码格式改变

- `refactor` : 某个已有功能重构

- `perf` : 性能优化

- `test` : 增加测试

- `revert` : 撤销上一次的 commit

#### 范围模块 | scope

使用一个词语涵盖此次提交的改动

#### 描述说明 | description

简洁明了，同时更加能突出此次改动的内容即可
