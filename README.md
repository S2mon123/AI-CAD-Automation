# AI CAD Automation

Source code, MCP servers and engineering Skills for AI-assisted CAD workflows.
The first integration targets **EPLAN Electric P8 2.9** electrical design and review.

[中文说明](README.zh-CN.md)

## EPLAN integration

| Component | Purpose |
| --- | --- |
| [Native MCP](mcp/eplan/README.md) | Python stdio server and C# in-process Add-in; review mode by default |
| [Authoring extension](mcp/eplan/authoring/README.md) | Bounded workstation authoring through a separate local Canary extension |
| [Engineering Skill](codex-skills/eplan-native-design/SKILL.md) | PLC boxes, common terminals, native connections, recovery and design checks |
| [Two-project lessons](codex-skills/eplan-native-design/references/two-project-lessons.md) | Motor reversal and conveyor/pneumatic-pusher case boundaries |
| [Verification contract](codex-skills/eplan-native-design/references/verification-contract.md) | Full endpoint comparison and semantic net validation |

## Setup

Use Python 3.10 or later. From this checkout:

```powershell
python -m pip install -e "./mcp/eplan[test]"
python -m pytest mcp/eplan/tests -q
python scripts/audit_public_repo.py
```

Copy the [private configuration template](mcp/eplan/examples/config.example.json)
into an ignored local `private/` directory and replace its placeholders. Register
the server using the [Codex example](mcp/eplan/examples/codex-config.example.toml).
Copy `codex-skills/eplan-native-design` into your Codex skills directory.
The authoring extension has its own environment template and build instructions.

The commercial EPLAN installation, matching local API assemblies and licensing
are supplied by the user. No vendor DLLs, manuals, customer drawings, native
identity snapshots or historical private authoring plans are distributed here.

## Validation scope

The public tests run offline and exercise local IPC, model validation and build
guards. They do not certify a new native application session, live PLC execution
or machine safety. Native compatibility is constrained to the documented build;
the bounded historical plans do not make this an arbitrary-project generator.

## Origin and license

EPLAN sources were separated from
[AI CAE Automation Lab](https://github.com/S2mon123/AI_CAE_Automation)
on 2026-11-02. Package and command names are retained for compatibility.
See [MIT License](LICENSE), [third-party notices](THIRD_PARTY_NOTICES.md) and
[source provenance](mcp/eplan/SOURCE_PROVENANCE.json).
