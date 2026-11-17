# app

App mobile do gestor de despensa.

## Telas previstas
- **Despensa:** itens que há em casa.
- **Enviar nota:** foto da notinha, enviada ao OCR via API.
- **Validação:** o usuário confere e corrige o rascunho lido antes de entrar na despensa.
- **Chat:** conversa com os agentes de receitas.
- **Perfil:** escolha entre **prático** (tempo e ingredientes, esconde números) e **nutrição** (mostra e filtra por calorias, gordura e açúcar).

## Ferramentas
- **React Native** com **Expo**.
- TypeScript (recomendado).
- Comunicação com a `src/api` pelo contrato OpenAPI.

## Aviso obrigatório na tela
O app apoia a decisão, **não** é aconselhamento nutricional nem garantia de segurança alimentar.

## Como trabalhar sem a API pronta
Use respostas simuladas (mocks) conforme o contrato OpenAPI definido em `src/api`.

## Frente
App (Rodrigo).

## Regras
- Nenhuma chave de API embutida no app.
- Imagens de notas reais nunca vão para o Git.
