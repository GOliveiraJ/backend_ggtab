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

🚀 Passo a Passo de Instalação e Configuração
Siga as etapas abaixo para configurar o banco de dados, a inteligência artificial e rodar o servidor localmente.

Passo 1: Configuração do Banco de Dados (Supabase)
O sistema utiliza o Supabase (PostgreSQL) para persistência em nuvem. Você precisará criar 3 tabelas no seu projeto do Supabase.

Crie uma conta gratuita em supabase.com e crie um novo projeto.

Vá no menu Table Editor e crie as seguintes tabelas (exatamente com estes nomes e colunas de texto):

Tabela 1: apreensoes (Guarda o histórico de fiscalização):

-operacao_id (text)

-data_hora (text)

-fiscal (text)

-loja (text)

-categoria (text)

-tipo (text)

-produto (text)

-cnpj (text)

-status (text)

-quantidade (int8 ou numeric)

-Tabela 2: auditoria (Guarda os logs de monitoramento)

-data_hora (text)

-fiscal (text)

-acao (text)

-detalhes (text)

-Tabela 3: produtos_customizados (Guarda novas marcas inseridas globalmente)

-categoria (text)

-tipo (text)

-produto (text)

-cnpj (text)

-status (text)

No painel do Supabase, vá em Project Settings > API e copie a sua Project URL e a anon public key.

Passo 2: Configuração da IA Local (Ollama)
O Motor Jurídico roda localmente para garantir o sigilo dos dados da ANVISA (zero envio de dados para APIs externas pagas).

Baixe e instale o Ollama.

Abra o seu terminal (Prompt de Comando ou PowerShell) e execute o download do modelo Llama 3.2:

Bash
ollama pull llama3.2
Mantenha o serviço do Ollama rodando em segundo plano (ele roda na porta 11434 automaticamente e o FastAPI se conectará a ele).

Passo 3: Dependências de Visão Computacional (OCR)
Para que o sistema consiga extrair CNPJs das fotos das embalagens:

Instale o Tesseract OCR no seu sistema operacional.

Windows: Baixe o instalador no GitHub oficial do UB-Mannheim e instale. Adicione o caminho do Tesseract nas variáveis de ambiente do Windows, se necessário.

Linux/Mac: sudo apt install tesseract-ocr ou brew install tesseract.

Passo 4: Configurando o Projeto Python
Abra o terminal na pasta backend_ggtab.

(Recomendado) Crie um ambiente virtual:

Bash
python -m venv venv
venv\Scripts\activate      # No Windows
source venv/bin/activate   # No Mac/Linux
Instale as bibliotecas:

Bash
pip install -r requirements.txt
Edite as credenciais no arquivo main.py (ou crie um arquivo .env baseado no .env.example se estiver usando python-dotenv), inserindo as chaves copiadas no Passo 1:

Python
SUPABASE_URL = "[https://SEU-PROJETO.supabase.co](https://SEU-PROJETO.supabase.co)"
SUPABASE_KEY = "SUA-CHAVE-ANON-PUBLICA"
Passo 5: Inicializando o Servidor (Start)
Com tudo configurado, inicie a API do FastAPI na porta 8000:

Bash
python -m uvicorn main:app --reload
A API estará rodando em http://127.0.0.1:8000. O seu Front-end em Next.js (porta 3000) já está configurado para consumir estas rotas automaticamente.

📡 Documentação Interativa da API
O FastAPI gera a documentação automática do Swagger. Com o servidor rodando, acesse no seu navegador:
👉 http://127.0.0.1:8000/docs para testar as rotas de PDF, Excel, OCR e Chat IA diretamente pela interface.

### Para completar a pasta do Backend no seu GitHub:

Apenas para ter certeza de que o repositório do back-end ficará padronizado e limpo como o front, garanta que os seus arquivos complementares de configuração estão assim:

**Arquivo `requirements.txt`:**
```txt
fastapi>=0.115.0
uvicorn[standard]>=0.30.6
pydantic>=2.9.0
supabase>=2.7.0
ollama>=0.3.0
pandas>=2.2.0
openpyxl>=3.1.5
fpdf2>=2.7.9
Pillow>=10.4.0
pytesseract>=0.3.13
python-multipart>=0.0.9

Arquivo .gitignore:
# Python
__pycache__/
*.py[cod]
.venv/
venv/
env/

# Segredos
.env

# Sistema
.DS_Store
Thumbs.db
