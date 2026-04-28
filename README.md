# Decision Tree
Deterministic Daily Reflection Tree

A structured end-of-day reflection system that guides users through a fixed decision tree across three psychological axes—without any LLM at runtime.

What this is

This project encodes reflection as a deterministic conversation.

No free text
No AI calls at runtime
Same inputs → same path → same output

Instead of generating advice, the system walks the user through a sequence of predefined questions, decisions, and reflections.

Core Idea

Most tools capture what happened.
This system focuses on how the user showed up.

It does that across three axes:

Locus (Agency)
Did I act, or did things happen to me?
Orientation (Contribution)
Was I giving, or expecting?
Radius (Perspective)
Was I focused only on myself, or did I consider others?

Each axis builds on the previous one, forming a single coherent reflection flow.

How the Tree Works

The system is driven entirely by a structured data file:
/tree/reflection-tree.json

Each node in the tree is one of the following:

Type	Description
start	Opens the session
question	Presents fixed options
decision	Routes based on previous answer
reflection	Shows contextual insight
bridge	Transitions between axes
summary	Final synthesis
end	Closes the session
Example Flow
START
  ↓
A1_OPEN (Question)
  ↓
A1_DECIDE (Decision)
  ↓
A1_HIGH / A1_LOW (Branch)
  ↓
Reflection → Bridge → Next Axis

Every branch is:

explicitly defined
fully traceable
deterministic
State & Signals

The tree itself is pure data and does not store any state.

Instead, state is computed at runtime by the agent as it walks through the tree.

Certain nodes emit signals like:

"signal": { "axis1": "internal" }

When such a node is visited, the agent updates an in-memory counter.

For example, during a session the agent may internally maintain:

{
  "axis1": { "internal": 2, "external": 1 },
  "axis2": { "contribution": 1, "entitlement": 1 },
  "axis3": { "self": 0, "other": 2 }
}

This state is:

not part of the tree
not persisted
computed dynamically per session

This separation allows the same tree to be executed by different agents without modifying the data.

Dominant Value Calculation

At the end of the session, the agent determines a dominant value for each axis:

axis1 → internal vs external
axis2 → contribution vs entitlement
axis3 → self vs other

These values are used in the summary through interpolation:

Today, you leaned {axis1.dominant}...

In case of a tie, the system may:

default to the most recent signal, or
treat the result as balanced
Determinism Guarantee

This system is intentionally constrained:

No randomness
No interpretation layer
No generated text

All behavior is:

pre-defined
auditable
consistent across sessions
Project Structure
  DecisionTree.json    
  README.md
  mermaid-diagram.png                 
  write-up.md         
  transcript1.md
  transcript2.md
If implemented, the agent:
Loads reflection-tree.json
Starts at START
Renders each node
Waits for input at question nodes
Routes via decision nodes
Accumulates signals in memory
Displays the final summary

A simple CLI implementation is sufficient.

Design Principles
Clarity over cleverness
Questions should be instantly understandable
Recognition over interpretation
Users select what they experienced; the system does not infer
Reflection over evaluation
No scoring, no judgment
Structure over generation
Insight comes from branching, not AI output
Use of AI (During Development)

AI was used as a design collaborator, not part of the final system.

It helped with:

brainstorming question variations
testing clarity of options
refining wording

All final outputs were:
manually reviewed
simplified
encoded deterministically
Limitations
Single-session only (no memory across days)
Equal weighting of signals
Fixed depth (no adaptive questioning beyond predefined branches)
Future Improvements
Multi-day pattern tracking
Weighted signal scoring
Conditional deeper probing
UI layer for better experience
Final Note
Sample Transcripts are included how different parts through the tree produce different reflections
This is not a chatbot.

It’s a structured reflection system—designed to help users see their day more clearly, one decision at a time.


