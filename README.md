# Classificação de Imagens com CNN em TensorFlow/Keras

# Descrição do Projeto
Este projeto utiliza uma Rede Neural Convolucional (CNN) para realizar a classificação de imagens em um dataset. O objetivo é treinar uma CNN em um dataset de imagens, medir o desempenho usando várias métricas, e salvar o modelo treinado para predições futuras.

# Estrutura do Repositório

* `train_model.ipynb`: Arquivo para treinar o modelo, registrar métricas e salvar os melhores pesos.
* `predict_model.ipynb`: Arquivo para carregar os pesos treinados e fazer predições em novos dados.
* `best_model.pth`: Arquivo que contém os pesos da melhor rede treinada, salvo automaticamente durante o treinamento.
* `README.md`: Documento explicativo do projeto.

# Dataset
O projeto utiliza o dataset CIFAR-10 disponível no TensorFlow/Keras, que consiste de 60.000 imagens coloridas em 10 classes (avião, automóvel, pássaro, gato, cervo, cachorro, sapo, cavalo, navio, caminhão). O CIFAR-10 é um dos datasets mais comuns para tarefas de classificação de imagens.

Caso deseje utilizar outro dataset, você pode substituí-lo no arquivo `train_model.ipynb` pela carga de um dataset personalizado.

# Pré-processamento
Para preparar os dados para o treinamento da CNN, foram aplicados os seguintes passos de pré-processamento:

1. Redimensionamento e Normalização: Todas as imagens foram escaladas para valores entre 0 e 1, dividindo por 255.

2. Divisão de Dados: O conjunto de dados foi dividido em 80% para treino e 20% para validação usando a função `train_test_split`.

3. Codificação dos Labels: No caso de datasets com labels não numéricos, utilizamos `LabelEncoder` para transformar os labels em valores numéricos.

# Modelo CNN
A rede neural convolucional foi construída usando a API `Sequential` do Keras, com a seguinte arquitetura:

* Camadas de Data Augmentation para reduzir o overfitting: `RandomFlip`, `RandomRotation`, e `RandomZoom`.

* Três camadas de convolução (`Conv2D`) e pooling (`MaxPooling2D`) para extrair características das imagens.

* Camadas densas (`Dense`) e camada de Dropout para evitar overfitting antes da saída final.

