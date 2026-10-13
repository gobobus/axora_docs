---
icon: magnifying-glass-plus
---

# Discovery and Review

AgentGuard separates two questions: **what is present in the environment**, and **what should be trusted**. Asset discovery establishes visibility. Component review evaluates the software and instructions that an agent may use.

## Discover AI assets

A host collector inventories agents and their connections, including:

* Models and model providers.
* MCP servers and tools.
* Retrieval-augmented generation (RAG) indexes and knowledge bases.
* Credential references, runtime endpoints, and outbound connections.

Assets are organized by environments such as Production and Staging. An attack-surface view shows relationships among agents, models, MCP servers, and tools. Unprotected agents and unapproved outbound connections are flagged.

The collector recognizes agent environments including Claude Code, Codex, OpenClaw, Hermes, Cursor, Gemini CLI, Copilot, Aider, Cline, and Goose. Recognition in the inventory does not imply native runtime interception for every environment.

The collector reports path-level evidence rather than secret values. It supports ongoing operation through cron, systemd, launchd, or Kubernetes, including air-gapped environments.

## Move from discovery to protection

The Discover → Protect workflow supports installing runtime protection on a host and binding a policy. The resulting coverage still depends on the host's supported integration paths.

{% hint style="info" %}
An inventory of a host's agents is therefore a starting point for coverage decisions, not proof that every action is already protected.
{% endhint %}

## Review components with DeepScan

**AgentGuard DeepScan** performs static security scanning of skills, plugins, MCP packages, and code repositories. GitHub repositories can be scanned at a specified branch, tag, or commit.

Detection areas include command execution, remote loading, credential reads, data exfiltration, obfuscation, prompt injection, Trojan distribution, social engineering, Web3 risks, hardcoded personal data, and LLM relay hijacking.

DeepScan also decodes Base64 content for rescanning and examines instructions embedded in Markdown and `SKILL.md` files. This is relevant because agent components can contain both executable code and instructions that shape the agent's behavior.

### DSH plugin review

For **DSH (DeepSeek Harness)** plugins, the review provides repository-wide and runtime-surface views, review priorities, and installation recommendations. An incomplete scan is handled conservatively rather than producing a recommendation that the component is safe to try.

### Review outputs

Scanning can produce findings, a score, review priorities, and installation guidance. Hosted scanning APIs, shareable reports, and optional AI deep analysis can support an organization's component-admission process.

{% hint style="warning" %}
A scan result supports a review decision. It is not a guarantee that a component is free of malicious behavior or vulnerabilities.
{% endhint %}

## Bind trust to component identity

The trust registry identifies a component by its **source, version, and content hash**. This connects a trust decision to the exact material reviewed, rather than only to a familiar package name.

Permissions can be assigned by capability, including network access, file access, execution, credential access, and Web3 actions. A version or hash change downgrades trust and requires review again.

On supported integrations, session-start scanning reviews newly installed skills and registers them as trusted, restricted, or untrusted according to risk.

## An example adoption workflow

{% stepper %}
{% step %}
### Scan the proposed source and version
{% endstep %}

{% step %}
### Review the findings and installation recommendation
{% endstep %}

{% step %}
### Register the component's identity and permitted capabilities
{% endstep %}

{% step %}
### Evaluate its actions at runtime on supported paths
{% endstep %}

{% step %}
### Re-review when the version or content changes
{% endstep %}
{% endstepper %}

{% hint style="info" %}
See [runtime-protection.md](runtime-protection.md "mention") for how component trust and action policy work together.
{% endhint %}
