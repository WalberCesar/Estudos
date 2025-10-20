### O que este MCP faz de diferente?

Primeiro, é fundamental entender o que este MCP faz.

  * O **Context7** (que já usámos) é uma ferramenta para *buscar dados* (documentação atualizada).
  * O **Sequential Thinking** é uma ferramenta para *mudar como a IA raciocina*.

[cite\_start]Como a documentação que você enviou explica, este MCP força a IA a usar um "processo de pensamento estruturado" para "resolução de problemas dinâmica e reflexiva"[cite: 330, 334]. [cite\_start]Em vez de te dar a resposta final de uma vez, a IA é forçada a parar, pensar passo a passo, gerar hipóteses, verificar essas hipóteses e até mesmo corrigir o seu próprio rumo no meio do caminho[cite: 336, 350, 351, 352].

Ele é ideal para:

  * [cite\_start]Dividir problemas complexos em etapas[cite: 337].
  * [cite\_start]Planear funcionalidades onde o âmbito não está 100% claro no início[cite: 340].
  * [cite\_start]Tarefas que exigem múltiplos passos e manutenção de contexto[cite: 341, 342].
  * [cite\_start]Análises que podem precisar de correção de curso[cite: 339].

-----

### Como Usar o "Sequential Thinking" nos seus Prompts

Existem duas formas de o usar: automática (implícita) e manual (explícita).

#### 1\. Invocação Automática (Implícita)

Para problemas genuinamente complexos, o Cursor (especialmente com modelos como o Claude 3.5 Sonnet) é inteligente o suficiente para reconhecer que precisa de "pensar mais". [cite\_start]Quando ele deteta um problema que se alinha com os objetivos do MCP (como os que listei acima), ele pode decidir usar a ferramenta `sequentialthinking` [cite: 332] automaticamente.

Você não precisa fazer nada, apenas descrever o seu problema complexo em detalhe.

#### 2\. Invocação Manual (Explícita)

Esta é a forma garantida de forçar a IA a usar este modo de pensamento. [cite\_start]Você invoca a ferramenta pelo nome dela, que, de acordo com a documentação, é `sequentialthinking`[cite: 332].

**Formato do Prompt:**
Basta adicionar `... use sequentialthinking` ao final do seu pedido.

```
[O SEU PROBLEMA COMPLEXO AQUI] ... use sequentialthinking
```

### Exemplos de Prompts para (React Native)

O segredo não é *apenas* o comando `use sequentialthinking`, mas sim o **tipo de problema** que você apresenta. Você precisa dar-lhe um problema que *valha a pena* ser pensado sequencialmente.

Aqui estão alguns exemplos perfeitos para o seu contexto de **React Native**:

  * **Exemplo 1: Refatoração de Código (Problema Complexo)**
    `"Eu tenho um 'componente deus' no meu app React Native que faz tudo: busca dados da API, gerencia o estado de um formulário com 10 campos e ainda lida com a lógica de animação do teclado. Está impossível de manter. Ajude-me a planear, passo a passo, como refatorar isto, dividindo-o em hooks personalizados, componentes de UI menores e um componente 'container' principal. Pense em qual ordem eu devo fazer isso. use sequentialthinking"`

  * **Exemplo 2: Depuração (Âmbito não claro)**
    `"Estou a enfrentar um bug de performance muito estranho. Quando o utilizador faz scroll rápido numa FlatList e imediatamente troca de aba no meu Bottom Tab Navigator, a UI inteira congela por 2 segundos. Não tenho a certeza se é um memory leak, um problema de renderização ou algo no 'navigation state'. Crie um plano de depuração passo a passo para eu encontrar a causa raiz. use sequentialthinking"`

  * **Exemplo 3: Planeamento de Nova Funcionalidade (Múltiplos Passos)**
    `"Preciso de construir um fluxo de 'checkout' de compras na minha aplicação. Isto vai envolver 4 ecrãs (Carrinho, Endereço, Pagamento, Confirmação), vai precisar de gestão de estado global (Zustand ou Context) e integração com uma API de pagamentos. Pense em todos os componentes que vou precisar, na estrutura do estado global e nos pontos de chamada de API. use sequentialthinking"`

### O que esperar como Resposta

Ao usar este MCP, você não vai ver o log `Ran get-library-docs` como no Context7.

Em vez disso, você verá a IA a "pensar" explicitamente na resposta. A resposta dela será estruturada como uma série de "Pensamentos", algo como:

> **Pensamento 1 (Hipótese):** O problema descrito parece ser uma refatoração clássica de um 'God Component'. O primeiro passo deve ser isolar a lógica de 'data fetching' para não bloquear a UI.
>
> **Pensamento 2 (Plano de Ação):** Vou sugerir a criação de um hook `useUserData()`.
>
> **Pensamento 3 (Revisão):** Espera, o utilizador também mencionou animações. Talvez isolar a lógica do formulário primeiro seja mais fácil. Deixa-me rever o passo 1.
>
> **Pensamento 4 (Plano Revisado):** Ok, primeiro vamos isolar o formulário...

Isto dá-te uma transparência incrível sobre o processo de raciocínio da IA e geralmente leva a soluções muito mais robustas e bem planeadas.