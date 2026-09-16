Eigen Portfolio Optimization

This project uses Principal Component Analysis (PCA) to find hidden patterns in how a group of stocks move together, builds portfolios from those patterns, tests whether those patterns actually hold up out of sample, and uses AI to explain everything in plain language and write a report automatically.

---

Core Idea

Stocks don't move alone. Many stocks tend to rise and fall together because of shared forces like sector trends, broad market moves, or regional economic conditions. PCA looks at historical price data for a group of stocks and finds these shared movement patterns without being told what to look for. Each pattern it finds is called a principal component, and each one can be turned into its own portfolio made up of the stocks that belong to that pattern — this is called an eigen portfolio.

The main concepts used here are:

- Standardized stock returns
- Covariance matrices, which measure how stocks move relative to each other
- Eigenvalues and eigenvectors, the mathematical building blocks of PCA
- Explained variance, which measures how much of the market's movement each pattern accounts for
- Sharpe ratio, which measures return earned per unit of risk taken

---

What's New in This Version

The first version of this project was a good proof of concept but a weak one to show off: 20 stocks, two months of data, no test of whether the results actually meant anything. This version fixes that with three real upgrades:

1. Bigger, more realistic universe: 60 large-cap stocks (30 US, 30 India) over two full years of data, with the last roughly six months held out as a genuine test set the model never sees while fitting.

2. Component stability check: PCA is fit on a series of rolling three-month windows within the training period, and consecutive windows' top components are compared using cosine similarity. This answers an honest question: is PC1 finding the same real pattern every time, or is it just noise that happens to look like a pattern in one particular window?

3. Out-of-sample backtest: PC1's eigenvector is turned into portfolio weights and applied to the held-out test period's real returns. Its Sharpe ratio is then compared against a naive equal-weighted portfolio over the same period and universe. This is the real test of whether the eigen portfolio is actually a good portfolio, not just a good explanation of past variance.

4. The GenAI layer from before — LLM component interpretation, RAG-grounded anomaly explanations, and an automated report — is kept, and now folds the stability and backtest results directly into the final report so the report is honest about how much to trust its own findings.

---

Project Structure

Eigen-Portfolio/
  PCA_Eigen_Portfolio_GenAI_v2.ipynb   Main notebook (data, PCA, stability check, backtest, GenAI sections)
  README.md                             You're reading it
  data/                                 Historical stock data, if saved locally

---

What the Notebook Covers

- Fetching two years of historical stock data using yfinance across a 60-stock US + India universe
- Computing intraday returns and standardizing them
- Building the covariance matrix and running PCA on it
- Extracting principal components and turning them into eigen portfolios
- Checking whether PC1 and PC2 are stable across rolling time windows, or just noise
- Running an out-of-sample backtest comparing the eigen portfolio against an equal-weighted baseline
- Using an LLM to label and explain each component in plain language
- Retrieving real news and generating grounded explanations for unusual moves
- Automatically generating a written report summarizing all of the above, including whether the stability and backtest results actually support trusting the model

---

Sample Outputs

- A breakdown of how much variance each principal component explains
- A stability score for the top components (cosine similarity across time windows)
- A side-by-side Sharpe ratio comparison: eigen portfolio vs. equal-weighted, on data neither model was fit on
- Plain-English explanations for what each component likely represents
- Short written explanations for unusual moves, backed by real news headlines
- A final markdown report combining everything with an honest executive summary

---

How to Run

1. Clone the repository:

git clone https://github.com/your-username/eigen-portfolio.git
cd eigen-portfolio

2. Install the dependencies:

pip install -r requirements.txt

3. Get a free Google AI Studio API key (needed for the GenAI sections) at aistudio.google.com/apikey.

4. Open the notebook in Jupyter Notebook, VS Code, or Google Colab, and run the cells in order from top to bottom. Fetching 60 tickers over two years takes a few minutes; the notebook will ask for your API key partway through, entered securely and never saved anywhere.

---

Dependencies

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

pip install numpy pandas matplotlib seaborn yfinance scikit-learn langchain langchain-google-genai langchain-community langchain-huggingface langchain-text-splitters faiss-cpu sentence-transformers feedparser

---

Honest Limitations

- Two years of data and 60 stocks is still a modest sample for financial time series. Results should be read as directional evidence, not proof.
- The out-of-sample backtest uses a single train/test split rather than multiple rolling backtests, which would give a more robust estimate.
- No transaction costs, slippage, or rebalancing frequency are modeled — a real trading implementation would need all three.
- News retrieval depends on a free RSS feed, which can miss the actual driving news for a given move.

---

Learn More

- PCA on Wikipedia: en.wikipedia.org/wiki/Principal_component_analysis
- Modern Portfolio Theory: en.wikipedia.org/wiki/Modern_portfolio_theory
- LangChain documentation: python.langchain.com

---

Author

Made by Shretima
