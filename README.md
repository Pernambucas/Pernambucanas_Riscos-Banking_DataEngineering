# Apresentação de Estágio na Squad de Ciência de Dados - Pernambucanas

## 1. Introdução
- **Nome:** Thiago Tavares, Sergio Ricardo e Vincenzo
- **Equipe:** Squad Riscos e Banking (TRIBO)

## 2. Papel da Squad de Ciência de Dados
- Objetivo: Utilizar dados para obter insights valiosos e apoiar a tomada de decisões estratégicas do time de Negócios.
- Principais responsabilidades:
  - Análise de dados
  - Tratamento de dados
  - Criação de Dashboards com dados tratados

## 3. Fluxo de Trabalho
- **Engenheiro de Dados:**
  - Define a lógica dos processos
- **Estagiário de Ciência de Dados:**
  - Implementa a lógica usando PySpark no ambiente Zeppelin

## 4. Ambiente de Trabalho e Ferramentas
- **Ferramentas:**
  - **Citrix:** Para se conectar aos softwares da Pernambucanas (Impala, Hue) e 2RP (Zeppelin)
  - **Impala e Hue:** Para acessar e consultar os dados
  - **Zeppelin:** Para desenvolvimento e execução de código PySpark, conectado ao Impala e Hue
  - **Spark:** Instalado no ambiente Zeppelin para processamento de dados
- **Processo:**
  - Acesso aos bancos de dados via Citrix
  - Seleção dos DataFrames
  - Tratamento de dados e seleção de colunas importantes

## 5. Exemplo de Processo de Tratamento de Dados

### Passos da Demonstração ao Vivo:
1. **Iniciar a SparkSession:**
    ```python
    from pyspark.sql import SparkSession
    spark = SparkSession.builder \
        .appName("Exemplo de Tratamento de Dados") \
        .getOrCreate()
    ```

2. **Ler dados de uma tabela do Impala:**
    ```python
    df = spark.read.format("jdbc") \
        .option("url", "jdbc:impala://<impala_host>:<impala_port>/<database>") \
        .option("dbtable", "<tabela>") \
        .option("user", "<usuario>") \
        .option("password", "<senha>") \
        .load()
    ```

3. **Selecionar colunas importantes:**
    ```python
    df_selecionado = df.select("coluna1", "coluna2", "coluna3")
    ```

4. **Renomear colunas:**
    ```python
    df_renomeado = df_selecionado.withColumnRenamed("coluna1", "nova_coluna1")
    ```

5. **Converter tipos de dados:**
    ```python
    df_convertido = df_renomeado.withColumn("nova_coluna1", col("nova_coluna1").cast("Integer"))
    ```

6. **Mostrar o resultado final:**
    ```python
    df_convertido.show()
    ```

## 6. Desafios e Soluções
- **Desafios:**
  - Integração de diferentes fontes de dados
  - Tratamento de grandes volumes de dados
- **Soluções:**
  - Colaboração constante com o engenheiro de dados
  - Utilização eficiente das ferramentas disponíveis (Impala, Hue, Zeppelin)

## 7. Resultados e Impacto
- **Resultados Significativos:**
  - Otimização de processos de tratamento de dados
  - Insights valiosos para a tomada de decisões estratégicas
- **Impacto no Negócio:**
  - Melhoria na eficiência operacional
  - Suporte à inovação e crescimento

## 8. Conclusão e Próximos Passos
- **Resumo:**
  - Papel na equipe
  - Ferramentas e processos utilizados
  - Resultados alcançados
- **Próximos Passos:**
  - Aderir ao Bitbucket para versionamento de código
  - Implementar Airflow hospedado no GCP para orquestração de workflows
  - Continuar aprimorando as habilidades em PySpark
  - Participar de novos projetos desafiadores
