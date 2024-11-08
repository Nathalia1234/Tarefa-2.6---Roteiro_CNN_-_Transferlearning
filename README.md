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

As melhores pesos do modelo, com base na menor loss de validação, são salvos automaticamente no arquivo `sbest_model.h5`.

## Visualização das Métricas
Os gráficos abaixo são gerados para analisar o desempenho do modelo durante o treinamento:

1. Loss durante o Treinamento e Validação: Para visualizar a convergência do modelo.
2. Acurácia durante o Treinamento e Validação: Para avaliar a precisão geral.
3. F1 Score de Validação: Para verificar o equilíbrio entre precisão e recall.
4. Precisão e Recall de Validação: Para uma análise mais detalhada do desempenho em cada classe.
5. Matriz de Confusão: Para avaliar o desempenho do modelo em cada classe específica após o treinamento.

## Exemplo de Visualização
![image](https://github.com/user-attachments/assets/84d785a8-cecc-4770-9395-d67383385d8c)


## Predição
O notebook `predict_model.ipynb` é usado para carregar o modelo salvo e realizar predições em novas imagens.

## Carregamento do Modelo e Predição
1. Carregue o modelo salvo usando o método `load_model`.
2. Insira uma nova imagem ou conjunto de imagens para que o modelo realize a predição.
![image](https://github.com/user-attachments/assets/d98b3369-082b-4047-ad83-e69ee25b49e8)


# Como Executar
## Passo 1: Treinamento
1. Abra o notebook `train_model.ipynb`.
2. Execute as células para carregar o dataset, pré-processar os dados, definir o modelo, treinar e salvar os melhores pesos em `best_model.h5`.

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
