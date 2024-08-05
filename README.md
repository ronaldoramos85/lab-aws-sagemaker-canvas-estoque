# 📊 Previsão de Estoque Inteligente na AWS com [SageMaker Canvas](https://aws.amazon.com/pt/sagemaker/canvas/)

Bem-vindo ao projeto "Previsão de Estoque Inteligente na AWS com SageMaker Canvas". Este  projeto é resultado de um Lab DIO (Digital Innovation One), onde foram exercitados os conhecimentos adquiridos ao longo do "Bootcamp Nexa - Machine Learning para Iniciantes na AWS" sobre uso do SageMaker Canvas para criar previsões de estoque baseadas em Machine Learning (ML).

## 📋 Pré-requisitos

Para a realização deste Lab (também chamado de desafio de projeto) foi necessário criar uma conta na AWS. Mais detalhes sobre como criar uma conta na AWS podem ser conferidos no repositório [AWS Cloud Quickstart](https://github.com/digitalinnovationone/aws-cloud-quickstart).


## 🎯 Objetivos Deste Desafio de Projeto (Lab)

![image](https://github.com/digitalinnovationone/lab-aws-sagemaker-canvas-estoque/assets/730492/72f5c21f-5562-491e-aa42-2885a3184650)

- Como resultado do referido Lab DIO foi criado este [passo a passo] com a descrição dos passos necessários para a realizar todo o processo de criação de um Modelo de Machine Learning no-code para uma "Previsão de Estoque Inteligente" com o Amazon SageMaker Canvas.
- A URL deste repositório com a solução foi fornecido na plataforma da DIO para avaliação de meu desempenho no referido Bootcamp.


## 🚀 Passo a Passo

### 0. Primeiros passos
-   Após a criação da conta na AWS, é necessário logar com o usuário criado na [AWS Console](https://signin.aws.amazon.com/signin?redirect_uri=https%3A%2F%2Fconsole.aws.amazon.com%2Fconsole%2Fhome%3FhashArgs%3D%2523%26isauthcode%3Dtrue%26nc2%3Dh_ct%26oauthStart%3D1722891305242%26src%3Dheader-signin%26state%3DhashArgsFromTB_us-east-2_1eb17e8439ff0272&client_id=arn%3Aaws%3Asignin%3A%3A%3Aconsole%2Fcanvas&forceMobileApp=0&code_challenge=ZRclOwZ9iEQarWEC2ALxQLWX9SXQzD1RI5PUn-fC_lQ&code_challenge_method=SHA-256), conforme imagem a seguir:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/login_console_AWS.jpg)
-   É necessário entrar com o e-mail utilizado para criar a conta na AWS como "Endereço de e-mail de usuário root". Após isso, na próxima tela será requisitada a senha.
-   Se o login for realizado com sucesso, será exibida a tela inicial da AWS Console, onde poderá buscar por "canvas", conforme segue:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Home_AWS_Console.jpg)


### 1. Selecionar Dataset

-   Na pasta `datasets` deste repositório foi escolhido o dataset "dataset-1000-com-preco-variavel-e-renovacao-estoque.csv" que é um conjunto de dados na forma de uma tabela em formato CSV (valores separados por vírgula).

### 2. Construir/Treinar

-   No SageMaker Canvas, importe o dataset que você selecionou.
-   Configure as variáveis de entrada e saída de acordo com os dados.
-   Inicie o treinamento do modelo. Isso pode levar algum tempo, dependendo do tamanho do dataset.

### 3. Analisar

-   Após o treinamento, examine as métricas de performance do modelo.
-   Verifique as principais características que influenciam as previsões.
-   Faça ajustes no modelo se necessário e re-treine até obter um desempenho satisfatório.

### 4. Prever

-   Use o modelo treinado para fazer previsões de estoque.
-   Exporte os resultados e analise as previsões geradas.
-   Documente suas conclusões e qualquer insight obtido a partir das previsões.

## 🤔 Dúvidas?

Esperamos que esta experiência tenha sido enriquecedora e que você tenha aprendido mais sobre Machine Learning aplicado a problemas reais. Se tiver alguma dúvida, não hesite em abrir uma issue neste repositório ou entrar em contato com a equipe da DIO.
