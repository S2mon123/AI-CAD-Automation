# SolidWorks MCP 与识图建模

基于 Cai-aa/CAD-Agent-Hub 的 MIT 源码，保留[原始许可](LICENSE.upstream)与[来源指纹](SOURCE_PROVENANCE.json)。本地补丁不是上游官方发布。

## 安装

需要 Windows、用户自己的 SolidWorks 与许可；本机实测版本为 SolidWorks 2024。
核心配置字节写入工具与离线测试使用 Python 3.11 以上，建议 Python 3.12。
在仓库根目录运行 `python -m pip install -e ./mcp/solidworks`。
识图模块另安装 `python -m pip install -r ./mcp/solidworks-drawing/requirements.txt`。
按[配置模板](examples/codex-config.example.toml)替换本机 Python、模板和有效临时目录。
复制 `codex-skills/solidworks-cad-agent` 和 `codex-skills/solidworks-drawing-modeling` 到个人 Codex skills 目录。
Skill 是文件目录，不把其 Markdown 正文粘贴到 TOML。

## 能力与边界

43 个核心工具与 10 个图纸工具是本地此次 stdio 发现结果，后续以工具目录为准。
核心支持原生特征图、文档身份绑定、持久请求结果、覆盖保护、重建和实体检查。
识图模块提取 PDF 文本/矢量证据，由代理审读形成 DrawingSpec，再进行有界建模。
它不是通用照片到参数化 CAD 网络；缺失深度或公差必须记录为未知。
三点固定面不等于全关联尺寸参考面。放样需检查截面对应和局部交界。
中文工作树由 display_name 与稳定图 ID 分离实现，图引用自动映射，独立编辑仍需查询实际原生名称。

## 复核与验证

先调用 solidworks_compile_feature_graph / solidworks_review_feature_graph。
离线规划结果明确 geometry_verified=false。实际验收需尺寸、实体、局部截面与文件回读。
写入前绑定明确文档；超时不等于取消，查询原请求状态后再决定恢复。
不要调用任意脚本执行入口绕过本包边界，也不通过重命名工程或重复请求绕过保护。

运行 `python -m unittest discover -s mcp/solidworks/tests -q`；PYTHONPATH 指向 `mcp/solidworks/src`。
识图模块测试单独运行，避免与 EPLAN 的同名包测试混合收集。
详细规则见[通用建模规范](docs/modeling-guidelines.zh-CN.md)与[故障复盘](../../docs/solidworks-hardening-2026-11-03.zh-CN.md)。
