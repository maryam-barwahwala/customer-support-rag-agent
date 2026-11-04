# AI Customer Support Agent (n8n + RAG)
An AI-powered support agent that reads incoming customer emails, searches company FAQs and policy documents using Pinecone (RAG), and sends professional, accurate replies through Gmail.

## 🎥 Demo
https://github.com/user-attachments/assets/2d44c24d-fdc6-4e94-bc81-4c5fe3693d71

## The Problem
Support teams spend hours answering the same questions. Generic AI replies can also be wrong or invent policies, which is risky when real customers are involved.

## The Solution
This workflow uses RAG so the AI answers only from the company's own knowledge base instead of guessing. Every reply is grounded in the FAQ and policy documents.

## How It Works
1. **Trigger:** the Gmail Trigger checks for new incoming emails (polls every minute)
2. **AI agent:** reads the email and decides what the customer is asking
3. **RAG search:** queries a Pinecone Chat Assistant loaded with FAQ and policy documents, which is the only source of truth for answers
4. **Reply:** the agent drafts a professional response based on the retrieved information
5. **Send:** Gmail sends the reply to the customer

## Key Design Choices
- **Grounded answers:** the agent is instructed to use only the knowledge base, which reduces made-up responses
- **Business-safe:** designed to work with real company documents without relying on the model's general knowledge
- **Reusable:** the same pattern can be adapted for HR, internal operations, and other domains

## Tools Used
n8n, Pinecone (RAG / Chat Assistant), Google Gemini, Gmail

## Repo Contents
- `workflows/n8n-workflow.json`: the exported n8n workflow
- `sample-data/`: sample FAQ and policy documents (fake content for demonstration)
- `docs/`: screenshots of the workflow

## Setup
1. Import `workflows/n8n-workflow.json` into n8n (Workflows > Import from File)
2. Upload the documents in `sample-data/` to your own Pinecone Assistant
3. Connect your own credentials for Gmail, Pinecone, and the AI model
4. Replace placeholders (such as `YOUR_ASSISTANT_NAME`) in the nodes
5. Test by sending an email that matches a question in the sample FAQ

## Notes
- All credentials and company data have been removed. Sample documents are fake.
