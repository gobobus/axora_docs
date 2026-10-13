---
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Who Are We?

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

> _"The Security Field for Enterprise AI. Governing access, protecting agent actions and validating the systems behind enterprise AI."_

Axora Security helps enterprises govern AI access, protect agent actions, and validate the systems they rely on. Its products address three different security decisions: who can use AI and where data goes, what an agent is allowed to do, and whether a system's boundaries hold under adversarial testing.

## Why These Decisions Matter?

An AI application may send a request to a model. An AI agent can go further: read a repository, run a command, call a tool, access a knowledge base, or interact with another system. These connections give AI practical value, but they also introduce decisions about identity, sensitive data, permissions, and accountability.

Access control alone does not explain what happens when an agent executes a command. Runtime protection alone does not establish how a system behaves under attack. Axora addresses these questions through complementary products.

***

## The Axora Product Family

| Control point           | Product                                                                     | What it does                                                                                                              |
| ----------------------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Govern Access**       | [axora-router](products/our-product-system/axora-router/ "mention")         | Organizes enterprise AI API access, identities, model channels, usage quotas, and policy-driven information flows.        |
| **Protect Actions**     | [axora-agentguard](products/our-product-system/axora-agentguard/ "mention") | Discovers AI assets, reviews agent components, and evaluates actions across supported execution paths.                    |
| **Validate Resilience** | [axora-arena](products/our-product-system/axora-arena/ "mention")           | Performs scoped adversarial testing and authorized security assessment, producing evidence for remediation and retesting. |

> **Choose the control point that matches the workflow you need to secure. You do not need to adopt every product at once.**

***

## How Axora Approaches Security

### Enable useful autonomy

The objective is to make AI safer to use, not to prevent it from doing useful work. Controls should reflect the risk of the workflow and the capabilities available in the deployment.

### Preserve human authority

People define authorization, policies, and exceptions. High-risk actions need clear decision ownership; an agent should not become its own approver.

### Make boundaries testable

Policies and controls need evidence. Asset inventories, runtime decisions, audit traces, and reproducible findings help teams understand what is protected and where further work is needed.

## Start Reading

* [our-product-system](products/our-product-system/ "mention") to compare the three control points.
* [axora-arena](products/our-product-system/axora-arena/ "mention") for authorized assessment and evidence-led retesting.
* [axora-agentguard](products/our-product-system/axora-agentguard/ "mention") for component security and agent runtime control.
* [axora-router](products/our-product-system/axora-router/ "mention") for enterprise AI access and information-flow policies.
* [contact-us.md](axora-security/contact-us.md "mention") to discuss a specific workflow or deployment.

Official website: [axorasecurity.com](https://axorasecurity.com/)
