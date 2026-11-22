# Publicar fontes completos e disponibilizar VSIX — WMK IA Assistente v0.6.0

**Autor:** Walney Moreira Klein — walneyk@hotmail.com.

## Estado atual

O ZIP original fornecido pelo autor contém `extension.js`, `package.json`, módulos JavaScript, `media/`, `tests/`, manuais e um VSIX v0.6.0. Em auditoria local, **43 testes passaram** com Node 22 e `npm run check` terminou sem erro. O conteúdo do pacote não foi testado na interface do VS Code Windows nesta verificação.

**O GitHub só oferecerá download dos fontes publicados depois do envio do ZIP e da execução bem-sucedida do workflow.** A presença deste manual ou do workflow não significa que os fontes já foram enviados.

## Método recomendado: publicação pelo próprio GitHub

1. Baixe a distribuição de fontes aprovada e renomeie-a para exatamente `wmk-ia-assistente-v0.6.0-fontes.zip`, se necessário.
2. Acesse a pasta [publicacao/](https://github.com/WalneyNF/WMK-IA-ASSISTENTE/tree/main/publicacao).
3. Clique **Add file → Upload files** e escolha o ZIP. O caminho final precisa ser exatamente `publicacao/wmk-ia-assistente-v0.6.0-fontes.zip`.
4. Confirme o commit na branch `main`. Essa publicação requer acesso de escrita do titular do repositório.
5. Acompanhe [Actions](https://github.com/WalneyNF/WMK-IA-ASSISTENTE/actions). O workflow `Publicar fontes WMK IA v0.6.0` executará checagem de sintaxe, testes, geração de VSIX, publicação dos fontes e criação de Release.
6. Após conclusão bem-sucedida, confira a raiz do repositório (`package.json`, `extension.js`, `media/`, `tests/`) e [Releases](https://github.com/WalneyNF/WMK-IA-ASSISTENTE/releases) para baixar `wmk-ia-assistente-0.6.0.vsix`.

A automação aceita ZIP com arquivos na raiz ou sob `wmk-ia-assistente/`, valida a identidade **wmk-estudos.wmk-ia-assistente** v0.6.0, rejeita caminhos suspeitos e só extrai uma lista restrita de fontes. O ZIP temporário é retirado do rastreamento Git após publicar para não duplicar binários. Outros documentos do repositório são preservados.

## Método alternativo: script de publicação local

Na distribuição de fontes, extraia a pasta e rode:

```powershell
cd D:\pasta-onde-extraiu\wmk-ia-assistente
.\PUBLICAR-FONTES-DO-ZIP.ps1 -RepoDir 'D:\Ferramentas\WMK-IA-ASSISTENTE'
```

O script executa `npm run check` e `npm test`, clona o repositório se necessário, copia somente os arquivos previstos, mostra mudanças e pede a palavra **PUBLICAR** antes do `git push`. Necessita Git e autenticação da sua conta. Não há upload automático oculto.

## Instalação do VSIX

No VS Code: Extensões (`Ctrl+Shift+X`) → menu `...` → **Instalar do VSIX...** → escolha `wmk-ia-assistente-0.6.0.vsix`. Também pode usar `code --install-extension .\wmk-ia-assistente-0.6.0.vsix --force`.

## Atenção à identidade da extensão

O `package.json` e o VSIX fornecidos declaram `publisher=wmk-estudos`, mas o README antigo possui link que aponta para `WMK.wmk-ia-assistente` no Marketplace. **Isso pode identificar extensões diferentes.** Confirme o publisher do seu cadastro antes de publicar uma atualização na loja.

## Segurança e funcionamento

Não compartilhe `.env`, chaves privadas, tokens, `node_modules` ou arquivos de clientes. A extensão permite execução **humana confirmada** de tarefas do VS Code, que podem executar scripts do workspace; use somente em projetos confiáveis. O catálogo MCP ainda não executa ferramentas externas. Não há comprovação de isolamento forte contra junções NTFS, symlinks ou condições de corrida.

Consulte o relatório `ANALISE-TECNICA-v060.md` dentro da distribuição para melhorias recomendadas.
