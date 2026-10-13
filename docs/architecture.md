# Nocted architecture

[English](architecture.md) · [Português (Brasil)](pt-BR/architecture.md)

## Layers

```text
Application UI
  windows · tabs · project tree · commands · settings

Editor-engine adapter
  text buffer · selections · undo/redo · incremental updates

Language tooling
  syntax parser · LSP client · process manager

Project services
  filesystem · Git status/diff · diagnostics · recent files
```

The UI owns workflow and presentation. The editor-engine adapter prevents the UI from depending on a concrete buffer implementation. Language tooling is process-based and must not be required for basic editing.

## Editor-engine boundary

The boundary must support:

- opening and saving text with explicit encoding behavior;
- selections, cursors and multiple carets where supported;
- undo/redo and dirty-state tracking;
- incremental edits suitable for LSP synchronization;
- line/column mapping for diagnostics and navigation;
- large-file limits that are visible rather than silent.

## Language and Git boundaries

LSP servers are external processes. Nocted must handle startup failure, malformed messages, server exit and workspace changes without losing edits. Git integration begins with read-only status and diff information; mutations require explicit user actions.

Nocted must not execute project code silently. Plugins and project configuration are untrusted inputs.

## Platform boundaries

Nocted uses XDG configuration/data/cache paths, exposes a valid `.desktop` entry and accepts documented file/line arguments. Noctalia integration is optional and cannot block startup.
