# Arquitetura baseada em Processamento de Linguagem Natural e Aprendizado Não Supervisionado para agrupamento temático de Leis de Curitiba

Repositório contendo os experimentos e as análises desenvolvidas no trabalho de conclusão de curso, cujo objetivo é aplicar técnicas de **Processamento de Linguagem Natural (PLN)** e **Aprendizado Não Supervisionado** ao conjunto de leis municipais do município de Curitiba, visando identificar padrões estruturais e temáticos nos textos legais. O estudo explora desde o pré-processamento textual até a representação vetorial, redução de dimensionalidade e algoritmos de agrupamento, com foco na análise exploratória e interpretativa de documentos legislativos.

**Instituição:** Universidade de São Paulo (USP) - São Carlos
**Curso:** MBA em Ciências de Dados
**Título do trabalho:** Agrupamento temático de leis de Curitiba por meio de Processamento de Linguagem Natural: Uma abordagem baseada em aprendizado não supervisionado
**Disponível em:** (*aguardando a banca...*)

---

## 📌 Objetivos

### Objetivo Geral
Aplicar técnicas de Processamento de Linguagem Natural e de Aprendizado Não Supervisionado para analisar estrutural e semanticamente leis ordinárias do município de Curitiba, publicadas entre 2017 e 2024.

### Objetivos Específicos
- Realizar o pré-processamento de textos legais (limpeza, normalização e tokenização);
- Identificar padrões linguísticos e estruturais recorrentes nos documentos;
- Analisar a distribuição de classes gramaticais e estruturas sintáticas;
- Representar os documentos em espaço vetorial utilizando diferentes abordagens;
- Aplicar técnicas de redução de dimensionalidade para visualização e análise;
- Empregar algoritmos de agrupamento para identificar temas predominantes;
- Comparar abordagens de clusterização baseadas em centroides e densidade.

---

## 📊 Fonte dos Dados

- **Origem:** Legisladoc, portal oficial contendo os atos normativos publicados pelo município de Curitiba
- **Tipo de documentos:** Leis ordinárias
- **Formato:** PDF
- **Período:** 2017 a 2024
- **Quantidade inicial:** 1.527 documentos
  - *2017:* 151
  - *2018:* 222
  - *2019:* 220
  - *2020:* 213
  - *2021:* 156
  - *2022:* 185
  - *2023:* 169
  - *2024:* 211
- **Quantidade final (após limpeza):** 1.458 documentos

Os documentos foram extraídos do portal, organizados em subpastas nomeadas conforme o ano de publicação, com posterior tratamento para remoção de duplicidades (manutenção da versão mais recente de leis republicadas), sendo organizados em formato tabular (`.csv`).

---

## 🧹 Pré-processamento Textual

As seguintes etapas de pré-processamento foram aplicadas:

- Extração de texto a partir de PDFs;
- Normalização textual (minúsculas, remoção de pontuação e caracteres especiais);
- Tokenização;
- Remoção de *stop words*;
- Lematização;
- Análise de frequência de termos;
- Geração de *n-gramas*;
- Análise morfossintática (*POS tagging* e *dependency parsing*).

---

## 🧠 Representação Vetorial

Foram utilizadas diferentes abordagens para representação dos textos:

- ***Bag of Words* (BoW)**
- **TF-IDF (*Term Frequency – Inverse Document Frequency*)**
- ***Embeddings* distribuídos**
- Análise de similaridade por distância do cosseno

Essas representações serviram como base para as etapas de redução de dimensionalidade e agrupamento.

---

## 📉 Redução de Dimensionalidade

Para apoiar a visualização e mitigar os efeitos da alta dimensionalidade, foram aplicadas as seguintes técnicas:

- **PCA (*Principal Component Analysis*)**  
  - Análise da variância explicada acumulada;
- **t-SNE (*t-Distributed Stochastic Neighbor Embedding*)**  
  - Ênfase na preservação de relações locais;
- **UMAP (*Uniform Manifold Approximation and Projection*)**  
  - Equilíbrio entre preservação de estruturas locais e globais.

O UMAP foi selecionado como abordagem principal para a etapa final de agrupamento.

---

## 🧩 Algoritmos de Agrupamento

Foram aplicados e comparados dois algoritmos de clusterização:

### 🔹 K-Means
- Método baseado em centroides;
- Seleção do número de clusters via **Método do Cotovelo**;
- Avaliação complementar com ***Silhouette Score***;
- Análise interpretativa por palavras representativas dos clusters.

### 🔹 HDBSCAN
- Algoritmo baseado em densidade;
- Identificação automática do número de clusters;
- Capacidade de identificar pontos de ruído;
- Análise da estrutura temática emergente sem imposição de *k* fixo.

A comparação entre os algoritmos evidenciou que diferentes abordagens capturam distintos aspectos da organização semântica do corpus.

---

## 📈 Visualizações e Análises

O projeto inclui diversas visualizações, tais como:

- Nuvem de palavras (*WordCloud*);
- Distribuição de classes gramaticais;
- Gráficos de variância explicada;
- Projeções em 2D (PCA, t-SNE e UMAP);
- Visualizações de *clusters* com rótulos semânticos;
- Comparações entre métodos de agrupamento.

---

## 🛠️ Tecnologias

- **Ambiente:** Google Colab (baseline), Pop!_OS 22.04 (comparação)
- **Linguagem:** Python 3.12.12 (Colab), Python 3.10.11 (Linux)
- **Bibliotecas:** `pandas`, `numpy`, `scikit-learn`,`spaCy`, `nltk`, `gensim`,`umap-learn`, `hdbscan`, `matplotlib`, `seaborn` e `wordcloud`;

---

## 🏆 Principais Resultados

Os resultados indicam que, enquanto o algoritmo K-Means oferece uma divisão mais acentuada dos temas, o algortimo HDBSCAN, tem foco em termos estruturais dos documentos.

---

## ⚠️ Limitações

- Natureza não determinística de alguns algoritmos (ex.: UMAP e HDBSCAN);
- Forte sobreposição semântica entre documentos legais;
- Dificuldade de definição de fronteiras claras entre temas legais;

---

## 🔮 Trabalhos Futuros

- Aplicação de modelos supervisionados para classificação temática;
- Uso de *topic modeling* (ex.: LDA ou BERTopic);
- Uso de bibliotecas especializadas em liguagem jurídica, como a LegalNLP;
- Análise temporal da evolução dos temas legislativos;
- Integração com sistemas de busca semântica;
- Expansão para outros tipos de atos normativos ou outros municípios.
