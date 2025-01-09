

# Introdução ao Projeto

Neste projeto de Ciência de Dados, trabalharemos com um conjunto de dados que contém informações financeiras de clientes, como saldo médio, frequência de compras, limite de crédito e adiantamentos em dinheiro. O objetivo principal é utilizar **técnicas de aprendizado não supervisionado**, especificamente o **algoritmo K-Means**, para realizar a **segmentação de clientes**. 

A segmentação de clientes é uma prática essencial em diversos setores, como marketing e gestão de negócios, permitindo identificar padrões de comportamento e criar estratégias personalizadas. Ao agrupar clientes com características similares, empresas podem:

- Otimizar campanhas de marketing.
- Identificar perfis de risco financeiro.
- Ajustar políticas de crédito e fidelidade.

### Dados e Análise Inicial

O conjunto de dados contém 8.950 registros e 18 variáveis, incluindo informações sobre saldo, limite de crédito, pagamentos, frequência de transações e outros comportamentos financeiros. Alguns dos destaques incluem:

- **BALANCE (Saldo):** Representa o saldo médio dos clientes. A distribuição é ampla, indicando diferentes níveis de engajamento financeiro.
- **PURCHASES (Compras):** Reflete os gastos dos clientes, que variam de pequenos a grandes volumes.
- **CREDIT_LIMIT (Limite de crédito):** Um indicativo da capacidade de crédito do cliente, variando de \$50 a \$30.000.
- **MINIMUM_PAYMENTS (Pagamentos mínimos):** Alguns clientes possuem valores ausentes, que podem ser tratados durante a preparação dos dados.

A presença de variáveis como frequência de compras e adiantamentos em dinheiro é particularmente relevante para identificar padrões de comportamento.

# analise dos dados 

