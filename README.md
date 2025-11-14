# sabor-express
Trabalho de Fundamentos de IA para otimização de rotas de delivery
# [cite_start]Rota Inteligente: Otimização de Entregas com Algoritmos de IA [cite: 4]

Projeto da disciplina *Artificial Intelligence Fundamentals* (UniFECAF), focado na resolução de um problema de otimização de rotas para uma empresa de delivery.

---

## [cite_start]1. 🎯 Descrição do Problema e Objetivos [cite: 51]

### O Problema
[cite_start]A "Sabor Express", uma empresa local de delivery de alimentos, enfrenta grandes desafios na gestão de suas entregas, especialmente em horários de pico[cite: 6, 7]. [cite_start]O processo atual de definição de rotas é totalmente manual, baseado apenas na experiência dos entregadores[cite: 10].

Isso resulta em:
* [cite_start]Rotas ineficientes[cite: 8].
* [cite_start]Atrasos nas entregas[cite: 8].
* [cite_start]Aumento no custo de combustível[cite: 8].
* [cite_start]Insatisfação dos clientes[cite: 8].

### O Desafio
[cite_start]O desafio deste projeto é desenvolver uma solução inteligente, baseada em algoritmos de Inteligência Artificial, capaz de sugerir as melhores rotas para os entregadores[cite: 11].

### Objetivos da Solução
* [cite_start]Implementar algoritmos de IA para encontrar o menor caminho entre múltiplos pontos[cite: 13].
* [cite_start]Desenvolver uma estratégia de agrupamento (clustering) de entregas próximas para otimizar o trabalho em momentos de alta demanda[cite: 18].
* [cite_start]Tornar as entregas mais rápidas, eficientes e econômicas[cite: 9].

---

## [cite_start]2. 💡 Abordagem Adotada [cite: 52]

Nossa solução foi estruturada em duas etapas principais para resolver o problema de forma completa:

### a) Modelagem do Problema (Grafo)
[cite_start]Para representar o cenário urbano, modelamos a cidade como um **grafo ponderado**[cite: 12].
* [cite_start]**Nós (Vértices):** Representam os locais (o restaurante "Sabor Express" e os pontos de entrega/bairros)[cite: 12].
* [cite_start]**Arestas (Arcos):** Representam as ruas que conectam os locais[cite: 12].
* [cite_start]**Pesos:** Cada aresta possui um peso, que representa a **distância** ou o **tempo estimado** de percurso entre dois nós[cite: 12].

### b) Agrupamento de Entregas (Clustering)
[cite_start]Em momentos de alta demanda (ex: hora do almoço), não é eficiente enviar um entregador para cada pedido[cite: 14]. [cite_start]Para resolver isso, aplicamos um algoritmo de clusterização (K-Means) para agrupar geograficamente os pedidos próximos[cite: 18].

Cada "cluster" formado representa um conjunto de entregas que será atribuído a um único entregador.

### c) Otimização da Rota (Busca de Caminho)
Após definir os clusters, o problema se torna encontrar o menor caminho que passa por todos os pontos de entrega de um cluster. Para isso, utilizamos um algoritmo de busca em grafos.

*(**Seu Trabalho:** Explique aqui a sua lógica. Você calculou o menor caminho do restaurante ao primeiro ponto, depois ao segundo? Ou usou um algoritmo para resolver o "Problema do Caixeiro Viajante" (TSP) dentro do cluster?)*

---

## [cite_start]3. ⚙️ Algoritmos Utilizados [cite: 53]

### K-Means (Aprendizado Não Supervisionado)
* [cite_start]**Para quê:** Usado para a etapa de **agrupamento de entregas**[cite: 19].
* **Por quê:** Escolhemos o K-Means por sua simplicidade e eficiência em particionar os pontos de entrega (pedidos) em 'K' zonas distintas. O 'K' pode ser definido como o número de entregadores disponíveis no momento.

### Algoritmo A* (Busca Heurística)
* [cite_start]**Para quê:** Usado para encontrar o **menor caminho** (rota mais rápida/curta) entre dois pontos no grafo (ex: do restaurante até o primeiro ponto de entrega do cluster)[cite: 19].
* [cite_start]**Por quê:** O A* é um algoritmo de busca informada que utiliza uma heurística (ex: distância em linha reta) para tomar decisões mais inteligentes, sendo mais eficiente que buscas cegas (como BFS ou DFS) em grafos que representam mapas[cite: 19].

*(**Nota:** Se você usou BFS ou DFS, troque o A* e justifique sua escolha.)*

---

## [cite_start]4. 🗺️ Diagrama do Grafo [cite: 54]

O modelo abaixo ilustra uma versão simplificada do grafo utilizado para representar o mapa da "Sabor Express". Os pesos nas arestas representam o tempo (em minutos) entre os locais.

> **[INSIRA A IMAGEM DO SEU GRAFO AQUI]**
>
> *(Dica: Use um `print` da sua visualização de grafo ou um diagrama simples feito em uma ferramenta online)*
>
> *Exemplo de como inserir a imagem no Markdown:*
> `![Diagrama do Grafo](caminho/para/sua/imagem.png)`

---

## [cite_start]5. 📊 Análise e Resultados [cite: 55]

### Eficiência da Solução
[cite_start]*(**Seu Trabalho:** Descreva aqui os resultados. Mostre um exemplo "Antes vs. Depois". Ex: "A rota manual A -> C -> B levava 30 min. Nossa solução A* encontrou A -> B -> C, que leva 22 min". Inclua prints do seu código em ação ou gráficos[cite: 59].)*

### Limitações Encontradas
* **Pesos Estáticos:** O modelo atual utiliza pesos fixos (distância/tempo fixo). [cite_start]Ele não considera condições dinâmicas como tráfego em tempo real, acidentes ou obras, como o sistema ORION da UPS faz[cite: 26].
* **Número de Clusters (K):** O K-Means exige que o número de clusters (entregadores) seja definido antecipadamente.

### Sugestões de Melhoria
* **Roteamento Dinâmico:** Integrar uma API de tráfego em tempo real (como Google Maps) para atualizar os pesos das arestas dinamicamente.
* [cite_start]**Algoritmos Avançados:** Para otimizar a rota *dentro* de um cluster (visitando múltiplos pontos), poderiam ser explorados algoritmos heurísticos mais avançados (como Algoritmos Genéticos)[cite: 37, 38].

---

## 6. 🚀 Executando o Projeto

[cite_start]Esta seção é parte da "Parte Prática"[cite: 57], mas é essencial no `README.md`.

### Pré-requisitos
* [cite_start][Liste as bibliotecas necessárias, ex: Python 3.9, Pandas, Scikit-learn, NetworkX] [cite: 60]

### [cite_start]Instruções de Execução [cite: 60]
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
