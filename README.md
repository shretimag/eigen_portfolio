# 📊 Eigen Portfolio Optimization

Harness the power of PCA and Eigen decomposition for smarter investing.

Welcome to Eigen Portfolio, a data science project that uses **Principal Component Analysis (PCA)** and **eigen decomposition** to create an optimized portfolio of assets. This project explores dimensionality reduction in finance and how eigenvectors and eigenvalues can guide investment strategies.

---

## 🧠 Core Idea

The goal is to analyze historical price data of multiple stocks and extract the principal components that explain the most variance. These components are then used to allocate weights to the assets, forming an optimal portfolio.

Key concepts include:

* **Covariance matrices**
* **Eigenvalues & eigenvectors**
* **PCA in financial markets**
* **Portfolio variance & risk**

---

## 📂 Project Structure

```bash
Eigen-Portfolio/
├── Eigen Portfolio.ipynb     # Main Jupyter notebook
├── README.md                 # You're reading it!
└── data/                     # Historical stock data (if applicable)
```

---

## ⚙️ What the Notebook Covers

* ✅ **Data fetching** using `yfinance`
* ✅ **Log returns** computation
* ✅ **Covariance matrix** and its decomposition
* ✅ **PCA-based portfolio construction**
* ✅ **Eigen portfolio vs equal-weighted portfolio** comparison
* ✅ **Visualization of risk-return tradeoff**

---

## 📈 Sample Outputs

* Scree plot of explained variance
* Portfolio weights based on eigenvectors
* Comparative performance graphs

---

## 🚀 How to Run

1.  **Clone the repo:**

    ```bash
    git clone [https://github.com/your-username/eigen-portfolio.git](https://github.com/your-username/eigen-portfolio.git)
    cd eigen-portfolio
    ```

2.  **Install dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the notebook:**

    Open `Eigen Portfolio.ipynb` in Jupyter Notebook or VSCode and run all cells.

---

## 📦 Dependencies

* `numpy`
* `pandas`
* `matplotlib`
* `yfinance`
* `seaborn`

Install all using:

```bash
pip install numpy pandas matplotlib yfinance seaborn
```

---

## 📚 Learn More

* [PCA on Wikipedia](https://en.wikipedia.org/wiki/Principal_component_analysis)
* [Modern Portfolio Theory](https://en.wikipedia.org/wiki/Modern_portfolio_theory)

---

## 🧑‍💻 Author

Made with ❤️ by Your Name

---

## 📄 License

MIT License – use it freely!
