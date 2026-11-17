# airflow

Orquestração dos pipelines de dados com **Apache Airflow**.

## DAGs previstas
1. `ingestao_receitas`: carrega e padroniza as receitas.
2. `enriquecimento_receitas`: nutrição (TBCA), culinária, categoria e tempo de preparo.
3. `geracao_notas_sinteticas`: gera notas sintéticas em lote e **termina publicando a versão do dataset**. O LLM aqui é uma chamada em lote, **não** é um agente.
4. `qualidade_ocr`: mede a qualidade do OCR.

O **treino do OCR é manual** (Colab ou Kaggle), não é uma DAG.

## O que vai ficar aqui
- Pasta `dags/` com as definições das DAGs (só orquestração).
- A lógica de cada tarefa em **funções Python testáveis**, para rodar sem o Airflow. A DAG só chama essas funções.
- Configuração do Airflow para Docker Compose (issue S1-07).

## Ferramentas
- Apache Airflow em Docker Compose.
- PostgreSQL (o mesmo do projeto).
- pytest para testar as funções das tarefas.

## Requisito de máquina
O Airflow em Docker pede 4 a 8 GB de RAM. Ele roda no Mac do Ângelo e no notebook do Matheus. Quem tem menos memória desenvolve as funções e valida o Airflow numa dessas máquinas.

## Princípios
- Tarefas **idempotentes**: rodar duas vezes dá o mesmo resultado.
- Sem segredos nas DAGs; use variáveis e conexões do Airflow.

## Frente
Engenharia de Dados (Yan). Ambiente: Ângelo.
