# api-architect

An API Architect skill for "Capability-First" design. Use for discovering business requirements, modelling lifecycles/workflows, and generating standardized OpenAPI/AsyncAPI specifications.

## The Problem

When working with teams designing and creating APIs, it is common for them to design with a focus on:

- data modelling
- exposing UI functions
- exposure of backend systems or databases

This results in API designs and specifications that don't define the capabilities well and can result in inconsistency across the design of the API (or combinations of APIs).

## The Solution

An agent skill that guides the user through the API design process with a focus on the capability ("What do you want to do?") of the API.
The agent follows a workflow:

- Discovery: the user is interviewed about the capability that is required and guided away from thinking solely in terms of data models or UI
- Application of design/style guides (The skill is configured to reference Zalando's style guide as a default. Override this style as required.)
- Generation of the OpenAPI Specification with a focus on good descriptions (especially important when considering AI agent discovery and consumption of APIs)

### Current Status

The skill generates a basic OpenAPI Specification and documentation but does not yet apply a linter to enforce adherence to the guidelines. This is a future enhancement.

## How to Use

### Setup

```bash
git clone https://github.com/munronai/api-architect.git
```

- Copy the contents of the skills directory into the appropriate CLI skills config directory (e.g. into .claude/skills for Claude Code) or upload the skills to Claude.ai if not using Claude Code. Alternatively, add the skills directory contents into .gemini/skills for Gemini CLI
- Reload and enable the skills if a session is already open

### Run

In Claude Code (or Gemini CLI), you can use the `/api-architect` command or simply ask for the API architect to help you with a design.
