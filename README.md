<p align="center">
  <img src="assets/logo-wmk.jpg" alt="Logo oficial WMK IA Assistente" width="220" />
</p>

# 🤖 WMK IA Assistente — v0.6.0

**Assistente de programação e documentação com IA para Visual Studio Code.** Chat lateral/ampliado, provedores configuráveis, agentes, skills, leitura de código e propostas de edição com aprovação.

**Autor:** Walney Moreira Klein — walneyk@hotmail.com  
**Versão funcional testada pelo autor no Windows:** **0.6.0** (17/11/2026)  
**Idioma:** Português brasileiro  
**Situação:** v0.6.0 publicada no Visual Studio Marketplace; etapa de desenvolvimento encerrada como versão experimental de referência.

> **Distribuição:** a extensão v0.6.0 foi publicada no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WMK.wmk-ia-assistente). O GitHub Releases ainda não tinha VSIX público na última verificação. Para instalar diretamente no VS Code, use a loja.

## ✅ Funcionalidades existentes na v0.6.0

| Recurso | Situação |
| --- | --- |
| Chat lateral, chat ampliado e streaming | Implementado |
| Copiar mensagens, copiar Markdown e ajustar fonte | Implementado |
| Ollama, Groq e OpenAI via API | Implementado |
| Provedor e modelo padrão compartilhados por todos os agentes | Implementado |
| Cadastro de agentes, prompts e parâmetros de geração | Implementado |
| Biblioteca de skills reutilizáveis (50 iniciais, ampliável) | Implementado |
| Associação de skills e permissões de ferramentas por agente | Implementado |
| **Arquivo ativo: LIGADO** — enviar código aberto ao chat | **Testado com sucesso** |
| Ler arquivos e inspecionar amostra de projeto | Implementado |
| Propor criação/edição de arquivos com revisão e aprovação | Implementado; ainda experimental |
| Executar tarefa do VS Code com confirmação | Implementado; ainda experimental |
| Cadastrar servidores MCP | Implementado **somente como catálogo** |
| Conexão/execução de ferramentas MCP ou Blender MCP | **Não implementado** |
| Execução autônoma de ferramentas pela IA | **Não implementado** |

### Teste confirmado: contexto do arquivo ativo

Em 17/11/2026, foi confirmado no VS Code que o WMK IA v0.6.0 enviou **201 caracteres** de `teste.js` para o modelo `openai/gpt-oss-20b` via Groq. A IA explicou a função `calcularTotal`, analisando o conteúdo real do editor, em vez de solicitar que o usuário copiasse o código manualmente.

**Como repetir:** abra um arquivo de testes, selecione um agente com permissão de inspeção, ative **Arquivo ativo: LIGADO**, confirme o nome do arquivo enviado e pergunte: `Explique este código e sugira melhorias sem modificar o arquivo`.

**Privacidade:** ao ativar esse recurso usando Groq/OpenAI, o código anexado é enviado ao provedor. Não envie documentos sigilosos sem autorização.

🌍 **[Instalar pelo Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WMK.wmk-ia-assistente)**

📥 **[Página de downloads e instalação](DOWNLOAD.md)**

## 📥 Como instalar o WMK IA

### A. Download pelo GitHub Releases

