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

-------


Ótima observação! O comando `task-master models` funcionou corretamente no seu terminal dentro da pasta do projeto (`TradeUP-Collects-app`), e a tabela que ele mostra é muito informativa.

Vamos analisar detalhadamente o que cada parte significa:

---

## 1. Configuração de Modelos Ativos (`Active Model Configuration`)

Esta tabela mostra quais modelos o Task Master está **atualmente configurado para usar** nas diferentes funções:

* **`Role` (Função):**
    * **`Main`:** O modelo principal usado para a maioria das tarefas (geração de código, análise de PRD, etc.).
    * **`Research`:** O modelo usado especificamente para o comando `research`, idealmente um modelo com acesso à internet ou otimizado para busca (como o Perplexity).
    * **`Fallback`:** O modelo a ser usado caso o `Main` ou `Research` falhem (por exemplo, devido a erro de API, limite de taxa, etc.).
* **`Provider` (Provedor):** A empresa ou serviço que fornece o modelo (ex: `gemini-cli`, `perplexity`, `anthropic`).
* **`Model ID`:** O nome específico do modelo (ex: `gemini-1.5-pro`, `sonar-pro`, `claude-3.5-sonnet-20240620`).
* **`SWE Score`:** Uma pontuação de desempenho em tarefas de engenharia de software (Software Engineering), se disponível. Mais estrelas/maior percentagem indica melhor desempenho nessas tarefas. `N/A` significa que não há uma pontuação conhecida para esse modelo.
* **`Cost ($/1M tkns)`:** O custo estimado por milhão de tokens processados (entrada + saída). "Free" indica que o provedor (neste caso, `gemini-cli`) não requer pagamento direto via API key (geralmente usa autenticação local).

**No seu caso:**
* Seu modelo **principal** está configurado para usar a integração `gemini-cli` com o `gemini-1.5-pro`. Isso significa que, por padrão, ele tentará usar a linha de comando do Gemini (que talvez use autenticação OAuth), **não a sua `GOOGLE_API_KEY` diretamente**.
* Seu modelo de **pesquisa** é o `sonar-pro` da Perplexity.
* Seu modelo de **fallback** é o `claude-3.5-sonnet` da Anthropic.

---

## 2. Status das Chaves de API (`API Key Status`) 🔑

Esta é a tabela crucial para a sua pergunta. Ela mostra onde o Task Master **encontrou (ou não encontrou)** as chaves de API ao ser executado **a partir do seu terminal naquele momento**.

* **`Provider`:** O nome do serviço (Anthropic, Google, etc.).
* **`CLI Key (.env)`:** Indica se o Task Master encontrou a chave correspondente (ex: `GOOGLE_API_KEY`) quando executado no terminal. Ele procura por:
    1.  **Variáveis de ambiente do sistema** (definidas no seu `.zshrc`, `.bash_profile`, etc.).
    2.  Um ficheiro `.env` **na pasta onde você executou o comando** (`TradeUP-Collects-app`).
* **`MCP Key (mcp.json)`:** Indica se o Task Master encontrou a chave correspondente dentro da secção `env` da configuração do `task-master-ai` num ficheiro `mcp.json`. **Importante:** Quando você executa `task-master models` **no terminal**, esta coluna **NÃO reflete o `mcp.json` do VS Code**. Ela só mostraria ✅ "Found" aqui se o próprio processo do terminal tivesse sido iniciado *através* de um mecanismo MCP que lesse um `mcp.json` (o que não é o caso aqui).

**Análise do seu Status:**

* **Google:** Está marcado como `❌ Missing` em ambas as colunas (`CLI Key` e `MCP Key`).
    * **Porquê?** Porque você executou o comando **no terminal**. O terminal **não lê automaticamente** o ficheiro `mcp.json` que você configurou **dentro do VS Code**. A configuração `env` no `mcp.json` do VS Code só é usada quando o *próprio VS Code* inicia o processo `task-master-ai` via MCP.
    * O `❌ Missing` na coluna `CLI Key (.env)` significa que você também não tem a `GOOGLE_API_KEY` definida como variável de ambiente no seu sistema ou num ficheiro `.env` na pasta `TradeUP-Collects-app`.
