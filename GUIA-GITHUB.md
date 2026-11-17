# Como contribuir e publicar novas versões

## Para usuários
Baixe o pacote `.vsix` da página Releases, no GitHub. Instale por **VS Code > Extensões > ... > Instalar do VSIX...**. Cada usuário configura sua própria IA e chave, se necessário.

## Para desenvolver
```powershell
git clone https://github.com/WalneyNF/WMK-IA-ASSISTENTE.git
cd WMK-IA-ASSISTENTE
npm run check
npm test
```

Edite `extension.js`, os arquivos de `media/`, os manuais HTML e os testes. Teste pelo `F5`.

## Para enviar alterações
```powershell
git add .
git commit -m "Descreva a melhoria"
git push
```

## Para preparar nova versão
Atualize a propriedade `version` no `package.json` e faça commit. Crie uma tag do mesmo número:
```powershell
git tag v0.5.3
git push origin v0.5.3
```
A ação de GitHub verifica sintaxe, executa testes e gera o VSIX. Se o job de Release falhar por falta de permissão, revise as permissões de Actions do repositório ou publique manualmente pelo menu Releases.

## Segurança
Nunca publique API keys, arquivos privados ou dados sensíveis de clientes. Revise cada alteração antes de aplicar.
