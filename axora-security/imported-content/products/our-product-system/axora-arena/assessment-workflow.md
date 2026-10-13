---
icon: diagram-project
---

# Assessment Workflow

Arena's autonomous audit runtime is a headless command-line application running in a Kali Linux container. It combines an orchestrating agent, parallel investigation, persistent Goal state, and evidence-led reporting.

This page explains the workflow and runtime model for authorized web and network assessment. AI-specific scenario coverage depends on the intended deployment and should be confirmed with Axora. This is not an installation guide or a list of commands to run against a target.

## Assessment lifecycle

| Stage                     | What happens                                                                                                                                                     |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Define the Goal           | The operator supplies an objective through an inline prompt or a UTF-8 task file.                                                                                |
| Confirm authorization     | `policy.md` records the operator's authorization and constraints. Scope remains unknown until confirmed.                                                         |
| Establish the environment | The assessment runs in a controlled container with a mounted workspace and a separate Goal-state directory. Network and browser capabilities can be constrained. |
| Investigate and validate  | The orchestrator delegates specific investigations to parallel subagents and maintains the overall assessment state.                                             |
| Record findings           | Findings, attack paths, status, and evidence references are consolidated into Markdown assessment records.                                                       |
| Resume and retest         | The persisted Goal can be continued after interruption or revisited following a target change.                                                                   |

## Runtime and investigation tools

The runtime uses a fixed image based on Kali's `kali-last-snapshot`. Its toolchain covers reconnaissance, network and web assessment, exploitation, credential assessment, and post-exploitation activities where authorized.

Tools named in the product description include Nmap, Nuclei, Subfinder, HTTPX, FFUF, SQLMap, Metasploit, Sliver, Hashcat, John, Hydra, and Pwntools. Arena also includes verified, version-pinned Nuclei templates and browser automation through Playwright MCP.

The orchestrator coordinates up to eight concurrent subagents. The delivered image and assessment scope determine the tools and techniques appropriate for a particular engagement.

## Findings and evidence

Each Goal maintains Markdown records for:

* Authorization policy.
* A live progress board.
* Findings.
* An evidence index.

Findings retain stable IDs and one of four states: **candidate, observed, verified, or ruled out**. These states keep a possible issue separate from an established result and preserve findings that were investigated but excluded.

The orchestrator maintains the consolidated records. Subagents write raw evidence in their own directories, helping keep evidence provenance separate from the final assessment narrative.

Assessment reports are written to the workspace's `reports/` directory.

## Execution controls

Arena supports a network-capability switch and browser origin allowlisting. The documented network-disabled mode removes network and browser tools from the agent's available capabilities. Operators can also interrupt an assessment gracefully.

These controls help define the permitted execution environment. Container deployment and tool restrictions must be considered together with the target scope and authorization policy.

## Persistence and recovery

Goal metadata is stored in SQLite, with session records in JSONL. The documented resume capability continues the same Goal using the original objective, report location, model configuration, and network settings.

Resuming a Goal makes it possible to continue interrupted work or retest a known attack path. It does not create authorization for a new target or an expanded scope.

## Protect assessment data

{% hint style="warning" %}
Assessment state and parent/subagent session records may contain prompts, conversations, tool output, and credentials. Treat them as confidential security data.
{% endhint %}

Restrict access to the workspace and Goal-state directories. Do not commit raw session records to a repository or share them externally. Review and sanitize evidence before using it outside the authorized assessment team.

See the [.](./ "mention") for use cases and scope, or [contact-us.md](../../../axora-security/contact-us.md "mention") to discuss delivery.
