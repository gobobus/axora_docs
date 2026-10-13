---
icon: router
---

# Axora Router

**One organized entry point for enterprise AI access.**

Axora Router is an enterprise AI security gateway for organizing access to large language models. Employees, applications, and agents use a managed entry point, where identities, group policies, model channels, usage quotas, and audit records can be handled at an organizational level.

Within Axora, **Router** addresses **Govern Access**: who uses AI, through which channels, under which information-flow policies, and with what usage allocation.

## The problem Router addresses

AI usage can become fragmented across personal accounts, shared API keys, and separate application integrations. That makes it difficult to attribute usage, apply consistent rules, and explain where enterprise data has been sent.

Router provides a common control point for AI API traffic routed through the gateway. It organizes access around users, groups, and administrators rather than a shared credential alone.

## Core capabilities

### 1. Unified model access

Model access is organized through configured **channels**. Different groups can use different channels, giving an organization a managed way to connect its applications to approved model paths.

Available providers, model compatibility, and application integrations depend on the delivered version.

### 2. Individual identities and quotas

Employees or systems receive separate identities and access credentials. Quotas can be allocated by user or team so usage can be arranged and attributed according to the organization's structure.

### 3. Bi-directional (Inbound & Outbound) content inspection

Router applies policy before a request is sent to a model and before the model's response is returned. This includes handling sensitive information such as personal data, credentials, and internal identifiers.

Inspection considers the requester, group, content type, destination model, and region. Content types can include prompts, retrieved material, model responses, and tool results.

### 4. Group-based policy

Policies are bound to groups and apply to group members using the gateway. Rules may use string matching or local-model analysis, such as named-entity recognition. AI assistance supports policy authoring, modification, and testing.

### 5. Audit visibility

Administrators can filter gateway flows by time, user, model, and allow/block status. Trace views show the input and output at key processing stages.

## Who it is for

| Team                    | Main need                                                                       |
| ----------------------- | ------------------------------------------------------------------------------- |
| Enterprise IT           | Organize employee and team access, credentials, and usage quotas.               |
| AI platform engineering | Provide a common model-access path and consistent policies across applications. |
| Security and compliance | Understand gateway data flows and preserve decision evidence.                   |

## Scope of control

Router's control point is traffic passing through the gateway. Protection of an agent's local commands and tool execution is addressed separately by [axora-agentguard](../axora-agentguard/ "mention") on supported paths.

Technical controls and audit records support governance and audit preparation. They do not establish a compliance outcome on their own; that depends on the organization's data, contracts, industry, deployment, and operating practices.

Continue with [policies-and-workflows.md](policies-and-workflows.md "mention"), or [contact-us.md](../../../axora-security/contact-us.md "mention") to discuss a workflow.
