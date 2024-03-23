### Modelo de Previsão de Aluguel de Bicicletas com Azure ML

Este projeto demonstra, como utilizar a funcionalidade de automação de aprendizado de máquina no Azure Machine Learning para treinar e avaliar um modelo de previsão de aluguel de bicicletas, baseados em dados históricos. E então realizar o deploy e testar o modelo treinado.

## Criação do Espaço de Trabalho

1. Acesso ao [Portal do Azure](https://portal.azure.com) usando credenciais da Microsoft.
2. Seleção de **+ Criar um recurso** no menu do portal, busca por **Machine Learning**, e criação de um novo recurso do Azure Machine Learning.
3. Preenchimento dos detalhes necessários como assinatura, grupo de recursos, nome, região, entre outros componentes necessários como conta de armazenamento, cofre de chaves, insights de aplicação e registro de contêiner.
4. Lançamento do [Azure Machine Learning Studio](https://ml.azure.com) e acesso ao workspace criado.

## Treinamento do Modelo com AutoML

1. No Azure Machine Learning Studio, navegação até a página **Automated ML** sob **Authoring**.
2. Criação de um novo trabalho de AutoML com as configurações:
   - **Nome do trabalho**: mslearn-bike-automl
   - **Tipo de tarefa**: Regressão
   - **Conjunto de dados**: Criação de um novo conjunto de dados chamado [bike-rentals] com dados de (https://aka.ms/bike-rentals).
   - **Algoritmos permitidos**: RandomForest e LightGBM
   - **Métrica de avaliação**: Normalized root mean squared error
3. Submissão do trabalho de treinamento.

## Implantação do Modelo

1. No Azure ML Studio, seleção da aba **Model** para o melhor modelo e escolha de **Deploy** para criar um serviço web.
2. Configuração do serviço web:
   - **Nome**: predict-rentals
   - **Descrição**: Previsão de aluguéis de bicicleta
   - **Tipo de computação**: Instância de Contêiner do Azure
   - **Autenticação**: Habilitada
3. Espera pela conclusão da implantação, indicada pelo status **Succeeded**.

## Teste do Modelo

1. No Azure ML Studio, seleção de **Endpoints** e abertura do endpoint predict-rentals para testar.
2. Substituição do JSON de entrada no painel de teste pelo exemplo fornecido e execução do teste.
3. Revisão dos resultados do teste, que incluem o número previsto de aluguéis.
