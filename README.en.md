# Nocted

[English](README.en.md) · [Português (Brasil)](README.md)

Nocted is the DINX lightweight code editor, with a Zig-owned UI, syntax support, LSP and Git integration.

This repository is private and alpha. The initial goal is a fast, reliable editor, not an IDE that attempts to reproduce the scope of VS Code.

## Goals

- open project files and directories;
- edit text with reliable selection, undo/redo and search/replace;
- provide syntax highlighting based on a proven parser;
- manage LSP servers and present diagnostics, definitions and references;
- show Git status, diffs and change markers;
- support file/line opening and `.desktop` integration;
- follow themes, fonts and light/dark modes through documented contracts;
- work without Noctalia and outside the DINX distribution.

## Architecture

```text
Nocted Zig UI
  windows · tabs · project tree · commands · settings

Editor-engine adapter
  buffer · selection · undo/redo · incremental updates

Language services
  syntax parser · LSP client · language-server processes

Project integration
  directories · Git · recent files · diagnostics
```

The editor should use mature components for buffers, parsing and LSP. Experience, integration and workflow are the differentiated parts.

## Initial roadmap

1. Window, buffer, file and directory.
2. Selection, undo/redo, search and shortcuts.
3. Syntax and project navigation.
4. LSP: diagnostics, definitions and references.
5. Git: status, diff and markers.
6. Noctalia and theme integration.

## Documentation

- [Architecture](docs/architecture.md)
- [Compatibility](docs/compatibility.md)

Portuguese (Brazil) versions:

- [Arquitetura](docs/pt-BR/architecture.md)
- [Compatibilidade](docs/pt-BR/compatibility.md)

DINX: [rufl/dinx-alpha](https://github.com/rufl/dinx-alpha)
