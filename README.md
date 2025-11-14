# sabor-express
Trabalho de Fundamentos de IA para otimização de rotas de delivery
# Rota Inteligente: Otimização de Entregas com Algoritmos de IA

Projeto da disciplina *Artificial Intelligence Fundamentals* (UniFECAF), focado na resolução de um problema de otimização de rotas para uma empresa de delivery.

---

## 1. 🎯 Descrição do Problema e Objetivos

### O Problema
A "Sabor Express", uma empresa local de delivery de alimentos, enfrenta grandes desafios na gestão de suas entregas, especialmente em horários de pico. O processo atual de definição de rotas é totalmente manual, baseado apenas na experiência dos entregadores.

Isso resulta em:
* Rotas ineficientes.
* Atrasos nas entregas.
* Aumento no custo de combustível.
* Insatisfação dos clientes.

### O Desafio
O desafio deste projeto é desenvolver uma solução inteligente, baseada em algoritmos de Inteligência Artificial, capaz de sugerir as melhores rotas para os entregadores.

### Objetivos da Solução
* Implementar algoritmos de IA para encontrar o menor caminho entre múltiplos pontos.
* Desenvolver uma estratégia de agrupamento (clustering) de entregas próximas para otimizar o trabalho em momentos de alta demanda.
* Tornar as entregas mais rápidas, eficientes e econômicas.

---

## 2. 💡 Abordagem Adotada

Nossa solução foi estruturada em duas etapas principais para resolver o problema de forma completa:

### a) Modelagem do Problema (Grafo)
Para representar o cenário urbano, modelamos a cidade como um **grafo ponderado**.
* **Nós (Vértices):** Representam os locais (o restaurante "Sabor Express" e os pontos de entrega/bairros).
* **Arestas (Arcos):** Representam as ruas que conectam os locais.
* **Pesos:** Cada aresta possui um peso, que representa a **distância** ou o **tempo estimado** de percurso entre dois nós.

### b) Agrupamento de Entregas (Clustering)
Em momentos de alta demanda (ex: hora do almoço), não é eficiente enviar um entregador para cada pedido. Para resolver isso, aplicamos um algoritmo de clusterização (K-Means) para agrupar geograficamente os pedidos próximos.

Cada "cluster" formado representa um conjunto de entregas que será atribuído a um único entregador.

### c) Otimização da Rota (Busca de Caminho)
Após definir os clusters, o problema se torna encontrar o menor caminho que passa por todos os pontos de entrega de um cluster. Para isso, utilizamos um algoritmo de busca em grafos.

*(**Seu Trabalho:** Explique aqui a sua lógica. Você calculou o menor caminho do restaurante ao primeiro ponto, depois ao segundo? Ou usou um algoritmo para resolver o "Problema do Caixeiro Viajante" (TSP) dentro do cluster?)*

---

## 3. ⚙️ Algoritmos Utilizados

### K-Means (Aprendizado Não Supervisionado)
* **Para quê:** Usado para a etapa de **agrupamento de entregas**.
* **Por quê:** Escolhemos o K-Means por sua simplicidade e eficiência em particionar os pontos de entrega (pedidos) em 'K' zonas distintas. O 'K' pode ser definido como o número de entregadores disponíveis no momento.

### Algoritmo A* (Busca Heurística)
* **Para quê:** Usado para encontrar o **menor caminho** (rota mais rápida/curta) entre dois pontos no grafo (ex: do restaurante até o primeiro ponto de entrega do cluster).
* **Por quê:** O A* é um algoritmo de busca informada que utiliza uma heurística (ex: distância em linha reta) para tomar decisões mais inteligentes, sendo mais eficiente que buscas cegas (como BFS ou DFS) em grafos que representam mapas.

*(**Nota:** Se você usou BFS ou DFS, troque o A* e justifique sua escolha.)*

---

## 4. 🗺️ Diagrama do Grafo

O modelo abaixo ilustra uma versão simplificada do grafo utilizado para representar o mapa da "Sabor Express". Os pesos nas arestas representam o tempo (em minutos) entre os locais.

> **[INSIRA A IMAGEM DO SEU GRAFO AQUI]**
>
> *(Dica: Use um `print` da sua visualização de grafo ou um diagrama simples feito em uma ferramenta online)*
>
> *Exemplo de como inserir a imagem no Markdown:*
> `![Diagrama do Grafo](caminho/para/sua/imagem.png)`

---

## 5. 📊 Análise e Resultados

### Eficiência da Solução
*(**Seu Trabalho:** Descreva aqui os resultados. Mostre um exemplo "Antes vs. Depois". Ex: "A rota manual A -> C -> B levava 30 min. Nossa solução A* encontrou A -> B -> C, que leva 22 min". Inclua prints do seu código em ação ou gráficos.)*

### Limitações Encontradas
* **Pesos Estáticos:** O modelo atual utiliza pesos fixos (distância/tempo fixo). Ele não considera condições dinâmicas como tráfego em tempo real, acidentes ou obras, como o sistema ORION da UPS faz.
* **Número de Clusters (K):** O K-Means exige que o número de clusters (entregadores) seja definido antecipadamente.

### Sugestões de Melhoria
* **Roteamento Dinâmico:** Integrar uma API de tráfego em tempo real (como Google Maps) para atualizar os pesos das arestas dinamicamente.
* **Algoritmos Avançados:** Para otimizar a rota *dentro* de um cluster (visitando múltiplos pontos), poderiam ser explorados algoritmos heurísticos mais avançados (como Algoritmos Genéticos).

---

## 6. 🚀 Executando o Projeto

Esta seção é parte da "Parte Prática", mas é essencial no `README.md`.

### Pré-requisitos
* [Liste as bibliotecas necessárias, ex: Python 3.9, Pandas, Scikit-learn, NetworkX]

### Instruções de Execução
1.  Clone o repositório:
    ```bash
    git clone [URL-DO-SEU-REPO]
    ```
2.  Navegue até a pasta do projeto:
    ```bash
    cd nome-do-projeto
    ```
3.  Instale as dependências (exemplo):
    ```bash
    pip install -r requirements.txt
    ```
4.  Execute o programa principal:
    ```bash
    python src/main.py
    ```
