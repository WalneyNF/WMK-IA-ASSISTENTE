# 🤖 WMK IA Assistente

Extensão experimental para **Visual Studio Code**, com chat de inteligência artificial, análise de código, agentes configuráveis e propostas de criação/edição de arquivos com aprovação.

**Autor:** Walney Moreira Klein — walneyk@hotmail.com  
**Versão em desenvolvimento:** 0.5.2  
**Idioma:** português brasileiro  
**Licença:** MIT (consulte o arquivo LICENSE após o envio do código-fonte)

> ⚠️ Projeto experimental: antes de utilizar a edição assistida, faça backup ou commit de seus arquivos. O projeto está em testes e ainda não equivale à execução autônoma do OpenCode/Codex.

## Funcionalidades

- Chat na barra lateral do VS Code e opção de abrir chat ampliado.
- Respostas em streaming, cópia de mensagens e exportação de texto em Markdown.
- Provedores: **Ollama (local)**, **Groq** e **OpenAI** por API.
- Configuração global do provedor e modelo padrão para todos os agentes.
- Cadastro de agentes com prompts, temperatura, `top_p` e limites de contexto e saída.
- Análise de arquivos e amostra do projeto.
- Propostas de edição/criação de arquivos com comparação e aprovação.
- Manuais HTML em português, exemplos, testes e roadmap.

## Instalação para usuários

### Opção A — VSIX (mais fácil)

Quando houver uma versão publicada, acesse **[Releases](https://github.com/WalneyNF/WMK-IA-ASSISTENTE/releases)** e baixe `wmk-ia-assistente-X.Y.Z.vsix`.

No VS Code:

1. Abra **Extensões** (`Ctrl + Shift + X`).
2. Clique no menu `...` → **Instalar do VSIX...**.
3. Selecione o arquivo baixado.
4. Abra o ícone do **WMK IA** na barra lateral.

> Se a página de Releases ainda não tiver o VSIX, significa que não houve publicação de um instalador. É possível gerar um pacote a partir do código-fonte quando ele estiver disponível.

### Opção B — Estudar e modificar o código-fonte

1. Instale Node.js, Git e VS Code.
2. Clone: `git clone https://github.com/WalneyNF/WMK-IA-ASSISTENTE.git`
3. Abra a pasta no VS Code.
4. Execute `npm run check` e `npm test`.
5. Pressione `F5` para testar a extensão.
6. Para gerar instalador: `npx --yes @vscode/vsce package --no-dependencies`.

## Configurar IA

### Ollama (local)

Instale Ollama, baixe um modelo de conversa/código e configure o WMK IA para usar o servidor local em `http://127.0.0.1:11434`. Exemplo: `ollama pull qwen2.5-coder:3b`.

### Groq (online)

Obtenha sua própria API key em [Groq Console](https://console.groq.com/keys), abra o cadastro de provedores da extensão, configure **Groq**, guarde a chave na opção protegida e escolha um modelo disponível em sua conta, como `openai/gpt-oss-20b` se estiver habilitado.

### OpenAI (online)

Configure a chave da API OpenAI na seção de provedores e selecione um modelo suportado pela conta.

**Importante:** cada usuário utiliza suas próprias credenciais; não publique sua chave em issues, commits, prints ou arquivos. O uso e os limites dos provedores dependem de cada serviço.

## Desenvolvimento e atualização

```powershell
npm run check
npm test
npx --yes @vscode/vsce package --no-dependencies
```

Depois de cada atualização, altere a versão em `package.json`, envie um commit e crie uma tag `vX.Y.Z`. O workflow em `.github/workflows/vsix.yml` gera o pacote e, para tags, publica o VSIX como Release.

Consulte **GUIA-GITHUB.md** e os **manuais/** assim que todos os arquivos do projeto forem publicados.

## Segurança

Não execute propostas de código sem revisar as diferenças. Não inclua arquivos privados de clientes, segredos, tokens ou credenciais nos contextos da IA. Provedores online recebem o texto enviado na requisição.

## Próximas melhorias

Histórico persistente por projeto, controle de consumo/tokens, múltiplos arquivos por tarefa, testes assistidos, agentes com permissões e relatórios de alterações.

---

**WMK — Walney Moreira Klein — walneyk@hotmail.com**
