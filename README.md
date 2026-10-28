# 🧠 DataMind Studio — Interactive AI & Data Science Workbench

> A client-side, zero-backend interactive web application for exploratory data analysis (EDA), data health profiling, and in-browser machine learning model training & evaluation.

[![Deploy to GitHub Pages](https://img.shields.io/badge/Deploy-GitHub%20Pages-blue?style=flat-square&logo=github)](https://pages.github.com/)
[![Built with JavaScript](https://img.shields.io/badge/Stack-HTML5%20%7C%20Tailwind%20%7C%20Chart.js-indigo?style=flat-square)](https://developer.mozilla.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-emerald?style=flat-square)](LICENSE)

---

## ✨ Project Highlights

Most beginner AI projects are either static calculator forms or Python scripts buried in a terminal. **DataMind Studio** turns foundational Data Science and Machine Learning concepts into **hands-on, visual, interactive tools** that run directly in your web browser with:

- **100% Client-Side Execution**: Zero backend server, zero hosting costs, 0ms network latency. Everything executes locally in the user's browser.
- **GitHub Pages Ready**: Can be pushed directly to GitHub and deployed live with a single toggle.
- **5 Preloaded Iconic Benchmark Datasets**:
  - 🚢 **Titanic Passenger Survival** (Binary Classification)
  - 🏡 **California/Suburban House Prices** (Multivariate Regression)
  - 👥 **Telco Customer Churn** (Imbalanced Classification)
  - 🌸 **Fisher's Iris Flower Species** (Multi-class Classification & Clustering)
  - 🎓 **Student Exam Scores** (Linear Regression)
- **Custom CSV Drag-and-Drop Ingestion**: Parse and profile any custom `.csv` dataset instantly via `PapaParse`.
- **Automated Data Health Engine**: Detects missing value severity, distribution skewness, outliers (via 1.5× IQR), and feature multicollinearity.
- **Interactive 2D Decision Boundary Playground**: Renders real-time spatial decision boundaries for classification algorithms directly on an HTML5 Canvas.
- **"What-If" Scenario Simulator**: Move dynamic sliders to feed custom values into trained models and observe real-time predictions.

---

## 🛠️ System Architecture & Features

```
AI_CASE_STUDY/
├── index.html               # Main dashboard with 6 specialized tabs & responsive UI
├── css/
│   └── style.css            # Dark mode glassmorphism, glowing badges, custom scrollbars
├── js/
│   ├── datasets.js          # Built-in structured datasets (prevents file:// CORS issues)
│   ├── data-engine.js       # Statistical profiler, IQR outlier tests, correlation matrix
│   ├── ml-engine.js         # Linear Regression, KNN, Decision Tree, K-Means & metrics
│   ├── chart-engine.js      # Chart.js renderers, heatmaps, confusion matrices & 2D canvas
│   └── app.js               # Application state, UI events, tab transitions, simulator
├── datasets/
│   ├── sample_housing.csv   # Standalone CSV for testing file upload
│   └── sample_telecom_churn.csv
└── README.md                # Documentation & GitHub Pages deployment guide
```

### 1. Automated Data Profiler (`data-engine.js`)
- Automatic type inference (`numeric` vs `categorical`).
- Descriptive statistics: Mean, Standard Deviation, Median, Min, Max, Q1, Q3, Interquartile Range (IQR).
- Distribution skewness calculation: $Skew = \frac{n}{(n-1)(n-2)} \sum \left(\frac{x_i - \bar{x}}{s}\right)^3$.
- Pearson Correlation Matrix ($r$ between all numerical variable pairs).
- Automated AI "Data Health Score" (0–100%) and heuristic warnings for class imbalance and multicollinearity.

### 2. Machine Learning Arena (`ml-engine.js`)
- **Multiple Linear Regression (OLS)**: Solves $\beta = (X^T X + \lambda I)^{-1} X^T y$ using Gaussian elimination with ridge regularization for numerical stability. Computes $R^2$, MSE, RMSE, and MAE.
- **K-Nearest Neighbors (KNN)**: Classifies test samples based on Euclidean distance voting with configurable $K$ (1 to 15).
- **Decision Tree Classifier (CART)**: Recursively splits features by minimizing Gini Impurity ($1 - \sum p_i^2$). Includes a plain-text syntax tree rule inspector.
- **K-Means Clustering**: Unsupervised iterative centroid convergence with inertia tracking and the **Elbow Method Curve** ($K = 1 \dots 6$).

---

## 🚀 How to Run Locally

You do not need to install Node.js, Python, or any packages to run this project!

### Option A: Direct Open (Simplest)
Double-click `index.html` in your file explorer to open it directly in Google Chrome, Microsoft Edge, Firefox, or Safari.

### Option B: Local Web Server
If you have Python or Node installed, you can start a local development server:

```bash
# Using Node.js (npx)
npx serve .

# OR using Python
python -m http.server 8000
```
Then visit `http://localhost:8000` or `http://localhost:3000`.

---

## 🌐 How to Make the Website Live on GitHub (Step-by-Step)

Follow these steps to deploy DataMind Studio to GitHub Pages:

### Step 1: Create a New GitHub Repository
1. Log in to [GitHub](https://github.com/).
2. Click the **+** (plus icon) in the top right corner $\rightarrow$ select **New repository**.
3. Name your repository (e.g. `ai-datamind-studio` or `data-science-workbench`).
4. Keep it **Public** and leave all checkboxes (README, .gitignore) unchecked.
5. Click **Create repository**.

### Step 2: Push Your Code
Open your terminal or PowerShell in this project folder (`c:\Users\akhil\OneDrive\Desktop\AI_CASE_STUDY`) and run:

```bash
# Initialize git repository
git init

# Stage all files
git add .

# Create initial commit
git commit -m "Initial commit: DataMind Studio AI & Data Science Web App"

# Rename branch to main
git branch -M main

# Link to your remote GitHub repo (replace with your actual GitHub URL)
git remote add origin https://github.com/<your-username>/<your-repo-name>.git

# Push to GitHub
git push -u origin main
```

*(Alternatively, you can drag and drop the folder contents into the GitHub web interface using the "Upload files" button!)*

### Step 3: Enable GitHub Pages
1. Go to your repository on GitHub.
2. Click **Settings** (gear tab near the top).
3. In the left sidebar, click **Pages** (under the "Code and automation" section).
4. Under **Build and deployment**:
   - **Source**: Select `Deploy from a branch`.
   - **Branch**: Select `main` and root `/(root)`.
5. Click **Save**.

🎉 **Your site is now live!** In about 30–60 seconds, GitHub will provide a link like:
`https://<your-username>.github.io/<your-repo-name>/`

---

## 📚 Key Concepts Explained for Beginners

| Concept | What It Does | Why It Matters |
| :--- | :--- | :--- |
| **Pearson Correlation ($r$)** | Measures linear correlation from -1 to +1 | Identifies which features have the strongest predictive link to target outcomes. |
| **$R^2$ Score** | Proportion of variance explained by the model | $R^2 = 0.85$ means 85% of target variance is explained by the input features. |
| **Confusion Matrix** | Breakdown of True/False Positives and Negatives | Shows where a classifier makes errors, beyond simple overall accuracy. |
| **Gini Impurity** | Measure of label mix within a node ($0 = \text{pure}$) | Governs where decision trees choose to make optimal partition splits. |
| **K-Means Inertia & Elbow** | Within-cluster sum of squared distances | The "elbow" marks the optimal cluster count $K$ before diminishing returns. |

---

## 💡 Future Expansion Ideas

If you want to expand this project further to impress recruiters or teachers:
1. **Transformers.js Integration**: Run lightweight sentiment analysis or text embeddings right in the browser using WebAssembly.
2. **PCA (Principal Component Analysis)**: Compute eigenvectors to project high-dimensional datasets down to 2D/3D for visualization.
3. **Model Weights Export**: Let users download their trained linear regression coefficients or decision tree rules as a ready-to-run Python script.

---

## 📄 License
This project is open-source under the [MIT License](LICENSE). Feel free to customize and showcase it in your portfolio!
