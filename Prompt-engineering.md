
````markdown
# 🧠 Guia de Engenharia de Prompts: Zero, One & Few-Shots

O termo **"shot"** refere-se ao número de **exemplos** que você fornece à IA dentro do seu prompt para ensiná-la o que você deseja como resposta. É uma técnica poderosa para guiar o modelo a produzir resultados mais precisos e no formato esperado.

---

## 🚀 1. Zero-Shot Prompting (Nenhum Exemplo)

É a forma mais simples e direta de interagir com a IA. Você faz uma pergunta ou dá uma instrução sem fornecer nenhum exemplo. O modelo depende inteiramente do seu conhecimento pré-treinado.

**🗓️ Quando Usar:**
- Tarefas simples e diretas (resumos, traduções).
- Quando a tarefa é muito comum.
- Para testar o conhecimento base do modelo.

**✅ Vantagens:**
- **Rápido e Simples:** Não exige preparação de exemplos.
- **Ótimo para Tarefas Genéricas.**

**⚠️ Desvantagens:**
- **Menos Controle:** A IA pode interpretar a tarefa de maneira diferente.
- **Pode Falhar em Tarefas Complexas.**

### 🔧 Exemplo de Prompt Zero-Shot para React.js

```jsx
Crie um componente funcional em React.js chamado 'UserProfile'.
Este componente deve receber um objeto 'user' como prop, contendo 'name' e 'email'.
O componente deve renderizar o nome do usuário em um cabeçalho h2 e o email em um parágrafo p.
````

-----

## 🎯 2. One-Shot Prompting (Um Único Exemplo)

Nesta abordagem, você fornece **um único exemplo** de alta qualidade que demonstra o padrão ou o formato que você espera na resposta. Isso ajuda a "ancorar" o entendimento da IA.

**🗓️ Quando Usar:**

  - Quando você precisa de uma resposta em um formato específico (JSON, HTML).
  - Para tarefas que podem ter múltiplas interpretações.

**✅ Vantagens:**

  - **Melhora a Precisão:** Aumenta a chance de obter o resultado desejado.
  - **Define o Formato:** Ensina o formato de saída de forma eficaz.

**⚠️ Desvantagens:**

  - **O Exemplo Pode Limitar:** Um exemplo ruim pode enviesar a resposta.

### 🔧 Exemplo de Prompt One-Shot para React.js

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

## 📚 3. Few-Shot Prompting (Poucos Exemplos)

Esta é a técnica mais poderosa. Você fornece **vários exemplos (geralmente de 2 a 5)** que ilustram a tarefa, permitindo que a IA aprenda um padrão mais complexo e entenda nuances.

**🗓️ Quando Usar:**

  - Tarefas complexas que exigem reconhecimento de padrões.
  - Quando a lógica da tarefa precisa ser inferida a partir dos exemplos.
  - Para garantir um estilo de código consistente.

**✅ Vantagens:**

  - **Alta Precisão e Confiabilidade:** Reduz drasticamente a ambiguidade.
  - **Ideal para Lógica Complexa:** Permite que o modelo "aprenda" a lógica.

**⚠️ Desvantagens:**

  - **Mais Trabalhoso:** Exige a criação de múltiplos exemplos de qualidade.
  - **Prompt Mais Longo:** Consome mais tokens.

### 🔧 Exemplo de Prompt Few-Shot para React.js

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

## 📋 Resumo Comparativo

| Tipo de Prompt | Nº de Exemplos | Ideal Para | Vantagem Principal |
| :--- | :---: | :--- | :--- |
| **🚀 Zero-Shot** | 0 | Tarefas simples, perguntas gerais, resumos. | Rapidez e simplicidade. |
| **🎯 One-Shot** | 1 | Definir um formato de saída específico, clareza. | Bom equilíbrio entre esforço e controle. |
| **📚 Few-Shot** | 2+ | Tarefas complexas, reconhecimento de padrões. | Máxima precisão e confiabilidade para tarefas. |

-----

## ⭐ Dica de Especialista

> Comece sempre com um prompt **zero-shot**. Se o resultado não for o esperado, adicione um exemplo (**one-shot**) para guiar o modelo. Se a tarefa for complexa e envolver padrões, invista tempo na criação de múltiplos exemplos (**few-shot**). A engenharia de prompts é um processo iterativo de refinamento.

```
```
