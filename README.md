# Step 2: Complex State & Agent Behavior

**🎯 Learning Focus**: Structured data schemas and agent personas with working memory

This step evolves from simple proverbs to a complex project management state schema. You'll learn how to design sophisticated shared-state with validation, agent personas, and structured data management across multiple clients.

## What You'll Learn

- ✅ **Complex State Schemas**: Structured data with Zod validation for users and tasks
- ✅ **Agent Personas**: Creating specialized agent behavior with detailed instructions
- ✅ **Working Memory**: Enhanced memory system with structured state snapshots
- ✅ **Data Validation**: Type-safe state management across clients
- ✅ **State Debugging**: Enhanced CLI with state snapshot events
- ✅ **Persona-Driven Behavior**: How agent instructions shape interactions

## Key Features in This Step

### Complex State Schema
```typescript
const AgentStateSchema = z.object({
  projectName: z.string(),
  projectDescription: z.string(), 
  users: z.array(UserSchema),
  tasks: z.array(TaskSchema),
});

const UserSchema = z.object({
  id: z.number(),
  role: z.string(),
  name: z.string(),
  email: z.string(),
  summary: z.string(),
  image: z.string(),
});

const TaskSchema = z.object({
  id: z.number(),
  name: z.string(),
  description: z.string(),
  status: z.enum(["todo", "in-progress", "done"]),
  assignedTo: z.number(),
});
```

### Agent Persona
The agent now has a **Product Manager** persona with specific instructions:
- Manages users and tasks
- Refers to updates as "board" changes (never "memory")
- Breaks down large tasks into smaller ones
- Biases toward planning with minimal user input

### Enhanced CLI Debugging
New state snapshot events show exactly how the agent's working memory evolves:
```typescript
onStateSnapshotEvent({ event }) {
  console.log("\n🔍 State snapshot:", event.snapshot);
}
```

## Running This Step

### 🌐 Web Interface
```bash
npm run dev
# Opens http://localhost:3000
```

**Try these interactions:**
- "Add a new user named Sarah as a designer"
- "Create a task to redesign the homepage"
- "Assign the homepage task to Tyler"
- "What tasks are currently in progress?"
- "Plan a feature for user authentication"

### 💻 CLI Interface  
```bash
npm run cli
# Interactive terminal chat with enhanced debugging
```

**Notice the enhanced CLI features:**
- **State Snapshots**: See exactly how agent memory changes
- **Same Complex State**: CLI shares the same project management data
- **Persona Consistency**: Agent behaves as product manager in both interfaces
- **Structured Responses**: Agent organizes information around users and tasks

## Key Observations

### Shared-State with Structure
1. **Web Interface**: See the proverbs UI (still simple in this step)
2. **CLI Interface**: Ask "What users do we have?" - see structured data
3. **Add via CLI**: "Add a task to improve performance"
4. **Check Web**: The memory update visualization shows the new task

### Agent Persona in Action
- **Consistent Behavior**: Same product manager persona in both clients
- **Task Planning**: Agent suggests breaking down large requests
- **Professional Language**: Refers to "board updates" not "memory changes"
- **User Management**: Understands team roles and assignments

### Enhanced Memory System  
- **Type Safety**: All state changes validated with Zod schemas
- **Structured Updates**: Agent works with complex nested data
- **Memory Visualization**: Web interface shows detailed memory updates
- **Debug Information**: CLI provides state snapshots for debugging

## Architecture in This Step

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Web Client    │    │   Weather Agent  │    │   CLI Client    │
│  (React + CK)   │◄──►│  (PM Persona)    │◄──►│   (Enhanced)    │
│   - Proverbs UI │    │   + AG-UI        │    │   - State debug │
│   - Memory viz  │    │   - Weather tool │    │   - Same schema │
└─────────────────┘    └──────────────────┘    └─────────────────┘
        │                        │                        │
        └────────────────────────┼────────────────────────┘
                                 │
                ┌─────────────────────────────────────────┐
                │           Shared-State                  │
                │  ┌─────────────────────────────────┐    │
                │  │ projectName: string             │    │
                │  │ projectDescription: string      │    │
                │  │ users: User[]                   │    │
                │  │ tasks: Task[]                   │    │
                │  └─────────────────────────────────┘    │
                │           + Working Memory              │
                │           + Type Validation             │
                └─────────────────────────────────────────┘
```

## Code Structure

```
src/
├── app/
│   ├── api/copilotkit/route.ts    # Same AG-UI integration
│   ├── page.tsx                   # Still simple proverbs UI
│   └── layout.tsx                 # CopilotKit provider
├── cli/index.ts                   # Enhanced with state snapshots
├── lib/
│   ├── state.ts                   # Complex state schema 
│   └── types.ts                   # User/Task schemas + sample data
├── mastra/
│   ├── agents/
│   │   ├── index.ts               # Enhanced agent with complex schema
│   │   └── systemPrompt.ts        # Product manager persona
│   ├── tools/index.ts             # Same weather tool
│   └── index.ts                   # Mastra configuration
```

## Comparing Step 1 vs Step 2

| Aspect | Step 1 | Step 2 |
|--------|--------|--------|
| **State** | Simple proverbs array | Complex project management schema |
| **Agent** | Basic helpful assistant | Product manager persona |
| **Memory** | Simple working memory | Structured memory with validation |
| **CLI** | Basic tool call events | Enhanced with state snapshots |
| **Data** | Unstructured strings | Typed users, tasks, projects |

## Key Learning Points

### 1. State Schema Evolution
See how simple strings evolved into complex, validated data structures that both clients can safely manipulate.

### 2. Agent Personas Matter
Notice how the product manager instructions change the agent's language and behavior across both interfaces.

### 3. Type Safety Across Clients
Both web and CLI interfaces work with the same validated schemas, preventing data inconsistencies.

### 4. Memory Debugging
The enhanced CLI shows exactly how agent memory evolves, crucial for understanding complex state changes.

## Next Steps

After completing Step 2:

1. **Compare Behaviors**: Notice personality differences from Step 1
2. **Test Complex Requests**: Ask for multi-step project planning  
3. **Observe Type Safety**: Try invalid data - see Zod validation
4. **Debug Memory**: Watch state snapshots in CLI

**Ready for Step 3?**
```bash
git checkout step-3
```

Step 3 adds a full project management UI that matches the complex state schema you just learned.

---

**🔑 Key Takeaway**: Complex shared-state enables sophisticated applications while maintaining consistency across multiple client types!