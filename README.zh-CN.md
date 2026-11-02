# AI CAD Automation

面向 AI 辅助 CAD 设计的 MCP、原生桥接与工程 Skill。当前首先维护
**EPLAN Electric P8 2.9** 电气设计与复核工具。

## 主要内容

- [EPLAN 原生 MCP](mcp/eplan/README.md)：Python stdio 服务、本机命名管道、C# Add-in，默认只读审查。
- [工作站绘图扩展](mcp/eplan/authoring/README.md)：通过独立 Canary 扩展实施受限计划、回读、导出与归档。
- [电气设计 Skill](codex-skills/eplan-native-design/SKILL.md)：PLC 盒、公共端、端子与原生连线的设计和检查。
- [两项目经验](codex-skills/eplan-native-design/references/two-project-lessons.md)：电机正反转和自动输送气动推料，明确不同案例的选型与参数边界。
- [验证契约](codex-skills/eplan-native-design/references/verification-contract.md)：完整端点集合、连接容量及语义网络核对。

## 安装和检查

在仓库根目录使用 Python 3.10 及以上版本：

```powershell
python -m pip install -e "./mcp/eplan[test]"
python -m pytest mcp/eplan/tests -q
python scripts/audit_public_repo.py
```

复制[配置模板](mcp/eplan/examples/config.example.json)到本机忽略目录 `private/`，
替换占位值，用环境变量 `EPLAN_MCP_CONFIG` 指向它。按
[Codex 服务模板](mcp/eplan/examples/codex-config.example.toml)注册 MCP，
将 `codex-skills/eplan-native-design` 复制到个人 Codex 的 skills 目录。
实际绘图扩展另按其 README 配置、编译并验证加载版本。

本仓库不附带商业 SDK、编译 DLL、厂家手册、客户工程、许可、历史身份快照或私有绘图计划。
公开测试和示例可独立运行；真实 EPLAN 访问需要用户自己的软件、版本和许可。
离线测试通过不代表已经完成新的原生回归、PLC 投运或施工验收。

## 迁移与许可

2026-11-02 从 [AI CAE Automation Lab](https://github.com/S2mon123/AI_CAE_Automation)
独立维护，保留 Python 包名与工具名，便于已有配置迁移。
开源范围见 [MIT 许可](LICENSE)、[第三方说明](THIRD_PARTY_NOTICES.md)和
[源码来源记录](mcp/eplan/SOURCE_PROVENANCE.json)。
