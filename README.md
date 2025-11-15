# Link Prediction using Node2Vec — Cora Dataset

Link prediction on the **Cora citation network** using **Node2Vec embeddings** and **Logistic Regression**.  
Includes data preprocessing, negative sampling, edge feature construction, model training, and evaluation with **AUC**, **AP**, **ROC/PR curves**, and **predicted link visualization**.

---

## 🚀 Libraries Used
- **networkx** – graph representation & manipulation  
- **node2vec** – node embedding generation  
- **scikit-learn** – classification & evaluation  
- **torch & torch-geometric** – dataset loading  
- **matplotlib** – visualizations  
- **tqdm** – progress bars  

These libraries support:
- Graph manipulation  
- Node2Vec + Logistic Regression model training  
- Evaluation (AUC, Precision-Recall)  
- Loading the Cora dataset via PyTorch Geometric  

---

## 📥 Loading the Cora Dataset
The Cora citation network contains:
- **Nodes:** research papers  
- **Edges:** citations  

The dataset is loaded using PyTorch Geometric and converted into a NetworkX graph.  
The graph is made **undirected** for simplified link prediction.

**Dataset Summary:**  
# Link Prediction using Node2Vec — Cora Dataset

Link prediction on the **Cora citation network** using **Node2Vec embeddings** and **Logistic Regression**.  
Includes data preprocessing, negative sampling, edge feature construction, model training, and evaluation with **AUC**, **AP**, **ROC/PR curves**, and **predicted link visualization**.

---

## 🚀 Libraries Used
- **networkx** – graph representation & manipulation  
- **node2vec** – node embedding generation  
- **scikit-learn** – classification & evaluation  
- **torch & torch-geometric** – dataset loading  
- **matplotlib** – visualizations  
- **tqdm** – progress bars  

These libraries support:
- Graph manipulation  
- Node2Vec + Logistic Regression model training  
- Evaluation (AUC, Precision-Recall)  
- Loading the Cora dataset via PyTorch Geometric  

---

## 📥 Loading the Cora Dataset
The Cora citation network contains:
- **Nodes:** research papers  
- **Edges:** citations  

The dataset is loaded using PyTorch Geometric and converted into a NetworkX graph.  
The graph is made **undirected** for simplified link prediction.

**Dataset Summary:**  
- **Nodes:** 2708
- **Edges:** 5278

---

## ✂️ Splitting Edges into Train & Test
- Randomly shuffled all edges  
- Split into **80% training** and **20% testing** (positive edges)  
- Constructed a **training graph** using only training edges  

Generated **negative samples** (non-existent edges) for balanced binary classification.

---

## 🔍 Node2Vec Embedding Generation
Trained Node2Vec on the training graph using:

- `dimensions = 128`  
- `walk_length = 20`  
- `num_walks = 100`  

This produced a **128-dimensional embedding** for each node.

Edge-level features were created using the **Hadamard product** of node embeddings.

---

## 🧠 Training Logistic Regression & Evaluation
Trained a binary classifier to predict whether an edge exists.

- **Input:** edge embedding vector  
- **Output:** 1 = link exists, 0 = link does not exist  

**Performance Results:**
- **AUC:** 0.8442  
- **Average Precision:** 0.8783  

These metrics confirm strong predictive performance.

---

## 📊 Graph Visualizations

### 1️⃣ Training Graph (Without Predicted Links)
Shows the structure of the Cora network using a spring layout.

### 2️⃣ Predicted Links Visualization
Top 20 predicted links (highlighted in **red**) showing likely future or missing citations.

---

## 📈 ROC, Precision–Recall, and Confusion Matrix
Includes:
- **ROC Curve**  
- **Precision–Recall Curve**  
- **Confusion Matrix** (threshold: 0.5)

These visualizations help assess classification performance.

---

## 🧮 Graph Metrics (Structural Insights)
Computed from the **largest connected component**:

| Metric | Meaning | Result |
|--------|---------|--------|
| **Average Path Length** | Avg. distance between nodes (*collaboration time*) | **6.9600** |
| **Clustering Coefficient** | Local interconnectedness (*collaboration intensity*) | **0.1823** |

These metrics describe structural patterns in the citation graph.

---

## 🧩 Project Pipeline

| Step | Purpose |
|------|---------|
| 1 | Install & import dependencies |
| 2 | Load Cora dataset |
| 3 | Convert to NetworkX graph |
| 4 | Split edges into train/test |
| 5 | Generate negative samples |
| 6 | Train Node2Vec embeddings |
| 7 | Construct edge feature vectors |
| 8 | Train Logistic Regression model |
| 9 | Evaluate using AUC & AP |
| 10 | Visualize training graph & predicted links |
| 11 | Plot ROC, PR, and confusion matrix |
| 12 | Analyze graph structural metrics |

