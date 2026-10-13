# Nocted compatibility

[English](compatibility.md) · [Português (Brasil)](pt-BR/compatibility.md)

## Desktop contract

- provide a valid `.desktop` entry;
- open files and directories through normal desktop actions;
- accept documented file and line arguments;
- use XDG configuration, data and cache locations;
- remain usable with no Noctalia session available.

## Noctalia contract

1. **Launcher:** Nocted is discoverable and can open a project or file.
2. **Navigation:** a launcher action can request a file and line when supported.
3. **Theme:** a documented Dinx Theme adapter maps semantic colors, fonts and light/dark mode.
4. **Failure isolation:** optional IPC or notifications never block editing.

Nocted must not parse private Noctalia configuration files as a stable API.

## Editor acceptance matrix

| Area | Acceptance check |
| --- | --- |
| Files | open, edit and save without losing content |
| Directories | project root and files are navigable |
| Undo | undo/redo preserves dirty state and selection behavior |
| Syntax | supported fixtures receive deterministic highlighting |
| LSP | diagnostics and navigation survive server failure |
| Git | status and diff reflect workspace changes |
| Launch | file/line and `.desktop` arguments are deterministic |
| Fallback | basic editing works without LSP, Git or Noctalia |
