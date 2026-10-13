# Compatibilidade do Nocted

[Português (Brasil)](compatibility.md) · [English](../compatibility.md)

## Contrato do desktop

- fornecer uma entrada `.desktop` válida;
- abrir arquivos e diretórios por ações normais do desktop;
- aceitar argumentos documentados de arquivo e linha;
- usar caminhos XDG para configuração, dados e cache;
- continuar utilizável sem uma sessão do Noctalia.

## Contrato com o Noctalia

1. **Launcher:** o Nocted é descoberto e consegue abrir um projeto ou arquivo.
2. **Navegação:** uma ação do launcher pode solicitar arquivo e linha quando suportado.
3. **Tema:** um adaptador documentado do Dinx Theme mapeia cores semânticas, fontes e modo claro/escuro.
4. **Isolamento de falhas:** IPC ou notificações opcionais nunca bloqueiam a edição.

O Nocted não deve interpretar arquivos de configuração privados do Noctalia como uma API estável.

## Matriz de aceitação do editor

| Área | Critério de aceitação |
| --- | --- |
| Arquivos | abrir, editar e salvar sem perder conteúdo |
| Diretórios | raiz do projeto e arquivos são navegáveis |
| Undo | undo/redo preserva estado alterado e comportamento da seleção |
| Sintaxe | fixtures suportados recebem destaque determinístico |
| LSP | diagnósticos e navegação sobrevivem à falha do servidor |
| Git | status e diff refletem alterações do workspace |
| Inicialização | argumentos de arquivo/linha e `.desktop` são determinísticos |
| Fallback | edição básica funciona sem LSP, Git ou Noctalia |
