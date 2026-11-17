# agents

Camada de **agentes**: o chat que sugere receitas com o que há na despensa.

## Arquitetura
Um **supervisor** com **dois especialistas independentes**:
- **Inventário:** cuida da despensa. A **leitura de nota é uma tool** dele, e ele faz o papel de **porteiro** (decide o que entra na despensa).
- **Receitas:** busca e sugere receitas usando a busca híbrida de `src/rag`.
- Os especialistas **não conversam entre si**. As **preferências de perfil** (prático ou nutrição) ficam no supervisor.

## O que vai ficar aqui
- Grafo do supervisor e dos especialistas.
- Tools (chamam os serviços de `src/api`, não o banco direto).
- Prompts, versionados e separados da lógica.
- Integração com o LangFuse.
- Conjunto de avaliação dos agentes.

## Ferramentas
- **LangGraph** para o grafo de agentes.
- LLM via **API** (o modelo treinado pelo grupo é o OCR, não o LLM).
- **LangFuse Cloud** (plano gratuito) para rastrear chamadas, latência e custo.
- pytest.

## Métricas
Acerto de roteamento, sucesso das tools, latência, custo e qualidade da resposta (a receita usa só ingredientes da despensa ou aponta o que falta).

## Frente
Multiagente (Pedro e Ângelo).

## Regras
- A chave do LLM só em variável de ambiente.
- Respostas devem deixar claro que o app apoia a decisão e não substitui orientação nutricional.
