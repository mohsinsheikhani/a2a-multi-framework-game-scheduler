# A2A Friend Scheduling Demo

## Executive Summary

The A2A Friend Scheduling project is a sophisticated multi-agent system that demonstrates Google's Agent-to-Agent (A2A) communication protocol for coordinating pickleball game scheduling among friends. This project showcases how autonomous agents built with different AI frameworks can seamlessly collaborate to solve real-world coordination challenges through standardized inter-agent communication.

## Project Overview

### Core Purpose

This multi-agent application demonstrates how to orchestrate conversations between different agents to automatically schedule pickleball games. The system eliminates the manual back-and-forth typically required for group scheduling by having intelligent agents communicate directly with each other to find optimal meeting times and book resources.

**Key Capabilities:**

- Automated availability checking across multiple participants
- Intelligent conflict resolution and time slot optimization
- Real-time court booking and reservation management
- Framework-agnostic agent communication using A2A protocol

### Business Use Case

While demonstrated through pickleball scheduling, this system addresses broader business coordination challenges:

**Primary Applications:**

- **Corporate Meeting Scheduling**: Automate finding common availability across team members
- **Resource Management**: Coordinate booking of shared facilities, equipment, or services
- **Event Planning**: Streamline multi-party event coordination and logistics
- **Service Orchestration**: Coordinate multiple service providers for complex deliveries

**Business Value:**

- Reduces scheduling overhead and administrative burden
- Eliminates coordination delays and miscommunications
- Scales to handle complex multi-party scheduling scenarios
- Demonstrates feasibility of autonomous agent collaboration

## System Architecture

This application contains four specialized agents that communicate via HTTP endpoints:

- **Host Agent (ADK)**: Central orchestrator that manages the scheduling workflow, checks court availability, and handles final bookings
- **Kaitlynn Agent (LangGraph)**: Manages Kaitlynn's calendar with realistic work-schedule availability patterns
- **Nate Agent (CrewAI)**: Handles Nate's scheduling using CrewAI's task-based agent framework
- **Karley Agent (ADK)**: Lightweight agent managing Karley's calendar and preferences

Each agent runs independently and exposes A2A-compliant APIs for seamless inter-agent communication.

## Setup and Deployment

### Prerequisites

Before running the application locally, ensure you have the following installed:

1. **uv:** The Python package management tool used in this project. Follow the installation guide: [https://docs.astral.sh/uv/getting-started/installation/](https://docs.astral.sh/uv/getting-started/installation/)
2. **python 3.13** Python 3.13 is required to run a2a-sdk
3. **set up .env**

Create a `.env` file in the root of the `a2a-multi-framework-game-scheduler` directory with your Google API Key:

```
GOOGLE_API_KEY="your_api_key_here"
```

## Run the Agents

You will need to run each agent in a separate terminal window. The first time you run these commands, `uv` will create a virtual environment and install all necessary dependencies before starting the agent.

### Terminal 1: Run Kaitlynn Agent

```bash
cd kaitlynn_agent_langgraph
uv venv
source .venv/bin/activate
uv run --active app/__main__.py
```

### Terminal 2: Run Nate Agent

```bash
cd nate_agent_crewai
uv venv
source .venv/bin/activate
uv run --active .
```

### Terminal 3: Run Karley Agent

```bash
cd karley_agent_adk
uv venv
source .venv/bin/activate
uv run --active .
```

### Terminal 4: Run Host Agent

```bash
cd host_agent_adk
uv venv
source .venv/bin/activate
uv run --active adk web
```

## Interact with the Host Agent

Once all agents are running, the host agent will begin the scheduling process. You can view the interaction in the terminal output of the `host_agent`.

## References

- https://github.com/google/a2a-python
- https://codelabs.developers.google.com/intro-a2a-purchasing-concierge#1
