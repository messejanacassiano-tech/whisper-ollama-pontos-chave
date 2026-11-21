
# Pipeline de Transcrição e Extração de Pontos-Chave (Whisper + Ollama)

Projeto acadêmico desenvolvido no **Google Colab** que automatiza a conversão de áudio, a transcrição de fala em português utilizando **OpenAI Whisper** e a extração dos principais pontos-chave em tópicos usando **Ollama** (`llama3.2`).

---

## 🛠️ Tecnologias e Dependências Utilizadas
* **Google Colab** — Ambiente de execução em nuvem (Python)
* **`zstd`** — Utilitário de descompressão utilizado para extrair o pacote de instalação do Ollama no Linux
* **`ffmpeg`** — Conversão do áudio original (`.m4a`) para `.mp3` e suporte interno de leitura de mídia para o Whisper
* **OpenAI Whisper (`base`)** — Modelo de reconhecimento de fala (*Speech-to-Text*) configurado para o idioma português (`language="pt"`)
* **Ollama (`llama3.2`)** — Modelo de linguagem executado localmente no ambiente para análise e sumarização em pontos-chave

---

## ⚙️ Fluxo do Pipeline
1. **Preparação do Ambiente:** Instalação das dependências do sistema (`ffmpeg` e `zstd`), bibliotecas Python (`openai-whisper` e `ollama`), inicialização do servidor Ollama em segundo plano e download do modelo `llama3.2`.
2. **Conversão e Reprodução do Áudio:** Conversão do arquivo gravado originalmente em `.m4a` para `.mp3` com `ffmpeg` (`audio_teste.mp3`) e exibição de um player nativo no Colab (`IPython.display.Audio`) para audição direta.
3. **Transcrição Automática:** Processamento do `audio_teste.mp3` com o modelo `base` do Whisper para transformar a fala em texto.
4. **Extração de Pontos-Chave:** Envio do texto transcrito para o modelo `llama3.2` via `ollama.chat`, gerando um resumo objetivo em tópicos.

---

## 📂 Arquivos do Repositório
* `whisper-ollama-pontos-chave.ipynb` — Notebook principal com todo o código do pipeline
* `Gravação.m4a` — Arquivo de áudio original utilizado como entrada
* `audio_teste.mp3` — Arquivo convertido via `ffmpeg` e utilizado na transcrição

---

## 🚀 Como Executar no Google Colab
1. Abra o arquivo `whisper-ollama-pontos-chave.ipynb` no **Google Colab**.
2. Execute as células iniciais de instalação (`ffmpeg`, `zstd`, `openai-whisper` e `ollama`) e aguarde o carregamento do modelo `llama3.2`.
3. Faça o upload do arquivo de áudio (`Gravação.m4a` ou `audio_teste.mp3`) na aba lateral **Arquivos** do Colab.
4. Execute em sequência as células de conversão (se partir do `.m4a`), reprodução do player de áudio, transcrição com o Whisper e extração dos pontos-chave com o Ollama.

---

## 💡 Observações Técnicas
* **Escolha do modelo `base` do Whisper:** Foi adotado o modelo `base` por oferecer um excelente equilíbrio entre velocidade de execução e consumo de memória no Google Colab, preservando todo o contexto da fala mesmo quando adapta foneticamente termos técnicos em inglês.