* **Anthropic:** Mesma situação que o Google. A chave está no `mcp.json` do VS Code, mas não acessível ao comando executado diretamente no terminal.
* **Outros Provedores (Bedrock, Claude-code, Gemini-cli, etc.):** Mostram ✅ `Found` na coluna `CLI Key (.env)`. Isso geralmente significa que esses provedores usam outros métodos de autenticação que o Task Master conseguiu detetar no seu ambiente (ex: ficheiros de configuração próprios, login via CLI, credenciais AWS padrão).

---

**Conclusão Detalhada:**

O comando `task-master models` executado no terminal está a funcionar corretamente, mas ele opera num **ambiente diferente** do Task Master quando executado pelo VS Code via MCP.

* O terminal **não** tem acesso às chaves definidas no `env` do `mcp.json` do VS Code. Por isso, ele reporta `❌ Missing` para Google e Anthropic nas duas colunas quando você o executa manualmente.
* Isso **não significa** que a sua configuração no `mcp.json` do VS Code esteja errada. Significa apenas que essa configuração específica (as chaves no `env`) só é válida quando o **VS Code inicia o Task Master**.
* A configuração do modelo `Main` como `gemini-cli` também explica porque ele pode funcionar mesmo sem detetar a `GOOGLE_API_KEY` no terminal (ele usa outro método).

Para confirmar que suas chaves no `mcp.json` do VS Code estão corretas, você deve tentar usar uma funcionalidade do Task Master **através do chat do VS Code** que dependa dessas chaves (ex: `Change the main model to gemini-pro` e depois `Research X using the main model`). Se funcionar lá, está tudo certo para o uso dentro do VS Code.


------

então mesmo sendo exibido Missing nos dois campos d atabela: env e MCP Key. A api key do google que configurei esta correta, pois no "Active model Configuration é exibido no Main o provider do gemini-cli que eu configurei manualmente ?

Exato, você entendeu a distinção corretamente, mas a conclusão precisa de um pequeno ajuste. Vamos clarificar:

1.  **"Missing" na Tabela:** O facto de aparecer `❌ Missing` para a chave Google nas colunas `CLI Key (.env)` e `MCP Key (mcp.json)` **quando você executa `task-master models` no terminal** significa apenas que *naquele ambiente específico* (o terminal), o Task Master não encontrou a `GOOGLE_API_KEY` (nem como variável de ambiente, nem num ficheiro `.env`, e o terminal não lê o `mcp.json` do VS Code). Isso é esperado.

2.  **Configuração no `mcp.json` do VS Code:** A configuração da `GOOGLE_API_KEY` que você fez dentro da secção `env` do `task-master-ai` no **ficheiro `mcp.json` do VS Code** está separada. Ela **só é usada** quando o **VS Code inicia o Task Master via MCP**. A tabela que você viu no terminal **não valida nem invalida** essa configuração específica do VS Code.

3.  [cite_start]**`gemini-cli` como Modelo Principal:** O facto de o modelo `Main` estar configurado como `gemini-cli` (que geralmente usa autenticação OAuth ou configuração local do CLI do Gemini, não a API key direta [cite: 104, 110, 112]) **não confirma** que a sua `GOOGLE_API_KEY` no `mcp.json` está correta. Apenas mostra qual *provedor/método* está selecionado como principal no momento.

**Em resumo:**

* O "Missing" na tabela do terminal **não significa** que a sua `GOOGLE_API_KEY` no `mcp.json` do VS Code esteja errada. É apenas um reflexo do ambiente do terminal.
* A configuração do `Main` model como `gemini-cli` **não prova** que a `GOOGLE_API_KEY` no `mcp.json` esteja correta, pois `gemini-cli` provavelmente usa outro método de autenticação.

**Para ter certeza de que a `GOOGLE_API_KEY` no `mcp.json` do VS Code está correta, você precisaria:**

1.  **Mudar o modelo principal** (dentro do VS Code, via chat ou comando `task-master models-set-main`) para um modelo que **use explicitamente a API key**, como `gemini-pro` ou `gemini-1.5-pro`.
2.  **Executar um comando do Task Master dentro do VS Code** (via chat) que use esse modelo principal (por exemplo, pedir para gerar uma tarefa ou analisar um PRD).
3.  Se o comando funcionar sem erros de autenticação, **então** a sua `GOOGLE_API_KEY` no `mcp.json` está correta e a ser utilizada pelo Task Master quando iniciado pelo VS Code.
