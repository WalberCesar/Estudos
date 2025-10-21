# Task-master

### links:
    https://www.youtube.com/watch?v=IIg56ZaktzM&list=PLRYZGSZEEG0GARkVCGV9MneN7Bj7r2zNc


# Guia Rápido: Instalação do Task Master AI MCP no Cursor

Este é um resumo objetivo de como instalar e configurar o MCP `task-master-ai` no Cursor, incluindo a solução para um problema comum de instalação.

## 1. Pré-requisitos: Chaves de API

O Task Master utiliza modelos de IA e requer **pelo menos uma** chave de API de um provedor suportado para funcionar.

* **Provedores Mínimos Necessários (pelo menos um):**
    * Anthropic (Claude) 
    * penAI (GPT) 
    * Google (Gemini) 
    * Outros (Groq, OpenRouter, Azure OpenAI, xAI, Mistral, Claude Code CLI, Codex CLI) 
* **Altamente Recomendados:**
    * `ANTHROPIC_API_KEY`: Recomendado como provedor primário[cite: 516]. **Observação:** Na nossa experiência, a ausência desta chave pode impedir o carregamento das ferramentas, mesmo que outra chave (como a do Google) esteja presente.
    * `PERPLEXITY_API_KEY`: Altamente recomendado para as funcionalidades de pesquisa (`research`)[cite: 517, 666].
* **Onde Obter:**
    * **Anthropic:** Anthropic Console 
    * **Google Gemini:** Google AI Studio 
    * **Perplexity:** Perplexity API 
    * **OpenAI:** OpenAI Platform

## 2. Configuração no Cursor (`mcp.json`)

1.  **Abra o `mcp.json`:** No Cursor, use a Paleta de Comandos (`Cmd+Shift+P` ou `Ctrl+Shift+P`) e procure por "MCP: Open User MCP Configuration File" ou navegue via `Settings > Tools & MCP > Add Custom MCP`.
2.  **Adicione a Configuração:** Insira o seguinte bloco dentro do objeto principal `"mcpServers"`, substituindo as chaves pelos seus tokens reais:

    ```json
    "task-master-ai": {
      "command": "npx", //
      "args": [ //
        "-y",
        "task-master-ai"
        // Se encontrar problemas com a versão 'latest', pode fixar uma versão, ex: "task-master-ai@0.30.0"
      ],
      "env": { //
        // Obrigatório (com base na nossa experiência para carregar ferramentas)
        "ANTHROPIC_API_KEY": "SUA_CHAVE_ANTHROPIC_AQUI", //
        
        // Pelo menos uma chave é necessária, adicione as que você tem:
        "GOOGLE_API_KEY": "SUA_CHAVE_GOOGLE_GEMINI_AQUI", //
        "OPENAI_API_KEY": "SUA_CHAVE_OPENAI_AQUI", //
        "PERPLEXITY_API_KEY": "SUA_CHAVE_PERPLEXITY_AQUI" //
        [cite_start]// Adicione outras chaves conforme necessário (GROQ, OPENROUTER, etc.) 
      }
    }
    ```

3.  **Salve** o ficheiro `mcp.json`.
4.  **Reinicie o Cursor:** Feche completamente o aplicativo Cursor e abra-o novamente.

## 3. Solução de Problemas: Erro "No tools, prompts, or resources"

- Se, após a configuração e reinicialização, o Cursor mostrar o `task-master-ai` como ativo mas com a mensagem "No tools, prompts, or resources" o problema pode ser um cache corrompido do `npx`.

1.  **Causa:** O `npx` pode falhar ao baixar/instalar dependências, resultando num erro como `ERR_MODULE_NOT_FOUND` ao tentar executar o `task-master-ai`.
2.  **Solução:** Limpe o cache do `npx`. Abra o seu terminal e execute (para macOS/Linux):
    ```bash
    rm -rf ~/.npm/_npx
    ```
3.  **Reinicie o Cursor:** Após limpar o cache, reinicie o Cursor completamente.

## 4. Verificação

Após a instalação (e a solução de problemas, se necessário):

1.  Vá para `Settings > Tools & MCP` no Cursor.
2.  Verifique se `task-master-ai` tem um **círculo verde** ✅ ao lado.
3.  Confirme que ele mostra o número de ferramentas habilitadas (ex: "44 tools enabled").

## 5. Uso Básico (Exemplos de Prompts no Cursor)
1. nicializar no projeto:** `Initialize taskmaster-ai in my project` 
2. Analisar um PRD:** `Can you parse my PRD at path/to/your/prd.txt?` 
3. Ver a próxima tarefa:** `What's the next task I should work on?` 
4. Implementar uma tarefa:** `Can you help me implement task 5?`
5. Pesquisar:** `Research the best way to handle authentication in React Native`
Consulte a [documentação completa](https://docs.task-master.dev/) para mais comandos e funcionalidades avançadas.
* [cite_start]**Pesquisar:** `Research the best way to handle authentication in React Native` [cite: 373]

Consulte a [documentação completa](https://docs.task-master.dev/) para mais comandos e funcionalidades avançadas.
