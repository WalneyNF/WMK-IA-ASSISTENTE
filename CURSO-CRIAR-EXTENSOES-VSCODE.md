# Curso prático — Crie sua primeira extensão para Visual Studio Code

**Público:** iniciantes, estudantes e desenvolvedores que nunca publicaram extensões.  
**Idioma:** português brasileiro.  
**Exemplo real:** WMK IA Assistente, de Walney Moreira Klein — walneyk@hotmail.com.

Este tutorial ensina a criar **sua própria extensão**, não apenas instalar a WMK IA. Você pode usar outro nome, logo e publicador.

## Módulo 1 — Como funciona uma extensão?

Uma extensão é um pacote que o VS Code carrega para adicionar comandos, menus, painéis e outras funcionalidades. Há quatro coisas diferentes:

| Item | Para que serve |
| --- | --- |
| Código-fonte | Arquivos JavaScript/TypeScript e demais recursos que você desenvolve |
| VSIX | Arquivo instalável criado a partir do código |
| GitHub | Hospeda projeto, documentação e downloads via Releases |
| Visual Studio Marketplace | Loja onde usuários encontram e instalam a extensão e recebem atualizações |

A versão de código rodando com **F5** numa janela de desenvolvimento não é a mesma que está instalada no VS Code normal.

## Módulo 2 — Criar uma extensão mínima do zero

Pré-requisitos: Node.js, VS Code e terminal PowerShell.

Crie uma pasta chamada `minha-primeira-extensao`. Dentro dela, crie **package.json**:

```json
{
  "name": "minha-primeira-extensao",
  "displayName": "Minha Primeira Extensão",
  "description": "Exemplo didático de extensão em português",
  "version": "0.0.1",
  "publisher": "SEU-PUBLICADOR",
  "engines": { "vscode": "^1.85.0" },
  "main": "./extension.js",
  "activationEvents": [],
  "contributes": {
    "commands": [
      { "command": "minhaExtensao.ola", "title": "Minha Extensão: Dizer olá" }
    ]
  },
  "scripts": {
    "check": "node --check extension.js"
  }
}
```

Crie **extension.js**:

```javascript
const vscode = require('vscode');

function activate(context) {
  const cmd = vscode.commands.registerCommand('minhaExtensao.ola', () => {
    vscode.window.showInformationMessage('Minha primeira extensão funciona!');
  });
  context.subscriptions.push(cmd);
}

function deactivate() {}

module.exports = { activate, deactivate };
```

