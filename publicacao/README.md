# Envio do pacote de fontes para publicação automática

Esta pasta recebe **temporariamente** o arquivo `wmk-ia-assistente-v0.6.0-fontes.zip`.

O workflow [publicar-v060.yml](../.github/workflows/publicar-v060.yml) está preparado para:
1. Validar a identidade `WMK.wmk-ia-assistente` e a versão `0.6.0`;
2. Extrair o código-fonte, as imagens e os manuais para a raiz do repositório;
3. Executar testes;
4. Gerar um VSIX via `@vscode/vsce`;
5. Fazer commit dos fontes completos;
6. Criar a Release `v0.6.0` com o VSIX, se o workflow passar.

Para iniciar, abra [esta pasta no GitHub](https://github.com/WalneyNF/WMK-IA-ASSISTENTE/tree/main/publicacao), escolha **Add file → Upload files**, arraste o arquivo com o nome **exato** `wmk-ia-assistente-v0.6.0-fontes.zip` e conclua **Commit changes** no ramo `main`.

**Não envie credenciais.** Verifique sempre [Actions](https://github.com/WalneyNF/WMK-IA-ASSISTENTE/actions) e [Releases](https://github.com/WalneyNF/WMK-IA-ASSISTENTE/releases) para confirmar a conclusão. O workflow não deve ser considerado publicado antes de apresentar sucesso e um VSIX disponível ao público.