Acesse **[Releases](https://github.com/WalneyNF/WMK-IA-ASSISTENTE/releases)**.

**Somente quando um arquivo `.vsix` estiver anexado ao Release:**

1. Baixe `wmk-ia-assistente-0.6.0.vsix` (ou a versão mais recente disponível).
2. Abra o VS Code → **Extensões** (`Ctrl+Shift+X`).
3. Abra o menu `...` → **Instalar do VSIX...**
4. Escolha o pacote e recarregue a janela.
5. Clique no ícone 🤖 WMK IA, configure Ollama ou suas chaves pessoais Groq/OpenAI e selecione um agente.

Também é possível instalar pelo PowerShell:

```powershell
code --install-extension ".\wmk-ia-assistente-0.6.0.vsix" --force
```

A instalação por VSIX **não garante atualização automática**; para isso, a extensão deve ser publicada no Marketplace.

### B. Desenvolvedores — compilar do código-fonte

**Depois que todos os fontes estiverem publicados** no repositório:

```powershell
git clone https://github.com/WalneyNF/WMK-IA-ASSISTENTE.git
cd WMK-IA-ASSISTENTE
npm run check
npm test
npx --yes @vscode/vsce package --no-dependencies
```

Abra a pasta no VS Code e pressione `F5` para testar no **Extension Development Host**. A execução por F5 não substitui a extensão instalada.

## 🔑 Provedores

- **Ollama local:** configure o servidor, normalmente `http://127.0.0.1:11434`. Exemplo: `ollama pull qwen2.5-coder:3b`.
- **Groq:** obtenha sua chave em https://console.groq.com/keys, configure-a no cadastro de provedores e escolha um modelo disponível para sua conta.
- **OpenAI API:** configure sua própria chave e um modelo habilitado.

Cada usuário fornece suas credenciais. **Não publique chaves no GitHub.** Os limites de consumo e custos dependem do provedor/conta.

## 🤖 Agentes, skills e ferramentas

**Agente:** configura o papel, prompt, parâmetros e permissões.  
**Skill:** instruções reutilizáveis para tarefas específicas, como revisão de código, testes, documentação ou jogos.  
**Ferramenta:** operação autorizada de leitura, proposta de edição, criação ou tarefa.  
**MCP (Model Context Protocol):** protocolo para integrar ferramentas e fontes externas; **a execução MCP ainda não funciona nesta versão**.

Não confunda permissões cadastradas com execução autônoma: na v0.6.0 as ferramentas existentes são acionadas pelos controles da interface e têm limitações descritas na documentação.

## 📚 Documentação

- [Manual da v0.6.0 e testes de código](MANUAL-V060.md)
- **[Curso completo: crie sua primeira extensão do zero](CURSO-CRIAR-EXTENSOES-VSCODE.md)**
- [Manual completo de publicação para iniciantes](MANUAL-PRIMEIRA-EXTENSAO-MARKETPLACE.md)
- [Como publicar no VS Code Marketplace](PUBLICAR-NO-MARKETPLACE.md)
- [Como publicar fontes e atualizações](GUIA-PUBLICACAO.md)
- [Roadmap técnico](ROADMAP.md)

Os manuais HTML completos deverão acompanhar a publicação do código-fonte em `manuais/`.

## 🌍 Como encontrar a extensão na busca do VS Code?

**Publicar no GitHub não coloca a extensão na busca.** É necessário criar/usar um publisher no [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers/), conferir `publisher` e `name` em `package.json`, testar o VSIX e publicá-lo pela plataforma. Consulte [o guia passo a passo](PUBLICAR-NO-MARKETPLACE.md).

## 🔄 Como atualizar

1. Desenvolva em uma única pasta de código-fonte.
2. Execute `npm run check`, `npm test` e teste a interface pelo F5.
3. Incremente a propriedade `version` do `package.json` (por exemplo, de 0.6.0 para 0.6.1).
4. Gere um novo VSIX: `npx --yes @vscode/vsce package --no-dependencies`.
5. Instale e valide localmente.
6. Envie os fontes ao GitHub com commit e push.
7. Crie um Release com o VSIX; quando publicado no Marketplace, envie também a nova versão por lá.

**Não basta mudar o número da versão: o pacote deve conter o código novo.**

## ⚠️ Segurança e limitações

- Projeto experimental: faça backup/commit antes de aplicar sugestões de código.
- A IA pode sugerir testes incorretos; confira regras de negócio e resultados.
- Não compartilhe segredos, chaves, documentos de clientes ou código privado sem autorização.
- O catálogo MCP ainda não permite comandar Blender nem outros servidores.
- A existência de testes automatizados não comprova que toda a interface funciona em todas as máquinas.

---

**WMK — Walney Moreira Klein — walneyk@hotmail.com**
