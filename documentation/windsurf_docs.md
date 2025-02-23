# Common Use Cases

Codeium, especially now with Windsurf, can serve a great variety of use cases at a high level. However, we see certain use cases to be more common than others, especially among our enterprise customers within their production codebases.

---

## Use Cases

### 1. Code Generation
- **Examples:**
  - Code generation
  - Boilerplate code
- **Guidance:**
  - Codeium should work well for this use case.
  - Features include:
    - Single-line suggestions
    - Multi-line suggestions
    - Fill-in-the-middle (FIM) completions
- **Best Practices:**
  - Use Next Completion (⌥ + ])
  - Use Context Pinning
  - Use @ Mentions
  - Use Custom Context

### 2. Front-end Development Tasks
- **Guidance:**
  - Codeium should work well for this use case.
  - Features include:
    - Single-line suggestions
    - Multi-line suggestions
    - Fill-in-the-middle (FIM) completions
- **Best Practices:**
  - Use Next Completion (⌥ + ])
  - Use Context Pinning
  - Use @ Mentions
  - Use Custom Context

### 3. Back-end Development Tasks
- **Guidance:**
  - Codeium should work well for this use case.
  - Features include:
    - Single-line suggestions
    - Multi-line suggestions
    - Fill-in-the-middle (FIM) completions
- **Best Practices:**
  - Use Next Completion (⌥ + ])
  - Use Context Pinning
  - Use @ Mentions
  - Use Custom Context

### 4. Unit Test Generation
- **Purpose:**
  - Generate unit tests and automatically remove redundant test cases.
- **Guidance:**
  - Basic usage of Codeium for generating unit tests should reliably generate 60-70% of unit tests.
  - Edge case coverage depends on the quality of the user prompting the model.
- **Best Practices:**
  - Use @ Mentions.
  - Follow Prompt Engineering best practices.
  - **Examples:**
    - *Write unit test for @function-name that tests all edge cases for X and for Y (e.g. email domain).*
    - *Use @testing-utility-class to write a unit test for @function-name.*

### 5. Generate Sample Data for Test Execution
- **Guidance:**
  - Good for low-hanging fruit use cases.
  - For very specific API specifications or in-house libraries, Codeium may not capture all intricacies.
- **Best Practices:**
  - Be very specific about the interface you expect.
  - Consider the complexity of the task and whether a single-shot LLM call is sufficient.

### 6. Internal Code Commentary
- **Purpose:**
  - Generate in-line comments and code descriptions.
- **Guidance:**
  - Codeium should work well for this use case.
  - Use Codeium Command or Codeium Chat to generate in-line comments and code descriptions.
- **Best Practices:**
  - Use @ Mentions.
  - Use Code Lenses to ensure the scope of the LLM call is correct.

### 7. Suggest Improvements and Clarifications
- **Guidance:**
  - The Refactor button or Codeium Command is best for prompting improvements.
  - Codeium Chat is the best place to ask for explanations or clarifications.
  - Although the instructions are somewhat vague, Codeium should be effective at both.
- **Best Practices:**
  - Use the dropdown prompts (i.e. Codeium’s Refactor button) which are custom engineered to deliver the expected answer.
  - Use Codeium Chat for clarifications.

### 8. Automate Function Headers (C/C++/C#)
- **Guidance:**
  - Create the header file.
  - Open chat, @ mention the function in the cpp file, and ask it to write the header function.
  - Perform this iteratively for each function in the cpp file to minimize hallucinations.
- **Best Practices:**
  - Avoid attempting to write an entire header file with one LLM call.
  - Breaking the task into smaller parts improves quality.

### 9. API Documentation and Integration
- **Purpose:**
  - Create documentation as APIs are created and provide proper context.
- **Guidance:**
  - Similar to test coverage, where common API specs can be accurately decorated.
  - For specialized in-house cases, quality may vary.
- **Best Practices:**
  - Walk Codeium through the intended API functionality to improve documentation quality.

### 10. Search Repo for APIs with Natural Language and Generate Code for Integrations
- **Guidance:**
  - Codeium’s context length for a single LLM call is 16,000 tokens.
  - For broad repo-wide searches, this may be insufficient.
  - Multi-step, multi-edit tasks across the repo will be supported in upcoming products.
  - Integration tasks are multi-step and fragile, requiring higher accuracy.
- **Best Practices:**
  - Codeium is not yet fully equipped to solve this problem.
  - If testing, build a detailed, step-by-step plan and prompt Codeium for each step individually.

### 11. Code Refactoring
#### A. Code Simplification and Modularization
- **Guidance:**
  - Use Codeium Code Lenses or @ Mentions to ensure all necessary context is provided.
  - Be aware that context lengths are finite; large refactors may require multi-step processes.
  - Windsurf’s Cascade now supports repo-wide, multi-step, multi-edit tasks.
- **Best Practices:**
  - Break down the refactoring prompt as much as possible.
  - Simpler and shorter commands yield better quality.