![image](https://github.com/user-attachments/assets/0750b5a8-09ed-4e5e-9c6f-2e6cc1ddbc84)

intepretaçao do codigo:
O código visa visualizar a distribuição dos dados de cada coluna do DataFrame creditcard_df. Ele cria um gráfico com vários subplots, onde cada subplot mostra a distribuição de uma coluna específica. A biblioteca seaborn é utilizada para gerar histogramas com curvas de densidade (KDE), permitindo a análise visual da distribuição dos dados, como padrões, outliers e assimetria.

![k1](https://github.com/user-attachments/assets/e7d01519-e187-4f3f-b872-14f508b5bbba)


podemos extrair os seguintes insights sobre os dados dos clientes de cartão de crédito:

* **Saldo (BALANCE):** A maioria dos clientes possui saldos baixos ou moderados, mas há uma parcela significativa com saldos muito altos. Isso indica que existe um grupo de clientes com dívidas consideráveis.
* **Frequência de Saldo (BALANCE_FREQUENCY):** A maioria dos clientes paga seus cartões de crédito em dia ou quase em dia. Isso sugere que a base de clientes, em geral, possui um bom histórico de crédito.
* **Compras (PURCHASES):** A distribuição das compras é semelhante à do saldo, com a maioria dos clientes realizando compras de valor moderado. No entanto, há um grupo menor que realiza compras de alto valor.

* ![k2](https://github.com/user-attachments/assets/4464a690-d372-41b5-9a6f-99eab52d4961)

**podemos extrair os seguintes insights sobre os dados dos clientes de cartão de crédito:**

* **Compras Únicas (ONEOFF_PURCHASES):** A maioria dos clientes realiza compras únicas de baixo valor ou não realiza esse tipo de compra. No entanto, há uma pequena parcela de clientes que realiza compras únicas de alto valor. Isso sugere que a base de clientes é composta principalmente por pessoas que preferem parcelar suas compras ou que fazem compras únicas de menor valor.
* **Compras Parceladas (INSTALLMENTS_PURCHASES):** A distribuição das compras parceladas também é assimétrica, com a maioria dos clientes realizando compras parceladas de menor valor. Um grupo menor, porém significativo, realiza compras parceladas de alto valor. Isso indica que, embora a maioria dos clientes prefira compras menores, existe um mercado para produtos ou serviços mais caros adquiridos por meio de parcelamento.
* **Adiantamentos em Dinheiro (CASH_ADVANCE):** A maioria dos clientes não utiliza a função de adiantamento em dinheiro ou utiliza-a de forma muito moderada. Um grupo menor, porém relevante, realiza adiantamentos em dinheiro de alto valor. Isso sugere que a função de adiantamento em dinheiro é utilizada por uma parcela específica da base de clientes, possivelmente para cobrir despesas emergenciais ou para outros fins.

![k3](https://github.com/user-attachments/assets/c42c88ea-47da-4dc0-b73e-9af0b35df4ec)


podemos extrair os seguintes insights sobre os dados dos clientes de cartão de crédito:**

* **Frequência de Compras (PURCHASES_FREQUENCY):** A distribuição da frequência de compras apresenta dois picos distintos. Isso indica que a base de clientes se divide em dois grupos principais: aqueles que realizam compras com muita frequência e aqueles que realizam compras com pouca frequência ou raramente. 
* **Frequência de Compras Únicas (ONEOFF_PURCHASES_FREQUENCY):** A maioria dos clientes realiza compras únicas de forma esporádica. Um grupo menor, porém significativo, realiza compras únicas com mais frequência. Isso sugere que há uma parcela de clientes que prefere realizar compras únicas de maior valor.
* **Frequência de Compras Parceladas (PURCHASES_INSTALLMENTS_FREQUENCY):** Assim como nas compras únicas, a maioria dos clientes utiliza o parcelamento de forma esporádica. Um grupo menor, porém relevante, utiliza o parcelamento com mais frequência. Isso indica que o parcelamento é utilizado por uma parcela específica da base de clientes, possivelmente para adquirir produtos ou serviços de maior valor.

![k4](https://github.com/user-attachments/assets/fa1b905a-0ac5-4f34-88bf-0ebe89d4d91f)


podemos extrair os seguintes insights sobre os dados dos clientes de cartão de crédito:**

* **Frequência de Transações de Adiantamento em Dinheiro (CASH_ADVANCE_TRX):** A maioria dos clientes realiza poucas ou nenhuma transação de adiantamento em dinheiro. Uma pequena parcela de clientes realiza um número significativamente maior dessas transações. Isso indica que a maioria dos clientes não utiliza essa função com frequência, enquanto um grupo específico utiliza-a de forma mais intensa, possivelmente para cobrir despesas emergenciais ou para outros fins.
* **Frequência de Transações de Compra (PURCHASES_TRX):** A maioria dos clientes realiza um número moderado de transações de compra. No entanto, há uma parcela de clientes que realiza um número muito alto de transações. Isso sugere que a base de clientes é composta por indivíduos com diferentes hábitos de consumo, desde aqueles que realizam compras esporádicas até aqueles que utilizam o cartão de crédito para pagamentos diários.


Recapitulando as informações extraídas dos gráficos anteriores, podemos construir uma visão mais completa do perfil dos clientes:

Frequência e Tipo de Transações
* **Compras:** A maioria dos clientes realiza um número moderado de compras. No entanto, há uma parcela significativa que realiza um número muito maior de transações, indicando um uso mais intensivo do cartão.
* **Compras Únicas:** Uma parcela considerável dos clientes realiza compras únicas, sugerindo que muitos utilizam o cartão para aquisições específicas e não necessariamente para compras do dia a dia.
* **Compras Parceladas:** A frequência de compras parceladas varia, com alguns clientes utilizando essa modalidade com mais frequência do que outros. Isso indica que o parcelamento é uma ferramenta utilizada por diversos perfis de clientes, seja para adquirir produtos de maior valor ou para gerenciar o orçamento.
* **Adiantamentos em Dinheiro:** A maioria dos clientes utiliza pouco ou nada os adiantamentos em dinheiro. No entanto, um grupo específico realiza um número significativamente maior dessas transações, indicando que essa função é utilizada por um público mais específico, possivelmente para cobrir emergências ou outras necessidades financeiras.

Implicações e Oportunidades
* **Segmentação de Clientes:** A análise dos dados revela a existência de diferentes segmentos de clientes, cada um com suas características e necessidades específicas. Isso permite que a empresa desenvolva estratégias de marketing e produtos personalizados para cada grupo.
* **Otimização de Produtos e Serviços:** Ao identificar os produtos e serviços mais utilizados por cada segmento, a empresa pode otimizar sua oferta, oferecendo opções mais atrativas e relevantes.
* **Gestão de Riscos:** A análise da frequência de transações e do uso de adiantamentos em dinheiro pode ajudar a identificar clientes com maior risco de inadimplência, permitindo que a empresa tome medidas preventivas.
* **Oportunidades de Crescimento:** A identificação de segmentos de clientes com alto potencial de consumo pode direcionar os esforços de marketing e vendas para aumentar a receita.

# Análise da Matriz de Correlação

![k9](https://github.com/user-attachments/assets/53d37796-3fb7-4d1e-935b-416c9fa91b99)

intepretaçao do codigo: 
O código calcula a correlação entre as colunas do DataFrame creditcard_df e visualiza essas correlações usando um mapa de calor (heatmap). Isso permite identificar rapidamente quais variáveis estão fortemente relacionadas entre si, seja positiva ou negativamente.

![k7](https://github.com/user-attachments/assets/ab311e2f-5609-406f-b987-8be1eeb90a46)

Correlações Fortes
* **Saldo e Frequência de Pagamento:** Clientes com saldos mais altos tendem a pagar suas contas com mais frequência. Isso indica uma gestão mais ativa da dívida por parte desses clientes.
* **Variáveis Relacionadas a Compras:** As variáveis relacionadas a compras (valor total, compras únicas, compras parceladas e suas respectivas frequências) apresentam fortes correlações entre si. Isso é esperado, pois clientes que gastam mais tendem a realizar mais transações, tanto únicas quanto parceladas.
* **Limite de Crédito e Gastos:** Clientes com limites de crédito mais altos tendem a gastar mais, o que é intuitivo, pois um limite mais elevado oferece mais flexibilidade para realizar compras.

Correlações Moderadas
* **Saldo e Gastos:** Clientes com saldos mais altos tendem a gastar mais, especialmente em compras parceladas. Isso sugere que a dívida pode estar influenciando o comportamento de compra de alguns clientes.
* **Adiantamentos em Dinheiro:** Clientes que utilizam adiantamentos em dinheiro com mais frequência tendem a ter um saldo maior e a realizar mais transações desse tipo.

Correlações Fracas ou Inexistentes
* **Pagamento Integral e Outras Variáveis:** A porcentagem de pagamentos feitos integralmente não apresenta uma forte correlação com a maioria das outras variáveis. Isso indica que a decisão de pagar a fatura integralmente pode ser influenciada por outros fatores não considerados na análise.
* **Tempo de Relacionamento:** A variável "tenure" (tempo de relacionamento com a empresa) apresenta correlações fracas com a maioria das outras variáveis. Isso sugere que a duração do relacionamento com a empresa não é um fator determinante para a maioria dos comportamentos observados.

# Definindo o número de clusters

![k10](https://github.com/user-attachments/assets/d2ea9f79-3b06-467e-9fd9-1c12295669a3)


O Código
O código Python apresentado gera o gráfico do método do cotovelo:

1. **Inicialização do WCSS:** Uma lista vazia `wcss_1` é criada para armazenar os valores do WCSS para cada número de clusters.
2. **Loop:** Um loop itera sobre um intervalo de valores de 1 a 20 (número de clusters).
3. **Criação e Treinamento do Modelo K-means:** Para cada valor de k, um modelo K-means é criado e ajustado aos dados.
4. **Cálculo do WCSS:** O atributo `inertia_` do modelo K-means retorna a soma dos quadrados das distâncias dentro dos clusters. Esse valor é adicionado à lista `wcss_1`.
5. **Plotagem do Gráfico:** Um gráfico de linha é plotado com o número de clusters no eixo x e o WCSS no eixo y.

Analisando o Gráfico do Método do Cotovelo (Elbow Method)

O que é o Método do Cotovelo?
O método do cotovelo é uma técnica utilizada em machine learning para determinar o número ideal de clusters em um algoritmo de clustering, como o K-means. A ideia é encontrar o ponto de inflexão no gráfico da soma dos quadrados das distâncias dentro dos clusters (WCSS - Within-Cluster Sum of Squares) em relação ao número de clusters. Esse ponto de inflexão, que se assemelha a um cotovelo, indica o número ideal de clusters que minimiza a variância intra-cluster e maximiza a variância inter-cluster.

Analisando o Gráfico
O gráfico apresentado mostra a relação entre o número de clusters e o WCSS. Podemos observar que:

* **Tendência Decrescente:** Conforme o número de clusters aumenta, o WCSS diminui. Isso ocorre porque, com mais clusters, os dados são divididos em grupos menores, e a distância média de cada ponto aos seus respectivos centróides tende a diminuir.
* **Ponto de Inflexão:** O gráfico apresenta um ponto de inflexão evidente, que parece ocorrer entre 3 e 4 clusters. A partir desse ponto, a redução do WCSS se torna menos acentuada.

Interpretação e Insights
* **Número Ideal de Clusters:** Com base no gráfico, o número ideal de clusters para este conjunto de dados parece ser **3 ou 4**. A partir desse ponto, adicionar mais clusters não resulta em uma melhoria significativa na qualidade da segmentação.
* **Segmentação dos Dados:** Ao agrupar os dados em 3 ou 4 clusters, espera-se que os pontos dentro de cada cluster sejam mais semelhantes entre si do que os pontos de clusters diferentes. Isso significa que os clientes dentro de cada cluster compartilham características comuns em relação ao seu comportamento de consumo ou outras variáveis relevantes.

## Analisando o Código e os Gráficos de Clusterização

![k11](https://github.com/user-attachments/assets/15adef56-38e1-4265-bc47-3dc1f11edb8d)


O que o Código Faz?

O código Python fornecido realiza uma análise de clusterização utilizando o algoritmo K-means em um conjunto de dados de cartões de crédito. As etapas principais são:

1. **Criação do Modelo K-means:** Um modelo K-means com 8 clusters é criado e ajustado aos dados escalados.
2. **Obtenção dos Rótulos dos Clusters:** Os rótulos dos clusters são atribuídos a cada ponto de dados.
3. **Cálculo dos Centróides:** Os centróides de cada cluster são calculados e transformados de volta para a escala original.
4. **Concatenando Rótulos:** Os rótulos dos clusters são concatenados ao DataFrame original.
5. **Visualização:** Para cada variável numérica no DataFrame, são gerados histogramas para cada um dos 8 clusters, permitindo visualizar a distribuição dos dados em cada cluster.

Interpretação dos Gráficos

Os histogramas gerados pelo código fornecem uma visão detalhada da distribuição das variáveis numéricas em cada um dos 8 clusters. Através deles, podemos identificar padrões e características distintas entre os grupos de clientes.

**Possíveis Insights:**

* **Segmentação de Clientes:** Os clusters representam diferentes segmentos de clientes com comportamentos de consumo distintos. Por exemplo, um cluster pode representar clientes com alto saldo e alta frequência de compras, enquanto outro pode representar clientes com baixo saldo e poucas compras.
* **Características de Cada Cluster:** Analisando os histogramas, podemos identificar as características que definem cada cluster. Por exemplo, um cluster pode ter uma distribuição de idade mais elevada, enquanto outro pode ter uma distribuição de renda mais alta.
* **Anomalias:** A análise dos histogramas também pode ajudar a identificar outliers ou valores atípicos nos dados. Por exemplo, um cluster pode apresentar uma distribuição de gastos com cartão de crédito muito mais dispersa do que os outros clusters.

## Analisando o Gráfico e o Código: Uma Visão Geral
![k12](https://github.com/user-attachments/assets/5f6e425a-acff-4c21-a041-3bb17527791d)
![k13](https://github.com/user-attachments/assets/af62c618-eeb6-4140-aec0-9016994669cf)


**O que o código faz:**

O código fornecido realiza uma análise de clusterização usando o algoritmo K-means em um conjunto de dados de cartões de crédito. As etapas principais são:

1. **Redução de Dimensionalidade com PCA:** O PCA (Análise de Componentes Principais) é aplicado para reduzir a dimensionalidade dos dados para apenas duas dimensões, permitindo uma visualização mais fácil.
2. **Criação do Gráfico de Dispersão:** Um gráfico de dispersão é criado onde cada ponto representa um cliente. A posição do ponto no gráfico é determinada pelos valores das duas primeiras componentes principais (PCA1 e PCA2). A cor de cada ponto indica o cluster ao qual o cliente pertence.

**Interpretação do Gráfico:**

O gráfico gerado nos permite visualizar como os clientes foram agrupados pelo algoritmo K-means. Cada cluster representa um grupo de clientes com características semelhantes. 

* **Separação dos Clusters:** A distância entre os clusters indica o grau de similaridade entre os grupos. Clusters mais distantes tendem a ter características mais distintas.
* **Densidade dos Clusters:** A densidade de pontos dentro de um cluster indica o número de clientes nesse grupo. Clusters mais densos podem representar segmentos de clientes maiores.
* **Outliers:** Pontos isolados podem representar outliers, ou seja, clientes que não se encaixam bem em nenhum dos clusters.

**Insights:**

* **Segmentação de Clientes:** O gráfico mostra como os clientes foram divididos em grupos distintos com base em seus comportamentos de consumo.
* **Visualização da Variabilidade:** A dispersão dos pontos no gráfico revela a variabilidade dos dados dentro de cada cluster e entre os clusters.
* **Identificação de Padrões:** Ao analisar a distribuição dos pontos, podemos identificar padrões e tendências nos dados. Por exemplo, um cluster pode estar concentrado em uma determinada região do gráfico, indicando que os clientes nesse cluster possuem características semelhantes.

![k14](https://github.com/user-attachments/assets/91893a69-bd38-47f1-a246-cf360d982681)


O código define um autoencoder simples que pode ser usado para aprender representações latentes de dados. A representação latente captura as características mais importantes dos dados e pode ser usada para diversas tarefas de aprendizado de máquina.

## Analisando o Código e a Saída do Treinamento do Autoencoder

![k15](https://github.com/user-attachments/assets/1ac262f1-d950-472a-bc1f-a9745a517604)


### Código
O código Python apresentado realiza o treinamento de um autoencoder e plota a curva de aprendizado. Vamos analisar cada parte:

* **Treinamento do Autoencoder:**
  * `autoencoder.fit()`: Essa linha inicia o processo de treinamento do modelo de autoencoder.
  * **Argumentos:**
    * `creditcard_df_scaled, creditcard_df_scaled`: Indica que o modelo será treinado com os mesmos dados de entrada e saída. Essa é uma característica comum em autoencoders, onde o objetivo é reconstruir a entrada original.
    * `epochs=50`: Define o número de iterações sobre o conjunto de dados durante o treinamento.
    * `batch_size=32`: Especifica o tamanho do lote de dados utilizado em cada atualização dos pesos da rede neural.
    * `shuffle=True`: Embaralha os dados a cada época para garantir que o modelo não aprenda padrões específicos da ordem dos dados.
    * `validation_split=0.2`: Reserva 20% dos dados para validação, ou seja, para avaliar o desempenho do modelo em dados que ele não viu durante o treinamento.
    * `verbose=1`: Mostra uma barra de progresso durante o treinamento.

* **Plotagem da Curva de Aprendizado:**
  * `plt.plot()`: Plota a perda (loss) do treinamento e da validação ao longo das épocas.
  * `plt.title()`, `plt.xlabel()`, `plt.ylabel()`: Adicionam título, rótulos dos eixos x e y ao gráfico, respectivamente.
  * `plt.legend()`: Adiciona uma legenda para diferenciar as curvas de treinamento e validação.
  * `plt.grid()`: Adiciona uma grade ao gráfico para facilitar a visualização.

### Saída do Treinamento
A saída do treinamento mostra o progresso do treinamento a cada época, incluindo:

* **Época:** Número da iteração sobre o conjunto de dados completo.
* **Tempo por época:** Tempo gasto para processar uma época.
* **loss:** Perda média do modelo nos dados de treinamento para aquela época.
* **val_loss:** Perda média do modelo nos dados de validação para aquela época.

## Analisando a Curva de Aprendizado do Autoencoder

![k16](https://github.com/user-attachments/assets/d67a55be-2931-4f58-bf03-f0a7a06f3f99)


A imagem apresenta a curva de aprendizado de um autoencoder durante 50 épocas de treinamento. A curva de aprendizado é um gráfico que mostra como a perda (loss) do modelo evolui ao longo do treinamento, tanto nos dados de treinamento quanto nos dados de validação.

**O que a curva nos mostra:**

* **Perda:** A perda é uma métrica que quantifica o erro do modelo ao tentar reconstruir os dados de entrada. Quanto menor a perda, melhor o modelo está aprendendo a representar os dados.
* **Treinamento:** A linha azul representa a perda nos dados de treinamento.
* **Validação:** A linha laranja representa a perda nos dados de validação, que o modelo nunca viu durante o treinamento. Essa curva é crucial para avaliar a capacidade de generalização do modelo.

**Interpretação:**

* **Descida Inicial:** No início do treinamento, a perda tanto de treinamento quanto de validação diminui rapidamente. Isso indica que o modelo está aprendendo as características mais simples dos dados.
* **Estabilização:** Após algumas épocas, a perda de treinamento continua diminuindo, mas a perda de validação se estabiliza ou até mesmo começa a aumentar ligeiramente. Isso é um sinal de que o modelo está começando a memorizar os dados de treinamento em vez de generalizar para novos dados. Esse fenômeno é conhecido como *overfitting*.
* **Generalização:** Um bom modelo deve ser capaz de generalizar para novos dados, ou seja, dados que ele não viu durante o treinamento. A curva de validação nos ajuda a avaliar essa capacidade. Se a perda de validação continuar diminuindo junto com a perda de treinamento, isso indica que o modelo está aprendendo de forma consistente e generalizando bem.

**Insights:**

* **Overfitting:** O gráfico indica que o modelo pode estar sofrendo um leve overfitting a partir de aproximadamente a época 20. Isso significa que o modelo está se ajustando demais aos dados de treinamento e pode ter dificuldade em generalizar para novos dados.
* **Complexidade do Modelo:** A arquitetura do autoencoder, o número de camadas e neurônios, e a complexidade dos dados podem influenciar o grau de overfitting.
* **Regularização:** Técnicas de regularização, como dropout ou L1/L2 regularization, podem ajudar a reduzir o overfitting e melhorar a capacidade de generalização do modelo.
* **Parada Antecipada:** Uma estratégia comum para evitar o overfitting é parar o treinamento quando a perda de validação começar a aumentar. Isso pode ser feito manualmente ou usando callbacks no Keras.

**Conclusão:**

A curva de aprendizado fornece informações valiosas sobre o desempenho do autoencoder. Ao analisar a curva, podemos identificar problemas como overfitting e underfitting e tomar medidas para melhorar o desempenho do modelo. 

## previsao

![k17](https://github.com/user-attachments/assets/9c82103a-77f7-4cfe-8af7-95acce487ddf)

**O que Significa a Representação Compacta?**

* **Redução de Dimensionalidade:** A representação compacta captura as características mais importantes dos dados originais em um espaço de menor dimensão. Isso é útil para visualizar os dados, reduzir a complexidade de modelos subsequentes e identificar padrões nos dados.
* **Novas Características:** As colunas da representação compacta não correspondem diretamente às features originais dos dados. Elas representam combinações complexas das features originais que o autoencoder aprendeu a ser mais relevantes para a tarefa em questão.
* **Interpretação:** A interpretação direta das features da representação compacta pode ser desafiadora, pois elas não possuem um significado intuitivo como as features originais. No entanto, técnicas de visualização e análise podem ajudar a entender como os dados estão sendo agrupados e quais características são mais importantes.

### Insights Valiosos

* **Visualização:** Plotando as features da representação compacta em um gráfico bidimensional ou tridimensional, podemos visualizar como os dados estão agrupados e identificar clusters ou outliers.
* **Análise de Componentes Principais (PCA):** Aplicando PCA à representação compacta, podemos identificar as componentes principais que explicam a maior parte da variância nos dados.
* **Clustering:** Utilizando algoritmos de clustering como K-means ou DBSCAN, podemos identificar grupos naturais nos dados.
* **Classificação:** A representação compacta pode ser utilizada como entrada para modelos de classificação para prever fraudes em cartões de crédito, por exemplo.
* **Anomalia:** Pontos que estão distantes dos outros pontos na representação compacta podem indicar transações fraudulentas ou outliers.


