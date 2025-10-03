````markdown
<div style="font-family: Arial, sans-serif; color: #333;">

<h1 style="color: #4A148C; font-size: 28px;">
  🧠 Guia de Engenharia de Prompts: Zero, One & Few-Shots
</h1>

<p style="font-size: 16px;">
  O termo <b style="color: #6A1B9A;">"shot"</b> refere-se ao número de <b>exemplos</b> que você fornece à IA dentro do seu prompt para ensiná-la o que você deseja como resposta. É uma técnica poderosa para guiar o modelo a produzir resultados mais precisos e no formato esperado.
</p>

---

<h2 style="color: #8E24AA; font-size: 24px;">
  🚀 1. Zero-Shot Prompting (Nenhum Exemplo)
</h2>

<p style="font-size: 16px;">
  É a forma mais simples e direta de interagir com a IA. Você faz uma pergunta ou dá uma instrução sem fornecer nenhum exemplo. O modelo depende inteiramente do seu conhecimento pré-treinado.
</p>

<p style="font-size: 16px;">
  🗓️ <b style="color: #333;">Quando Usar:</b>
  <ul>
    <li>Tarefas simples e diretas (resumos, traduções).</li>
    <li>Quando a tarefa é muito comum.</li>
    <li>Para testar o conhecimento base do modelo.</li>
  </ul>
</p>

<p style="font-size: 16px;">
  ✅ <b style="color: #2E7D32;">Vantagens:</b>
  <ul>
    <li><b>Rápido e Simples:</b> Não exige preparação de exemplos.</li>
    <li><b>Ótimo para Tarefas Genéricas.</b></li>
  </ul>
</p>

<p style="font-size: 16px;">
  ⚠️ <b style="color: #D84315;">Desvantagens:</b>
  <ul>
    <li><b>Menos Controle:</b> A IA pode interpretar a tarefa de maneira diferente.</li>
    <li><b>Pode Falhar em Tarefas Complexas.</b></li>
  </ul>
</p>

<h4>
  🔧 Exemplo de Prompt Zero-Shot para React.js
</h4>

```jsx
Crie um componente funcional em React.js chamado 'UserProfile'.
Este componente deve receber um objeto 'user' como prop, contendo 'name' e 'email'.
O componente deve renderizar o nome do usuário em um cabeçalho h2 e o email em um parágrafo p.
````

-----

\<h2 style="color: \#8E24AA; font-size: 24px;"\>
🎯 2. One-Shot Prompting (Um Único Exemplo)
\</h2\>

\<p style="font-size: 16px;"\>
Nesta abordagem, você fornece \<b\>um único exemplo\</b\> de alta qualidade que demonstra o padrão ou o formato que você espera na resposta. Isso ajuda a "ancorar" o entendimento da IA.
\</p\>

\<p style="font-size: 16px;"\>
🗓️ \<b style="color: \#333;"\>Quando Usar:\</b\>
\<ul\>
\<li\>Quando você precisa de uma resposta em um formato específico (JSON, HTML).\</li\>
\<li\>Para tarefas que podem ter múltiplas interpretações.\</li\>
\</ul\>
\</p\>

\<p style="font-size: 16px;"\>
✅ \<b style="color: \#2E7D32;"\>Vantagens:\</b\>
\<ul\>
\<li\>\<b\>Melhora a Precisão:\</b\> Aumenta a chance de obter o resultado desejado.\</li\>
\<li\>\<b\>Define o Formato:\</b\> Ensina o formato de saída de forma eficaz.\</li\>
\</ul\>
\</p\>

\<p style="font-size: 16px;"\>
⚠️ \<b style="color: \#D84315;"\>Desvantagens:\</b\>
\<ul\>
\<li\>\<b\>O Exemplo Pode Limitar:\</b\> Um exemplo ruim pode enviesar a resposta.\</li\>
\</ul\>
\</p\>

\<h4\>
🔧 Exemplo de Prompt One-Shot para React.js
\</h4\>

```jsx
Eu preciso criar um componente de card em React.
Siga o exemplo abaixo para entender a estrutura e o estilo.

# Exemplo:
## Entrada (Props): { title: "Usuário", content: "Informações do usuário." }
## Saída (Componente):
function Card(props) {
  return (
    <div style={{ border: '1px solid #ccc', borderRadius: '8px', padding: '16px' }}>
      <h2>{props.title}</h2>
      <p>{props.content}</p>
    </div>
  );
}

