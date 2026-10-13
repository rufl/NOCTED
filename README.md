# Nocted

[Português (Brasil)](README.md) · [English](README.en.md)

Nocted é o editor de código leve da família DINX, com interface própria em Zig, sintaxe, LSP e integração com Git.

O repositório é privado e está em alpha. O objetivo inicial é um editor rápido e confiável, não um IDE que tente reproduzir o escopo do VS Code.

## Objetivos

- abrir arquivos e diretórios de projetos;
- editar texto com seleção, undo/redo e busca/substituição confiáveis;
- oferecer destaque de sintaxe baseado em parser comprovado;
- gerenciar servidores LSP e apresentar diagnósticos, definições e referências;
- mostrar status, diffs e marcadores de alterações do Git;
- aceitar abertura por arquivo/linha e integração com `.desktop`;
- seguir temas, fontes e modos claro/escuro por contrato documentado;
- funcionar sem o Noctalia e fora da distribuição DINX.

## Arquitetura

```text
Interface Nocted em Zig
  janelas · abas · árvore de projeto · comandos · configurações

Adaptador do motor de edição
  buffer · seleção · undo/redo · atualizações incrementais

Serviços de linguagem
  parser de sintaxe · cliente LSP · processos de language server

Integração de projeto
  diretórios · Git · arquivos recentes · diagnósticos
```

O editor deve usar componentes maduros para buffer, parsing e LSP. A experiência, integração e fluxo de trabalho são as partes diferenciadoras.

## Roadmap inicial

1. Janela, buffer, arquivo e diretório.
2. Seleção, undo/redo, busca e atalhos.
3. Sintaxe e navegação de projeto.
4. LSP: diagnósticos, definições e referências.
5. Git: status, diff e marcadores.
6. Integração Noctalia e temas.

## Documentação

- [Arquitetura](docs/pt-BR/architecture.md)
- [Compatibilidade](docs/pt-BR/compatibility.md)

Versões em inglês:

- [Architecture](docs/architecture.md)
- [Compatibility](docs/compatibility.md)

DINX: [rufl/dinx-alpha](https://github.com/rufl/dinx-alpha)
