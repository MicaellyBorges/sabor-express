# sabor-express
Trabalho de Fundamentos de IA para otimização de rotas de delivery
# Rota Inteligente: Otimização de Entregas com Algoritmos de IA

## 1. Descrição do Problema, Desafio e Objetivos

### O Problema

Este projeto foi desenvolvido para a disciplina "Artificial Intelligence Fundamentals". O cenário do desafio envolve uma pequena empresa de delivery de alimentos, a "Sabor Express", que atua na região central da cidade.

A empresa enfrenta grandes desafios logísticos, especialmente em horários de pico. O método atual de definição de rotas é totalmente manual, baseado apenas na experiência dos entregadores. Isso resulta em:
* Rotas ineficientes e demoradas.
* Aumento nos custos de combustível.
* Atrasos nas entregas e, consequentemente, insatisfação dos clientes.

### O Desafio

O desafio consiste em desenvolver uma solução inteligente, baseada em algoritmos de Inteligência Artificial, para substituir o processo manual e sugerir as melhores rotas para os entregadores.

### Objetivos

O objetivo principal é tornar as entregas da "Sabor Express" mais rápidas, eficientes e econômicas. Para isso, a solução deve ser capaz de:
1.  Modelar a cidade como um grafo, com pontos de entrega e ruas com pesos.
2.  Encontrar o menor caminho entre múltiplos pontos de entrega.
3.  Em situações de alta demanda, agrupar entregas próximas (clustering) para otimizar o trabalho de múltiplos entregadores.

---

## 2. Abordagem Adotada

Para solucionar os dois principais desafios (roteamento e agrupamento), a seguinte abordagem foi implementada:

### a) Modelagem do Grafo
A área de atuação da "Sabor Express" foi modelada como um grafo não-direcionado e ponderado.
* **Nós (Vértices):** Representam a localização do restaurante e os diferentes pontos/bairros de entrega.
* **Arestas:** Representam as ruas que conectam os locais.
* **Pesos:** Associados às arestas, representando a distância ou o tempo estimado de percurso entre dois nós.

Os dados do grafo (locais, conexões e pesos) foram armazenados em arquivos `.csv` (ou formato similar) na pasta `/data` para serem lidos pela aplicação.

### b) Fluxo da Solução

O sistema opera em duas fases, dependendo da demanda:

**1. Agrupamento de Pedidos (Clustering):**
Quando há um grande volume de pedidos simultâneos, o sistema primeiro aplica um algoritmo de clustering (K-Means).
* **Entrada:** Uma lista de coordenadas (lat/long ou x/y) dos locais de entrega.
* **Processo:** O K-Means agrupa os pedidos em 'K' clusters, onde 'K' pode representar o número
