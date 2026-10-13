---
description: Protect AI before it acts.
icon: block-brick-fire
---

# Axora AgentGuard

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

**Axora AgentGuard** is a runtime and component security platform for AI agents. It helps enterprises discover agent assets and dependencies, review components before adoption, evaluate actions before execution, and govern policies, approvals, and security evidence.

Within Axora, AgentGuard addresses **Protect Actions**. Its focus is the agent's components and behavior, rather than only the gateway through which a model request travels.

## Why agent security needs its own control point

An agent may read a repository, execute a terminal command, call an MCP tool, access credentials, and send context to a model. A third-party component or untrusted input can influence those actions.

AgentGuard addresses three connected areas of risk:

* **Component risk:** a skill, plugin, or MCP package can introduce harmful code or instructions.
* **Action risk:** a tool call can delete data, alter a protected path, execute remote code, or access a credential.
* **Data-boundary risk:** prompts or workspace data can be sent to an untrusted model endpoint or an unknown host.

Component review, runtime decisions, and data-boundary controls serve different purposes. AgentGuard brings them into an enterprise governance workflow while preserving the limitations of each host integration.

## Four capability areas

| Area         | Question it answers                                                         | Main outputs                                                                                                |
| ------------ | --------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Discover** | Which agents and dependencies are present, and where is protection missing? | Environment-organized asset inventories and attack-surface relationships.                                   |
| **Review**   | Should this component be adopted or trusted?                                | DeepScan findings, scores, review priorities, installation recommendations, and trust records.              |
| **Protect**  | Should this action proceed?                                                 | Policy-driven allow, alert, approval, or block decisions, with attribution where supported.                 |
| **Govern**   | Who controls policy, approvals, and evidence?                               | Versioned policies, approval inboxes, event timelines, security reports, and threat-intelligence workflows. |

***

## Typical use cases

### Coding and operations agents

A development or operations agent needs to read files, run commands, and use tools. AgentGuard evaluates supported execution paths for destructive activity, remote execution, credential access, and other configured risks. Approval and blocking events become part of the audit timeline.

### Third-party component adoption

A team wants to install a community skill, plugin, or MCP package. DeepScan reviews it before adoption, and the trust registry binds the decision to its source, version, and content hash. A changed version or hash requires renewed review.

### Enterprise AI asset visibility

Security teams need an inventory of agents, models, tools, and connections across environments. AgentGuard identifies unprotected agents and unapproved outbound connections so teams can prioritize coverage.

### Personal-data and credential egress

An agent may include personal information or a credential in data sent to a model. On supported paths, AgentGuard evaluates the destination and data categories, applying approval or blocking rules according to policy.

### Supply-chain threat response

A signed advisory identifies a risky component or URL. Hosts compare local installations with threat intelligence and report matches with recommended response actions.

These examples describe product workflows, not named customer deployments.

## Who it is for?

AgentGuard is intended for organizations using agents in development, operations, or business workflows. Primary users include AppSec, AI platform engineering, DevOps, data security, compliance, and audit teams.

## Coverage and delivery

Discovery, scanning, observation, and enforceable interception are different capabilities. Support depends on the host, integration path, and delivered version. A skill-based integration should not be assumed to provide the same enforcement as native hooks or a plugin.

Enterprise deployment is primarily private, with a hosted option for evaluation and small pilots. Details appear in [deployment-privacy-and-integrations.md](deployment-privacy-and-integrations.md "mention").

## Explore AgentGuard

* [discovery-and-review.md](discovery-and-review.md "mention").
* [runtime-protection.md](runtime-protection.md "mention").
* [governance-threat-intelligence-and-validation.md](governance-threat-intelligence-and-validation.md "mention").
* [deployment-privacy-and-integrations.md](deployment-privacy-and-integrations.md "mention").

For a proof of concept or an integration review, [contact-us.md](../../../axora-security/contact-us.md "mention").
