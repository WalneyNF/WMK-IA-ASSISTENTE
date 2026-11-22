# 📥 Download do WMK IA Assistente

## Versão de referência: v0.6.0

**Estado:** código-fonte v0.6.0 recebido e validado em ambiente de análise (43 testes aprovados). A publicação dos fontes no GitHub e do VSIX no Release depende do envio do ZIP pelo mantenedor e da conclusão da automação. Não confunda workflow preparado com arquivo já publicado.

### 1. Baixar para instalar
➡️ **[Abrir Releases](https://github.com/WalneyNF/WMK-IA-ASSISTENTE/releases)**

Na Release `v0.6.0`, baixe o arquivo `wmk-ia-assistente-0.6.0.vsix` **se ele estiver anexado**. Não confunda com os arquivos automáticos "Source code (zip/tar.gz)" do GitHub: eles não instalam a extensão diretamente.

### 2. Instalar no VS Code
1. Abra o Visual Studio Code.
2. Pressione `Ctrl+Shift+X`.
3. No menu `...` da página Extensões, escolha **Instalar do VSIX...**.
4. Selecione `wmk-ia-assistente-0.6.0.vsix`.
5. Recarregue a janela do editor, se solicitado.
6. Abra o robô WMK IA e configure Ollama ou suas credenciais próprias de Groq/OpenAI.

Ou no terminal:

```powershell
code --install-extension ".\wmk-ia-assistente-0.6.0.vsix" --force
```

### 3. Baixar ou publicar os fontes

Quando o repositório mostrar `package.json`, `extension.js`, `media/`, `tests/` e `manuais/`, os fontes estarão publicados. Nesse momento, use **Code → Download ZIP** ou `git clone` para obtê-los. Consulte [PUBLICAR-FONTES-v060.md](PUBLICAR-FONTES-v060.md) para enviar o pacote à pasta `publicacao/` e acionar a automação que valida e publica fontes/VSIX.

### 4. Para desenvolvedores
Acesse [repositório](https://github.com/WalneyNF/WMK-IA-ASSISTENTE). Para clonar e compilar, é necessário que o projeto completo, incluindo `package.json`, `extension.js`, `media/` e `tests/`, tenha sido publicado.

### 5. Aviso de segurança e recursos disponíveis
- Chat, seleção de agentes, skills e contexto do arquivo ativo funcionando na v0.6.0 testada.
- As alterações de código são propostas e devem ser revisadas/aprovadas.
- **MCP é apenas um catálogo nesta versão:** não executa comandos em Blender ou outros servidores.
- Chaves da Groq/OpenAI são particulares de cada usuário. Nunca as publique no repositório.

### 6. Disponibilizar o VSIX (para o mantenedor)
Se o VSIX já existe no computador:

1. Abra [Releases](https://github.com/WalneyNF/WMK-IA-ASSISTENTE/releases).
2. Clique **Draft a new release**.
3. Crie/selecione a tag `v0.6.0` somente após publicar os fontes correspondentes.
4. Anexe `wmk-ia-assistente-0.6.0.vsix` em **Attach binaries**.
5. Marque **pre-release** enquanto experimental e publique.

Para atualizações automáticas e pesquisa dentro do VS Code, é necessário publicar separadamente no Marketplace. Veja [o guia](PUBLICAR-NO-MARKETPLACE.md).

---
Walney Moreira Klein — walneyk@hotmail.com
