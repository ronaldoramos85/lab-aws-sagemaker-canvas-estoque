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
-	Para treinar o modelo podem ser escolhidas uma de duas opções: Quick Build ou Standard Build. Standard Build realiza um treinamento que demora mais tempo (algumas horas) e resulta em maior precisão, ao passo que Quick Build realiza um treinamento mais rápido (alguns minutos) que resulta em uma precisão menor nas predições. Para a finalidade deste Lab DIO foi escolhido Quick Build.
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Build_011.jpg)
-	É exibida uma mensagem informando que o treinamento do modelo está em progresso.
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Build_013.jpg)
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Build_014.jpg)
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Build_015.jpg)

### 3. Analisar

-   Na etapa de Análise são exibidos os percentuais de impacto das variáveis (colunas), bem como as informações de Avg. wQL, MAPE, WAPE, RMSE e MASE que resultaram do treinamento realizado. Grosso modo, quanto mais próximo esses valores estiverem de zero, isso representa uma menor diferença entre a predição e o resultado, o que denota um alto índice de acerto.
![image](https://github.com/ronaldoramos85/lab-aws-sagemaker-canvas-estoque/blob/main/images/Analyze_001.jpg)

Agora, vamos entender as métricas mencionadas:

1. **MAPE (Erro Absoluto Percentual Médio)**: É uma métrica para avaliar modelos de regressão em machine learning. O MAPE é expresso em porcentagem, o que facilita a compreensão para a maioria das pessoas e ajuda na comunicação de resultados para pessoas que não têm conhecimento técnico em machine learning⁵. A fórmula do MAPE é:

    $$MAPE = \frac{1}{n} \sum_{i=1}^{n} \left| \frac{y_i - p_i}{y_i} \right| * 100$$

    onde `n` é o número total de amostras, `y_i` é o valor real para a amostra `i` e `p_i` é o valor previsto para a amostra `i`⁵.

2. **WAPE (Erro Percentual Médio Ponderado)**: É uma métrica que permite que vários modelos contribuam para uma previsão em proporção ao seu desempenho estimado¹⁴. A fórmula do WAPE é:

    $$WAPE = \frac{\sum_{t=1}^{n} |A_t - F_t|}{\sum_{t=1}^{n} A_t}$$

    onde `A_t` é o valor real e `F_t` é o valor previsto¹⁴.

3. **RMSE (Raiz do Erro Quadrático Médio)**: É uma métrica amplamente utilizada para avaliar o desempenho de modelos de regressão. Ela quantifica a diferença entre os valores previstos e os valores reais, calculando a raiz quadrada da média dos quadrados das diferenças¹⁶. A fórmula do RMSE é:

    $$RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - p_i)^2}$$

    onde `n` é o número total de amostras, `y_i` é o valor real para a amostra `i` e `p_i` é o valor previsto para a amostra `i`¹⁶.

4. **MASE (Erro Absoluto Médio Escalado)**: É uma medida de precisão de previsão que compara as previsões com a saída de uma abordagem de previsão ingênua²³. A fórmula do MASE é:

    $$MASE = \frac{MAE}{MAE_{in-sample, naive}}$$

    onde `MAE` é o erro absoluto médio produzido pela previsão real e `MAE_{in-sample, naive}` é o erro absoluto médio produzido por uma previsão ingênua, calculado nos dados de treinamento²¹.

Essas métricas são essenciais para avaliar a precisão e o desempenho dos modelos de machine learning. Cada uma delas tem suas próprias vantagens e desvantagens, e a escolha da métrica correta depende do problema específico que está sendo resolvido.

