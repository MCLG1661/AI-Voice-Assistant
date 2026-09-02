# 🎙️ AI Voice Assistant

> Assistente conversacional por voz que integra **Speech-to-Text, Inteligência Artificial Generativa e Text-to-Speech** utilizando Python, Whisper, OpenAI e gTTS.

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-Generative%20AI-412991?logo=openai&logoColor=white)
![Whisper](https://img.shields.io/badge/Whisper-Speech--to--Text-412991?logo=openai&logoColor=white)
![gTTS](https://img.shields.io/badge/gTTS-Text--to--Speech-4285F4?logo=google&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google-Colab-F9AB00?logo=googlecolab&logoColor=white)
![Voice AI](https://img.shields.io/badge/AI-Voice%20Assistant-8A2BE2)
![DIO](https://img.shields.io/badge/DIO-Bradesco%20GenAI-5A0FC8)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen)

---

## 📌 Sobre o Projeto

O **AI Voice Assistant** é um assistente conversacional desenvolvido para explorar a integração entre tecnologias de **processamento de voz e Inteligência Artificial Generativa**.

A aplicação transforma a fala do usuário em texto, processa a solicitação utilizando um modelo de linguagem e converte a resposta novamente em áudio.

O fluxo principal é:

```text
Voz
 ↓
Speech-to-Text
 ↓
Whisper
 ↓
Texto
 ↓
LLM / OpenAI
 ↓
Resposta
 ↓
Text-to-Speech
 ↓
gTTS
 ↓
Voz
```

Além do pipeline principal, o projeto explora recursos como **histórico conversacional, cache de respostas, configuração de idioma, detecção de silêncio e interface interativa**.

---

## 🎯 Objetivo

Construir um protótipo funcional de **Voice AI** integrando diferentes componentes de Inteligência Artificial em um único fluxo conversacional.

O projeto trabalha conceitos relacionados a:

- Speech-to-Text
- Voice AI
- Inteligência Artificial Generativa
- Large Language Models
- Natural Language Processing
- Text-to-Speech
- Processamento de áudio
- Integração com APIs
- Gerenciamento de contexto
- Cache
- Interfaces interativas
- Multilinguismo

---

## 🧠 Arquitetura

```text
┌─────────────────┐
│    Usuário      │
│      🎤         │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Captura de Áudio│
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Detecção de     │
│ Silêncio / VAD  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│     Whisper     │
│ Speech-to-Text  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│      Texto      │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Histórico /     │
│ Contexto / Cache│
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   OpenAI / LLM  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Resposta Textual│
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│      gTTS       │
│ Text-to-Speech  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Resposta em Voz │
│       🔊        │
└─────────────────┘
```

A arquitetura combina três componentes centrais:

**Reconhecimento de fala → Inteligência → Síntese de voz**

---

# ✨ Funcionalidades

## 🎤 Captura de Voz

O sistema permite trabalhar com entrada de áudio do usuário para iniciar o fluxo conversacional.

O projeto inclui configurações relacionadas a:

- tempo máximo de gravação;
- nível de ruído;
- detecção de silêncio;
- controle do processo de captura.

---

## 📝 Speech-to-Text com Whisper

O áudio é convertido em texto utilizando **Whisper**.

A configuração do projeto permite selecionar diferentes modelos:

```text
tiny
base
small
medium
large
```

O notebook utiliza `base` como configuração inicial.

A escolha do modelo envolve um trade-off entre:

```text
Velocidade ↔ Recursos Computacionais ↔ Qualidade da Transcrição
```

---

## 🤖 Inteligência Artificial Generativa

Após a transcrição, o texto pode ser enviado para um modelo da OpenAI.

O histórico conversacional é utilizado para fornecer contexto às interações, permitindo que o assistente considere mensagens anteriores ao produzir novas respostas.

---

## 🔊 Text-to-Speech com gTTS

A resposta textual é convertida novamente em áudio utilizando **Google Text-to-Speech (gTTS)**.

O fluxo completo passa a ser:

```text
Fala do usuário
      ↓
Transcrição
      ↓
Processamento
      ↓
Resposta textual
      ↓
Síntese
      ↓
Resposta falada
```

---

## 🌍 Configuração de Idioma

O projeto permite configurar parâmetros relacionados ao idioma utilizado na transcrição e na síntese.

Exemplo:

```python
CONFIG = {
    "modelo_whisper": "base",
    "idioma": "pt",
    "voz_gtts": "pt-br"
}
```

Essa arquitetura permite experimentar diferentes configurações linguísticas suportadas pelos componentes utilizados.

---

## 📦 Cache de Respostas

O projeto implementa uma classe dedicada ao gerenciamento de cache.

A lógica utiliza um hash da pergunta para identificar respostas previamente armazenadas.

Fluxo:

```text
Pergunta
   ↓
Geração de Hash
   ↓
Existe no Cache?
   │
   ├── Sim → Recupera Resposta
   │
   └── Não → Processa com IA
                  ↓
             Salva no Cache
```

O cache é armazenado em arquivos JSON.

Esse mecanismo pode reduzir chamadas repetidas ao modelo em perguntas idênticas.

---

## 💬 Histórico Conversacional

O projeto implementa gerenciamento de histórico para preservar contexto entre mensagens.

O histórico trabalha com papéis como:

```text
system
user
assistant
```

Também existe controle da quantidade de mensagens preservadas para limitar o contexto utilizado.

O histórico pode ser armazenado em JSON para reutilização posterior.

---

## 🎛️ Interface Interativa

A interface é construída com **ipywidgets** dentro do ambiente de notebook.

Entre os componentes utilizados estão controles para:

- iniciar gravação;
- interromper gravação;
- processar interação;
- exibir pergunta;
- apresentar resposta.

Isso permite experimentar o assistente diretamente no ambiente interativo.

---

## 🔄 Pipeline Completo

```text
Microfone
   ↓
Captura de Áudio
   ↓
Detecção de Silêncio
   ↓
Whisper
   ↓
Speech-to-Text
   ↓
Transcrição
   ↓
Cache
   ↓
Histórico / Contexto
   ↓
OpenAI / LLM
   ↓
Resposta
   ↓
gTTS
   ↓
Text-to-Speech
   ↓
Áudio
   ↓
Usuário
```

---

## 🛠️ Tecnologias

| Tecnologia | Aplicação |
|---|---|
| **Python** | Linguagem principal |
| **Whisper** | Speech-to-Text |
| **OpenAI API** | Processamento generativo |
| **gTTS** | Text-to-Speech |
| **ipywidgets** | Interface interativa |
| **Google Colab** | Ambiente de desenvolvimento |
| **JSON** | Cache e histórico |
| **Git** | Versionamento |
| **GitHub** | Repositório e documentação |

O notebook também utiliza bibliotecas auxiliares para manipulação e processamento de áudio.

---

## 📂 Estrutura do Repositório

```text
AI-Voice-Assistant/
│
├── notebooks/
│   └── ai-voice-assistant.ipynb
│
└── README.md
```

---

# ▶️ Como Executar

## Pré-requisitos

Para executar o projeto são necessários:

- Google Colab ou ambiente compatível;
- microfone;
- acesso às dependências utilizadas;
- credenciais necessárias para utilização da API da OpenAI.

---

### 1. Clone o repositório

```bash
git clone https://github.com/MCLG1661/AI-Voice-Assistant.git
cd AI-Voice-Assistant
```

### 2. Abra o notebook

Utilize:

```text
notebooks/ai-voice-assistant.ipynb
```

O projeto foi estruturado para experimentação em ambiente de notebook.

### 3. Instale as dependências

O próprio notebook contém comandos para instalação das bibliotecas necessárias.

Entre elas:

```text
openai
openai-whisper
gtts
pydub
ipywidgets
sounddevice
numpy
scipy
webrtcvad
```

### 4. Configure a credencial

O notebook utiliza o mecanismo de secrets do Google Colab para recuperar:

```text
OPENAI_API_KEY
```

Configure a credencial antes de executar as funcionalidades que dependem da API.

### 5. Execute as células

Execute o notebook na ordem apresentada para:

```text
Instalar dependências
        ↓
Carregar configurações
        ↓
Inicializar Whisper
        ↓
Configurar cache
        ↓
Configurar histórico
        ↓
Inicializar interface
        ↓
Executar o assistente
```

---

# 🔐 Segurança das Credenciais

Chaves de API **não devem ser armazenadas diretamente no código ou publicadas no GitHub**.

O notebook utiliza:

```python
from google.colab import userdata

openai.api_key = userdata.get("OPENAI_API_KEY")
```

Esse padrão permite manter a credencial fora do código versionado.

Nunca utilize em um repositório público:

```python
API_KEY = "minha-chave-real"
```

---

## 💡 Competências Demonstradas

### Inteligência Artificial

- Generative AI
- Large Language Models
- Natural Language Processing
- Voice AI
- Prompt Engineering
- Context Management

### Speech & Audio

- Speech-to-Text
- Whisper
- Text-to-Speech
- gTTS
- Processamento de áudio
- Detecção de silêncio

### Python

- Classes
- Manipulação de arquivos
- JSON
- Hashing
- Configuração
- Integração de bibliotecas
- Integração com APIs

### Arquitetura

- Pipeline de IA
- Cache
- Histórico conversacional
- Separação de componentes
- Gerenciamento de credenciais
- Interface interativa

---

## 💼 Aplicações Potenciais

A arquitetura demonstrada pode ser utilizada como base conceitual para diferentes soluções.

### Atendimento

```text
Cliente
   ↓
Voz
   ↓
Assistente
   ↓
Resposta
```

### Customer Service

- FAQ por voz;
- triagem inicial;
- atendimento automatizado;
- suporte conversacional.

### Produtividade

- assistentes pessoais;
- consultas por voz;
- captura de informações;
- interfaces hands-free.

### Acessibilidade

Interfaces de voz também podem ampliar possibilidades de interação para cenários em que interfaces tradicionais não são adequadas.

### Empresas

A arquitetura pode evoluir para integrar:

```text
Voz
 ↓
STT
 ↓
LLM
 ↓
CRM / ERP / APIs / Knowledge Base
 ↓
LLM
 ↓
TTS
 ↓
Voz
```

---

## 🚀 Possíveis Evoluções

### Voice AI

- streaming de áudio;
- respostas em tempo real;
- redução de latência;
- interrupção da resposta pelo usuário;
- detecção automática de idioma.

### Inteligência

- RAG;
- memória persistente;
- integração com bases de conhecimento;
- function calling;
- agentes;
- ferramentas externas.

### Arquitetura

- backend com FastAPI;
- API REST;
- WebSocket;
- arquitetura modular;
- containerização com Docker;
- deploy em Cloud.

### Interface

- aplicação web;
- aplicação mobile;
- Streamlit;
- interface independente do notebook.

### Engenharia

- logging;
- observabilidade;
- testes automatizados;
- tratamento de falhas;
- métricas de latência;
- avaliação da qualidade das respostas.

Uma possível evolução arquitetural seria:

```text
Frontend de Voz
       ↓
Streaming
       ↓
Speech-to-Text
       ↓
Orquestrador
       ↓
LLM + RAG + Tools
       ↓
Text-to-Speech
       ↓
Streaming de Áudio
       ↓
Usuário
```

---

## ⚠️ Limitações

Este projeto possui finalidade **educacional e demonstrativa**.

A implementação utiliza um notebook como ambiente principal e não representa uma arquitetura de Voice AI pronta para produção.

Entre as limitações estão:

- dependência do ambiente de notebook;
- ausência de backend dedicado;
- ausência de streaming de áudio em tempo real;
- latência entre as diferentes etapas;
- ausência de observabilidade de produção;
- ausência de testes automatizados;
- dependência de serviços externos para determinadas funcionalidades.

Essas limitações representam também oportunidades naturais para evolução do projeto.

---

## 🎓 Contexto Acadêmico

Projeto desenvolvido durante o **Bootcamp GenAI — DIO / Bradesco**, no módulo **Os Pilares Formais da IA**.

O desafio proporcionou uma experiência prática de integração entre tecnologias de reconhecimento de fala, Inteligência Artificial Generativa e síntese de voz.

**Professor:** Diego Renan Bruno

---

## 🙏 Agradecimentos

- DIO e Bradesco pelo Bootcamp GenAI;
- Prof. Diego Renan Bruno pelo conteúdo do módulo;
- OpenAI pelas tecnologias utilizadas no projeto;
- Google pelo gTTS e ambiente Google Colab.

---

## 👨‍💻 Autor

**Marcus Guedes**

Marketing | Data Science | Inteligência Artificial | Gestão de Projetos

- **GitHub:** [MCLG1661](https://github.com/MCLG1661)
- **LinkedIn:** [Marcus Guedes](https://www.linkedin.com/in/marcusguedes/)

---

⭐ Se este projeto foi útil como referência para Voice AI ou Inteligência Artificial Generativa, considere deixar uma estrela no repositório.

🎙️ **Transformando voz em texto, texto em inteligência e inteligência novamente em voz.**
