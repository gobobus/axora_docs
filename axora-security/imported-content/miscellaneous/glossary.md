# Glossary

This glossary explains terms used across the Axora product documentation.

| Term                                  | Meaning in these documents                                                                                                                                           |
| ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AI agent**                          | Software that uses a model and tools to carry out tasks, potentially including actions on connected systems.                                                         |
| **AI API gateway**                    | A managed entry point through which applications or agents send model requests and receive responses. Axora Router applies policies at this point.                   |
| **Model channel**                     | A configured model-access path in Router, made available to selected groups.                                                                                         |
| **Skill**                             | A component containing instructions or capabilities that an agent can use. Depending on the host, it may include Markdown instructions, scripts, or other resources. |
| **Plugin**                            | An extension that adds behavior or capabilities to an agent host. Its integration depth depends on the host.                                                         |
| **MCP**                               | Model Context Protocol, a protocol through which agent hosts can connect to tools and data sources.                                                                  |
| **RAG**                               | Retrieval-augmented generation: supplying retrieved information, such as knowledge-base content, as model context.                                                   |
| **Prompt injection**                  | Untrusted instructions that attempt to redirect a model or agent away from the intended task or rules.                                                               |
| **Runtime protection**                | Evaluating actions during execution, with interception and enforcement where the integration supports them.                                                          |
| **Egress**                            | Data leaving a host or controlled environment, including data sent to a model endpoint.                                                                              |
| **Tokenization**                      | In Router's privacy workflow, replacing identified sensitive values with placeholders. This differs from language-model token counting.                              |
| **Content hash**                      | A value used to identify a component's content. AgentGuard uses it with source and version to bind trust to the reviewed component.                                  |
| **Fail closed**                       | Withholding permission or a positive decision when the required validation cannot be completed.                                                                      |
| **Air-gapped environment**            | An environment isolated from external networks. AgentGuard supports private deployment in such environments.                                                         |
| **Goal**                              | Arena's persisted assessment objective and associated authorization, state, findings, and evidence.                                                                  |
| **Red teaming / adversarial testing** | Testing an explicitly authorized scope from an adversarial perspective to identify weaknesses and generate evidence.                                                 |
| **Observation-only coverage**         | Visibility into activity without enforceable prevention on that integration path.                                                                                    |

For product-specific boundaries, see [our-product-system](../products/our-product-system/ "mention").
