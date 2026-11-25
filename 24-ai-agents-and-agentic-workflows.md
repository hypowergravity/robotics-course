# AI Agents and Agentic Workflows

This stage is the thread that ties the whole course together. Every earlier stage can now be driven, at least in part, by an AI agent: a language model that is given tools, calls them in a loop, looks at the results and tries again. Instead of drawing a part by hand in CAD, you describe it and an agent writes the CadQuery script, runs it, checks the result and repairs its own mistakes. Instead of wiring a circuit blind, an agent can drive KiCad through an MCP server, run a SPICE simulation and read the waveforms back. The student's job changes from typing every step to specifying, supervising and verifying, and that is only possible if you understand the earlier stages well enough to judge what the agent produced.

Most repositories here were verified to exist on 25 November 2026 with a read-only `git ls-remote`. That proves they exist, not that they are maintained or good. Items marked "(search-confirmed)" were found in web searches this session. Anything without that marker comes from memory and should be checked before you rely on it. Star counts change quickly, so look them up yourself.

## How agentic building works

An agent is made of three parts. The model reasons and writes code or tool calls. The tools are functions it may call, such as "run this Python file", "open this KiCad project" or "read this ROS topic". The loop feeds each result back to the model until the task is finished or a limit is hit. The Model Context Protocol, usually shortened to MCP, is an open standard that lets any agent talk to any tool server in the same way, which is why so many CAD, EDA and robotics projects now publish an MCP server. Once a tool speaks MCP, you can plug it into Claude, a LangGraph agent, a smolagents agent or an OpenAI Agents SDK program without rewriting it.

A habit worth building from day one is to make the agent produce code or files you can read, rather than opaque actions. A CadQuery script is reviewable, versionable and re-runnable. A KiCad netlist can be diffed. A chain of mouse clicks cannot. Prefer tools where the output is text.

## Open agent frameworks

These are the libraries you build your own agent with. You do not need all of them; pick one and learn it properly, then read another to see the different design choices.

### [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph)
LangGraph models an agent as a graph of steps with shared state, which suits workflows with branches, retries and a human approval step. It is a good fit when your build process has clear phases, such as plan, generate CAD, validate, then fix.

### [huggingface/smolagents](https://github.com/huggingface/smolagents)
A small library whose agents write and run Python code as their actions, instead of emitting JSON tool calls. That "code as action" idea is a natural match for CadQuery, OpenSCAD and simulation scripts, and the library is small enough to read in an afternoon.

### [openai/openai-agents-python](https://github.com/openai/openai-agents-python)
A lightweight framework with agents, handoffs between agents, guardrails and tracing. It works with other model providers too, not only OpenAI's.

### [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI)
Frames agents as a crew of roles, such as a mechanical designer, an electronics engineer and a reviewer, each with its own goal. This is easy to understand for beginners, though you must watch for roles that simply agree with each other.

### [microsoft/autogen](https://github.com/microsoft/autogen)
A multi-agent conversation framework from Microsoft. Check the repository for the current status and for its community fork AG2, because the project's direction has changed over time.

### [pydantic/pydantic-ai](https://github.com/pydantic/pydantic-ai)
An agent framework built around typed, validated outputs. It is valuable for engineering because you can force the model to return a parameter table or bill of materials that matches a schema, then reject anything malformed.

### [strands-agents/sdk-python](https://github.com/strands-agents/sdk-python)
The Strands Agents SDK, a model-driven framework that is also the base for the robotics wrapper mentioned below.

### [anthropics/claude-agent-sdk-python](https://github.com/anthropics/claude-agent-sdk-python)
The Python SDK for building agents on the same agent loop that powers Claude Code, with file, shell and MCP tool support built in.

### [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
The reference collection of MCP servers and the best place to see how a tool server is written. When you want to give an agent access to your own bench instrument or simulator, you will write a small server like these.

Other frameworks you will meet are Google's Agent Development Kit, Agno, LlamaIndex agents, Mastra for TypeScript, and Microsoft Semantic Kernel. They solve the same problem with different trade-offs.

## Text-to-CAD

The most successful approach so far is not to generate a mesh directly, but to have the model write CAD code, usually CadQuery, because code gives exact dimensions, can be edited, and fails loudly when it is wrong.

### [Text-to-CadQuery/Text-to-CadQuery](https://github.com/Text-to-CadQuery/Text-to-CadQuery) (search-confirmed)
Research code that fine-tunes language models to turn a text description into a CadQuery script. Read it to understand how training data pairs are built and how generated scripts are scored.