## Estrutura do Modelo
![image](https://github.com/user-attachments/assets/7d0c57a0-a07d-42d2-a16b-2230ec081d8e)



## Treinamento
O modelo é compilado com o otimizador `Adam` e a função de perda `sparse_categorical_crossentropy`. O treinamento é realizado com 50 épocas, e as métricas de desempenho são registradas em cada época.
![image](https://github.com/user-attachments/assets/131787e2-0b9b-42bd-bb08-95f0ac32ef9a)


## Métricas Monitoradas
Durante o treinamento, são monitoradas as seguintes métricas:

* Loss de Treinamento e Validação
* Acurácia de Treinamento e Validação
* F1 Score de Validação
* Precisão e Recall de Validação
* Matriz de Confusão ao final do treinamento

As melhores pesos do modelo, com base na menor loss de validação, são salvos automaticamente no arquivo `best_model.keras`.

## Visualização das Métricas
Os gráficos abaixo são gerados para analisar o desempenho do modelo durante o treinamento:

1. Loss durante o Treinamento e Validação: Para visualizar a convergência do modelo.

![image](https://github.com/user-attachments/assets/eedae1f9-487b-475d-9a61-4fc3332552d6)

3. Acurácia durante o Treinamento e Validação: Para avaliar a precisão geral.

![image](https://github.com/user-attachments/assets/923b51c2-36b3-412e-95da-0ea522851981)

5. F1 Score de Validação: Para verificar o equilíbrio entre precisão e recall.
6. Precisão e Recall de Validação: Para uma análise mais detalhada do desempenho em cada classe.
7. Matriz de Confusão: Para avaliar o desempenho do modelo em cada classe específica após o treinamento.

![image](https://github.com/user-attachments/assets/46b8272f-01c9-4af2-be04-f7d1abe9f032)


## Exemplo de Visualização
![image](https://github.com/user-attachments/assets/84d785a8-cecc-4770-9395-d67383385d8c)


## Predição
O arquivo `predict_model.ipynb` é usado para carregar o modelo salvo e realizar predições em novas imagens.

## Carregamento do Modelo e Predição
1. Carregue o modelo salvo usando o método `load_model`.
2. Insira uma nova imagem ou conjunto de imagens para que o modelo realize a predição.
![image](https://github.com/user-attachments/assets/d98b3369-082b-4047-ad83-e69ee25b49e8)


# Como Executar
## Passo 1: Treinamento
1. Abra o notebook `train_model.ipynb`.
2. Execute as células para carregar o dataset, pré-processar os dados, definir o modelo, treinar e salvar os melhores pesos em `best_model.keras`.

## Passo 2: Predição
1. Após o treinamento, abra o arquivo `predict_model.ipynb`.
2. Carregue os pesos do modelo salvo e execute as células para realizar predições em novas imagens.

## Requisitos
Para executar o projeto, você precisará das seguintes bibliotecas:

* TensorFlow
* NumPy
* scikit-learn
* Matplotlib
  
Para instalar as dependências, use o seguinte comando:

![image](https://github.com/user-attachments/assets/e4459c89-13c3-470d-86ff-c3a0ed9dfebd)


## Conclusão
Este projeto demonstra como usar uma rede neural convolucional para classificação de imagens usando TensorFlow e Keras. Utilizando métricas como acurácia, F1 Score, precisão e recall, é possível avaliar e ajustar o modelo para melhorar o desempenho. Esse mini-projeto é uma excelente introdução ao uso de CNNs para tarefas de visão computacional e classificação de imagens.

---
# Classificação de Imagens com Transfer Learning e Fine-Tuning

# Descrição do Projeto
Este projeto usa Transfer Learning e Fine-Tuning para realizar classificação de imagens em um dataset específico. Utilizamos um modelo pré-treinado (InceptionV3) da biblioteca `keras.applications`, que foi ajustado para atender ao nosso problema. O projeto inclui o pré-processamento das imagens, treinamento com fine-tuning, e avaliação de métricas de desempenho.

# Estrutura do Repositório
* `train_model.ipynb`: Arquivo para treinar o modelo, registrar métricas e salvar os melhores pesos.
* `predict_model.ipynb`: Arquivo para carregar os pesos treinados e fazer predições em novos dados.
* `best_model.pth`: Arquivo que contém os pesos da melhor rede treinada, salvo automaticamente durante o treinamento.
* `README.md`: Documento explicativo do projeto.

# Dataset
Para este projeto, utilizamos um dataset de classificação de imagens, que pode ser baixado em sites como Kaggle ou CV Datasets. O dataset escolhido contém várias classes de imagens e foi dividido em conjuntos de treino e validação. O dataset é redimensionado para o tamanho necessário pelo modelo escolhido (224x224 pixels para o InceptionV3).

# Pré-processamento
As imagens foram submetidas a um pré-processamento para otimizar o treinamento:

1. Redimensionamento: Todas as imagens foram redimensionadas para 224x224 pixels.
2. Normalização: Os valores dos pixels foram escalados para o intervalo [0, 1].
3. Data Augmentation: Incluímos rotação, espelhamento e zoom para aumentar a variabilidade dos dados de treino e evitar overfitting.

# Modelo: Transfer Learning com InceptionV3 e Fine-Tuning
O modelo pré-treinado InceptionV3 foi utilizado como base. As camadas iniciais foram congeladas, de modo que apenas as últimas camadas foram ajustadas ao dataset específico. Camadas adicionais foram adicionadas para personalizar o modelo ao problema:

1. Camadas de Data Augmentation: RandomFlip, RandomRotation, e RandomZoom para aumentar a variabilidade.
2. Camadas Convolucionais Pré-treinadas: As camadas convolucionais do InceptionV3 foram congeladas para aproveitar o conhecimento pré-treinado.
3. Novas Camadas de Classificação: Adicionamos uma camada densa com 1024 neurônios e uma camada de saída com softmax para classificar as imagens nas classes do dataset.

## Estrutura do Modelo

## Treinamento
O modelo foi treinado em 20 épocas, e os melhores pesos foram salvos automaticamente com base na menor perda (loss) de validação.

## Métricas Monitoradas
Durante o treinamento, registramos as seguintes métricas:

* Loss de Treinamento e Validação
* Acurácia de Treinamento e Validação
* F1 Score de Validação
* Precisão e Recall de Validação
* Matriz de Confusão: Exibida ao final para avaliar o desempenho do modelo em cada classe.

As métricas foram usadas para avaliar e ajustar o modelo, melhorando seu desempenho no dataset específico.

## Visualização das Métricas
Geramos gráficos para analisar o desempenho do modelo ao longo do treinamento, incluindo:

1. Loss durante o Treinamento e Validação
2. Acurácia durante o Treinamento e Validação
3. F1 Score de Validação
4. Precisão e Recall de Validação
5. Matriz de Confusão

## Exemplo de Visualização

## Predição
No arquivo `predict_model.ipynb`, carregamos o modelo salvo e realizamos predições em novas imagens. Este notebook demonstra como usar o modelo para classificar novas entradas.

## Carregamento do Modelo e Predição
1. Carregue o Modelo Salvo: O modelo treinado é carregado com o método `load_model`.
2. Realize a Predição: Insira uma imagem para obter a classe prevista pelo modelo.

# Como Executar
## Passo 1: Treinamento
1. Abra o arquivo  `train_model.ipynb `.
2. Execute todas as células para carregar o dataset, realizar o pré-processamento, definir o modelo e treinar.
3. O modelo será salvo automaticamente como  `best_model.h5 ` com os melhores pesos.

## Passo 2: Predição
1. Abra o arquivo `predict_model.ipynb` após o treinamento.
2. Carregue o modelo salvo e execute as células para realizar predições em novas imagens.

## Requisitos
Para executar o projeto, você precisará das seguintes bibliotecas:

* `TensorFlow`
* `NumPy`
* `scikit-learn`
* `Matplotlib`

Para instalar as dependências, execute:

![image](https://github.com/user-attachments/assets/900f52b4-5aca-42e8-bc95-5c652e73842a)

## Conclusão
Este projeto demonstra o uso de Transfer Learning com fine-tuning para classificação de imagens, usando um modelo pré-treinado (InceptionV3). O projeto fornece uma visão prática do uso de modelos de deep learning pré-treinados para resolver novos problemas, com o auxílio de métricas como acurácia, F1 Score, precisão e recall para avaliar o desempenho do modelo.
