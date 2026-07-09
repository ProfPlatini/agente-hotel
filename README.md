# Agente Hotel - Travesseiro Nervoso

API de atendimento virtual para o site do Hotel Travesseiro Nervoso. O agente responde dúvidas de clientes sobre quartos, serviços, preços e reservas usando um modelo de linguagem (OpenAI gpt-4o-mini) através do framework Agno.

Slogan do hotel: "Aqui até a insônia dorme"

## Funcionalidades

- Responde perguntas sobre tipos de quarto e preços
- Informa sobre serviços disponíveis no hotel
- Tom de resposta claro e com humor
- API REST simples, pronta para integrar em um site (via CORS liberado)

## Tecnologias

- Python
- Flask
- Flask-CORS
- Agno (orquestração do agente)
- OpenAI gpt-4o-mini
- python-dotenv
- Gunicorn (deploy em produção)

## Pré-requisitos

- Python 3.10+
- Uma chave de API da OpenAI

## Instalação

1. Clone o repositório:
```bash
git clone https://github.com/ProfPlatini/agente-hotel.git
cd agente-hotel
```

2. Crie e ative um ambiente virtual:
```bash
python -m venv .venv
source .venv/bin/activate   # Linux/Mac
.venv\Scripts\activate      # Windows
```

3. Instale as dependências:
```bash
pip install -r requirements.txt
```

4. Crie um arquivo `.env` na raiz do projeto com a sua chave da OpenAI:
```
OPENAI_API_KEY=sua_chave_aqui
```

## Como rodar

```bash
python app.py
```

A API sobe em `http://localhost:8000`.

## Endpoints

### GET /

Testa se a API está no ar.

Resposta:
```json
{
  "mensagem": "API funcionando"
}
```

### POST /chat

Envia uma pergunta para o agente e recebe a resposta.

Corpo da requisição:
```json
{
  "pergunta": "Quanto custa o quarto Deluxe?"
}
```

Resposta:
```json
{
  "resposta": "O quarto Deluxe custa $700 a diária..."
}
```

## Informações que o agente conhece

Quartos:
- Standard: $500
- Deluxe: $700
- Suíte Presidencial: $1000

Serviços:
- Academia
- Café da Manhã
- Lavanderia
- Restaurante
- Piscina

Essas informações estão fixas na descrição do agente em `app.py`. Para adicionar ou alterar quartos, preços e serviços, edite a variável `description` do agente.

## Deploy

O projeto já inclui `gunicorn` nas dependências, pronto para deploy em serviços como o Render.

Exemplo de start command:
```bash
gunicorn app:app
```

Lembre-se de configurar a variável de ambiente `OPENAI_API_KEY` no painel do serviço de hospedagem.

## Estrutura do projeto

```
agente-hotel/
├── app.py              # API Flask com o agente
├── requirements.txt    # Dependências do projeto
└── .gitignore
```
