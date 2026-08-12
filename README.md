# 🎙️ Assistente de Voz com IA 

*Speech-to-Text + IA Generativa + Text-to-Speech com Whisper, ChatGPT e gTTS*

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-ChatGPT-412991?logo=openai&logoColor=white)
![Whisper](https://img.shields.io/badge/Whisper-Speech--to--Text-412991?logo=openai&logoColor=white)
![gTTS](https://img.shields.io/badge/gTTS-Text--to--Speech-4285F4?logo=google&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google-Colab-F9AB00?logo=googlecolab&logoColor=white)
![Generative AI](https://img.shields.io/badge/Generative%20AI-Voice%20Assistant-8A2BE2)
![DIO](https://img.shields.io/badge/DIO-Bradesco%20GenAI-5A0FC8)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen)

O **Assistente de Voz com IA** é um projeto desenvolvido para explorar a integração
entre **reconhecimento de fala, Inteligência Artificial Generativa e síntese de voz**.

A aplicação captura a entrada de áudio do usuário, realiza a transcrição utilizando
**Whisper**, envia o conteúdo textual para um modelo da OpenAI e converte a resposta
gerada novamente em áudio utilizando **gTTS**.

O resultado é um pipeline conversacional capaz de receber e responder interações
por voz.

---

## 🎯 Objetivo

Construir um assistente conversacional por voz integrando diferentes tecnologias
de IA em um único fluxo.

O projeto explora conceitos relacionados a :

- Speech-to-Text
- Natural Language Processing
- Inteligência Artificial Generativa
- APIs de modelos de linguagem
- Text-to-Speech
- Processamento de áudio
- Engenharia de prompts
- Gerenciamento de contexto
- Interfaces interativas em notebooks

---

## 🧠 Arquitetura

O funcionamento do assistente pode ser representado por :

```text
Usuário
   ↓
🎤 Entrada de Voz
   ↓
Detecção de Silêncio
   ↓
🎧 Áudio
   ↓
Whisper
   ↓
📝 Speech-to-Text
   ↓
ChatGPT
   ↓
🤖 Resposta Generativa
   ↓
gTTS
   ↓
🔊 Text-to-Speech
   ↓
Usuário

```
Essa arquitetura integra três componentes fundamentais:

**Reconhecimento de fala → Inteligência → Síntese de voz**

---

## ✨ Funcionalidades

🎤 Captura de Voz

O sistema permite capturar a fala do usuário utilizando o microfone.

A gravação possui mecanismo de detecção de silêncio para auxiliar no encerramento
automático da captura.

📝 Transcrição com Whisper

O áudio capturado é convertido em texto utilizando **Whisper**.

O projeto permite experimentar diferentes modelos de transcrição de acordo com
os recursos computacionais disponíveis.

🤖 Processamento com IA Generativa

Depois da transcrição, a pergunta é enviada para um modelo da OpenAI.

O histórico da conversa pode ser utilizado para preservar contexto entre
interações sucessivas.

🔊 Síntese de Voz

A resposta textual é convertida novamente em áudio utilizando **Google Text-to-Speech
(gTTS)**.

Isso completa o ciclo de interação por voz.

💾 Cache de Respostas

O projeto implementa um mecanismo de cache para reutilizar determinadas respostas
e reduzir chamadas repetidas ao modelo.

📜 Histórico de Conversa

As interações podem ser mantidas em histórico para preservar contexto durante
a conversa.

🎛️ Interface Interativa

A experiência utiliza **ipywidgets** para disponibilizar controles diretamente
no ambiente do notebook.

---

## 🔄 Pipeline

```text
Microfone
   ↓
Captura de Áudio
   ↓
VAD / Detecção de Silêncio
   ↓
Whisper
   ↓
Transcrição
   ↓
Histórico / Contexto
   ↓
OpenAI
   ↓
Resposta
   ↓
gTTS
   ↓
Áudio
   ↓
Reprodução

```

---

## 🌍 Suporte a Idiomas

A arquitetura permite configurar diferentes idiomas para transcrição e síntese
de voz.

Isso possibilita experimentar o assistente em diferentes cenários linguísticos,
dependendo da configuração utilizada para Whisper e gTTS.

---

## ⚙️ Modelos Whisper

O projeto permite experimentar diferentes tamanhos de modelos Whisper:

- `tiny`
- `base`
- `small`
- `medium`
- `large`

A escolha envolve um trade-off entre :

**Recursos computacionais ↔ velocidade ↔ qualidade da transcrição**

Modelos maiores normalmente demandam mais memória e processamento, enquanto
modelos menores são mais adequados para experimentação rápida.

---

## 🛠️ Tecnologias

**Python** - Linguagem principal

**Whisper** - Reconhecimento e transcrição de fala

**OpenAI API** - Geração das respostas

**gTTS** - Conversão de texto em áudio

**ipywidgets** - Interface interativa

**Google Colab** - Ambiente de desenvolvimento e execução

**JSON** - Armazenamento de informações e histórico

---

## 📂 Estrutura do Repositório

```text
Assistente-de-Voz-com-IA-ChatGPT-Whisper-gTTS/
│
├── Assistente_de_Voz_Multi_Idiomas_com_Whisper_e_ChatGPT.ipynb
└── README.md

```

---

## ▶️ Como Executar

### Pré-requisitos

Para executar o projeto são necessários:

- Google Colab
- Microfone
- Credenciais/API necessárias para utilização do modelo

### Execução

1. Abra o notebook no Google Colab
2. Execute as células de instalação e configuração
3. Configure as credenciais necessárias
4. Execute as células do assistente
5. Autorize o acesso ao microfone
6. Utilize a interface para iniciar uma interação

> Nunca publique chaves de API diretamente no notebook ou no repositório.

---

## 🔐 Segurança das Credenciais

Credenciais e chaves de API devem ser armazenadas utilizando mecanismos seguros,
como variáveis de ambiente ou gerenciamento de secrets.

Nunca utilize :

API_KEY = "minha-chave-real"

em código enviado para um repositório público.

---

## 💡 Competências Demonstradas

- Python
- Inteligência Artificial Generativa
- Speech-to-Text
- Whisper
- Text-to-Speech
- gTTS
- Integração com APIs
- Processamento de áudio
- Natural Language Processing
- Prompt Engineering
- Gerenciamento de contexto
- Cache
- Desenvolvimento em Google Colab
- Integração de componentes de IA

---

## 🚀 Possíveis Evoluções

O projeto pode evoluir para uma arquitetura mais completa de Voice AI :

- Interface web independente do notebook
- Streaming de áudio
- Respostas em tempo real
- Detecção automática de idioma
- Tradução entre idiomas
- Memória conversacional persistente
- Backend com API
- Containerização
- Deploy em Cloud
- Observabilidade
- Avaliação de latência e qualidade
- Arquitetura modular para diferentes provedores de STT, LLM e TTS

Uma evolução arquitetural poderia assumir o formato :

```text
Voz
 ↓
STT
 ↓
LLM
 ↓
Ferramentas / APIs
 ↓
Resposta
 ↓
TTS
 ↓
Voz

```
---

## 🎓 Contexto Acadêmico

Projeto desenvolvido durante o **Bootcamp GenAI — DIO / Bradesco**, no módulo
**Os Pilares Formais da IA**.

O desafio proporcionou uma experiência prática de integração entre tecnologias
de reconhecimento de fala, modelos generativos e síntese de voz.

---

## 🤝 Como Contribuir

Contribuições são bem-vindas, especialmente em áreas relacionadas a:

- Speech-to-Text
- Text-to-Speech
- Voice AI
- Interfaces
- Multilinguismo
- Otimização de latência
- APIs
- Arquitetura de IA

Para contribuir:

1. Faça um Fork do repositório
2. Crie uma branch para sua funcionalidade
3. Implemente e teste as alterações
4. Faça o commit
5. Envie a branch
6. Abra um Pull Request descrevendo a melhoria

---

## 👨‍💻 Autor

**Marcus Guedes**

Marketing | Data Science | Inteligência Artificial | Gestão de Projetos

GitHub: MCLG1661

LinkedIn: Marcus Guedes

---

🎙️ **Transformando voz em texto, texto em inteligência e inteligência novamente em voz.**

## 🙏 Agradecimentos

- OpenAI pelo Whisper e ChatGPT
- Google pelo gTTS
- Comunidade do Google Colab pela infraestrutura
- Prof. Diego Renan Bruno - Bootcamp GenAI DIO/Bradesco - Módulo : OS PILARES FORMAIS DA IA

## Autor

- Marcus Guedes
- Linkedin : https://www.linkedin.com/in/marcusguedes/
- GitHub :  https://github.com/MCLG1661
