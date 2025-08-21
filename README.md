# 🤖 AI Blog Generator

A powerful Streamlit application that generates comprehensive, well-researched blog posts on any topic using AI agents powered by CrewAI. The application employs a multi-agent system where specialized AI agents work together to research, analyze, and create high-quality content with proper citations.

![demo](demo/demo.gif)

## 🌟 Features

- **Multi-Agent AI System**: Utilizes specialized AI agents for research and content creation
- **Web Research Integration**: Automatically searches and analyzes web sources for up-to-date information
- **Multiple Export Formats**: Download generated content as Markdown or Word documents
- **Citation Management**: Automatically includes proper source citations and references
- **User-Friendly Interface**: Clean, intuitive Streamlit web interface
- **Customizable Settings**: Adjustable temperature settings for content creativity
- **Professional Formatting**: Well-structured output with headings, bullet points, and proper formatting

## 🔧 Prerequisites

Before running the application, ensure you have:

- Python 3.10 or higher
- API keys for:
  - **Cohere API** (for the Command-R model)
  - **Serper API** (for web search functionality)

## 📦 Installation

1. **Clone the repository** (or save the code file):
   ```bash
   git clone https://github.com/codemaker2015/ai-blog-generator
   cd ai-blog-generator
   ```

2. **Install required dependencies**:
   Install dependencies (using [uv](https://github.com/astral-sh/uv) or pip):  
   ```bash
   uv venv
   .venv\Scripts\activate
   uv sync
   ```
   or 
   ```
   pip install streamlit crewai crewai-tools python-docx python-dotenv
   ```

3. **Set up environment variables**:
   
   Create a `.env` file in the project root directory and add your API keys:
   ```env
   COHERE_API_KEY=your_cohere_api_key_here
   SERPER_API_KEY=your_serper_api_key_here
   ```

   **How to get API keys:**
   - **Cohere API Key**: Visit [Cohere's website](https://cohere.ai) and sign up for an account
   - **Serper API Key**: Visit [Serper.dev](https://serper.dev) and create an account

## 🚀 Usage

1. **Start the application**:
   ```bash
   streamlit run main.py
   ```

2. **Access the web interface**:
   Open your browser and navigate to `http://localhost:8501`

3. **Generate content**:
   - Enter your desired topic in the text area
   - Optionally adjust the temperature setting in the sidebar (higher = more creative)
   - Click "Generate Content" and wait for the AI agents to work
   - Download your generated article as Markdown or Word document

## 🤖 How It Works

The application uses a two-agent system powered by CrewAI:

### Agent 1: Senior Research Analyst
- **Role**: Conducts comprehensive web research on the given topic
- **Capabilities**: 
  - Searches for recent developments and news
  - Identifies key industry trends and innovations
  - Gathers expert opinions and statistical data
  - Evaluates source credibility and fact-checks information
- **Output**: Structured research brief with verified facts and citations

### Agent 2: Content Writer
- **Role**: Transforms research findings into engaging blog posts
- **Capabilities**:
  - Maintains factual accuracy while creating readable content
  - Balances informative and entertaining writing
  - Incorporates proper citations and formatting
  - Structures content with clear headings and sections
- **Output**: Polished blog post in markdown format with inline citations

## 🔄 Workflow

1. **User Input**: Enter topic and configure settings
2. **Research Phase**: Senior Research Analyst searches and analyzes web sources
3. **Content Creation**: Content Writer transforms research into engaging blog post
4. **Output Generation**: Article is formatted and made available for download
5. **Export Options**: Download as Markdown (.md) or Word (.docx) format

## ⚙️ Configuration Options

- **Temperature**: Controls creativity level (0.0 = conservative, 1.0 = very creative)
- **Model**: Currently uses Cohere's Command-R model
- **Search Results**: Configured to retrieve top 10 search results per query

## 📄 Output Features

### Markdown Format
- Proper heading hierarchy (H1, H2, H3)
- Bullet points and numbered lists
- Inline hyperlinks to sources
- References section at the end

### Word Document Format
- Professional document formatting
- Clickable hyperlinks (excluding "Source:" references)
- Styled headings and lists
- Proper paragraph spacing

## 🛠️ Customization

### Adding New Models
To use different LLM models, modify the `LLM` configuration in the `generate_content()` function:

```python
llm = LLM(
    model="your-preferred-model",
    temperature=temperature
)
```

### Modifying Agent Behavior
Customize agent roles, goals, and backstories in the agent definitions to change their behavior and output style.

### Adjusting Search Parameters
Modify the `SerperDevTool` configuration to change the number of search results:

```python
search_tool = SerperDevTool(n_results=15)  # Increase search results
```

## 📋 Dependencies

```
streamlit>=1.28.0
crewai>=0.22.0
crewai-tools>=0.1.6
python-docx>=0.8.11
python-dotenv>=1.0.0
```

## 🔗 Useful Links

- [CrewAI Documentation](https://docs.crewai.com/)
- [Streamlit Documentation](https://docs.streamlit.io/)
- [Cohere API Documentation](https://docs.cohere.ai/)
- [Serper API Documentation](https://serper.dev/api-key)

## 💡 Tips for Best Results

1. **Be Specific**: More specific topics generally yield better results
2. **Current Topics**: The system works best with topics that have recent online coverage
3. **Adjust Temperature**: Lower temperatures for factual content, higher for creative writing
4. **Review Output**: Always review generated content for accuracy and relevance
5. **Citations**: Check that all important claims are properly cited