# Arquitetura do Nocted

[Português (Brasil)](architecture.md) · [English](../architecture.md)

## Camadas

```text
Interface do aplicativo
  janelas · abas · árvore de projeto · comandos · configurações

Adaptador do motor de edição
  buffer de texto · seleções · undo/redo · atualizações incrementais

Ferramentas de linguagem
  parser de sintaxe · cliente LSP · gerenciador de processos

Serviços de projeto
  filesystem · status/diff do Git · diagnósticos · arquivos recentes
```

A interface controla o fluxo de trabalho e a apresentação. O adaptador do motor de edição impede que a interface dependa de uma implementação concreta de buffer. As ferramentas de linguagem usam processos e não podem ser necessárias para a edição básica.

## Limite do motor de edição

O limite deve suportar:

- abrir e salvar texto com comportamento de encoding explícito;
- seleções, cursores e múltiplos cursores quando suportados;
- undo/redo e rastreamento de estado alterado;
- edições incrementais adequadas à sincronização LSP;
- mapeamento de linha/coluna para diagnósticos e navegação;
- limites para arquivos grandes que sejam visíveis, nunca silenciosos.

## Limites de linguagem e Git

Servidores LSP são processos externos. O Nocted deve tratar falha de inicialização, mensagens malformadas, encerramento do servidor e mudanças de workspace sem perder edições. A integração Git começa com status e diff somente leitura; mutações exigem ações explícitas da pessoa usuária.

O Nocted não pode executar código do projeto silenciosamente. Plugins e configurações do projeto são entradas não confiáveis.

## Limites da plataforma

O Nocted usa caminhos XDG para configuração/dados/cache, expõe uma entrada `.desktop` válida e aceita argumentos documentados de arquivo/linha. A integração com o Noctalia é opcional e não pode impedir a inicialização.
