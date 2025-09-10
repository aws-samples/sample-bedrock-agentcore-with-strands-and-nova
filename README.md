# Bedrock AgentCore with Strands Agents SDK and Nova Pro Workshop

This workshop provides hands-on experience with Amazon Bedrock AgentCore, demonstrating how to build sophisticated AI agents using various tools and runtime environments. You'll learn to integrate code interpreters, browser automation, secure credential management, memory capabilities, and deploy scalable agent solutions.

## Workshop Overview

The workshop consists of 8 progressive labs that build upon each other:

| Lab       | Title                                       | Description                                                                                                                 | Key Learning Points                                                                                                                                                                                                                                         | Directory                                                                                            | File                                                                                                                                            |
| --------- | ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Lab 0** | Getting Started with Strands Agents         | Introduction to Strands Agents framework and basic agent creation                                                           | • Learn Strands Agents fundamentals<br>• Create your first AI agent<br>• Use built-in tools like calculator<br>• Develop custom tools and integrate them with agents                                                                                        | [00-strands-agents/](./00-strands-agents/)                                                           | [00-strands-agents-getting-started.ipynb](./00-strands-agents/00-strands-agents-getting-started.ipynb)                                          |
| **Lab 1** | Code Interpreter Integration                | Learn how to integrate Strands Agents with Bedrock AgentCore Code Interpreter for dynamic code execution capabilities       | • Test default Code Interpreter functionality<br>• Create custom Code Interpreter with network access<br>• Compare execution environments and limitations<br>• Execute Python code dynamically within AI agents                                             | [01-bedrock-agentcore-code-interpreter/](./01-bedrock-agentcore-code-interpreter/)                   | [01-agentcore-code-interpreter.ipynb](./01-bedrock-agentcore-code-interpreter/01-agentcore-code-interpreter.ipynb)                              |
| **Lab 2** | Browser Automation                          | Explore browser automation capabilities for web interaction and data extraction                                             | • Integrate browser automation with Strands Agents<br>• Navigate websites programmatically<br>• Extract information from web pages<br>• Implement common browser automation use cases                                                                       | [02-bedrock-agentcore-browser/](./02-bedrock-agentcore-browser/)                                     | [02-agentcore-browser-use.ipynb](./02-bedrock-agentcore-browser/02-agentcore-browser-use.ipynb)                                                 |
| **Lab 3** | Secure Credential Management with Exa MCP   | Implement secure credential management for external API integrations using Exa search as an example                         | • Understand credential management challenges<br>• Create API Key Credential Providers for Exa API<br>• Securely store and retrieve external service credentials<br>• Test secure credential access with Exa MCP server                                     | [03-bedrock-agentcore-identity-apikey/](./03-bedrock-agentcore-identity-apikey/)                     | [03-agentcore-identity-for-exa-mcp.ipynb](./03-bedrock-agentcore-identity-apikey/03-agentcore-identity-for-exa-mcp.ipynb)                       |
| **Lab 4** | MCP Server Deployment                       | Deploy Model Context Protocol (MCP) servers in Bedrock AgentCore Runtime                                                    | • Create custom MCP servers with web search functionality<br>• Set up inbound authentication using Amazon Cognito<br>• Deploy MCP server to AgentCore Runtime<br>• Test deployed MCP server with Strands Agents                                             | [04-bedrock-agentcore-runtime-mcp/](./04-bedrock-agentcore-runtime-mcp/)                             | [04-agentcore-runtime-for-mcp-deploy.ipynb](./04-bedrock-agentcore-runtime-mcp/04-agentcore-runtime-for-mcp-deploy.ipynb)                       |
| **Lab 5** | Agent Runtime Deployment with Observability | Deploy Strands Agents with built-in and custom tools to Bedrock AgentCore Runtime with comprehensive observability features | • Deploy the Strands Agents with tools to Bedrock AgentCore Runtime<br>• Use `boto3` with IAM permission to invoke the deployed agent<br>• Understand the nature of Bedrock AgentCore Runtime session<br>• Learn about GenAI Observability and Traceability | [05-bedrock-agentcore-runtime-and-observability/](./05-bedrock-agentcore-runtime-and-observability/) | [05-agentcore-runtime-for-strands-deploy.ipynb](./05-bedrock-agentcore-runtime-and-observability/05-agentcore-runtime-for-strands-deploy.ipynb) |
| **Lab 6** | Memory Integration                          | Integrate persistent memory capabilities with Strands Agents using Bedrock AgentCore Memory                                 | • Understand memory concepts in AI agents<br>• Implement short-term and long-term memory<br>• Create memory-enabled agents for conversational continuity<br>• Test memory retrieval across sessions                                                         | [06-bedrock-agentcore-memory/](./06-bedrock-agentcore-memory/)                                       | [06-agentcore-memory.ipynb](./06-bedrock-agentcore-memory/06-agentcore-memory.ipynb)                                                            |
| **Lab 7** | Gateway Integration with OpenAPI            | Use Bedrock AgentCore Gateway to automatically generate MCP servers from OpenAPI specifications                             | • Create Cognito inbound authentication for gateway access<br>• Upload OpenAPI specifications to generate MCP server<br>• Configure API key credential providers for outbound authentication<br>• Test generated MCP server with Strands Agents             | [07-bedrock-agentcore-gateway-openapi/](./07-bedrock-agentcore-gateway-openapi/)                     | [07-agentcore-gateway-for-exa-openapi.ipynb](./07-bedrock-agentcore-gateway-openapi/07-agentcore-gateway-for-exa-openapi.ipynb)                 |

