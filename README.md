# Specs UX Compliance — Routine Config

This repo exists solely to give the "Specs UX Compliance Checker" Claude Routine
a committed `.mcp.json`, so it can use a PAT-authenticated Figma MCP server
instead of the official OAuth-based Figma connector.

## Why

The official Figma connector uses OAuth, and the OAuth session used by
cloud Routines has been expiring roughly daily, requiring manual reconnection
at claude.ai/customize/connectors. A Personal Access Token has no session to
expire, which removes that failure mode entirely.

## Setup

1. This repo is attached to the Routine as its repository.
2. `FIGMA_ACCESS_TOKEN` is set in the Routine's environment (not in this repo).
3. The official Figma connector is removed from the Routine's Connectors list
   once this is confirmed working, since `.mcp.json` supplies Figma access instead.

## Server

Uses [`@nexus2520/figma-mcp-server`](https://github.com/pdogra1299/figma-mcp-server),
a community Figma MCP server authenticated via `FIGMA_ACCESS_TOKEN`
(a Figma Personal Access Token) rather than OAuth.
