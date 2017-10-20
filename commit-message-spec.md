# 提交信息规范

我们对项目的 git 提交信息和 pull request 标题的格式进行统一格式的约定，这将提升项目日志的可读性，并且提交信息将用来生成 change log ，对于不符合规范的 pull request 将**不予合入**。

### 信息格式

```
<type>: <subject>
```

#### type

必须是以下之一：

- feat: 新功能
- fix: 修复bug
- docs: 文档
- style: 格式（不影响代码运行的变动）
- refactor: 重构（即不是新增功能，也不是修改bug的代码变动）
- test: 增加测试
- chore: 构建过程或辅助工具的变动
- revert: 回滚代码
- release: 发布版本

注意以下：

1. 其中 `feat, fix, docs` 的提交，将被列到项目发布新版本的 release notes 中。
2. 如果是基于 issue 修复的问题，直接使用 `fix: #1, #2` 即可

### subject

不为空的修改描述，使用中文，可以直接突出修改变更的内容。

如：

```
test: 优化 mip.js 测试用例，覆盖到100%
docs: 更新 README.md 中代码高亮
fix: 修复在 ios8 中不可滑动
style: 优化代码风格
chore: 更新 npm scripts 脚本名称
fix: #3, #4
```
