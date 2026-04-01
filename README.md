# Figma KAI

A construction scope management platform with Figma integration, MCP server support, and an interactive scope review interface.

## Contents

- [Projects](#projects)
- [Quick Start](#quick-start)
- [Scope Review Dashboard](#scope-review-dashboard)
- [Figma Plugin](#figma-plugin)
- [MCP Server](#mcp-server)

## Projects

This repository contains two interconnected projects:

### 1. **Figma KAI Plugin** (`src/`, root directory files)
A Figma plugin built with TypeScript and SCSS using Gulp. Enables users to create and manage construction scopes directly within Figma.

**Build commands:**
```bash
npm run dev    # Watch mode (rebuilds on file changes)
npm run build  # Production build (minified output to dist/)
```

### 2. **Claude Talk to Figma MCP** (`claude-talk-to-figma-mcp/`)
An MCP (Model Context Protocol) server that bridges AI agents (Claude, Cursor, VS Code) to Figma via WebSocket. Allows AI agents to read and write Figma data programmatically.

**Build & run commands:**
```bash
cd claude-talk-to-figma-mcp
bun run build          # Compile TypeScript
bun run dev            # Watch mode
bun run start          # Start MCP server
bun run socket         # Start WebSocket bridge
bun test               # Run tests
bun run pack           # Package for Claude Desktop
```

## Quick Start

### Scope Review Dashboard

The main interactive prototype is `scope-review-single-scroller.html` — a single-file construction scope management interface with:

- **Task table** with contractor assignments, quantities, prices, and cost deltas
- **Group/Trade view modes** with dynamic photo timeline rows
- **Photo gallery** with real property images from `images/Exterior_General/`
- **Activity sidebar** for notes, photos, and task details
- **Persistent cost tracking** showing original vs. modified prices
- **Status badges** and visual indicators for task completion

**Features:**
- Real-time cost recalculation with red/green price indicators
- Custom horizontal photo scrollbars for each task row
- Group-level photo cards with status labels
- Collapsible task detail modals
- Photo date filtering and task-based visibility

**To use locally:**
1. Open `scope-review-single-scroller.html` in a browser
2. Interact with the table to modify costs, add/remove groups, manage photos
3. Icons and property photos load from `images/` folder

## Figma Plugin

Build a plugin that integrates with Figma's design environment:

```
src/
├── main/
│   └── code.ts         # Plugin business logic (accesses Figma API)
└── ui/
    ├── index.html      # UI markup
    ├── styles/         # SCSS styles
    └── scripts/        # JavaScript logic
```

The build process (Gulp) inlines all CSS, JavaScript, and images into a single `dist/` directory for Figma.

## MCP Server

The MCP server enables AI agents to interact with Figma. For full setup and usage:

- See [`claude-talk-to-figma-mcp/INSTALLATION.md`](claude-talk-to-figma-mcp/INSTALLATION.md) for Claude Desktop, Cursor, and VS Code integration
- See [`claude-talk-to-figma-mcp/COMMANDS.md`](claude-talk-to-figma-mcp/COMMANDS.md) for available MCP tools
- See [`claude-talk-to-figma-mcp/CONTRIBUTING.md`](claude-talk-to-figma-mcp/CONTRIBUTING.md) for architecture details

## Resources

- **Icon library:** `images/icons/` (camera, notes, calendar SVGs)
- **Property photos:** `images/Exterior_General/` (40 sample images organized by task category)
- **Scope data import:** `scope-import-data.js` (external task/group definitions)
