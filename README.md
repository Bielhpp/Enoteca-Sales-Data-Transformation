Enoteca Sales Data Transformation
Este projeto se concentra na transformação de dados brutos de vendas de uma enoteca, que foram extraídos da plataforma de controle de vendas Bling (https://www.bling.com.br). Os dados extraídos estão desorganizados e requerem limpeza e formatação antes de serem usados para análise ou outras finalidades. Neste repositório, você encontrará o código utilizado para a transformação dos dados usando a linguagem de programação Python e a biblioteca Apache Spark.

Requisitos
Antes de executar o código neste projeto, é necessário ter as seguintes ferramentas e bibliotecas instaladas:

Apache Spark
Pandas
Jupyter Notebook
Certifique-se de que todas as dependências estejam instaladas antes de prosseguir.

Transformação de Dados
Leitura dos Dados
Primeiramente, é necessário ler os dados brutos que foram extraídos da plataforma Bling. O código a seguir faz isso usando o Apache Spark:

python
Copy code
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName('projCasaTardeli').getOrCreate() 
dataCasaTardeli = "/FileStore/tables/CasaTardeli_04_10_23.csv"

data = spark.read.csv(dataCasaTardeli, sep=";", header=True, inferSchema=True)
Limpeza e Formatação
A limpeza e formatação dos dados envolvem várias etapas:

Remoção de linhas desnecessárias
Preenchimento de valores nulos na coluna "Cliente"
Conversão de números em strings para números decimais
Remoção de colunas não desejadas
O código a seguir executa essas operações:

python
Copy code
import pandas as pd

# Converter DataFrame do Spark para um DataFrame do Pandas
df = df.toPandas()

# Setar cliente como nulo se não tiver valor definido
df['Cliente'] = df['Cliente'].str.strip().replace('', pd.NA)

# Completar linhas nulas da coluna "Cliente" com o último valor não nulo
df['Cliente'].fillna(method='ffill', inplace=True)

# Remover última linha
df = df.iloc[:-1]

# Remover linhas onde o produto está nulo
df = df.dropna(subset=['Produto'])

# Converter números em string para decimal
columns_to convert = ['Qtde', 'Preço Médio', 'Valor', 'Frete', 'Desconto', 'Outras despesas', 'Total Venda']
df[columns_to convert] = df[columns_to convert].applymap(lambda x: float(x.replace('.', '').replace(',', '.')))
df = df.drop("Código", axis=1)
Visualização dos Dados
Se necessário, você pode exibir o DataFrame resultante usando Pandas:

python
Copy code
print(df)
Exportação dos Dados
Para facilitar o manuseio em outras ferramentas, os dados transformados são exportados em um arquivo CSV:

python
Copy code
df.to_csv("enoteca.csv", index=True)
Uso
Você pode usar os dados transformados para análise, relatórios ou qualquer outra finalidade desejada.

Contribuições
Contribuições são bem-vindas! Se você encontrar maneiras de melhorar o código ou identificar problemas, sinta-se à vontade para criar uma issue ou enviar um pull request.

Licença
Este projeto é licenciado sob a Licença MIT. Veja o arquivo LICENSE para obter mais detalhes.

Esse README fornece uma visão geral do projeto, das etapas de transformação de dados e dos requisitos necessários. Certifique-se de adaptá-lo ao seu projeto e adicionar qualquer informação adicional relevante.