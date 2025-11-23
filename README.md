🚀 RAG Inteligente com Pinecone + Gemini + n8n

Sistema completo de Recuperação Aumentada por Geração (RAG) aplicado a documentos técnicos, permitindo que uma IA responda perguntas de forma precisa, com base em PDFs reais enviados pelo usuário.

🔍 Visão Geral do Projeto

Este sistema utiliza IA generativa + busca vetorial + automação para criar um assistente inteligente capaz de responder perguntas fundamentadas somente no conteúdo dos documentos.

Ele combina:

Pinecone → Banco vetorial para busca por similaridade

Gemini / OpenAI → Modelo generativo para respostas contextuais

n8n → Orquestração do fluxo completo (ETL + automação)

Embeddings → Conversão de texto em vetores

Webhook / API → Ponto de entrada para perguntas

Ideal para:

✔ Suporte técnico interno
✔ Documentação industrial
✔ Manuais operacionais
✔ Chatbots corporativos
✔ Assistentes especializados em normas internas
✔ Redução de erros e alucinação

🧠 Arquitetura Geral
[Usuário]
   ↓ (pergunta via Webhook)
[n8n]
   ↓ consulta vetorial
[Pinecone]
   ↓ retorna trechos relevantes
[n8n]
   ↓ envia pergunta + contexto
[Gemini / OpenAI]
   ↓ gera resposta fundamentada
[n8n]
   ↓ retorna ao usuário (JSON)

🔧 Tecnologias Utilizadas
Tecnologia	Função
n8n	Automação e orquestração
Pinecone	Banco vetorial
Gemini / GPT-4o	IA generativa
Embeddings OpenAI/Google	Vetorização de textos
PDF Extract Node	Leitura de PDFs
HTTP Node	API / Webhook
JavaScript Node	Pré-processamento e formatação
📂 Funcionalidades do Projeto
✔ 1. Indexação automática de documentos

Upload de PDF

Extração do texto

Divisão em chunks

Criação de embeddings

Armazenamento no Pinecone com metadados:

nome do arquivo

página

trecho original

✔ 2. Chat / API inteligente

Perguntas podem ser enviadas por:

Webhook (padrão)

API REST

Interface simples (opcional)

Chat interno do n8n

✔ 3. Recuperação contextual

Busca vetorial no Pinecone

Organização do contexto

Envio ao modelo generativo

Resposta totalmente baseada no documento

✔ 4. Anti-alucinação

Toda resposta inclui:

Trechos usados

Nome do arquivo

Página

Evidências textuais

📝 Workflow Completo no n8n

O workflow inclui:

Entrada via Webhook

Extração e pré-processamento

Busca vetorial no Pinecone

Montagem do prompt

Geração com Gemini / OpenAI

Resposta final estruturada

(Opcional) logs em Notion / Sheets

🎯 Uma captura do workflow está disponível em:

👉 https://github.com/Michael-MDT22/rag-n8n-pinecone-gemini/blob/main/docs/workflow.png

🧪 Exemplo de Funcionamento

Pergunta:

“Qual o procedimento correto para ajustar o equipamento X na etapa Y?”

Resposta:

Procedimento completo

Página do documento

Nome do PDF

Trecho usado como evidência

Explicação contextual

📁 Estrutura do Repositório
📦 rag-n8n-pinecone-gemini
│
├── README.md              ← documentação principal
├── workflow.json          ← exportação do fluxo n8n
├── .env.example           ← variáveis de ambiente
│
├── /docs
│     ├── workflow.png     ← print do workflow no n8n
│     └── README.md        ← documentação complementar
│
└── /scripts
      └── preprocess.js    ← scripts opcionais

🔑 Variáveis de Ambiente (.env.example)
PINECONE_API_KEY=xxxxx
PINECONE_ENVIRONMENT=gcp-starter
PINECONE_INDEX=my-index

OPENAI_API_KEY=xxxxx
GEMINI_API_KEY=xxxxx

N8N_WEBHOOK_URL=https://seu-n8n.cloud/webhook

▶️ Como Executar o Projeto
1. Importar o workflow

n8n → Settings → Workflows → Import

2. Configurar variáveis

Adicionar .env ou configurar dentro dos nós.

3. Criar o index no Pinecone

Defina:

dimensão dos vetores (de acordo com o embedding)

namespace (opcional)

4. Executar

Envie perguntas para a URL do Webhook.

🧑‍💻 Endpoint
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
      "snippet": "trecho usado..."
    }
  ]
}

🎥 Vídeo Demonstrativo

👉 https://www.linkedin.com/feed/update/urn:li:activity:7385082313673674752/

🚀 Resultados e Impacto

Este projeto demonstra:

Aplicação de IA generativa em casos reais

Automação avançada com n8n

Uso de bancos vetoriais para busca contextual

Implementação de pipelines RAG completos

Arquitetura profissional e escalável

Redução de alucinação em assistentes de IA

👨‍💻 Autor

MICHAEL DOUGLAS TEOFILO
Especialista em Automação com IA e n8n

🔗 LinkedIn:
https://www.linkedin.com/in/michael-douglas-automacao-ia/

🔗 Portfólio (GitHub):
https://github.com/Michael-MDT22
