# WMK IA Assistente v0.6.0 — Testes e instalação

## Funcionamento confirmado no Windows
O teste enviado pelo autor em 17/11/2026 mostra o painel WMK IA `v0.6.0`, o Groq `openai/gpt-oss-20b` conectado, o arquivo `teste.js` enviado (201 caracteres) e uma resposta explicando a função `calcularTotal`.

## Recursos
- Chat com Ollama, Groq e OpenAI; provedor/modelo globais.
- Chat lateral e ampliado, cópia de respostas e Markdown.
- Agentes com prompts, parâmetros, seleção de skills e permissões.
- Catálogo de 50 skills iniciais, ampliável.
- Leitura de arquivo ativo com consentimento: `Arquivo ativo: LIGADO`; ao desativar, não anexa automaticamente.
- Propostas de alteração/criação de arquivos com confirmação e comparação.
- Inspeção de arquivos e tarefas VS Code sob autorização.
- Catálogo de MCP: **cadastro apenas; execução MCP ainda não disponível**.
- Tool calling autônomo multi-etapas e MCP Blender **ainda não implementados**.

## Tutorial: testar revisão de código
1. Abra um projeto de testes e `teste.js`.
2. Selecione o agente Revisor de código.
3. No cadastro do agente, habilite a ferramenta Inspecionar arquivo e as skills desejadas (precisam estar habilitadas globalmente).
4. Ative `Arquivo ativo: LIGADO` no chat e confira o arquivo informado.
5. Pergunte: "Explique o arquivo ativo, identifique erros e sugira testes. Não edite ainda".
6. Revise a resposta da IA: sugestões não são garantia de correção.
7. Para modificar, use Propor edição, examine o diff e aprove somente se estiver correto.

## Tutorial: skills
Em Ferramentas > Skills, selecione uma skill, leia suas instruções, habilite-a e salve. Em Gerenciar agentes, selecione um agente e associe as skills desejadas. Uma skill é uma instrução reutilizável, não um programa executável.

## Tutorial: MCP
Em Ferramentas > MCP, é possível cadastrar metadados do servidor (nome, transporte e comando/URL). Na v0.6.0 **não é possível conectar e executar ferramentas MCP**; o campo de conexão está indisponível. Para integrar Blender MCP futuramente, será preciso um cliente MCP de verdade com descoberta de ferramentas, autorização, execução, resultados e tratamento de erros.

## Código-fonte e instalação
A publicação do README não substitui o código-fonte. O repositório deve incluir `package.json`, `extension.js`, `media/`, `tests/`, `manuais/` e demais arquivos. O instalador é um arquivo `.vsix`, que deve ser publicado em Releases.

## Segurança
Não inclua credenciais ou código privado em issues, prints ou commits. Ao usar Groq/OpenAI, o conteúdo anexado é enviado ao provedor. Use projetos de teste para validar edição assistida.

Autor: Walney Moreira Klein — walneyk@hotmail.com
