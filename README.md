🚀 RAG Inteligente com Pinecone + Gemini + n8n

Sistema de Recuperação de Conhecimento com IA Generativa aplicado a documentos técnicos

🔍 Visão Geral do Projeto

Este projeto é um sistema completo de RAG (Retrieval Augmented Generation) que permite que uma IA responda perguntas com base em documentos reais enviados pelo usuário (PDFs, manuais, relatórios, SOPs, normas internas etc.).

Ele combina:

Pinecone → Banco vetorial para busca por similaridade

Gemini / OpenAI → Modelo generativo para produzir respostas contextualizadas

n8n → Orquestração do fluxo completo

Embeddings → Conversão do texto em vetores

API / Webhook → Canal de comunicação com o usuário

Ideal para:

✔ Suporte técnico interno
✔ Documentação industrial
✔ Chatbots corporativos
✔ Manuais de operação
✔ Assistentes inteligentes especializados
✔ Redução de erros e alucinação

🧠 Arquitetura Geral
[Usuário]
   ↓ envia pergunta (HTTP/Webhook)
[n8n]
   ↓ busca contexto
[Pinecone – vetores]
   ↓ retorna trechos relevantes
[n8n]
   ↓ envia contexto + pergunta
[Gemini / OpenAI]
   ↓ gera resposta com base nos documentos
[n8n]
   ↓ entrega a resposta final

🔧 Tecnologias Utilizadas
Tecnologia	Função
n8n	Automação e orquestração
Pinecone	Banco vetorial
Gemini / GPT-4o	Geração de respostas
Embeddings (OpenAI ou Google)	Vetorização de textos
PDF Extract Node	Extração de conteúdo
HTTP Node	API / Webhook
JavaScript Node	Tratamento de dados
📂 Funcionalidades do Projeto
✔ 1. Upload e indexação automática de documentos

Envio de PDF

Extração de texto

Divisão em chunks

Criação de embeddings

Inserção no Pinecone com metadados (nome, página, trecho)

✔ 2. Chat / API inteligente

O usuário pode enviar perguntas via:

Webhook

API REST

Interface simples (HTML opcional)

Chat interno do n8n

✔ 3. Recuperação contextual inteligente

Busca trechos relevantes no Pinecone

Organiza o contexto

Envia para o modelo generativo

A resposta é construída somente com base no documento

✔ 4. Anti-alucinação

A resposta contém:

Trechos usados

Nome do arquivo

Página

Evidências textuais

📝 Fluxo Completo no n8n

Workflow inclui:

Webhook (entrada de perguntas)

Busca vetorial no Pinecone

Formatação do contexto

LLM (Gemini ou OpenAI)

Retorno em JSON

Logs opcionais em Notion / Sheets

🧪 Demonstração – Exemplo real

Pergunta:

“Qual o procedimento correto para ajustar o equipamento X na etapa Y?”

Resposta gerada:

Procedimento completo

Página do documento

Fonte (nome do PDF)

Trecho usado para justificar a resposta

Informações adicionais

📁 Estrutura recomendada do repositório
📦 rag-n8n-pinecone-gemini
│
├── README.md                ← documentação principal
├── workflow.json            ← export do workflow n8n
├── .env.example             ← exemplo de variáveis
│
├── /docs
│     ├── arquitetura.png
│     ├── diagrama.png
│     └── documentos-exemplo.pdf
│
└── /scripts
      └── preprocess.js

🔑 Variáveis de Ambiente Necessárias

Crie um arquivo .env.example com:

PINECONE_API_KEY=xxxxx
PINECONE_ENVIRONMENT=gcp-starter
PINECONE_INDEX=my-index

OPENAI_API_KEY=xxxxx
GEMINI_API_KEY=xxxxx

N8N_WEBHOOK_URL=https://seu-n8n.cloud/webhook

▶️ Como executar o projeto
1. Importar o workflow

No n8n:
Settings → Workflows → Import

2. Configurar as variáveis

Coloque seu .env ou configure diretamente nos nós.

3. Criar o Index no Pinecone

Dimensão corresponde ao embedding

Namespaces opcionais

4. Executar

Use a URL do webhook para enviar perguntas.

🧑‍💻 Endpoints
POST /ask
Body:
{
  "question": "como ajustar a máquina X?"
}

Resposta:
{
  "answer": "...",
  "sources": [
    {
      "file": "manual.pdf",
      "page": 12,
      "snippet": "..."
    }
  ]
}

🎥 Vídeo Demonstrativo

➡ https://www.linkedin.com/feed/update/urn:li:activity:7385082313673674752/

🚀 Resultados e Impacto

Este projeto demonstra:

Domínio de IA generativa aplicada a negócios

Operação de bancos vetoriais

Construção de automações complexas com n8n

Arquitetura profissional e escalável

Mitigação de alucinação

Uso de modelos avançados (Gemini / OpenAI)

👨‍💻 Autor

MICHAEL DOUGLAS TEOFILO
Especialista em Automação com IA e n8n
LinkedIn: https://www.linkedin.com/in/michael-douglas-automacao-ia/
Portfólio: 
