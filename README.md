# ⚙️ GGTAB / ANVISA — Motor API e Inteligência Artificial (Back-end)

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama_AI-Llama_3.2-000000?style=for-the-badge)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)

Este repositório contém o **Cérebro (Back-end)** da plataforma de fiscalização sanitária da GGTAB. Construído em **FastAPI (Python)**, ele é responsável por processar as requisições do Front-end (Next.js), conectar-se ao banco de dados em nuvem (Supabase), executar a leitura óptica de CNPJs (PyTesseract OCR), gerar documentos oficiais (PDF e Excel) e orquestrar o Motor Jurídico Híbrido com IA Local (Ollama).

---

## 🏗️ Estrutura do Repositório

```text
backend_ggtab/
├── .env.example       # Exemplo de variáveis de ambiente
├── .gitignore         # Arquivos ignorados pelo Git
├── requirements.txt   # Dependências do Python
└── main.py            # Código-fonte principal da API (Rotas e Lógica)

🧠 GGTAB API - Motor Jurídico e Fiscalização Enterprise

Este repositório contém o **Cérebro (Back-end)** da plataforma de fiscalização sanitária da GGTAB. Construído com alta performance utilizando **FastAPI (Python)**, o sistema é responsável por orquestrar toda a lógica de negócio entre o Front-end (Next.js/React), o banco de dados em nuvem e o motor de Inteligência Artificial.

A API atua como um hub central, processando evidências de campo (OCR), salvando operações em tempo real e fornecendo pareceres jurídicos automatizados utilizando IA executada localmente.

🚀 Principais Funcionalidades

- **Motor Jurídico Híbrido (IA Local):** Integração direta com o modelo **Llama 3.2 via Ollama**. A API recebe perguntas dos fiscais, cruza com a base de dados em memória e gera pareceres jurídicos formatados (citando RDCs da ANVISA) sem enviar dados sensíveis para a nuvem.
- **Visão Computacional Avançada (OCR):** Endpoint dedicado para receber fotos de embalagens em Base64 e utilizar o `PyTesseract` para extrair, higienizar e validar números de CNPJ diretamente das imagens.
- **Geração Assíncrona de Documentos:** Endpoints de exportação que compilam os dados das apreensões em tempo real, devolvendo **Planilhas Excel** (separadas por abas) e **Autos de Infração em PDF** (com fotos anexadas e laudos de fundamentação legal).
- **Sincronização em Nuvem (BaaS):** Conexão nativa com o **Supabase** (PostgreSQL) para persistência de dados de produtos customizados, trilha de auditoria (logs) e histórico de operações.
- **Arquitetura Escalável:** Construído com FastAPI e Pydantic, garantindo documentação automática (Swagger/OpenAPI), validação de tipos rigorosa e suporte a requisições assíncronas de alta concorrência.

🛠️ Stack Tecnológico

| Componente | Tecnologia |
| :--- | :--- |
| **Framework Web** | FastAPI (Python) |
| **Inteligência Artificial** | Ollama (Llama 3.2) |
| **Visão Computacional** | PyTesseract, Pillow (PIL) |
| **Banco de Dados** | Supabase (PostgreSQL) |
| **Manipulação de Dados/Docs** | Pandas, FPDF, OpenPyXL |

📦 Como Instalar e Configurar

1. Pré-requisitos
- Python 3.8+
- [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) instalado no sistema operacional (Obrigatório para o endpoint de leitura de CNPJ).
- [Ollama](https://ollama.ai/) rodando localmente com o modelo `llama3.2` baixado.

2. Instalação
Clone o repositório e instale as dependências:
```bash
git clone [https://github.com/seu-usuario/ggtab-api-backend.git](https://github.com/seu-usuario/ggtab-api-backend.git)
cd ggtab-api-backend
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
pip install fastapi uvicorn pandas fpdf pillow supabase pytesseract openpyxl ollama

3. Variáveis de Ambiente
Configure suas credenciais do Supabase no início do arquivo app.py (ou idealmente em um arquivo .env):

Python
SUPABASE_URL = "sua_url_aqui"
SUPABASE_KEY = "sua_chave_aqui"

4. Executando o Servidor
Inicie a API utilizando o Uvicorn:

Bash
uvicorn app:app --reload --host 0.0.0.0 --port 8000
Acesse a documentação interativa (Swagger UI) gerada automaticamente em: http://localhost:8000/docs

🔗 Endpoints Principais
POST /api/ocr-cnpj: Recebe imagem em Base64 e retorna o CNPJ extraído.

POST /api/chat: Envia um prompt para o Motor Jurídico (Ollama) e retorna o parecer técnico.

POST /api/exportar-pdf: Gera o Auto de Apreensão oficial formatado.

POST /api/salvar-operacao: Sincroniza a operação de campo com o Supabase.