# Agora, sua tarefa:
Crie um componente chamado 'ProductCard' que recebe as props 'productName' e 'price'. Use a mesma estrutura de estilo do exemplo.
```

-----

\<h2 style="color: \#8E24AA; font-size: 24px;"\>
📚 3. Few-Shot Prompting (Poucos Exemplos)
\</h2\>

\<p style="font-size: 16px;"\>
Esta é a técnica mais poderosa. Você fornece \<b\>vários exemplos (geralmente de 2 a 5)\</b\> que ilustram a tarefa, permitindo que a IA aprenda um padrão mais complexo e entenda nuances.
\</p\>

\<p style="font-size: 16px;"\>
🗓️ \<b style="color: \#333;"\>Quando Usar:\</b\>
\<ul\>
\<li\>Tarefas complexas que exigem reconhecimento de padrões.\</li\>
\<li\>Quando a lógica da tarefa precisa ser inferida a partir dos exemplos.\</li\>
\<li\>Para garantir um estilo de código consistente.\</li\>
\</ul\>
\</p\>

\<p style="font-size: 16px;"\>
✅ \<b style="color: \#2E7D32;"\>Vantagens:\</b\>
\<ul\>
\<li\>\<b\>Alta Precisão e Confiabilidade:\</b\> Reduz drasticamente a ambiguidade.\</li\>
\<li\>\<b\>Ideal para Lógica Complexa:\</b\> Permite que o modelo "aprenda" a lógica.\</li\>
\</ul\>
\</p\>

\<p style="font-size: 16px;"\>
⚠️ \<b style="color: \#D84315;"\>Desvantagens:\</b\>
\<ul\>
\<li\>\<b\>Mais Trabalhoso:\</b\> Exige a criação de múltiplos exemplos de qualidade.\</li\>
\<li\>\<b\>Prompt Mais Longo:\</b\> Consome mais tokens.\</li\>
\</ul\>
\</p\>

\<h4\>
🔧 Exemplo de Prompt Few-Shot para React.js
\</h4\>

```jsx
Eu quero criar um componente React que renderiza um selo de status com cores diferentes com base em uma prop 'status'.
Use Tailwind CSS para as classes de estilo. Siga os exemplos para entender o padrão.

# Exemplo 1
## Entrada: { status: 'approved' }
## Saída (JSX): <span className="bg-green-100 text-green-800 text-xs font-medium me-2 px-2.5 py-0.5 rounded">Approved</span>

# Exemplo 2
## Entrada: { status: 'pending' }
## Saída (JSX): <span className="bg-yellow-100 text-yellow-800 text-xs font-medium me-2 px-2.5 py-0.5 rounded">Pending</span>

# Exemplo 3
## Entrada: { status: 'rejected' }
## Saída (JSX): <span className="bg-red-100 text-red-800 text-xs font-medium me-2 px-2.5 py-0.5 rounded">Rejected</span>

# Agora, sua tarefa:
Crie o código completo para o componente funcional 'StatusBadge' que recebe a prop 'status'.
Ele deve implementar a lógica mostrada nos exemplos. O texto dentro do span deve ser o valor do status com a primeira letra maiúscula.
```

-----

\<h2 style="color: \#4A148C; font-size: 24px;"\>
📋 Resumo Comparativo
\</h2\>

| Tipo de Prompt | Nº de Exemplos | Ideal Para                                       | Vantagem Principal                                |
| :------------- | :------------: | :----------------------------------------------- | :------------------------------------------------ |
| \<b style="color:\#0D47A1"\>🚀 Zero-Shot\</b\> | 0              | Tarefas simples, perguntas gerais, resumos.      | Rapidez e simplicidade.                           |
| \<b style="color:\#0D47A1"\>🎯 One-Shot\</b\> | 1              | Definir um formato de saída específico, clareza. | Bom equilíbrio entre esforço e controle.          |
| \<b style="color:\#0D47A1"\>📚 Few-Shot\</b\> | 2+             | Tarefas complexas, reconhecimento de padrões.    | Máxima precisão e confiabilidade para tarefas. |

<br>

\<div style="background-color: \#F3E5F5; border-left: 5px solid \#8E24AA; padding: 15px; margin-top: 20px; border-radius: 5px;"\>
\<h3 style="margin-top: 0; color: \#4A148C;"\>
⭐ Dica de Especialista
\</h3\>
\<p style="font-size: 16px; margin-bottom: 0;"\>
Comece sempre com um prompt \<b\>zero-shot\</b\>. Se o resultado não for o esperado, adicione um exemplo (\<b\>one-shot\</b\>) para guiar o modelo. Se a tarefa for complexa e envolver padrões, invista tempo na criação de múltiplos exemplos (\<b\>few-shot\</b\>). A engenharia de prompts é um processo iterativo de refinamento.
\</p\>
\</div\>

\</div\>

```
```
