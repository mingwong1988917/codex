# 杯壶产品池采集与清洗

这是 `building-drinkware-product-pools` 的分享副本，适用于天猫杯壶商品导出数据的清洗、规格拆分、母品合并、热销图池构建与验收。

## 包含内容

- `SKILL.md`：入口说明与工作流程。
- `references/rules.md`：杯壶类目的具体清洗规则。
- `scripts/validate_pool.py`：部分 Excel 结构与图片检查。
- `agents/openai.yaml`：Codex 中的名称、简介与默认提示词。
- [其他类目改造说明](ADAPT_TO_OTHER_CATEGORIES.md)：可直接复制给 Codex 的改造提示词。

分享副本已排除 `scripts/__pycache__` 和 `.pyc` 缓存文件。原始 Skill 的四个源文件保持原样；此包不包含商品数据、项目文档或聊天记录。

## 安装和使用

将整个 `building-drinkware-product-pools` 文件夹放入 Codex 的 skills 目录，默认位置为 `~/.codex/skills/`。请保持内部目录结构，若已存在同名 Skill，先比较内容并保留备份。新开一轮对话后调用：

```text
请使用 $building-drinkware-product-pools 清洗我提供的杯壶商品数据，并保留原始数据与筛选依据。
```

也可以让有仓库读取权限的 Codex 使用 `skill-installer` 安装仓库 `mingwong1988917/codex` 下的 `skills/building-drinkware-product-pools`。

这个 Skill 提供清洗规则，实际执行由 Codex 完成。校验脚本需要 Python 3 和 `openpyxl`，不会自动安装依赖。脚本目前检查指定热销表的行数和嵌入图片数，以及散点表的累计热度占比列；商品归类、价格和热度口径等仍须按 Skill 规则核对。

## 用于其他类目

先阅读 [其他类目改造说明](ADAPT_TO_OTHER_CATEGORIES.md)，提供目标类目的样例数据，再复制成独立的新 Skill。类目特有规则需要重新定义。

## 分享权限

上传时该仓库为私有仓库，链接接收方需要仓库读取权限。没有权限时，可以将本文件夹压缩为 ZIP 单独分享。
