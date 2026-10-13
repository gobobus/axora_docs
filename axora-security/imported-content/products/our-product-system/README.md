# Our Product System

**Axora Security** organizes enterprise AI security around **access, actions, and validation**. These are complementary control points, not interchangeable ways to describe the same product.

## Compare The Products

<table><thead><tr><th width="118.953125"></th><th>Axora Router</th><th>Axora AgentGuard</th><th>Axora Arena</th></tr></thead><tbody><tr><td>Primary question</td><td>Who can use AI, through which model channels, and under which data policies?</td><td>Can this component be trusted, and should this agent action proceed?</td><td>What can an adversary do within the authorized test scope?</td></tr><tr><td>Main control point</td><td>AI API access and request/response flow</td><td>Agent components and supported runtime execution paths</td><td>Scoped adversarial testing and security assessment</td></tr><tr><td>Main objects</td><td>Users, groups, applications, model channels, quotas, and content</td><td>Agents, skills, plugins, MCP tools, knowledge-base connections, credentials, and permissions</td><td>Authorized target systems and connected workflows</td></tr><tr><td>Typical evidence</td><td>Request decisions, information-flow traces, and usage attribution</td><td>Asset inventories, scan reports, policy decisions, approvals, and event timelines</td><td>Findings with stable IDs, attack paths, and reproducible evidence</td></tr><tr><td>Primary teams</td><td>Enterprise IT, AI platform, security, and compliance</td><td>AppSec, platform engineering, DevOps, data security, and audit</td><td>Security, product security, red team, and penetration testing</td></tr></tbody></table>

## How The Control Points Complement One Another?

Consider an enterprise coding agent that uses an external model and tools on a development host:

{% stepper %}
{% step %}
## Access

Router provides a managed path for model API usage. Group policies determine how requests and responses are handled, while identities and quotas organize usage.
{% endstep %}

{% step %}
## Actions

AgentGuard reviews installed components and evaluates supported tool calls on the agent host. A risky action can generate an alert, require human approval, or be blocked according to policy and integration capability.
{% endstep %}

{% step %}
## Validation

Arena tests an explicitly authorized target and records findings and evidence. Teams use that evidence to prioritize fixes and retest the relevant attack paths.
{% endstep %}
{% endstepper %}

## Where The Boundaries Differ?

### Gateway policy is not host-level action control

Router evaluates information flowing through its gateway. An agent's local command execution, file access, or tool use is a separate control point addressed by AgentGuard on supported integrations.

### Component review is not runtime approval

A reviewed skill or plugin can still request a risky action. AgentGuard combines pre-adoption review with action evaluation so component trust does not replace runtime policy.

### Testing is not continuous enforcement

Arena produces evidence from authorized assessment. Router and AgentGuard apply policies at their respective control points. A test finding informs security decisions; it does not itself enforce a production policy.

### Visibility is not blocking

Discovering an agent does not establish that its actions can be intercepted. AgentGuard distinguishes full, partial, observation-only, and unsupported coverage according to host capabilities.

***

## Choose a starting point

| Your immediate need                                                    | Start with                                                                                                                      |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Organize employee or application AI access and sensitive-data handling | [axora-router](axora-router/ "mention")                                                                                         |
| Review third-party agent components before adoption                    | [discovery-and-review.md](axora-agentguard/discovery-and-review.md "mention")                                                   |
| Evaluate commands, tool calls, credential access, or agent data egress | [runtime-protection.md](axora-agentguard/runtime-protection.md "mention")                                                       |
| Establish AI asset visibility, approvals, and audit evidence           | [governance-threat-intelligence-and-validation.md](axora-agentguard/governance-threat-intelligence-and-validation.md "mention") |
| Validate an authorized target and reproduce security findings          | [axora-arena](axora-arena/ "mention")                                                                                           |

{% hint style="info" %}
**Start with a real workflow, make its boundary visible, and define the evidence needed to judge whether the control is working.**
{% endhint %}
