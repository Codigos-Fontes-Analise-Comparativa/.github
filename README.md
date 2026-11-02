# Análise Comparativa de Algoritmos de Pathfinding

**O impacto de paradigmas de programação e topologias espaciais**

Código-fonte do trabalho apresentado na **JOSIF 2026** (18ª Jornada Científica e Tecnológica do IFSULDEMINAS), desenvolvido no IFSULDEMINAS – Campus Machado.

Este trabalho compara o desempenho de quatro algoritmos clássicos de busca de caminhos, implementados de forma nativa (sem bibliotecas de roteamento) em quatro linguagens de paradigmas distintos, avaliando **tempo de processamento** e **pico de consumo de memória RAM**.

## Autores

- Gustavo M. de Lima
- José Gabriel R. da Cruz
- Saulo F. dos Santos
- Matheus G. Vilas Boas (orientador)

## O que há nesta organização

| Componente | Descrição | Repositório |
|---|---|---|
| **C** | BFS, DFS, Dijkstra e A* | [implementacao_buscas_c](https://github.com/Codigos-Fontes-Analise-Comparativa/implementacao_buscas_c) |
| **Java** | BFS, DFS, Dijkstra e A* | [implementacao_buscas_java](https://github.com/Codigos-Fontes-Analise-Comparativa/implementacao_buscas_java) |
| **Python** | BFS, DFS, Dijkstra e A* | [implementacao-buscas-python](https://github.com/Codigos-Fontes-Analise-Comparativa/implementacao-buscas-python) |
| **Elixir** | BFS, DFS, Dijkstra e A* | [buscar_elixir](https://github.com/Codigos-Fontes-Analise-Comparativa/buscar_elixir) |
| **Gerador de mapas (C#)** | Gera labirintos perfeitos e cavernas | [gerador_de_labirintos](https://github.com/Codigos-Fontes-Analise-Comparativa/gerador_de_labirintos) |

As instruções de uso do gerador de mapas estão no README do repositório [gerador_de_labirintos](https://github.com/Codigos-Fontes-Analise-Comparativa/gerador_de_labirintos).

## Algoritmos

- **BFS** (Busca em Largura)
- **DFS** (Busca em Profundidade)
- **Dijkstra**
- **A\*** (heurística de distância de Manhattan)

Todos foram implementados de forma nativa em C, Java, Python e Elixir, totalizando 16 implementações, sobre matrizes bidimensionais convencionais para garantir equidade na comparação.

## Gerador de mapas

Ferramenta própria em C# que gera arquivos de texto padronizados com duas topologias:

- **Labirintos perfeitos**, gerados com o algoritmo *Recursive Backtracker*.
- **Cavernas**, geradas com *autômato celular*, produzindo mapas **válidos** (com caminho entre entrada e saída) e **inválidos** (sem caminho), úteis para testar a exploração cega dos algoritmos.

### Formato dos arquivos

Seguindo o padrão do Moving AI Lab, cada célula do mapa é representada por:

| Símbolo | Significado |
|---|---|
| `0` | Obstáculo |
| `1` | Caminho |
| `E` | Entrada |
| `S` | Saída |

### Resoluções

Os mapas foram avaliados em **128×128**, **512×512** e **1024×1024**.

## Mapas de referência

Além dos mapas gerados, o trabalho utilizou cenários das bases do **Moving AI Lab** (Sturtevant, 2012). Os mapas dessa base devem ser obtidos diretamente na fonte: <https://www.movingai.com/benchmarks/>.

## Metodologia de medição

- **Métricas:** tempo de processamento (ms), pico de memória RAM (bytes) e iterações por segundo (IPS). As matrizes são clonadas a cada rodada para não alterar a exploração.
- **Memória por linguagem:** leitura determinística única em C e Python; média de 3 execuções em Java (para mitigar a inércia do *Garbage Collector*); biblioteca *Benchee* em Elixir.
- **Desempenho padrão** (*out-of-the-box*): C compilado sem flags de otimização explícitas.

### Ambiente dos experimentos

| Item | Especificação |
|---|---|
| Sistema | Windows 11 |
| Processador | Intel Core i5-11400H (2,70 GHz) |
| Memória | 24 GB de RAM |
| C | GCC 16.1.0 |
| Java | JDK 25.0.1 |
| Python | 3.13.5 |
| Elixir | 1.20.1 (Erlang/OTP 29) |

## Principais achados

- O motor JIT do Java pode rivalizar e até superar o C em varreduras massivas, ao custo de maior consumo de memória.
- O C teve o menor consumo de RAM; Elixir e Java apresentaram os maiores custos de memória.
- O Python se mostrou inadequado para pathfinding de alta performance em mapas grandes.
- O A\* é eficiente em cenários abertos e válidos, mas degrada em malhas inválidas; o DFS é ineficiente em mapas densos e rotas bloqueadas.

## Referências

- STURTEVANT, N. Benchmarks for Grid-Based Pathfinding. *IEEE Transactions on Computational Intelligence and AI in Games*, v. 4, n. 2, p. 144-148, 2012.
- CORMEN, T. H.; LEISERSON, C. E.; RIVEST, R. L.; STEIN, C. *Algoritmos: teoria e prática*. 3. ed. Rio de Janeiro: Elsevier, 2012.
- RUSSELL, S.; NORVIG, P. *Inteligência artificial*. 3. ed. Rio de Janeiro: Elsevier, 2013.

## Licença

Consulte o arquivo `LICENSE` em cada repositório.