### [anniedoris/CAD-Coder](https://github.com/anniedoris/CAD-Coder) (search-confirmed)
CAD-Coder treats CAD generation as a vision-language task that outputs CadQuery code, including from a picture of a part. A second repository, [gudo7208/CAD-Coder](https://github.com/gudo7208/CAD-Coder), also exists under the same name, so check which one matches the paper you are reading.

### CADSmith, CADDesigner, CAD-Assistant and Query2CAD (search-confirmed, papers)
These are research systems rather than polished tools, and they show the pattern you should copy. CADSmith uses separate planner, coder, executor, validator and refiner agents, so the generated part is run, measured and corrected in a loop. The others use similar generate, execute, inspect and repair cycles. Search for their papers; I did not verify public code for each one.

### [Milkdomeda/ai-mechanical-3dcad-design-agent](https://github.com/Milkdomeda/ai-mechanical-3dcad-design-agent) (search-confirmed)
A community project for agent-driven mechanical CAD. Treat it as an example to read and compare, not as a finished product.

### CAD tools driven through MCP
[ahujasid/blender-mcp](https://github.com/ahujasid/blender-mcp) lets an agent control Blender, which suits visuals and meshes more than precise mechanical parts. For real parametric work there are several FreeCAD servers, including [proximile/FreeCAD-MCP](https://github.com/proximile/FreeCAD-MCP), [spkane/freecad-robust-mcp-and-more](https://github.com/spkane/freecad-robust-mcp-and-more) and [blwfish/freecad-mcp](https://github.com/blwfish/freecad-mcp), and [altendky/onshape-mcp](https://github.com/altendky/onshape-mcp) connects to the Onshape cloud CAD system. These are all community projects of varying maturity, so try two and compare.

A sensible student exercise is to ask an agent for a bracket for your motor from file 15, with the bolt pattern given in millimetres. Run the generated CadQuery script yourself, measure the part, and check the hole spacing against the motor datasheet. The agent will often be wrong in some small dimension, and finding that error is exactly the skill being trained.

## Electronics and EDA with agents

### KiCad MCP servers
[mixelpixx/KiCAD-MCP-Server](https://github.com/mixelpixx/KiCAD-MCP-Server), [mixelpixx/Konnect](https://github.com/mixelpixx/Konnect) and [oaslananka/kicad-mcp-pro](https://github.com/oaslananka/kicad-mcp-pro) (all search-confirmed) expose KiCad to an agent so it can inspect schematics, run design rule checks and help with layout. Agents are better at reviewing and checking a board than at routing one from nothing, so start with "review my schematic for missing pull-ups and decoupling" before "design me a board".

### Agentic analog circuit design (search-confirmed, research)
AnalogCoder, AnalogAgent, AnalogSAGE, AmpAgent and similar papers have a model write a SPICE netlist, simulate it with ngspice, read the measured gain or bandwidth, and revise. Even if you do not use their code, the loop is something you can build yourself with ngspice and any framework above, and it is a very good way to learn why simulators and datasheets matter.

### Embedded and hardware-in-the-loop
[agentic-hil/agentic-hil](https://github.com/agentic-hil/agentic-hil) and [jl-codes/platformio-mcp](https://github.com/jl-codes/platformio-mcp) (both search-confirmed) let an agent build firmware, flash a board and read serial output. This is powerful and also the first place an agent can do real damage, because it can drive real pins. Keep a motor disconnected or current-limited on the bench supply while an agent iterates, and use the habits in file 16.

## Robots driven by agents

### [nasa-jpl/rosa](https://github.com/nasa-jpl/rosa) (search-confirmed)
ROSA from NASA JPL lets you talk to a ROS system in plain language, such as asking what topics are active or what a node is publishing. It is a friendly way to learn what is inside a running ROS 2 graph from file 13.

### [robotmcp/ros-mcp-server](https://github.com/robotmcp/ros-mcp-server) (search-confirmed)
An MCP server that bridges an agent to ROS topics, services and actions, so any MCP-capable agent can inspect and command a robot.

### [NVlabs/sage](https://github.com/NVlabs/sage) (search-confirmed)
Uses agents to build simulation scenes for robots, which is a way to generate varied training worlds for the sim-to-real work in file 17.

### Strands Robots, CaP-X and Graph-as-Policy (search-confirmed)
These projects explore agents that write robot policy code, wrap robot control for the Strands SDK, or plan with Isaac simulation. They are young and change fast, so read them as a map of what is possible rather than a stable foundation. The older "Code as Policies" idea behind them is worth understanding: the model writes a short program that calls perception and motion functions, instead of outputting motor commands directly.

## Rules for working with agents

Agents make confident mistakes, so treat their output as a draft from a fast junior colleague. Review every generated file before running it on hardware. Run agent-written code in a sandbox or a simulator first. Never give an agent unattended control of a powered actuator, a battery pack or mains equipment, and keep the emergency stop from file 16 within reach. Pin the versions of the tools you use, because MCP servers and frameworks change often. Keep prompts and generated scripts in version control so every design step can be reproduced.

## Practice projects

First, build a text-to-CAD loop of your own with smolagents or LangGraph: the agent writes CadQuery, runs it, exports an STL, measures the bounding box and retries until it matches the requested size. Second, connect a ROS 2 simulation to ROSA or the ROS MCP server and have the agent explain and then change a robot's behaviour. Third, write a small MCP server that wraps ngspice, and let an agent size a resistor divider or an RC filter to a target and verify it from the simulated result. Fourth, as a capstone, have a crew of agents propose a gripper for the arm you built earlier, then you review, print and test it, and write down which parts the agents got right and which you had to fix.

## Checkpoint

You are ready to move on when you can explain the loop of model, tools and results in your own words, can name two ways an agent's CAD or circuit output can be silently wrong, and have built one working agent loop that produces a file you verified by hand.
