# Agentic Workflow Enhancer

This repository is designed to optimize your workflow with Agentic Integrated Development Environments (IDEs) such as Cursor, Windsurf, Cline, and others.

## Repository Structure

- **/documentation**: A comprehensive knowledge base for your agents. Copy and paste this folder into your project to provide essential information and guidelines.

- **/perfect_prompts**: A collection of pre-built prompts designed to maximize the efficiency and output of your coding agents.

- **/rules**: A set of global rules to standardize and enhance your workflow.

## Getting Started

1. **Initialize Your Project**: Utilize the GPT model available at [https://chatgpt.com/g/g-67b8925ce3948191ad4e7616c9df07db-agentic-workflow-master](https://chatgpt.com/g/g-67b8925ce3948191ad4e7616c9df07db-agentic-workflow-master) to kickstart your project. This model will guide you through approximately 50 questions about your project to generate optimal `.md` files.

2. **Integrate Documentation**: Once generated, place these `.md` files into a folder within your project directory.

## Recommended Workflow

1. **Feature Generation**: Import the generated `.md` files into your preferred AI model and prompt it to create the associated features.

2. **Organize Features**: Save the newly generated `.md` files in a folder named `/documentation/features`.

3. **Track Progress**: Request the AI to generate a `progress.csv` file with the following format:

   ```
   {feature_id}, {completed: Boolean}
   ```


## Advanced Integration

For enhanced project management, consider importing the AI-generated tasks into Jira using CSV importation. This allows for efficient tracking and management of tasks. Additionally, by setting up an MCP server, you can automate the retrieval and closure of tickets as features are completed.

---

By following this structured approach, you can streamline your development process and fully leverage the capabilities of Agentic IDEs. 