#### B. Restructuring Code to Improve Readability/Maintainability
- **Guidance:**
  - Use Codeium Code Lenses or @ Mentions to ensure proper context.
  - Context length limitations (16,000 tokens) may affect large refactors.
  - Future products will support multi-step, multi-edit tasks.
- **Best Practices:**
  - Break down the prompt into smaller parts.
  - Simpler, shorter commands yield better results.

---

## Local Indexing

- **Indexing Engine:** Codeium’s codebase awareness service powering:
  - Codebase-Aware Chat
  - Codebase-Aware Autocomplete
- Retrieves context from the entire codebase, not just recently edited files.
- **Local Indexing** is enabled by default for all Extension users and always on for Windsurf users.

### How It Works
- Generates embeddings for your codebase to capture underlying meaning.
- Embeddings can be queried using natural language and code snippets.
- **Privacy:** No code or embeddings are stored remotely; all data remains on your device.

### How to Toggle the Indexing Engine
- **VS Code / JetBrains:**
  - Open “Settings (UI)” and search for “Codeium Search.”
  - Enable search and set the Max Workspace Size.
  - Restart the IDE to apply changes.
- Verify indexing via the “Context” pane in the “Chat” panel (green dot indicates indexing).

### CodeiumIgnore
- By default, Codeium Indexing ignores:
  - Paths specified in .gitignore
  - Files in node_modules
  - Hidden pathnames (starting with ".")
- To further configure, add a `.codeiumignore` file to the repo root using .gitignore syntax.

### System Requirements
- Initial indexing consumes a fraction of CPU (5-10 minutes per workspace).
- CPU usage normalizes automatically.
- RAM requirement: ~300MB for a 5000-file workspace.
- "Max Workspace Size (File Count)" determines the maximum number of files to index.
  - For ~10GB of RAM, a recommended maximum is 10,000 files.

---

## Remote Indexing
- **Availability:** Only for Codeium Teams and Enterprise users.
- **Purpose:** Index codebases not stored locally.
- Organizations can use Codeium’s Indexing Service to import repositories globally.
  - Indexing and embedding are performed on Codeium’s servers (isolated tenant).
  - Once created, the index is available to any team member.

