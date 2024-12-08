# Flight Analytics BR

Este projeto utiliza dados sobre ocorrências de aviação civil no Brasil para realizar análise exploratória, processamento de dados e modelagem preditiva. O objetivo é identificar o fator predominante (humano ou técnico) nas ocorrências, utilizando modelos de aprendizado de máquina.

## Descrição

O código realiza os seguintes passos:

1. **Importação de Bibliotecas**:  
   Bibliotecas para manipulação de dados (`pandas`, `numpy`), visualização (`matplotlib`, `seaborn`) e machine learning (`sklearn`) são carregadas.

2. **Upload e Leitura dos Dados**:  
   O arquivo zip contendo o dataset é carregado, descompactado e lido para um DataFrame do Pandas.

3. **Análise Exploratória**:  
   Exploração da coluna de categorias de ocorrência para classificar os dados em fatores predominantes: 'Humano', 'Técnico' ou 'Outros'.

4. **Processamento de Dados**:  
   Criação da coluna `fator_predominante` com base na classificação e preparação dos dados para treinamento.

5. **Balanceamento de Dados**:  
   Uso do SMOTE (Synthetic Minority Over-sampling Technique) para balancear as classes nos dados de treinamento.

6. **Modelagem Preditiva**:  
   Treinamento de modelos de aprendizado de máquina, como Árvore de Decisão, Regressão Logística e Floresta Aleatória, para prever o fator predominante.

7. **Avaliação de Modelos**:  
   Apresentação das métricas de avaliação, como acurácia e matrizes de confusão, para cada modelo.

## Dados

### Variáveis Independentes Utilizadas no Modelo

As variáveis independentes utilizadas nos modelos preditivos foram:

- `ocorrencia_classificacao`: Classificação do tipo de ocorrência.
- `ocorrencia_uf`: Estado onde ocorreu o evento.
- `total_recomendacoes`: Número total de recomendações associadas à ocorrência.
- `investigacao_status`: Status da investigação.
- `ocorrencia_saida_pista`: Indicador de saída de pista.
- `ocorrencia_tipo_categoria`: Categoria atribuída à ocorrência.
- `aeronave_operador_categoria`: Categoria do operador da aeronave envolvida.

### Fatores Humanos e Técnicos

Além das variáveis gerais, as variáveis relacionadas aos fatores humanos e técnicos também foram consideradas, com base na coluna `ocorrencia_tipo_categoria`. A classificação foi realizada da seguinte forma:

1. **Fatores Humanos**:
   - As ocorrências com as categorias `PERDA DE CONTROLE EM VOO`, `PERDA DE CONTROLE NO SOLO`, `MANOBRA ABRUPTA` e `OPERAÇÃO A BAIXA ALTITUDE` foram classificadas como **Humanos**.

2. **Fatores Técnicos**:
   - As ocorrências com as categorias `FALHA OU MAU FUNCIONAMENTO DO MOTOR`, `FALHA OU MAU FUNCIONAMENTO DE SISTEMA / COMPONENTE` e `FOGO/FUMAÇA (SEM IMPACTO)` foram classificadas como **Técnicos**.


A função de classificação foi aplicada à coluna `ocorrencia_tipo_categoria`, criando uma nova coluna chamada `fator_predominante`, que foi utilizada para filtrar as ocorrências relacionadas aos fatores humanos e técnicos. Isso possibilitou a análise mais focada nos fatores que influenciam as ocorrências, auxiliando na construção do modelo preditivo.

Essas variáveis relacionadas a fatores humanos e técnicos ajudam a capturar as causas subjacentes dos eventos, o que pode ser crucial para o modelo preditivo.

## Ambiente

O **Google Colab** foi escolhido como ambiente principal para facilitar o upload de dados e execução do código, permitindo que o projeto seja facilmente reproduzido por outros usuários.

## Como Usar

1. **Obtenha o Dataset**:  
   - Faça o upload do arquivo zip contendo os dados diretamente no repositório do projeto **ou** baixe o dataset pelo [Kaggle](https://www.kaggle.com/datasets/ronnycfs/ocorrencias-aviacao-civil-brasileira).

2. **Carregue os Dados no Colab**:  
   - Acesse o **Google Colab** e faça o upload do arquivo zip baixado.  
   - Extraia os dados do arquivo zip e carregue o arquivo CSV em um DataFrame do Pandas utilizando o código disponibilizado no projeto.

3. **Execute o Código**:  
   - Siga a ordem das células no notebook, que inclui processamento dos dados, treinamento dos modelos e avaliação dos resultados.  

Ao final, você terá as métricas de avaliação dos modelos e insights gerados pela análise exploratória.


## Resultados

O gráfico de barras acima apresenta a **acurácia** dos três modelos treinados: Árvore de Decisão, Regressão Logística e Floresta Aleatória. Observa-se que:

- **Regressão Logística** obteve a maior acurácia (0.78), sendo o modelo mais eficaz dentre os avaliados.
- **Floresta Aleatória** ficou em segundo lugar (0.77), com um desempenho próximo ao da Regressão Logística.
- **Árvore de Decisão** apresentou a menor acurácia (0.76).

Além disso, as **matrizes de confusão** fornecem uma visão detalhada sobre o desempenho dos modelos em termos de acertos e erros em cada classe:

- **Floresta Aleatória:**
  - Alto número de verdadeiros positivos (339) para a classe predominante.
  - O desempenho foi razoável para a classe minoritária, com 106 acertos.

- **Árvore de Decisão:**
  - Apresentou mais erros de classificação na classe minoritária (24 predições incorretas).
  - Foi menos precisa ao classificar a classe predominante em comparação com os outros modelos.

- **Regressão Logística:**
  - Obteve um equilíbrio razoável entre as classes, acertando 138 casos da classe minoritária.
  - Também apresentou o maior número de acertos na classe predominante (311).

Esses resultados mostram que, embora todos os modelos sejam comparáveis em termos de acurácia geral, a **Regressão Logística** apresentou uma performance mais consistente entre as classes.

![alt text](https://github.com/queirogaraffael/flight-analytics-br/blob/main/imagens-resultado/Untitled.png?raw=true)
![alt text](https://github.com/queirogaraffael/flight-analytics-br/blob/main/imagens-resultado/Untitled-1.png?raw=true)

## Contribuições

Este projeto está aberto para contribuições. Caso deseje melhorar ou sugerir modificações, sinta-se à vontade para fazer um fork e enviar um pull request.

## Licença

Este projeto está licenciado sob a [Licença MIT](LICENSE).
