# ocr

Modelo que lê a foto da notinha e devolve os itens em **JSON** (imagem para JSON).

## O que vai ficar aqui
- **Esquema do JSON** da nota (issue S1-10).
- **Gerador de notas sintéticas:** um LLM gera o JSON e um renderizador desenha a imagem, com variações (fonte, ruído, borrão, inclinação).
- **Divisão** do dataset em treino, validação e teste.
- **Notebooks/scripts de treino** (fine-tuning no Colab ou Kaggle, executado manualmente).
- **Avaliação:** acerto por campo e fração de notas 100% corretas, **sintético e real separados**.
- Código de inferência usado pela API.

## Ferramentas
- Candidato de modelo: **Donut** (visão para texto estruturado).
- **LoRA** (fine-tuning leve, sem GPU local). Não treinamos do zero.
- Hugging Face Transformers e PEFT, PyTorch.
- Colab ou Kaggle para treinar.
- Pillow (ou similar) para renderizar as notas.

## Planejamento do treino
- Primeiro treino com 2 a 3 mil notas sintéticas.
- Curva de aprendizado com 500, 1.000 e 2.000.
- Teste rápido inicial (S1-11): o Donut aprende o formato com 50 notas?

## Dados que NÃO entram no Git
- **Notas reais** (cerca de 20, borradas): só teste, resultado indicativo, **nunca** em treino. Ficam fora do repositório.
- **Dataset sintético e pesos**: fora do Git, versionados (issue S2-02). Já cobertos pelo `.gitignore`.

## Frente
OCR (Matheus e Ângelo).