Fonte:
(1) No-code Machine Learning - Amazon SageMaker Canvas - AWS. https://aws.amazon.com/sagemaker/canvas/.
(2) MAPE (Erro Absoluto Percentual Médio) em Machine Learning. https://mariofilho.com/mape-erro-absoluto-percentual-medio-em-machine-learning/.
(3) Understanding Forecast Accuracy: MAPE, WAPE, WMAPE. https://www.baeldung.com/cs/mape-vs-wape-vs-wmape.
(4) How to Interpret Root Mean Square Error (RMSE) - Statology. https://www.statology.org/how-to-interpret-rmse/.
(5) Mean Absolute Scaled Error (MASE) in Forecasting - Medium. https://medium.com/@ashishdce/mean-absolute-scaled-error-mase-in-forecasting-8f3aecc21968.
(6) Interpretation of mean absolute scaled error (MASE). https://stats.stackexchange.com/questions/124365/interpretation-of-mean-absolute-scaled-error-mase.
(7) Log In to Canvas - AWS Academy. https://awsacademy.instructure.com/login/canvas.
(8) GitHub - digitalinnovationone/lab-aws-sagemaker-canvas-estoque. https://github.com/digitalinnovationone/lab-aws-sagemaker-canvas-estoque.
(9) Previsão-de-Estoque-Inteligente-na-AWS-com-Sagemaker-Canvas. https://github.com/EriAssunPereira/-Previs-o-de-Estoque-Inteligente-na-AWS-com-Sagemaker-Canvas.
(10) Mean Average Precision (mAP) Explained | Paperspace Blog. https://blog.paperspace.com/mean-average-precision/.
(11) Mean absolute percentage error - Wikipedia. https://en.wikipedia.org/wiki/Mean_absolute_percentage_error.
(12) What Is MAPE? Your Guide to Mean Absolute Percentage Error. https://www.indeed.com/career-advice/career-development/what-is-mape.
(13) Mean Average Precision (mAP) Explained: Everything You Need to Know. https://www.v7labs.com/blog/mean-average-precision.
(14) classification - macro average and weighted average meaning in .... https://datascience.stackexchange.com/questions/65839/macro-average-and-weighted-average-meaning-in-classification-report.
(15) Understanding Micro, Macro, and Weighted Averages for Scikit-Learn .... http://sefidian.com/2022/06/19/understanding-micro-macro-and-weighted-averages-for-scikit-learn-metrics-in-multi-class-classification-with-example/.
(16) What Is Machine Learning? Definition, Types, and Examples. https://www.coursera.org/articles/what-is-machine-learning.
(17) How to Develop a Weighted Average Ensemble for Deep Learning Neural .... https://machinelearningmastery.com/weighted-average-ensemble-for-deep-learning-neural-networks/.
(18) Introducing WAPE - Obviously AI. https://www.obviously.ai/post/introducing-wape.
(19) RMSE (Raiz Do Erro Quadrático Médio) Em Machine Learning. https://mariofilho.com/rmse-raiz-do-erro-quadratico-medio-em-machine-learning/.
(20) Root Mean Squared Error (RMSE) - AI Wiki. https://aiwiki.ai/wiki/Root_Mean_Squared_Error_%28RMSE%29.
(21) RMSE: Root-Mean-Square Error in Machine Learning - Includehelp.com. https://www.includehelp.com/ml-ai/root-mean-square%20error-rmse.aspx.
(22) What is Root Mean Square Error? Calculation & Importance - Deepchecks. https://deepchecks.com/glossary/root-mean-square-error/.
(23) Mean absolute scaled error - Wikipedia. https://en.wikipedia.org/wiki/Mean_absolute_scaled_error.
(24) mase : Mean Absolute Scaled Error - R Package Documentation. https://rdrr.io/cran/Metrics/man/mase.html.
(25) [Machine Learning] Introduction To MAE Metric (With Example). https://clay-atlas.com/us/blog/2021/11/24/machine-learning-mean-absolute-error/.

### 4. Prever

-   Use o modelo treinado para fazer previsões de estoque.
-   Exporte os resultados e analise as previsões geradas.
-   Documente suas conclusões e qualquer insight obtido a partir das previsões.

## 🤔 Dúvidas?

Esperamos que esta experiência tenha sido enriquecedora e que você tenha aprendido mais sobre Machine Learning aplicado a problemas reais. Se tiver alguma dúvida, não hesite em abrir uma issue neste repositório ou entrar em contato com a equipe da DIO.
