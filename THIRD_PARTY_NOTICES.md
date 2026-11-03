# Third-party notices

EPLAN Electric P8 and EPLAN API belong to their respective vendor. This repository
contains project-owned integration source, not vendor DLLs, manuals, licenses,
databases or customer projects. The matching API assemblies remain local inputs.

The workstation authoring extension uses the local extension mechanism of
[Canary-ECAD/eplan-mcp](https://github.com/Canary-ECAD/eplan-mcp), installed
separately under its own license. Its source is not vendored here.

Comparison references include Canary-ECAD/eplan-mcp,
Canary-ECAD/eplan-scripting-skill, paulinholt/eplan-mcp-bridge (MIT), and
swater-kankyo/eplan-mcp-oss (Apache-2.0). No implementations from those projects
were copied. See the [comparison and source list](docs/eplan-mcp-comparison-2026-10-26.zh-CN.md).

Public Python runtime dependencies retain their own licenses. This project's
original source remains covered by the root MIT license, retained from its
AI CAE Automation Lab origin.

SolidWorks core is adapted from Cai-aa/CAD-Agent-Hub, commit 339840b5f775e81d0b18519806ccb5e59885e2a6. Copyright (c) 2026 Cai-aa; MIT terms are retained in mcp/solidworks/LICENSE.upstream. Local modifications and the DrawingSpec integration are documented separately. No vendor CAD binaries or customer drawings are redistributed.
