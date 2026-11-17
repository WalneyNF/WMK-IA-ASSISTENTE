# Como publicar WMK IA Assistente no VS Code Marketplace

> Confira também https://code.visualstudio.com/api/working-with-extensions/publishing-extension

## Passo 1: verificar o projeto
O repositório público está em https://github.com/WalneyNF/WMK-IA-ASSISTENTE . Antes de publicar, confirme que os arquivos-fonte estão efetivamente no GitHub. Atualize README, LICENSE, imagens e manuais.

No `package.json`, confira `name: wmk-ia-assistente`, `publisher: wmk-estudos`, `version: 0.6.0` (ou a versão efetiva). **O ID do publisher do Marketplace deve ser exatamente o informado no pacote**. Se `wmk-estudos` não estiver disponível para sua conta, será necessário escolher um publisher próprio e alterar a identidade da extensão, o que pode impedir atualização automática dos VSIX antigos.

## Passo 2: criar o publicador
1. Abra https://marketplace.visualstudio.com/manage/publishers/ e entre na conta Microsoft.
2. Crie um publisher, escolhendo um ID disponível (idealmente `wmk-estudos`, se puder).
3. Preencha nome de exibição, descrição, página oficial e demais dados solicitados.
4. Confirme que a conta tem permissão para publicar nesse publisher.

## Passo 3: gerar o VSIX
Na pasta que contém o código real:
```powershell
npm run check
npm test
npx --yes @vscode/vsce package --no-dependencies
```
Confira se foi gerado `wmk-ia-assistente-0.6.0.vsix`. Instale e teste antes de publicar.

## Passo 4: primeira publicação (recomendada: manual)
1. No portal do publisher, escolha **New Extension > Visual Studio Code**.
2. Envie o VSIX testado e siga as validações.
3. Aguarde o processamento/aprovação da listagem.
4. Procure `WMK IA Assistente` em Extensões no VS Code.
5. A listagem ficará no formato `https://marketplace.visualstudio.com/items?itemName=wmk-estudos.wmk-ia-assistente` **somente depois de publicada com esse ID**.

## Passo 5: atualizar
1. Faça alterações e testes; incremente `version` (ex.: 0.6.1).
2. Gere e instale localmente o novo VSIX.
3. Envie o novo VSIX pelo portal do publisher.
4. O VS Code poderá atualizar automaticamente a extensão distribuída pelo Marketplace.
5. Publique também código-fonte, changelog e Release no GitHub.

## Automação futura sem PAT
A documentação oficial de novembro/2026 recomenda **Trusted Publishing/OIDC** em GitHub Actions. Configure uma política de trusted publishing no publisher, associada ao repositório e workflow. O workflow de publicação precisará de `id-token: write` e de versão compatível de `@vscode/vsce` (4.0.2+), então execute `npx @vscode/vsce publish --oidc`. Faça isso apenas depois de testar a publicação manual. Não coloque tokens em README nem no código.

## Diferenças importantes
- GitHub com código: permite estudar e contribuir.
- GitHub Release com VSIX: permite instalar manualmente.
- Marketplace: permite encontrar por pesquisa e receber atualizações.
- F5: executa código de desenvolvimento, não substitui a extensão instalada.

## Cuidados
A versão 0.6.0 continua experimental: o MCP ainda não executa ações e as propostas de edição precisam ser revisadas. Não prometa autonomia total nem integração Blender MCP até haver testes reais.
