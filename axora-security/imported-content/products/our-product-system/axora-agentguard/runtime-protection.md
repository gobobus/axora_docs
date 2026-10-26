---
icon: shield-user
---

# Runtime Protection

AgentGuard evaluates an agent's proposed actions before execution on supported integration paths. Policy determines whether an action is allowed, generates an alert, requires approval, or is blocked.

## What is evaluated

Supported action categories include shell commands, file reads and writes, network requests, web searches, browser operations, MCP tools, skill installation, and deployment activity. LLM traffic inspection is available according to the host's integration capability.

Risk checks cover activities such as destructive commands, system-path modification, remote code execution, credential access, and data exfiltration. Other documented checks include unpinned remote execution, webhook egress, blockchain transactions and signatures, and social-account modification.

Blockchain transaction checks use transaction simulation and phishing-address intelligence. Their availability depends on the delivered integration and deployment configuration.

Network-behavior checks include request bursts, replay, unusual-time activity, malicious scripts in responses, and credential exposure in returned output.

## Policy outcomes

| Outcome              | Meaning                                                     |
| -------------------- | ----------------------------------------------------------- |
| **Allow**            | The action proceeds under policy.                           |
| **Alert**            | The action is reported as a risk event according to policy. |
| **Require approval** | The action waits for an explicit human decision.            |
| **Block**            | The action is denied on an enforceable integration path.    |

The product description specifies default blocking for destructive commands, system-path tampering, and data exfiltration, and default approval for remote code execution, credential access, and deployment. Actual behavior is determined by the active policy, mode, and available host capabilities.

An agent action can be attributed to the initiating skill or plugin where the integration supports that attribution. This helps teams trace a risky action back to the component that requested it.

## Human approval

An intercepted action that requires approval receives a one-time approval ID. The agent must present the exact approval command and wait for explicit consent. An approved action may be retried once.

The approval mechanism blocks agent self-approval. If the host does not support interactive approval, the request is treated as denied. A centralized approval inbox and configurable webhook notifications help security teams handle approval requests.

These controls preserve the distinction between an agent proposing an action and a person authorizing it.

## Guard the data boundary

On supported LLM traffic paths, AgentGuard detects personal-data egress, endpoint hijacking, relay-response tampering, API key forwarding to unknown hosts, and bulk workspace egress.

Personal-data categories include identity documents, financial accounts, biometrics, minors' data, health records, and location histories.

### Destination-aware decisions

Model endpoints are classified into five categories:

| Category          | Description                                             |
| ----------------- | ------------------------------------------------------- |
| Local             | A local model endpoint.                                 |
| Official provider | An official model-provider endpoint.                    |
| Auditable cloud   | A cloud endpoint categorized as auditable.              |
| Unknown           | A destination that has not been established as trusted. |
| High risk         | A destination categorized as high risk.                 |

Untrusted endpoints default to approval. When the relevant path can be enforced, API key forwarding to an unknown host is blocked rather than approved as an exception.

### Optional semantic privacy enhancement

Semantic privacy enhancement is off by default. When enabled, it evaluates candidate snippets in on-demand scans and checkups, excluding credentials. It does not analyze live prompts.

This optional feature is separate from runtime LLM traffic evaluation.

## Local decisions and offline continuity

Core decisions are made on the agent host. If the management service is unreachable, local enforcement continues and events are queued for later synchronization. Cached policy supports this local-first model.

## Understand coverage

Coverage is reported as **full, partial, observation-only, or unsupported** according to host capabilities. Missing visibility is not evidence that an action is safe.

{% hint style="warning" %}
On an observation-only path, AgentGuard can record an action that should have been blocked, but observation must not be described as actual prevention.
{% endhint %}

Confirm the [deployment-privacy-and-integrations.md](deployment-privacy-and-integrations.md "mention") before relying on blocking or approval for a workflow.
