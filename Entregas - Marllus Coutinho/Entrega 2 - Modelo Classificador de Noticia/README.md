# Classificador de Notícias Financeiras (Reuters)

**Estudante:** Marllus Coutinho Nascimento Júnior  
**Matrícula:** 202505642

## Sobre o projeto

Desenvolvimento de um modelo de Inteligência Artificial para classificar automaticamente notícias financeiras em **46 categorias**, utilizando o dataset Reuters disponibilizado pelo Keras.

O projeto aborda o desbalanceamento entre as categorias e implementa o pipeline completo de classificação, desde o pré-processamento dos dados até a inferência de novas notícias.

## Entrega

O notebook inclui:

- exploração e análise do dataset Reuters;
- análise e tratamento do desbalanceamento com pesos de classe;
- pré-processamento e padronização das sequências;
- construção e treinamento de uma rede neural com Keras;
- avaliação com Accuracy, Precision, Recall e F1-score;
- matriz de confusão;
- inferência com uma notícia do conjunto de teste e uma notícia externa.

## Tecnologias

- Python
- TensorFlow / Keras
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## Como executar

Instale as dependências:

```bash
pip install notebook tensorflow numpy matplotlib scikit-learn
```

Inicie o Jupyter:

```bash
jupyter notebook
```

Abra `Entrega_2_Classificador_de_Notícias_Financeiras_.ipynb` e execute as células em ordem. O dataset Reuters será carregado diretamente pelo Keras.
