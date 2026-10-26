---
icon: landmark-dome
---

# Governance, Threat Intelligence and Validation

AgentGuard combines local protection with centralized governance. Security teams can define policies, handle approvals, inspect events, and produce evidence organized by environment, host, or agent.

## Policy management

The policy editor provides **Observe, Balanced, and Strict** modes. Administrators can configure allow, alert, approval, or block outcomes for five risk categories:

* Destructive commands.
* Remote code execution.
* Data exfiltration.
* Credential access.
* Deployment.

Policies also maintain protected paths, blocked domains, blocked commands, and allowed-command lists. They can be bound to environments, hosts, or agents, distributed with versioning, and cached locally after retrieval.

{% hint style="info" %}
A policy's name or mode is not a substitute for checking the actual rules and host coverage. Observe mode is intended to support visibility and evaluation before a team introduces stronger enforcement.
{% endhint %}

## Events and approvals

**Protection Events** brings risk events, guardrail matches, and approval records into a central view. Teams can filter by environment, host, or agent and replay a session timeline.

The approval inbox supports centralized review of actions waiting for a human decision. This complements the one-time authorization mechanism described in [runtime-protection.md](runtime-protection.md "mention").

## Environment security reports

Reports can be scoped to an environment, host, or agent. They summarize assets, coverage, runtime events, guardrail matches, policy-hit rankings, supply-chain scans, and threat intelligence.

PDF export supports management reporting and audit preparation.

{% hint style="info" %}
The report is security evidence, not a certification or a legal compliance determination.
{% endhint %}

## Threat intelligence and local self-checks

AgentGuard supports signed threat advisories covering skills, plugins, MCP servers, supply-chain dependencies, malicious URLs, and prompt injection. Organizations can also publish their own internal advisories.

Host self-checks compare advisories with installed skills and plugins, MCP configuration, npm and pip dependencies, and DSH inventories. A match generates response recommendations such as isolation, removal, URL blocking, or token revocation, and is reported back to management.

Scheduling is supported through native tasks in OpenClaw, QClaw, Hermes, and DSH, as well as system cron and Windows Task Scheduler. Private deployments can distribute intelligence locally, including in air-gapped environments.

{% hint style="warning" %}
A response recommendation is distinct from automatic remediation. Teams should review the affected component and authorized response before taking action.
{% endhint %}

## Patrol and checkup

### Daily patrol

Daily patrol checks skill integrity, credential exposure, network exposure, scheduled tasks, recent file changes, attack patterns in audit logs, environment configuration, and trust-registry health.

### Security checkup

Checkup evaluates code security, trust hygiene, runtime defense, credential protection, blockchain protection, and configuration posture, producing a visual report.

These workflows help teams identify changes and maintenance needs beyond a single blocked action.

## Validate policies and agents

AgentGuard includes AI red-team probes for prompt injection, jailbreaks, tool misuse, excessive agency, and memory poisoning. Probes map to OWASP risk categories and MITRE ATLAS techniques and can retest runtime policies and online agents with scorecard outputs.

These built-in probes are part of AgentGuard's validation workflow. [axora-arena](../axora-arena/ "mention") is a separate product for scoped adversarial testing and authorized assessment.

## Framework alignment and audit use

Policy versions, approval records, event timelines, and reports provide traceable evidence for internal reviews and external audits. Component capabilities and management roles support least-privilege decisions.

AgentGuard's personal-data detection categories are organized with reference to sensitive personal information under China's Personal Information Protection Law. OWASP and MITRE ATLAS mappings help teams relate checks to existing threat models.

{% hint style="warning" %}
Framework mapping and exported evidence do not imply certification or guarantee regulatory compliance. Compliance depends on the organization's deployment, data handling, contracts, applicable rules, and operations.
{% endhint %}

## A staged adoption approach

| Stage                 | Focus                                                                                     | Evidence to review                                                         |
| --------------------- | ----------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| Establish visibility  | Introduce management and collectors in a pilot environment.                               | Asset inventory, attack-surface relationships, and unprotected-agent list. |
| Observe a pilot       | Apply protection with Observe mode.                                                       | Event samples, false-positive assessment, and an initial report.           |
| Introduce enforcement | Configure rules, approvals, protected paths, identity, and appropriate enforcement modes. | Policy versions, approval behavior, and verified host coverage.            |
| Expand by environment | Extend coverage and recurring intelligence, patrol, and validation workflows.             | Coverage measures, periodic reports, and retest scorecards.                |

This is a rollout model, not a command-level deployment guide. For deployment boundaries and identity options, see [deployment-privacy-and-integrations.md](deployment-privacy-and-integrations.md "mention").
