# Eigen Portfolio Optimization

This project uses Principal Component Analysis (PCA) to find hidden patterns in how a group of stocks move together, and then uses those patterns to build portfolios. On top of that, it adds a layer of AI that explains what each pattern means in plain language and writes a report about it automatically.

---

**Core Idea**

Stocks don't move alone. Many stocks tend to rise and fall together because of shared forces like sector trends, broad market moves, or regional economic conditions. PCA looks at historical price data for a group of stocks and finds these shared movement patterns without being told what to look for. Each pattern it finds is called a principal component, and each one can be turned into its own portfolio made up of the stocks that belong to that pattern — this is called an eigen portfolio.

The main concepts used here are:

- Standardized stock returns
- Covariance matrices, which measure how stocks move relative to each other
- Eigenvalues and eigenvectors, the mathematical building blocks of PCA
- Explained variance, which measures how much of the market's movement each pattern accounts for
- Sharpe ratio, which measures return earned per unit of risk taken

---

**What's New: GenAI Layer**

The original project only produced numbers — a table of stocks and weights per component. That's useful for a computer but not easy for a person to read. This project adds three AI-powered pieces on top of the math:

1. Component interpretation: an LLM looks at which stocks are most strongly tied to each pattern and writes a short, plain-English label and explanation for what that pattern likely represents.
2. News-grounded explanations (RAG): when a pattern makes an unusually large move on a specific day, the project fetches real news headlines from that day and asks the AI to explain the move using only that real evidence, so it doesn't guess or make things up.
3. Automatic report generation: everything above gets compiled into one readable report, complete with an AI-written summary at the top.

These are built using LangChain to organize the prompts and connect the pieces together, along with a free embedding model and a vector search tool (FAISS) to power the news retrieval step.

---

**Project Structure**

```
Eigen-Portfolio/
├── PCA_Eigen_Portfolio_GenAI.ipynb     Main notebook (data, PCA, and GenAI sections)
├── README.md                            You're reading it
└── data/                                Historical stock data, if saved locally
```

---

**What the Notebook Covers**

- Fetching historical stock data using yfinance
- Computing intraday returns and standardizing them
- Building the covariance matrix and running PCA on it
- Extracting principal components and turning them into eigen portfolios
- Calculating the Sharpe ratio for each portfolio
- Using an LLM to label and explain each component in plain language
- Retrieving real news and generating grounded explanations for unusual moves
- Automatically generating a written report summarizing all of the above

---

**Sample Outputs**

- A breakdown of how much variance each principal component explains
- Portfolio weights for each component, based on which stocks are most strongly tied to it
- Plain-English explanations for what each component likely represents
- Short written explanations for unusual moves, backed by real news headlines
- A final markdown report combining everything with an executive summary

---

**How to Run**

1. Clone the repository:

```
git clone https://github.com/your-username/eigen-portfolio.git
cd eigen-portfolio
```

2. Install the dependencies:

```
pip install -r requirements.txt
```

3. Get a free Google AI Studio API key (needed for the GenAI sections) at aistudio.google.com/apikey.

4. Open the notebook in Jupyter Notebook, VS Code, or Google Colab, and run the cells in order from top to bottom. The notebook will ask for your API key partway through — it's entered securely and never saved anywhere.

---

**Dependencies**

Core data and math:
- numpy
- pandas
- matplotlib
- seaborn
- yfinance
- scikit-learn

GenAI layer:
- langchain
- langchain-google-genai
- langchain-community
- langchain-huggingface
- langchain-text-splitters
- faiss-cpu
- sentence-transformers
- feedparser

Install everything with:

```
pip install numpy pandas matplotlib seaborn yfinance scikit-learn langchain langchain-google-genai langchain-community langchain-huggingface langchain-text-splitters faiss-cpu sentence-transformers feedparser
```

---

**Learn More**

- PCA on Wikipedia: en.wikipedia.org/wiki/Principal_component_analysis
- Modern Portfolio Theory: en.wikipedia.org/wiki/Modern_portfolio_theory
- LangChain documentation: python.langchain.com

---

**Author**

Made by Shretima