Crie **.vscode/launch.json** para executar pelo F5:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Executar extensão",
      "type": "extensionHost",
      "request": "launch",
      "args": ["--extensionDevelopmentPath=${workspaceFolder}"]
    }
  ]
}
```

> `publisher: "SEU-PUBLICADOR"` é provisório. Antes de publicar no Marketplace, substitua pelo ID real do publicador cadastrado em sua conta Microsoft. Evite usar nomes de marcas de terceiros.

## Módulo 3 — Primeiro teste real

1. Abra a pasta `minha-primeira-extensao` no VS Code.
2. Execute `npm run check`.
3. Pressione **F5** para abrir a janela **Extension Development Host**.
4. Na janela nova, pressione `Ctrl+Shift+P` e procure **Minha Extensão: Dizer olá**.
5. Execute o comando: deve aparecer **Minha primeira extensão funciona!**.
6. Se falhar, verifique **Exibir → Saída → Extension Host** e o **Developer Tools**.

**Exercício:** crie outro comando `minhaExtensao.hora` que apresente a hora do computador.

## Módulo 4 — Criar ícone, README, licença e exemplos

O Marketplace usa o nome e o ícone do manifesto, enquanto o GitHub usa o README e as imagens do repositório.

- Crie um PNG quadrado para seu ícone, por exemplo `assets/icon.png`.
- Acrescente `"icon": "assets/icon.png"` ao manifesto.
- Coloque uma imagem maior no README com `![Minha extensão](assets/capa.png)`.
- Confira no GitHub se **os arquivos existem**, caso contrário o README mostrará imagens quebradas.
- Escolha uma licença adequada e inclua o arquivo `LICENSE`. Não declare uma licença que você não publicou.

**Exercício:** crie uma imagem de capa, salve em `assets/capa.png` e abra o README em pré-visualização.

## Módulo 5 — Gerar o VSIX

Na pasta do projeto, execute:

```powershell
npm run check
npx --yes @vscode/vsce package --no-dependencies
```

O comando deverá produzir `minha-primeira-extensao-0.0.1.vsix`, se a configuração do projeto e requisitos forem válidos.

Para instalar:

```powershell
code --install-extension ".\minha-primeira-extensao-0.0.1.vsix" --force
code --list-extensions --show-versions
```

**Verificação:** feche a janela F5, abra o VS Code normal e execute o comando da extensão instalada. Não confunda um VSIX existente com uma instalação realmente concluída.

## Módulo 6 — Criar seu publicador no Marketplace

1. Acesse https://marketplace.visualstudio.com/manage/publishers/ .
2. Entre com sua conta Microsoft.
3. Crie um **publisher**, preenchendo **Name** (nome exibido) e **ID** (identificador único).
4. Preencha descrição, suporte, site, código-fonte e logo conforme necessário.
5. Coloque exatamente o ID escolhido na propriedade `publisher` do `package.json`.
6. **Empacote novamente** depois de corrigir o manifesto.

**Erro real que ocorreu na WMK:** o site tinha o publisher `WMK`, mas o VSIX havia sido construído com `wmk-estudos`; o Marketplace recusou. A correção não é renomear o VSIX: é corrigir o manifesto e criar outro VSIX.

## Módulo 7 — Publicar a extensão para o mundo

1. No painel do publisher, escolha **New extension → Visual Studio Code**.
2. Selecione o arquivo VSIX corrigido.
3. Aguarde o processamento: **Verifying** ainda não é **Published**.
4. Após aprovação, abra a página pública do item e pesquise-o dentro do VS Code.
5. Teste a instalação como usuário novo e confirme ícone, nome, comandos e versão.

No caso WMK, o publicador apareceu como **WMK** e a extensão como **WMK IA Assistente**, versão `0.6.0`, com status verde e disponibilidade pública.

## Módulo 8 — Publicar o código e os downloads no GitHub

1. Crie um repositório no GitHub e envie o código completo (não apenas o README).
2. Mantenha `README.md`, `LICENSE`, `CHANGELOG.md`, imagens e manuais.
3. Não envie tokens, chaves de API, dados privados, `node_modules` e arquivos de clientes.
4. Em **Releases → Draft a new release**, escolha uma tag (por exemplo `v0.0.1`).
5. Anexe o **VSIX real** e publique.
6. Abra os links numa janela anônima para comprovar acesso público.

O GitHub Releases e o Marketplace são **canais diferentes**. Ter um deles publicado não significa que o outro esteja pronto.

## Módulo 9 — Atualizar sem quebrar os usuários

1. Altere a propriedade `version` em `package.json`, por exemplo de `0.0.1` para `0.0.2`.
2. Execute testes, gere novo VSIX e instale-o para validar.
3. Faça commit dos fontes e atualize o CHANGELOG.
4. Crie uma nova Release e envie uma atualização ao Marketplace.
5. Preserve os campos `publisher` e `name` para manter a identidade da extensão. Alterá-los costuma criar outra extensão.

## Módulo 10 — Erros frequentes e como diagnosticar

| Sintoma | Possível causa | O que conferir |
| --- | --- | --- |
| A versão nova não aparece | F5 executa fontes antigos; VSIX incorreto | Caminho aberto, versão em `package.json`, versão instalada |
| `An error occurred while loading view` | Exceção no JavaScript da Webview | Logs do Extension Host, inicialização do painel, variáveis indefinidas |
| VSIX gerado, mas BAT falha | Erro no script de validação ou instalação | Separar empacotamento, verificação e instalação |
| Marketplace rejeita publisher | `publisher` divergente do ID da conta | `package.json` e manifesto interno do VSIX |
| Imagem quebrada no README | Arquivo não enviado ou caminho incorreto | Caminhos e letras maiúsculas/minúsculas no GitHub |
| IA ignora o código aberto | Arquivo não foi anexado ao contexto | Permissão, botão de arquivo ativo e confirmação do conteúdo enviado |
| Testes verdes e interface quebrada | Testes não cobrem a Webview em execução | Testar abertura real, comandos e regressões |

## Módulo 11 — Segurança e privacidade

- Nunca grave API keys dentro do ZIP ou repositório.
- Prefira o `SecretStorage` do VS Code para segredos de usuários.
- Confirme antes de executar tarefas ou editar arquivos.
- Ao enviar código a modelos online, informe o usuário sobre a transmissão.
- Não anuncie MCP, execução autônoma ou outras integrações que ainda não funcionam.
- Leia as exigências de privacidade e publicação do Marketplace antes de distribuir.

## Módulo 12 — Projeto final para o estudante

Crie uma extensão chamada **Meu Organizador** que:
1. Adiciona dois comandos à paleta;
2. Exibe notificações úteis;
3. Tem ícone e README com screenshots;
4. Passa na verificação de sintaxe;
5. Gera um VSIX instalável;
6. É instalada e testada num segundo ambiente;
7. É publicada em um repositório GitHub com Release;
8. Opcionalmente, é publicada no Marketplace usando publisher próprio.

### Lista de verificação de publicação

- [ ] Nome, versão, publisher e ícone corretos
- [ ] Código completo disponível
- [ ] Testes de sintaxe e funcionamento concluídos
- [ ] VSIX gerado e instalado com sucesso
- [ ] Chaves e dados privados removidos
- [ ] README e imagens exibidos corretamente
- [ ] Release com VSIX público confirmado
- [ ] Marketplace publicado e localizado na busca
- [ ] Manual de usuário e histórico de versões disponíveis

## Referências

- [Documentação oficial VS Code Extension API](https://code.visualstudio.com/api)
- [Guia oficial de publicação de extensões](https://code.visualstudio.com/api/working-with-extensions/publishing-extension)
- [Documentação de teste de extensões](https://code.visualstudio.com/api/working-with-extensions/testing-extension)
- [Guia da primeira extensão WMK](MANUAL-PRIMEIRA-EXTENSAO-MARKETPLACE.md)
- [Manual de utilização do WMK IA Assistente](MANUAL-V060.md)

---
**WMK — Walney Moreira Klein — walneyk@hotmail.com**
