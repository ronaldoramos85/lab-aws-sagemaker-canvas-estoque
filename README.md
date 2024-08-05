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
-   Escolha a opção do SageMaker Canvas que é exibida.
-	Será mostrada a tela de domínios. Caso ainda não tenha sido criado um domínio, será necessário fazê-lo, seguindo as instruções para criação de um domínio de único usuário, visto se tratar apenas de teste. Caso o domínio já tenha sido criado, será exibida uma tela semelhante a seguinte, onde deverá ser clicada a opção "Tela" (Canvas em português) no menu à esquerda:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Dominio.jpg)
-	A próxima tela exibirá o usuário criado na etapa de criação de domínio de um único usuário. Basta clicar no botão amarelo "Abrir o Canvas", como segue:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/usuario.jpg)
-	A tela inicial do Canvas é como se segue:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Home_SageMaker_Canvas.jpg)
-	Em "My models" aparecerão os modelos já criados:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Modelo_criado.jpg)
-	Caso não tenha um modelo criado ou queira criar um novo, deverá clicar em "New model", no canto superior direito:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Modelo_criado.jpg)
-	Aparerá uma janela onde deverá ser colocado o nome do modelo que será criado:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/nomear_modelo.jpg)
-	Os passos descritos a seguir detalharão a criação e treinamento do modelo, bem como a etapa de predição.


### 1. Selecionar Dataset

-   Na pasta `datasets` deste repositório foi escolhido o dataset "dataset-1000-com-preco-variavel-e-renovacao-estoque.csv" que é um conjunto de dados na forma de uma tabela em formato CSV (valores separados por vírgula).
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Dataset.jpg)

### 2. Construir/Treinar

-   Após a importação do dataset no SageMaker Canvas, será necessário configurar as variáveis de entrada e saída de acordo com os dados, bem como a quantidade de registros que serão considerados como amostra para o treinamento do modelo.
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Build_002.jpg)
-	Ao clicar em "Configure model" é possível realizar o ajuste fino do tratamento dos dados, com a definição da coluna que identifica os itens, a coluna que será usada para a criação da série temporal, bem como o número de dias da predição e se será usado o calendário de feriados de algum país, como pode ser visto a seguir:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Build_006.jpg)
-	São apresentados fatores que poderão resultar em problemas, a partir dos dados fornecidos:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Build_004.jpg)
-	Um tratamento básico dos dados pode ser realizado, com a eliminação de duplicatas e preenchimento de valores faltantes:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Build_005.jpg)
-	Ao clicar em "Data Visualizer" é possível ter uma visão gráfica dos dados do dataset, escolhendo variáveis distintas e diversos formatos de gráficos:
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Build_010.jpg)


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
