# Roadmap WMK IA Assistente

> **Marco encerrado: WMK IA Assistente v0.6.0**, publicada no Visual Studio Marketplace sob o publicador WMK (confirmada pelo painel do autor em 17/11/2026). A versão permanece experimental. Os próximos itens são um backlog para eventual retomada; não estão prometidos para esta versão.

## Objetivo
Assistente de desenvolvimento acessível e em português, com chat, Ollama/Groq/OpenAI, agentes, skills, ferramentas e futura integração MCP. A escolha de provedor/modelo é **global**. Cada agente escolhe skills e permissões, nunca outra chave de IA.

## Prioridade P0 — Confiabilidade e código
- [ ] Publicar TODOS os fontes, testes, media e manuais HTML no repositório
- [ ] Executar testes e empacotamento automaticamente no GitHub Actions
- [ ] Histórico de conversas por projeto com exportação JSON/Markdown
- [ ] Backup e recuperação de configurações, agentes e skills
- [ ] Painel de atividade do agente e logs pesquisáveis
- [ ] Verificador de permissões reais para cada ferramenta e workspace
- [ ] Edições multi-arquivo via diff, aprovação e rollback
- [ ] Regras de segurança: não enviar segredos, bloquear paths externos, revisar código gerado

## P1 — Assistente programador
- [ ] Indexar e pesquisar arquivos por relevância sem enviar tudo para a IA
- [ ] Ferramentas: listar pasta, ler arquivo, pesquisar texto, criar proposta, aplicar com confirmação
- [ ] Ciclo de tool calling com limites de passos, tokens e autorização
- [ ] Executar testes/comandos selecionados após confirmação
- [ ] Diagnosticar e corrigir erros de compilação mostrando evidências
- [ ] Agentes Planejador, Programador, Revisor, Testador e Documentador
- [ ] Perfis específicos para Godot, Blender, Visual FoxPro, Python e web
- [ ] Skills importáveis/exportáveis via SKILL.md, sem limite arbitrário de quantidade
- [ ] Seleção dinâmica de skills por tarefa para economizar contexto

## P1 — MCP
- [ ] Cliente MCP real com descoberta de ferramentas, schemas e execução controlada
- [ ] Conexões stdio e Streamable HTTP, com autenticação e gerenciamento de processos
- [ ] Inventário de servidores MCP permitidos; credenciais em SecretStorage
- [ ] Integração de testes com servidor MCP Blender, em ambiente isolado
- [ ] Aprovar ferramentas de modelagem que alteram arquivos/projetos antes da execução
- [ ] Cancelamento, limites de tempo configuráveis e logs de cada chamada MCP

## P2 — Experiência
- [ ] Chat expansível com layout/altura/fonte persistidos
- [ ] Histórico pesquisável e múltiplas conversas por projeto
- [ ] Painel de consumo com tokens reais versus estimados
- [ ] Limites preventivos RPM/TPM configuráveis por provedor
- [ ] Chat de professor WMK Academy com exercícios progressivos
- [ ] Catálogo comunitário de agentes/skills com revisão de segurança
- [ ] Acessibilidade por teclado, leitores de tela, contraste e dispositivos modestos
- [ ] Compatibilidade Windows, Linux e macOS

## Publicação e distribuição
- [ ] Revisar privacidade, segurança, LICENSE e código-fonte
- [ ] Gerar VSIX via GitHub Actions
- [ ] Criar Release com VSIX e CHANGELOG
- [x] Criar publisher WMK no Marketplace do VS Code
- [x] Publicar extensão v0.6.0 no Marketplace (versão experimental)
- [ ] Automatizar publicação via Trusted Publishing (OIDC), se disponível

## Regra de entrega
Cada recurso deve acompanhar: código, testes, manual HTML em pt-BR, limitações conhecidas, documentação para usuários e desenvolvedores, e instruções de atualização.

Autor: Walney Moreira Klein — walneyk@hotmail.com

## Registro de encerramento da v0.6.0

- Chat, agentes, skills e leitura consentida do arquivo aberto demonstrados em execução real no Windows.
- Marketplace: extensão WMK IA Assistente v0.6.0 com verificação concluída e disponibilidade pública, conforme screenshots do painel do autor.
- Manual para iniciantes: [Curso completo](CURSO-CRIAR-EXTENSOES-VSCODE.md) e [Guia de primeira publicação](MANUAL-PRIMEIRA-EXTENSAO-MARKETPLACE.md).
- Pendências separadas do fechamento funcional: publicação de fontes completos no GitHub e Release com VSIX. Não marcar esses itens como concluídos até serem comprovados.
- MCP externo, Blender e agente autônomo não integram o escopo funcional entregue.
