# Link-Prediction-using-Node2Vec---Cora-Dataset
Link prediction on the Cora citation network using Node2Vec embeddings and logistic regression. Includes data preprocessing, negative sampling, edge feature construction, model training, and evaluation with AUC, AP, ROC/PR curves, and predicted link visualization.


##	Libraries Used : 
networkx – for graph representation and manipulation
node2vec – for learning embeddings of nodes
scikit-learn – for classification and evaluation
torch & torch-geometric – to load graph datasets
matplotlib – for visualization
 tqdm – for progress bars

These imports bring in all necessary functions for:
•	Graph manipulation
•	Model training (Node2Vec + Logistic Regression)
•	Evaluation (AUC, precision-recall)
•	Dataset handling (Cora via PyTorch Geometric)

##	Loading Cora Dataset : 

Loads the Cora citation network, a classic graph dataset where:
Nodes = research papers
Edges = citations between papers
Converts PyTorch Geometric format to a NetworkX graph.
Makes it undirected to simplify link prediction.

RESULT : 
Nodes: 2708, Edges: 5278

##	Splitting Edges into Train and Test : 
Randomly shuffles all edges.
Splits them into 80% training and 20% testing edges (positive examples).
             Next, builds a train graph with only training edges
Then defines a function to create negative samples (non-existent            edges)
randomly samples pairs of nodes that don’t have edges — these act as negative edges for binary classification.

##	Node2Vec Embedding Generation
Trains a Node2Vec model on the training graph:
dimensions=128: embedding vector size
walk_length=20, num_walks=100: control random walks per node
This produces a 128-dimensional embedding vector for each node.

Used a helper function to get edge-level features (Hadamard product).
Then prepared the Train Test Data by : 
•	Positive and negative edge pairs are converted into features +labels.

##	Training logistic Regression model and evaluation: 
A simple binary classifier is trained:
•	Input: edge embeddings
•	Output: whether an edge exists (1) or not (0)

Evaluation: AUC (Area Under ROC Curve) and Average Precision are calculated to measure link prediction quality.
AUC: 0.8442
Average Precision: 0.8783

##	Visualizing the Training graphs: 

1)	Graph structure without predicted Links : 
 
2)	Visualizing Predicted Links: 
 
Shows top 20 new links (red) predicted by the model — likely new potential connections.

##	ROC , Precision-Recall and Confusion Matrix: 
(a) ROC Curve
(b) Precision–Recall Curve
(c) Confusion Matrix (based on threshold 0.5)

a)	 
b)	 
c)	 

##	Graph Metrices (Interpretation of Graph Structure)
Extracts the largest connected component (since small ones may be isolated).
Calculates:
•	Average Path Length → average “distance” between nodes (collaboration time)
•	Average Clustering Coefficient → how interconnected nodes are (collaboration intensity)
Result: 
	Average Collaboration Time (path length): 6.9600
Average Collaboration Intensity (clustering): 0.1823


Step	Purpose
1	Install & import dependencies
2	Load Cora dataset
3	Convert to NetworkX graph
4	Split edges into train/test
5	Generate negative samples
6	Learn Node2Vec embeddings
7	Build edge feature vectors
8	Train Logistic Regression model
9	Evaluate with AUC & AP
10	Visualize training graph & predicted links
11	Plot ROC, PR, and Confusion Matrix
12	Analyze structural graph metrics

