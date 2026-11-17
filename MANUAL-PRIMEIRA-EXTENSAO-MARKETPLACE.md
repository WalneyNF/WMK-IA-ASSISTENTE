# Manual completo: minha primeira extensão no Visual Studio Code Marketplace

**Projeto-exemplo:** WMK IA Assistente — Walney Moreira Klein — walneyk@hotmail.com

## 1. Conceitos antes de publicar

- **Extensão**: código que roda no VS Code e pode criar comandos, painéis e ferramentas.
- **Nome público (`displayName`)**: nome que as pessoas enxergam, por exemplo **WMK IA Assistente**.
- **`name`**: identificador interno do pacote, por exemplo `wmk-ia-assistente`.
- **`publisher`**: ID do publicador registrado no Marketplace, por exemplo `WMK`. O nome visível e o publisher são coisas diferentes.
- **VSIX**: arquivo instalável da extensão.
- **GitHub repositório**: hospeda os fontes, README, imagens, manuais e testes.
- **GitHub Release**: página para distribuir downloads oficiais do VSIX.
- **Visual Studio Marketplace**: loja onde qualquer pessoa pesquisa, instala e recebe atualizações da extensão.

## 2. Criar uma conta e um publicador

1. Entre em https://marketplace.visualstudio.com/manage/publishers/ com conta Microsoft.
2. Crie um publicador. O ID precisa ser único e pertencer à sua conta.
3. Preencha nome visível, descrição, site, suporte, links e logo.
4. Guarde o **ID exato**, por exemplo `WMK`.
5. O campo `publisher` em `package.json` precisa coincidir com esse ID.

## 3. Configurar o package.json

```json
{
  "name": "wmk-ia-assistente",
  "displayName": "WMK IA Assistente",
  "publisher": "WMK",
  "version": "0.6.0",
  "icon": "assets/icon.png",
  "repository": {
    "type": "git",
    "url": "https://github.com/WalneyNF/WMK-IA-ASSISTENTE.git"
  }
}
```

Este é apenas um **trecho ilustrativo**, não substitui o restante do `package.json`. A imagem referenciada em `icon` precisa existir no pacote. Confira o campo `engines.vscode`, `main`, `contributes` e eventuais dependências.

**Erro observado na primeira publicação:** o VSIX tinha `publisher: wmk-estudos`, mas o publicador cadastrado era `WMK`. A correção exige editar o `package.json`, **gerar novamente o VSIX** e reenviá-lo. Só renomear o arquivo não altera os metadados internos.

## 4. Testar antes de empacotar

Abra a pasta verdadeira do projeto e execute:

```powershell
npm run check
npm test
```

Teste a interface com **F5**, que abre uma janela *Extension Development Host*. Essa janela não equivale à extensão instalada. Confira também com a extensão instalada normalmente.

Teste: chat, provedores, leitura do arquivo ativo, agentes e skills, permissões, edição com aprovação e erros do painel. Revise respostas geradas por IA.

## 5. Gerar e conferir o VSIX

```powershell
npx --yes @vscode/vsce package --no-dependencies
```

Confira se `wmk-ia-assistente-0.6.0.vsix` foi criado. Um VSIX é um arquivo ZIP com estrutura própria; não confunda ZIP dos fontes com VSIX.

No Windows, instale em uma cópia de teste do VS Code:

```powershell
code --install-extension ".\wmk-ia-assistente-0.6.0.vsix" --force
code --list-extensions --show-versions
```

Se mudar o `publisher`, o VS Code poderá interpretar a extensão como outra identidade técnica. Desinstale a antiga quando necessário.

## 6. Publicar fontes e manuais no GitHub

1. Crie ou abra um repositório, por exemplo https://github.com/WalneyNF/WMK-IA-ASSISTENTE .
2. Envie os arquivos de código reais: `package.json`, `extension.js`, `media/`, `assets/`, `tests/`, `manuais/`, etc.
3. Escreva um README com nome, versão, logo, funcionalidades, instalação, limitações, links e créditos.
4. Antes de enviar, remova `node_modules`, segredos, tokens, arquivos de clientes e pastas temporárias.
5. Faça `git add`, `git commit` e `git push`. Verifique no navegador que **os arquivos aparecem**.

**Imagens no README:** o caminho `assets/capa.png` só funciona quando esse arquivo foi publicado no repositório. Não basta escrevê-lo no Markdown.

## 7. Criar uma Release pública no GitHub

1. Abra https://github.com/WalneyNF/WMK-IA-ASSISTENTE/releases/new .
2. Crie ou selecione a tag `v0.6.0`.
3. Escreva o título **WMK IA Assistente v0.6.0**.
4. Anexe o arquivo **`wmk-ia-assistente-0.6.0.vsix`**.
5. Opcionalmente, anexe o código-fonte em ZIP e manuais.
6. Marque **pre-release** para versões experimentais.
7. Clique **Publish release**.
8. Confira numa janela anônima se o link pode ser acessado e o VSIX baixado.

A página https://github.com/WalneyNF/WMK-IA-ASSISTENTE/releases não oferece o instalador até ele estar anexado a uma Release publicada.

## 8. Publicar no Marketplace

1. Abra o painel do seu publisher e escolha **New extension → Visual Studio Code**.
2. Envie o VSIX **com o `publisher` correto**.
3. Aguarde as verificações do Marketplace. O status `Verifying` ainda não é `Published`.
4. Quando publicado, abra a página pública e pesquise por **WMK IA Assistente** dentro do VS Code.
5. Teste instalação, screenshot, descrição, créditos e comportamento da extensão.

Endereço esperado, se publicado sob o publisher WMK: https://marketplace.visualstudio.com/items?itemName=WMK.wmk-ia-assistente .

## 9. Atualizações futuras

1. Faça melhorias e testes.
2. Incremente a versão `version` no `package.json` (por exemplo `0.6.1`).
3. Gere e valide um novo VSIX.
4. Faça push do código atualizado, publique o Release correspondente no GitHub.
5. Envie a versão nova ao Marketplace. O VS Code poderá atualizar quem instalou pela loja.

Não confunda versão no README com o número real compilado no pacote. Eles devem coincidir.

## 10. Checklist final

- [ ] Nome público correto
- [ ] Publisher e name corretos
- [ ] Logo incluída e exibida corretamente
- [ ] README com imagens realmente publicadas
- [ ] Código-fonte completo disponível
- [ ] Testes e instalação reais realizados
- [ ] VSIX na Release pública
- [ ] Marketplace no estado Published
- [ ] Extensão encontrada por pesquisa no VS Code
- [ ] Chaves e dados privados fora da publicação

## 11. Lições do WMK IA Assistente

Os problemas encontrados ao publicar a primeira versão foram: versões antigas de fonte e VSIX, erros em Webview não cobertos por testes de sintaxe, identificador `publisher` diferente do cadastro Microsoft, confusão entre a janela F5 e a instalação normal e referências de README para imagens que ainda não haviam sido enviadas.

A solução sustentável é ter uma única fonte de verdade, teste funcional, versão identificada na interface, integração contínua, Release por tag e documentação em português.

---
**WMK — Walney Moreira Klein — walneyk@hotmail.com**
