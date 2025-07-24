# AG-UI Mastra Workshop

![preview](./assets/preview.png)

A comprehensive workshop demonstrating **AG-UI** (Agent User Interaction) protocol with **Mastra** integration. This workshop shows how to build sophisticated AI applications with shared state, multiple client interfaces, and rich user interactions.

## What is AG-UI?

AG-UI is a protocol for communicating between AI Agents and Users, enabling:
- **Shared-State**: Real-time synchronization between agents and UI components
- **Multiple Clients**: Build web apps, CLI tools, mobile apps - all connected to the same agent
- **Generative UI**: Agents can render dynamic interface components
- **Tool Integration**: Seamless integration of agent tools with user interfaces

Learn more: [@ag-ui/mastra on npm](https://www.npmjs.com/package/@ag-ui/mastra)

## Workshop Structure

This workshop is organized into **3 progressive steps**, each building on the previous to demonstrate different aspects of AG-UI:

### 🎯 **Step 1**: Basic AG-UI Integration
**Branch**: `git checkout step-1`

**Link**: https://github.com/CopilotKit/mastra-pm-canvas/tree/step-1

**Focus**: Core concepts and simple state management

- Simple agent state (proverbs array)
- Basic CopilotKit integration with Mastra
- Frontend actions and generative UI
- CLI and Web clients with same agent

### 🎯 **Step 2**: Complex State & Agent Behavior  
**Branch**: `git checkout step-2`

**Link**: https://github.com/CopilotKit/mastra-pm-canvas/tree/step-2

**Focus**: Structured data and agent personas

- Complex state schemas with Zod validation
- Product manager agent with specific instructions
- Working memory with structured data types
- Enhanced CLI debugging with state snapshots

### 🎯 **Step 3**: Production-Ready Application
**Branch**: `git checkout step-3`

**Link**: https://github.com/CopilotKit/mastra-pm-canvas/tree/step-3

**Focus**: Full-featured project management interface

- Complete kanban board and team management UI
- Rich React component architecture
- Professional project management interface
- Multiple interaction patterns (modals, drag-drop, etc.)

## Key Learning Outcomes

By completing this workshop, you'll understand:

- ✅ **Multi-Client Architecture**: How to build CLI and web interfaces for the same agent
- ✅ **Shared-State Management**: How state synchronizes between agents and multiple UI clients
- ✅ **Agent Design**: Creating agents with personas, tools, and memory
- ✅ **UI Integration**: Building rich interfaces that react to agent state
- ✅ **Production Patterns**: Scalable architecture for real-world applications

## Quick Start

### Prerequisites

- Node.js 18+
- OpenAI API key
- Package manager (pnpm recommended)

### Setup

1. **Clone and install dependencies**:
```bash
git clone <repository-url>
cd mastra-pm-canvas
pnpm install
```

2. **Add your OpenAI API key**:
```bash
echo "OPENAI_API_KEY=your-key-here" >> .env
```

3. **Choose your starting point**:
```bash
# Start from the beginning
git checkout step-1

# Or jump to a specific step
git checkout step-2
git checkout step-3
```

### Running the Workshop

Each step provides **two different client interfaces** for the same agent:

#### 🌐 **Web Interface** (CopilotKit + React)
```bash
pnpm dev
# Opens http://localhost:3000
```

#### 💻 **CLI Interface** (Terminal-based)
```bash
pnpm cli
# Interactive chat in your terminal
```

**Key Point**: Both interfaces connect to the **same agent** and share **the same state**. This demonstrates AG-UI's power in enabling multiple client types.

## Workshop Navigation

### Step-by-Step Progression
```bash
git checkout step-1    # Basic concepts
# Work through step-1, then:

git checkout step-2    # Enhanced state management  
# Work through step-2, then:

git checkout step-3    # Full application
```

### Compare Between Steps
```bash
# See what changed between steps
git diff step-1 step-2 --name-only
git diff step-2 step-3 --name-only
```

## Architecture Overview

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Web Client    │    │   Mastra Agent   │    │   CLI Client    │
│  (CopilotKit)   │◄──►│   + AG-UI        │◄──►│   (Terminal)    │
│                 │    │                  │    │                 │
└─────────────────┘    └──────────────────┘    └─────────────────┘
        │                        │                        │
        └────────────────────────┼────────────────────────┘
                                 │
                         ┌──────────────┐
                         │ Shared-State │
                         │   + Memory   │
                         └──────────────┘
```

## Technologies Used

- **[Mastra](https://mastra.ai)**: AI agent framework
- **[AG-UI](https://www.npmjs.com/package/@ag-ui/mastra)**: Agent User Interaction protocol  
- **[CopilotKit](https://copilotkit.ai)**: React AI interface components
- **[Next.js](https://nextjs.org)**: React framework
- **[Zod](https://zod.dev)**: Schema validation
- **[LibSQL](https://github.com/libsql/libsql)**: SQLite-compatible database

## Support & Resources

- 📖 [Mastra Documentation](https://mastra.ai/en/docs)
- 📖 [CopilotKit Documentation](https://docs.copilotkit.ai)
- 📦 [AG-UI Mastra Package](https://www.npmjs.com/package/@ag-ui/mastra)

## Next Steps

After completing this workshop:
1. Experiment with custom tools and agent instructions
2. Try building additional client interfaces (mobile, desktop)
3. Explore more complex agent behaviors and state schemas
4. Build your own production AG-UI application

---

**Happy Building! 🚀**