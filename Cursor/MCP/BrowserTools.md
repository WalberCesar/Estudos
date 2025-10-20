# BrowserTools

## Documentação:
###     https://browsertools.agentdesk.ai/installation





    MCP NAVEGADOR:
        - browsertools.agentdesk.ai/installation
            - MCP NAVEGADOR:
                {
                    "mcpServers": {
                        "browser-tools": {
                        "type": "command",
                        "command": "npx @agentdeskai/browser-tools-mcp@1.2.0"
                        }
                    }
                }   

                no terminal: npx @agentdeskai/browser-tools-mcp@1.2.0


### Pré-requisitos para o Uso (O que precisas de ter a funcionar)

Para que funcione, lembra-te de ter sempre:

1.  **O Terminal a Correr:** A janela do terminal com o `npx @agentdeskai/browser-tools-server@1.2.0` precisa de ficar aberta a correr em segundo plano. (Como está na tua imagem).
2.  [cite_start]**O Chrome DevTools Aberto:** A extensão só captura logs e dados do separador (aba) onde as Ferramentas de Programador (DevTools) estão abertas[cite: 294]. (Como está na tua imagem).
3.  [cite_start]**O Modelo Correto no Cursor:** Como o guia menciona, certifica-te de que estás a usar um modelo Anthropic, como o **Claude 3.5 Sonnet**, no Cursor para dar os comandos[cite: 44, 45].

---

### 1. Como Usar: Interagir com o Cursor (O Método Principal)

Esta é a principal forma de uso. Abre o Cursor, seleciona o modelo Claude 3.5 Sonnet, e podes começar a usar prompts (comandos de texto) que interagem com o navegador.

O guia de instalação dá-nos exemplos perfeitos de prompts que agora podes experimentar:

* **Para Depuração (Debugging):**
    Se algo no teu site não estiver a funcionar, podes dizer:
    [cite_start]`"Isto não está a funcionar... entra em modo de depuração!"` [cite: 21]
    * [cite_start]*Documentação:* Ao fazeres isto, a IA usará as ferramentas do MCP para aceder aos logs da consola [cite: 12][cite_start], erros e pedidos de rede [cite: 13] para tentar encontrar o problema.

* **Para Tirar Screenshots:**
    Se vires um problema visual na tua página, podes pedir:
    [cite_start]`"Algo não parece bem na UI. Podes tirar um screenshot?"` [cite: 30]
    * [cite_start]*Documentação:* Isto irá acionar a capacidade de screenshot[cite: 14]. [cite_start]A imagem será guardada no caminho que definiste (ou na pasta "Downloads" por defeito [cite: 278]).

* **Para Editar o DOM (Elementos da Página):**
    Esta é incrivelmente poderosa. No teu navegador, "Inspeciona" um elemento (clica com o botão direito > Inspecionar) para que ele fique selecionado no painel "Elements" do Chrome. Depois, vai ao Cursor e diz:
    [cite_start]`"Podes editar o elemento atualmente selecionado para fazer x, y e z?"` [cite: 22]
    * [cite_start]*Documentação:* O MCP tem acesso ao elemento DOM que está selecionado[cite: 15], permitindo que a IA sugira ou até (dependendo da implementação) execute alterações nesse elemento.

* **Para Auditorias:**
    Podes pedir auditorias completas da tua página:
    [cite_start]`"Executa uma auditoria de SEO nesta página."` (baseado na capacidade de correr scans de SEO e Lighthouse [cite: 16]).
    [cite_start]`"Entra em 'Modo de Auditoria' para fazer uma auditoria completa da aplicação web."` [cite: 19]

---

### 2. Como Usar: O Painel no Chrome (Ajustes Manuais)

A aba "BrowserToolsMCP" que abriste no Chrome (como na tua imagem) serve para controlo manual e configuração.

[cite_start]Como vês no painel[cite: 266], podes:

* [cite_start]**Capture Screenshot:** Clicar neste botão tira manualmente um screenshot[cite: 273].
* [cite_start]**Wipe All Logs:** Limpa todos os logs que o servidor armazenou[cite: 279, 282]. Isto é útil se estiveres a começar uma nova sessão de depuração e quiseres apenas os logs mais recentes.
* [cite_start]**Screenshot Settings:** Aqui podes definir um caminho (uma pasta) específico no teu computador onde queres que todos os screenshots sejam guardados[cite: 278]. [cite_start]Por defeito, eles vão para a tua pasta `Downloads/mcp-screenshots`[cite: 278].
* [cite_start]**Advanced Settings:** Permite-te modificar limites de tamanho dos logs, caso estejas a receber demasiados dados ou a perder informação[cite: 280].

### Próximo Passo Recomendado

Conseguiste! Instalaste e configuraste tudo com sucesso.

[cite_start]O próprio guia de instalação recomenda como próximo passo o **"Quickstart Guide"** (Guia de Início Rápido) para aprenderes a interagir com a tua nova ferramenta MCP[cite: 284].

Experimenta um dos prompts que te sugeri acima e vê a magia a acontecer! Se tiveres mais alguma dúvida, estou aqui para ajudar.