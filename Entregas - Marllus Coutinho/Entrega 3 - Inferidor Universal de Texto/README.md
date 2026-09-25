# Inferidor Universal de Texto ONNX

## Identificação

- **Aluno:** Marllus Coutinho Nascimento Júnior
- **Matrícula:** 202505642
- **Aplicação hospedada:** [https://text-classifier-onnx.lovable.app](https://text-classifier-onnx.lovable.app)

## Arquivos da entrega

Este repositório contém os dois arquivos necessários para utilizar o classificador Reuters:

- [`modelo_reuters.onnx`](./modelo_reuters.onnx): rede neural executável no formato ONNX;
- [`semantica_reuters.json`](./semantica_reuters.json): identidade, vocabulário, pré-processamento, categorias e explicações do modelo.

## Sobre o projeto

O **Inferidor Universal de Texto ONNX** é uma aplicação web para executar modelos de classificação de texto diretamente no navegador.

Cada classificador é representado por um modelo `.onnx` e um arquivo de semântica `.json`. A aplicação interpreta esses dois arquivos, verifica se são compatíveis e monta dinamicamente a experiência de inferência. Dessa forma, novos classificadores podem ser utilizados sem alterações manuais na interface.

O Reuters News Classifier é o primeiro modelo utilizado para demonstrar a plataforma. Ele identifica o assunto predominante de notícias econômicas e financeiras entre 46 categorias do conjunto Reuters/Keras.

## Objetivo

O projeto foi desenvolvido para demonstrar uma integração completa entre uma aplicação React e modelos ONNX de classificação de texto, incluindo:

- validação do contrato de entrada e saída;
- preparação e tokenização do texto;
- tradução quando necessária;
- execução local da rede neural;
- interpretação dinâmica das probabilidades;
- apresentação acessível e responsiva dos resultados.

## Principais funcionalidades

- Upload do modelo ONNX e de sua semântica JSON.
- Validação cruzada de nomes, tipos, shapes e número de classes.
- Tokenizer genérico `word-index` configurado pelo JSON.
- Tradução de notícias em português para inglês.
- Inferência local utilizando ONNX Runtime Web.
- Exibição do texto efetivamente enviado ao modelo.
- Apresentação das classes mais prováveis em Top 3, Top 5, Top 10 ou todas.
- Página de categorias gerada a partir da semântica.
- Pipeline e explicação do modelo definidos no JSON.
- Temas claro, escuro e automático.
- Interface responsiva inspirada em jornal impresso.

## Fluxo da inferência

```text
modelo_reuters.onnx + semantica_reuters.json
                       ↓
               Validação cruzada
                       ↓
                Texto da notícia
                       ↓
            Detecção do idioma
                       ↓
        Tradução, quando necessária
                       ↓
                  Tokenização
                       ↓
               Inferência ONNX
                       ↓
       Probabilidades e categorias
```

A tradução é utilizada somente para preparar o idioma esperado pelo modelo. A classificação e as probabilidades são produzidas exclusivamente pelo arquivo ONNX.

## Modelo Reuters

O modelo utilizado na demonstração possui a seguinte interface:

| Elemento | Nome | Tipo | Shape |
| --- | --- | --- | --- |
| Entrada | `noticia` | `int32` | `[batch, 300]` |
| Saída | `probabilidades` | `float32` | `[batch, 46]` |

Características principais:

- **Tarefa:** classificação de texto;
- **Dataset:** Keras Reuters newswire topics;
- **Idioma esperado:** inglês;
- **Tokenizer:** `word-index`;
- **Vocabulário:** 30.979 termos;
- **Tamanho máximo:** 300 tokens;
- **Classes:** 46 categorias;
- **Saída:** probabilidades normalizadas.

## Arquivo de semântica

O arquivo `semantica_reuters.json` segue a **ONNX Text Classifier Specification v1** e está organizado em:

```text
semantica_reuters.json
├── specification
├── model
├── language
├── input
├── preprocessing
├── output
├── explanation
└── labels
```

Ele contém o vocabulário completo, tokens especiais, regras de padding e truncamento, traduções das classes e informações utilizadas para explicar o modelo na interface.

## Como utilizar

1. Acesse a aplicação hospedada no Lovable.
2. Selecione o arquivo `modelo_reuters.onnx` no campo **Modelo ONNX**.
3. Selecione o arquivo `semantica_reuters.json` no campo **Semântica**.
4. Aguarde a mensagem de compatibilidade validada.
5. Insira uma notícia em português ou inglês.
6. Clique em **Executar inferência**.
7. Consulte a classe prevista, as probabilidades e o texto processado.

## Tecnologias

- React 19
- TypeScript
- TanStack Start
- Vite
- Tailwind CSS
- ONNX Runtime Web
- Zod
- Bun

## Observação

As classificações oferecem contexto temático e não constituem recomendação de investimento, previsão de preço ou garantia de impacto no mercado.
