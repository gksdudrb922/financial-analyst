# Financial Analyst

An AI-powered financial advisor system that provides comprehensive stock analysis and investment recommendations using specialized sub-agents for data analysis, financial statement analysis, and news research.

## Overview

Financial Analyst is a multi-agent system built with Google's ADK (Agent Development Kit) that combines three specialized sub-agents to deliver thorough equity analysis:

- **Financial Advisor (Main Agent)**: Orchestrates the analysis and provides investment recommendations
- **Data Analyst**: Gathers market data, company information, pricing, and financial metrics
- **Financial Analyst**: Analyzes detailed financial statements (income, balance sheet, cash flow)
- **News Analyst**: Searches current news and industry information using web scraping

## Features

### Comprehensive Analysis

- Company information and industry classification
- Historical stock price data and current pricing
- Key financial metrics (market cap, P/E ratio, dividend yield, beta)
- Detailed financial statement analysis
- Real-time news and market sentiment research

### Investment Recommendations

- BUY/SELL/HOLD recommendations based on comprehensive analysis
- Customized advice based on user's:
  - Investment goals (growth, income, speculation)
  - Risk tolerance (conservative, moderate, aggressive)
  - Investment timeline (short-term, medium-term, long-term)

### Report Generation

- Executive summaries with clear recommendations
- Fundamental and technical analysis
- News and sentiment analysis
- Risk assessment
- Price targets and action plans
- Generated as markdown artifacts

## Architecture

The system uses a hierarchical agent architecture:

```text
FinancialAdvisor (Main Agent)
├── DataAnalyst (LlmAgent)
│   ├── get_company_info()
│   ├── get_stock_price()
│   └── get_financial_metrics()
├── FinancialAnalyst (Agent)
│   ├── get_income_statement()
│   ├── get_balance_sheet()
│   └── get_cash_flow()
├── NewsAnalyst (Agent)
│   └── web_search_tool()
└── save_advice_report()
```

## Installation

### Prerequisites

- Python >= 3.13
- UV package manager (recommended)

### Setup

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd financial-analyst
   ```

2. Install dependencies using UV:

```bash
uv sync
```

Or using pip:

```bash
pip install -r requirements.txt
```

### Environment Configuration

Create a `.env` file in the root directory with the following required API keys:

```bash
FIRECRAWL_API_KEY=your_firecrawl_api_key_here
```

Additional environment variables may be required for Google ADK and OpenAI configurations.

## Usage

### Basic Usage

```python
from financial_advisor import root_agent

# Run the financial advisor agent
# The agent will interactively gather information and provide recommendations
```

### Agent Capabilities

The Financial Advisor agent can help with:

- Stock ticker analysis and recommendations
- Financial statement interpretation
- Market data gathering
- Current news and sentiment research
- Customized investment advice based on user profile

### Example Workflow

1. **User asks**: "Should I buy Apple stock?"
2. **Agent gathers info**:
   - User's investment goals and risk tolerance
   - Current market data via Data Analyst
   - Financial statements via Financial Analyst
   - Recent news via News Analyst
3. **Agent provides**: Comprehensive BUY/SELL/HOLD recommendation with supporting analysis
4. **Report generated**: Markdown report saved as an artifact

## Project Structure

```text
financial-analyst/
├── financial_advisor/
│   ├── __init__.py
│   ├── agent.py              # Main financial advisor agent
│   ├── prompt.py             # Agent instructions and prompts
│   └── sub_agents/
│       ├── data_analyst.py   # Market data collection agent
│       ├── financial_analyst.py  # Financial statement analysis agent
│       └── news_analyst.py   # News and web research agent
├── tools.py                  # Web search utilities
├── pyproject.toml           # Project configuration and dependencies
└── README.md               # This file
```

## Dependencies

- **google-adk**: Google's Agent Development Kit for building multi-agent systems
- **google-genai**: Google Generative AI models
- **litellm**: LLM abstraction layer supporting multiple providers
- **yfinance**: Yahoo Finance data retrieval
- **firecrawl-py**: Web scraping and content extraction
- **python-dotenv**: Environment variable management

## Development

### Running in Development Mode

```bash
uv run python -m financial_advisor.agent
```

Or with watch mode for development:

```bash
uv run watchdog
```

## Model Configuration

The system currently uses:

- **LLM**: OpenAI GPT-4o (via LiteLLM)
- **Model**: `openai/gpt-4o`

Model configuration can be changed in:

- `financial_advisor/agent.py` (line 11)
- `financial_advisor/sub_agents/data_analyst.py` (line 6)
- `financial_advisor/sub_agents/financial_analyst.py` (line 5)
- `financial_advisor/sub_agents/news_analyst.py` (line 6)

## Scope Limitations

The Financial Advisor has strict scope limitations:

- ✅ Stocks, trading, and investment decisions
- ✅ Financial markets and company analysis
- ❌ General knowledge questions
- ❌ Technology help unrelated to finance
- ❌ Personal advice outside of financial topics

## Limitations

- Requires active API keys for external services (Firecrawl, OpenAI)
- Market data depends on Yahoo Finance availability
- Web search results depend on Firecrawl service
- Financial information accuracy depends on source data quality

## License

License information not specified. Please check with the project maintainers for licensing details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Acknowledgments

Built with Google ADK, utilizing OpenAI GPT-4o for natural language understanding and reasoning.