### Adding a Repository
- Visit [https://codeium.com/indexing](https://codeium.com/indexing) to add a repository.
- Supports Git repositories from GitHub, GitLab, and BitBucket.
- Options:
  - Index a specific branch.
  - Set automatic re-indexing frequency.

### Security Guarantees
- The repository is cloned to create the index.
- After embeddings are created, all code and snippets are deleted (if "Store Snippets" is unchecked).
- Only embeddings are retained, from which original code cannot be derived.
- Indexing is performed on a single-tenant instance; no data is shared between Codeium Teams customers.

---

## MCP Integration
- **Availability:** Currently only for paying individual users.
- **MCP (Model Context Protocol):**
  - Enables LLMs to access custom tools and services.
  - An MCP client (Cascade) can make requests to MCP servers for tool access.
  - Cascade now natively integrates with MCP; you can use your own MCP servers.
  - See official MCP docs for details.

### Configuring MCP with Cascade
- Specify a list of MCP servers with required arguments and environment variables.
- Configuration is stored in a JSON file at `~/.codeium/windsurf/mcp_config.json` following the Claude Desktop schema.
- **Quick Access:**
  - Click the hammer icon in the Cascade toolbar, then “Configure” to open the `mcp_config.json` file.
- **Example Configuration:**
{ "mcpServers": { "google-maps": { "command": "npx", "args": ["-y", "@modelcontextprotocol/server-google-maps"], "env": { "GOOGLE_MAPS_API_KEY": "<YOUR_API_KEY>" } } } }

pgsql
Copier
- After configuration, click “Refresh” in the toolbar. A successful integration shows available MCP servers.
- Click the server line to view an expanded list of the server’s tools.
- Refer to the official MCP server reference repository or OpenTools for examples.

---

## Notes
- **Liability Disclaimer:**
- MCP tool calls can invoke code by arbitrary server implementers; Codeium does not assume liability for any failures.
- MCP tool calls consume credits regardless of success or failure.
- **Current Limitations:**
- Only tools are supported, not prompts or resources.
- Tools that output images are not supported.
- Only servers using the stdio transport type are supported.

# Memories System Overview

Memories is the system for sharing and persisting context across conversations.

There are two types of memories:
- **User-generated Memories (aka Rules)**
- **Auto-generated Memories** (automatically generated by Cascade)

---

## User-generated Memories (aka Rules)

- **Definition:**
  - Users can explicitly define their own Memories (rules) for Cascade to follow.
  - Examples of rules:
    - Respond in a certain language
    - Communicate in a specific style
    - Use a specific API
- **Persistence:**
  - Cascade remains aware of your rules at all times—even if you change them mid-conversation.
  - It will try its best to follow the rules you set.

- **Where Rules Are Defined:**
  - **global_rules.md** – Rules applied across all workspaces.
  - **.windsurfrules** – Rules for the local workspace where the file is located.
  
- **How to Edit Rules:**
  - Click on the **Windsurf - Settings** menu.
  - Select the **Settings** tab.
  - Click **Edit Rules** next to either **Set Global AI Rules** or **Set Workspace AI Rules**.
  
- **Limitations:**
  - Both `global_rules.md` and `.windsurfrules` are limited to 6000 characters each.
  - Any content above 6000 characters will be truncated, and Cascade will not be aware of it.

---

## Best Practices for User-generated Memories

- **Keep Rules Simple, Concise, and Specific:**
  - Communicate as if you are instructing another human.
  - Avoid rules that are too long or vague, as they may confuse Cascade.
- **Avoid Generic Rules:**
  - There is no need to add generic rules (e.g. “write good code”) since these are already part of Cascade’s training data.
  - Focus on rules that are specific to you, your project, or are otherwise exceptional.
- **Iterate on Your Rules:**
  - If Cascade is not following your rules, consider if they are being misinterpreted.
  - Experiment with different prompting approaches.
- **Formatting:**
  - Format your rules using bullet points, numbered lists, and markdown for clarity.
  - **Example:**

      4-space indented code block for formatting example:
      
          # Coding Guidelines 
          - My project's programming language is python
          - Use early returns when possible
          - Always add documentation when creating new functions and classes

- **XML Tag Grouping:**
  - XML tags can be used to group similar rules together.
  - **Example:**

      4-space indented code block for XML example:
      
          <coding_guidelines>
          - My project's programming language is python
          - Use early returns when possible
          - Always add documentation when creating new functions and classes
          </coding_guidelines>

- **Local Application:**
  - To ensure that rules are applied only to your local project, add `.windsurfrules` to your project’s `.gitignore`.

---

## Multiple Workspaces

- If your window has multiple workspaces:
  - The `.windsurfrules` from each workspace will be applied.
  - If the combined global and local rules exceed 12,000 characters:
    - Global rules have priority.
    - Workspace rules follow.
    - Any rules beyond 12,000 characters will be truncated.

---

## Auto-generated Memories

- **Functionality:**
  - During conversations, Cascade can automatically generate and store memories when it encounters useful context.
  - You can also prompt Cascade to "create a memory of …" to remember important context for future conversations.
- **Association:**
  - Auto-generated memories are linked to the workspace in which they were created.
  - Memories from one workspace will not appear in another, preventing unwanted crosstalk between projects.
- **User Notification:**
  - When a memory is generated successfully, a “Memory has been updated” notification will appear at the bottom of Cascade’s response.
  - Click **Manage** to open the Memories panel and view or delete memories.
- **Cost:**
  - Creating and using auto-generated memories does NOT consume credits.

---

## Managing Memories

- **Accessing the Memories Panel:**
  - Click on **Windsurf - Settings** in the bottom-right corner.
  - Select the **Settings** tab.
  - Click **Manage** next to **Cascade-Generated Memories**.
- **Alternative Access:**
  - Click the three dots in the top right corner of the Cascade window.
  - Select **Manage Memories**.

# Prompt Engineering

If you’re reading this, you’re probably someone that already understands some of the use cases and limitations of LLMs. The better prompt and context you provide to the model, the better the outcome will be.

Similarly with Codeium, there are best practices for crafting more effective prompts to get the most out of the tool and produce the best quality code possible to help you accelerate your workflows.

> **Note:** For more complex tasks that may require you to @-Mention specific code blocks, use **Chat** instead of **Command**.

---

## Components of a High Quality Prompt

- **Clear Objective or Outcome**
  - What are you asking the model to produce?
  - Are you asking the model for a plan? For new code? Is it a refactor?

- **All Relevant Context to Perform the Task(s)**
  - Have you properly used @-Mentions to ensure that the proper context is included?
  - Is there any context that is customer-specific that may be unclear to Codeium?

- **Necessary Constraints**
  - Are there any specific frameworks, libraries, or languages that must be utilized?
  - Are there any space or time complexity constraints?
  - Are there any security considerations?

---

## Examples

### Example #1

- **Bad:**  
  Write unit tests for all test cases for an Order Book object.

- **Good:**  
  Using `@class:unit-testing-module`, write unit tests for `@func:src-order-book-add` testing for exceptions thrown when above or below stop loss.

---

### Example #2

- **Bad:**  
  Refactor rawDataTransform.

- **Good:**  
  Refactor `@func:rawDataTransform` by turning the while loop into a for loop and using the same data structure output as `@func:otherDataTransformer`.

---

### Example #3

- **Bad:**  
  Create a new Button for the Contact Form.

- **Good:**  
  Create a new Button component for the `@class:ContactForm` using the style guide in `@repo:frontend-components` that says “Continue”.
