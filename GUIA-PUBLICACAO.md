# WMK IA — Guia para publicar código e atualizações

## Situação do repositório
O GitHub está público, mas confirme que a árvore contém `package.json`, `extension.js`, `media/`, `tests/` e `manuais/`. Um README sozinho **não** permite instalar nem compilar a extensão.

## 1. Publicar o código-fonte
Na pasta do projeto **mais recente e testado** (não na pasta interna de extensões do VS Code):
```powershell
git status
git remote -v
git add .
git commit -m "Publicar código-fonte e documentação"
git push origin main
```
Se a pasta não foi clonada do repositório, primeiro use `git clone https://github.com/WalneyNF/WMK-IA-ASSISTENTE.git` e copie os arquivos de fonte para dentro da pasta clonada, preservando `.git`. **Não envie chaves, tokens, projetos de clientes ou .env**.

## 2. Criar o VSIX local
```powershell
npm run check
npm test
npx --yes @vscode/vsce package
```
O arquivo final terá nome parecido com `wmk-ia-assistente-0.5.7.vsix`.

## 3. Testar a atualização local
```powershell
code --install-extension ".\wmk-ia-assistente-0.5.7.vsix" --force
```
Em seguida, no VS Code, execute **Developer: Reload Window**. Mantenha o mesmo `publisher` e `name` da extensão entre versões. Em novas versões, aumente `version` no package.json.

## 4. Release do GitHub
Envie primeiro fontes e workflow. Depois crie uma tag correspondente à versão testada:
```powershell
git tag v0.5.7
git push origin v0.5.7
```
Se `.github/workflows/vsix.yml` estiver configurado e tiver permissão de escrita, a Action poderá criar uma Release com o instalador. Confira a aba **Actions** e **Releases**; não presuma sucesso.

## 5. Marketplace VS Code
O GitHub não coloca automaticamente a extensão na pesquisa do VS Code. Crie um publicador em https://marketplace.visualstudio.com/manage/publishers/ ; o identificador precisa corresponder a `publisher` no package.json. Revise ícone, README, LICENSE, políticas e testes. Gere o VSIX e publique manualmente pelo portal ou use `vsce publish` com autenticação segura.

Documentação oficial: https://code.visualstudio.com/api/working-with-extensions/publishing-extension

Para automação futura, considere Trusted Publishing (OIDC) em vez de guardar tokens permanentes no repositório. Não exponha credenciais no código ou na conversa.

## 6. Atualizações para usuários
- **VSIX manual:** usuários baixam e instalam novo VSIX.
- **Marketplace:** VS Code pode buscar atualizações automaticamente da extensão publicada.
- **F5:** somente desenvolvimento, não instala a versão pública.

## 7. Antes de distribuir
- Testar com Ollama e provedores online usando credenciais próprias.
- Confirmar que ferramentas não executam comandos sem consentimento.
- Garantir backup e aprovação para edições de arquivos.
- Publicar manuais de usuário, desenvolvedor, agentes, skills e MCP.
- Informar claramente recursos experimentais e limitações.

Autor: Walney Moreira Klein — walneyk@hotmail.com
