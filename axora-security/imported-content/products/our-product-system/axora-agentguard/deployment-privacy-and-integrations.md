---
icon: rocket-launch
---

# Deployment, Privacy and Integrations

AgentGuard's enterprise delivery is primarily privately deployed. It also provides a hosted option for evaluation and small pilots. The enterprise capability set, license, host integration, and delivered version determine the available features.

## Private deployment

| Area                 | Enterprise deployment model                                                                                                   |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Runtime              | Docker Compose deployment in a private network or VPC, with support for fully air-gapped environments.                        |
| Data services        | Self-hosted Postgres and Redis for management data.                                                                           |
| Image distribution   | Images can be mirrored into an internal registry.                                                                             |
| Identity             | OIDC or SAML single sign-on, with Keycloak, Okta, and Azure AD named as supported identity providers.                         |
| Management roles     | `admin`, `security`, `auditor`, and `read_only`.                                                                              |
| Optional AI analysis | Can be disabled or directed to an internal OpenAI-compatible model endpoint, including vLLM or Ollama.                        |
| Threat intelligence  | Local distribution and organization-authored advisories, including air-gapped use.                                            |
| Licensing            | Offline-verified signed licenses control edition, seats, and feature availability. Invalid license verification fails closed. |

In private deployment, audit events, asset inventories, and reports remain within the enterprise's management environment. This deployment boundary does not mean that agents or business applications are automatically prevented from calling external models; their allowed destinations and actions remain a policy and integration decision.

### External connectivity

The private-deployment description specifies that billing, analytics, external AI, and external URL fetching are disabled by default. Disconnected smoke checks are part of deployment verification.

{% hint style="warning" %}
Before relying on an air-gapped or no-egress setup, validate the actual configuration, enabled integrations, and network behavior in the deployment being used.
{% endhint %}

## Host-to-management data boundary

Private deployment still has a boundary between the agent host and the management service. AgentGuard uses local evaluation and minimizes the evidence sent to management.

| Evaluated or retained on the agent host              | Sent to management after redaction                                 |
| ---------------------------------------------------- | ------------------------------------------------------------------ |
| Full prompts, file contents, and command output      | Session ID, host type, action type, and tool name.                 |
| Full credentials, private keys, and tokens           | Redacted input previews of up to 2,000 characters.                 |
| Local audit logs and cached policy                   | Decision, risk score, reason, and policy version.                  |
| LLM request and response bodies, evaluated in memory | Credential type and presence; personal-data categories and counts. |

Core decisions run locally. If management is unavailable, local enforcement continues and events wait in a local synchronization queue.

The collector reports credential references and path-level evidence, not secret values. Redacted evidence is still security data and should be protected with appropriate access and retention controls.

## Supported integration paths

The following describes the paths named in the enterprise product materials. Capabilities are not identical across hosts; confirm compatibility with the version and workflow you intend to deploy.

| Environment                          | Integration path                   | Documented capability scope                                                                                                            |
| ------------------------------------ | ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Claude Code                          | Native hooks and skill             | Prompt and tool-call interception, dangerous configuration and model-switch checks, session-start scanning, and initiator attribution. |
| OpenAI Codex CLI                     | Native synchronous hooks and skill | Prompt and tool-call interception and permission-request evaluation.                                                                   |
| OpenClaw / QClaw                     | Native plugin and skill            | Plugin scanning and registration on load, tool-to-plugin attribution, hard blocking, patrol, and native scheduled tasks.               |
| Hermes Agent                         | Native plugin or shell hooks       | Pre-tool-call interception, post-call auditing, LLM traffic observation, and session-start scanning.                                   |
| DSH (DeepSeek Harness)               | Native tool plugin or bundle       | Pre-dispatch evaluation, one-time approval, pre-send model-traffic interception, plugin review, and subscription tools.                |
| Gemini CLI / Cursor / GitHub Copilot | Skill                              | Scanning, action-evaluation commands, and trust-management commands.                                                                   |
| MCP hosts                            | MCP Server or Desktop Extension    | Scanning, trust-registry, and action-decision tools.                                                                                   |

{% hint style="info" %}
Skill or MCP tools provide evaluation capabilities; they should not be treated as universal, unavoidable interception of all host activity. LLM traffic observation should likewise not be described as pre-send blocking.
{% endhint %}

Coverage is reported as full, partial, observation-only, or unsupported. Asset recognition and runtime protection have different support scopes.

## Commercial delivery and pilot support

Enterprise licensing uses annual signed licenses, with seats and feature switches defined by contract. Unlimited-seat arrangements are supported. Private and hosted editions use the same code and build artifacts, with availability controlled by licensing.

Proof-of-concept support includes pilot deployment, baseline policy configuration, and interpretation of an initial security report. [contact-us.md](../../../axora-security/contact-us.md "mention") for pricing, supported versions, or an integration review.

## Before relying on a deployment

Confirm the target host, supported interception path, active policy, approval behavior, data boundary, and external-connectivity settings. Test the control point required by your workflow rather than assuming that installation alone establishes complete protection.
