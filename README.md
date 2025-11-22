# 📝 Long Text Summarizer

A powerful Streamlit-based web application that leverages LangChain and OpenAI to summarize long text documents that exceed ChatGPT's token limits. This application intelligently splits large texts into manageable chunks and uses a map-reduce approach to generate comprehensive summaries.

[![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangChain-0.2.11-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)](https://www.langchain.com/)
[![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com/)

## 🚀 Live Demo

**Try it now:** [https://gdgzhvd43xcvhxtocvdtwx.streamlit.app/](https://gdgzhvd43xcvhxtocvdtwx.streamlit.app/)

## ✨ Features

- 📄 **Long Text Processing**: Handles text documents up to 20,000 words
- 🔄 **Intelligent Text Splitting**: Uses RecursiveCharacterTextSplitter to break down large documents
- 🧠 **Map-Reduce Summarization**: Efficiently summarizes long texts using LangChain's map-reduce chain
- 🔐 **Secure API Key Input**: Password-protected OpenAI API key input
- 📤 **File Upload**: Easy drag-and-drop text file upload interface
- ⚡ **Real-time Processing**: Fast and efficient summarization pipeline

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Streamlit Web Interface                   │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ File Upload  │  │ API Key Input│  │   Summary    │      │
│  │   Handler    │  │   Handler    │  │   Display    │      │
│  └──────┬───────┘  └──────┬───────┘  └──────────────┘      │
└─────────┼──────────────────┼────────────────────────────────┘
          │                  │
          ▼                  ▼
┌─────────────────────────────────────────────────────────────┐
│              LangChain Processing Pipeline                    │
│                                                               │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  1. Text Input Validation (max 20,000 words)        │   │
│  └──────────────────┬──────────────────────────────────┘   │
│                     ▼                                       │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  2. RecursiveCharacterTextSplitter                  │   │
│  │     - Chunk Size: 5000 characters                   │   │
│  │     - Chunk Overlap: 350 characters                 │   │
│  │     - Separators: ["\n\n", "\n"]                    │   │
│  └──────────────────┬──────────────────────────────────┘   │
│                     ▼                                       │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  3. Document Chunks Creation                        │   │
│  └──────────────────┬──────────────────────────────────┘   │
│                     ▼                                       │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  4. Map-Reduce Summarization Chain                  │   │
│  │     - Map: Summarize each chunk individually        │   │
│  │     - Reduce: Combine chunk summaries              │   │
│  └──────────────────┬──────────────────────────────────┘   │
│                     ▼                                       │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  5. OpenAI LLM (GPT Model)                          │   │
│  │     - Temperature: 0 (deterministic)                │   │
│  └──────────────────┬──────────────────────────────────┘   │
│                     ▼                                       │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  6. Final Summary Output                            │   │
│  └─────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

### Architecture Components

1. **Frontend Layer (Streamlit)**
   - User interface for file upload and API key input
   - Real-time display of summarization results
   - Input validation and error handling

2. **Processing Layer (LangChain)**
   - Text splitting and chunking mechanism
   - Document processing pipeline
   - Chain orchestration

3. **LLM Layer (OpenAI)**
   - Language model integration
   - Summarization execution
   - Response generation

## 🛠️ Technology Stack

- **Frontend Framework**: [Streamlit](https://streamlit.io/) - Rapid web app development
- **LLM Framework**: [LangChain](https://www.langchain.com/) - Orchestration and chain management
- **Language Model**: [OpenAI GPT](https://openai.com/) - Text summarization
- **Text Processing**: LangChain RecursiveCharacterTextSplitter
- **Language**: Python 3.11

## 📋 Prerequisites

- Python 3.11
- OpenAI API Key ([Get one here](https://platform.openai.com/api-keys))
- Conda (recommended) or pip

## 🔧 Installation

### Using Conda (Recommended)

```bash
# Create a new conda environment
conda create -n llmapp python=3.11 -y

# Activate the environment
conda activate llmapp

# Install dependencies
pip install -r requirements.txt
```

### Using pip

```bash
# Create a virtual environment (optional but recommended)
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

## 🚀 Usage

1. **Start the Streamlit application:**
   ```bash
   streamlit run main.py
   ```

2. **Access the application:**
   - The app will automatically open in your default web browser
   - Default URL: `http://localhost:8501`

3. **Using the application:**
   - Enter your OpenAI API key in the provided field
   - Upload a `.txt` file containing the text you want to summarize
   - Wait for the processing to complete
   - View your summary in the output section

## 📁 Project Structure

```
streamlit-split-and-summarize/
│
├── main.py                 # Main Streamlit application
├── requirements.txt        # Python dependencies
├── README.md              # Project documentation
└── data.txt               # Sample data file (optional)
```

## 🔑 API Key Setup

1. Visit [OpenAI Platform](https://platform.openai.com/api-keys)
2. Sign up or log in to your account
3. Navigate to API Keys section
4. Create a new secret key
5. Copy the key and paste it into the application

**Note**: Keep your API key secure and never share it publicly. The application uses password input to protect your key.

## ⚙️ Configuration

The application uses the following default settings:

- **Chunk Size**: 5000 characters
- **Chunk Overlap**: 350 characters
- **Max Words**: 20,000 words
- **Temperature**: 0 (for deterministic outputs)
- **Chain Type**: map_reduce

You can modify these settings in `main.py` if needed.

## 📝 Limitations

- Maximum text length: 20,000 words
- Requires active OpenAI API key
- Supports only `.txt` file format
- Processing time depends on document length and API response time

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is open source and available for educational purposes.

## 👤 Author

**MD UZZAL MIA**

## 🙏 Acknowledgments

- [Streamlit](https://streamlit.io/) for the amazing web framework
- [LangChain](https://www.langchain.com/) for the powerful LLM orchestration
- [OpenAI](https://openai.com/) for the language models

---

⭐ If you find this project helpful, please consider giving it a star!