## Prerequisites

Before starting the workshop, ensure you have:

- **AWS Account** with appropriate permissions for Bedrock AgentCore and related services
  - `BedrockAgentCoreFullAccess` managed policy
  - `AmazonBedrockFullAccess` managed policy
  - `CloudWatchFullAccess` managed policy 
  - `Caller permissions`: See detailed policy [here](https://github.com/aws/bedrock-agentcore-starter-toolkit/blob/main/documentation/docs/user-guide/runtime/permissions.md#developercaller-permissions)
- [Amazon Nova Pro Model Access](https://docs.aws.amazon.com/nova/latest/userguide/getting-started-console.html) request in Bedrock
- [Enable CloudWatch Transaction Search](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/observability-configure.html#observability-configure-builtin) for AgentCore Observability
- **AWS Credentials** configured (IAM role or environment variables) 
- **Python Environment** with required packages (listed in `pyproject.toml` and instructions in each notebook)
- **Exa API Key** (required for Labs 3 and 7) - Get one from [Exa Dashboard](https://dashboard.exa.ai/api-keys)

### AWS Regions

We suggest to use `us-east-1` for this workshop. Bedrock AgentCore is available in specific AWS regions. Ensure you're working in a supported region.

### Environment Setup

If not using an IAM role, configure your AWS credentials:

```python
import os

os.environ["AWS_ACCESS_KEY_ID"] = "<YOUR_ACCESS_KEY>"
os.environ["AWS_SECRET_ACCESS_KEY"] = "<YOUR_SECRET_KEY>"
os.environ["AWS_SESSION_TOKEN"] = "<OPTIONAL_SESSION_TOKEN>"
os.environ["AWS_REGION"] = "<AWS_REGION>"
```

## Workshop Structure

```
sample-bedrock-agentcore-with-strands-and-nova/
├── 00-strands-agents/
│   └── 00-strands-agents-getting-started.ipynb
├── 01-bedrock-agentcore-code-interpreter/
│   └── 01-agentcore-code-interpreter.ipynb
├── 02-bedrock-agentcore-browser/
│   └── 02-agentcore-browser-use.ipynb
├── 03-bedrock-agentcore-identity-apikey/
│   └── 03-agentcore-identity-for-exa-mcp.ipynb
├── 04-bedrock-agentcore-runtime-mcp/
│   ├── 04-agentcore-runtime-for-mcp-deploy.ipynb
├── 05-bedrock-agentcore-runtime-and-observability/
│   ├── 05-agentcore-runtime-for-strands-deploy.ipynb
├── 06-bedrock-agentcore-memory/
│   ├── 06-agentcore-memory.ipynb
├── 07-bedrock-agentcore-gateway-openapi/
│   ├── 07-agentcore-gateway-for-exa-openapi.ipynb
│   └── exa-openapi-spec.yaml
├── pyproject.toml
├── uv.lock
└── README.md
```

## Getting Started

1. **Set up your AWS credentials** and ensure you're in a supported region
2. Setup workshop environment with **uv** - [Installing uv](https://docs.astral.sh/uv/getting-started/installation/)
   ```bash
   uv sync
   ```
3. **Start with Lab 0** and progress sequentially through the labs
4. **Complete each lab** to clean up AWS resources 

> **Note:** Ensure you clean up AWS resources created during the workshop to avoid unnecessary charges. Each lab includes cleanup instructions where applicable.

## Key Learning Outcomes

By completing this workshop, you will:

- Understand Strands Agents fundamentals and framework
- Build AI agents with code execution capabilities
- Implement browser automation for web interactions
- Manage credentials securely for external service integrations
- Deploy and scale MCP servers in production environments
- Create comprehensive agent solutions with observability
- Integrate persistent memory capabilities for conversational continuity
- Generate MCP servers from OpenAPI specifications using Gateway
- Apply best practices for agent development and deployment

## Support and Resources

- [Amazon Bedrock AgentCore Developer Guide](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/)
- [Amazon Bedrock AgentCore Samples](https://github.com/awslabs/amazon-bedrock-agentcore-samples)
- [Strands Agents SDK](https://strandsagents.com/latest/)
- [Strands Agents Samples](https://github.com/strands-agents/samples)
- [Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/)
- [Amazon Nova User Guide](https://docs.aws.amazon.com/nova/latest/userguide/)

---

## Contributing

We welcome community contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the [LICENSE](LICENSE) file.