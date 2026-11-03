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

