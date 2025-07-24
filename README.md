# Step 1: Basic AG-UI Integration

**🎯 Learning Focus**: Core AG-UI concepts with simple shared-state management

This step introduces the fundamental concepts of **AG-UI** (Agent User Interaction) using a simple proverbs application. You'll learn how one agent can power multiple client interfaces with synchronized state.

## What You'll Learn

- ✅ **AG-UI Fundamentals**: How to integrate Mastra agents with AG-UI protocol
- ✅ **Multiple Client Types**: Same agent powering both web and CLI interfaces  
- ✅ **Shared-State Basics**: Simple state synchronization with a proverbs array
- ✅ **Frontend Actions**: UI components that trigger agent actions (`setThemeColor`)
- ✅ **Generative UI**: Agents rendering dynamic components (weather cards)
- ✅ **Memory Visualization**: See agent memory updates in real-time

## Key Features in This Step

### Simple State Schema
```typescript
const AgentState = z.object({
  proverbs: z.array(z.string()).default([]),
});
```

### Two Client Interfaces
1. **Web Interface**: React + CopilotKit with chat sidebar
2. **CLI Interface**: Terminal-based chat with the same agent

### Agent Configuration
- Basic instructions: "You are a helpful assistant"
- Weather tool integration
- Simple proverbs management
- Working memory with LibSQL

## Running This Step

### 🌐 Web Interface
```bash
npm run dev
# Opens http://localhost:3000
```

**Try these interactions:**
- "Add a proverb about AI"
- "Set the theme to orange" 
- "Get the weather in San Francisco"
- "Remove the first proverb"

### 💻 CLI Interface  
```bash
npm run cli
# Interactive terminal chat
```

**Try the same interactions in terminal!** Notice how both interfaces:
- Connect to the same agent
- Share the same memory and state
- Both can add/remove proverbs
- Both can trigger weather tool calls

## Key Observations

### Shared-State in Action
1. Start the web interface and add some proverbs
2. Open the CLI and ask "What proverbs do we have?"
3. Add a proverb via CLI
4. Refresh the web interface - your CLI changes appear!

### Multiple Tool Interactions
- **Frontend Actions**: `setThemeColor` only works in web interface
- **Agent Tools**: `weatherTool` works in both interfaces  
- **Memory Updates**: Both interfaces show memory update notifications

## Architecture in This Step

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Web Client    │    │   Weather Agent  │    │   CLI Client    │
│  (React + CK)   │◄──►│   + AG-UI        │◄──►│   (Terminal)    │
│   - Theme ctrl  │    │   - Weather tool │    │   - Pure chat   │
│   - Proverbs UI │    │   - Proverbs     │    │   - Tool calls  │
└─────────────────┘    └──────────────────┘    └─────────────────┘
        │                        │                        │
        └────────────────────────┼────────────────────────┘
                                 │
                    ┌─────────────────────────┐
                    │    Shared-State         │
                    │  proverbs: string[]     │
                    │  + Working Memory       │
                    └─────────────────────────┘
```

## Code Structure

```
src/
├── app/
│   ├── api/copilotkit/route.ts    # AG-UI integration endpoint
│   ├── page.tsx                   # Web interface with proverbs
│   └── layout.tsx                 # CopilotKit provider
├── cli/index.ts                   # Terminal client
├── mastra/
│   ├── agents/index.ts            # Agent definition 
│   ├── tools/index.ts             # Weather tool
│   └── index.ts                   # Mastra configuration
```

## Next Steps

After completing Step 1:

1. **Experiment**: Try adding proverbs from both interfaces
2. **Observe**: Notice how state synchronizes between clients
3. **Compare**: Test tool calls in both web and CLI
4. **Understand**: See how AG-UI enables multiple client types

**Ready for Step 2?**
```bash
git checkout step-2
```

Step 2 introduces complex state schemas and agent personas - building toward a full project management application.

---

**🔑 Key Takeaway**: One agent, multiple interfaces, shared-state. This is the power of AG-UI!