

#### Introduction
Support Vector Machines (SVMs) are supervised learning algorithms used for classification and regression. The primary goal of an SVM is to find the optimal hyperplane that separates data points of different classes with the maximum margin.

In many real-world scenarios, data is not linearly separable in its original space. Classical SVMs use the "kernel trick" to map data into a higher-dimensional feature space where a separating hyperplane might exist. However, computing these kernels for large and complex datasets can be computationally expensive.

#### Quantum Support Vector Machines (QSVM)
Quantum Support Vector Machines (QSVMs) leverage quantum computing principles to enhance the classical SVM algorithm. The core idea is to use a quantum computer to map classical data into a high-dimensional quantum Hilbert space, which might uncover patterns that are difficult to find classically.

#### Quantum Feature Mapping
The most significant advantage of a QSVM is its utilization of *Quantum Feature Maps*. A quantum feature map $\phi(\vec{x})$ maps a classical data vector $\vec{x}$ to a quantum state $|\Phi(\vec{x})\rangle$. This mapping is performed using a parameterized quantum circuit known as a data encoding circuit.

By encoding data into quantum states, the quantum computer naturally operates in a Hilbert space whose dimension scales exponentially with the number of qubits.

#### Quantum Kernel Estimation
The quantum kernel is the inner product of the quantum states representing two data points, $\vec{x}_i$ and $\vec{x}_j$:
$$K(\vec{x}_i, \vec{x}_j) = |\langle\Phi(\vec{x}_i)|\Phi(\vec{x}_j)\rangle|^2$$

A quantum computer can estimate this kernel by preparing the states $|\Phi(\vec{x}_i)\rangle$ and $|\Phi(\vec{x}_j)\rangle$, and then applying a specific quantum circuit (like a Swap Test or inversion circuit) followed by measurements. The classical SVM optimization problem then uses this quantum-evaluated kernel matrix to find the support vectors and the optimal hyperplane.

#### How it works 
1.  **Dataset Selection**: We typically start with a non-linear dataset like the XOR dataset, which is a standard benchmark for non-linear classifiers.
2.  **Quantum Feature Mapping**: Choose a quantum circuit architecture (e.g., ZZFeatureMap) to encode the classical data into quantum states. The choice of feature map significantly impacts the performance of the QSVM.
3.  **Kernel Matrix Calculation**: Use the quantum simulator or hardware to calculate the kernel matrix for all pairs of training data points by measuring the fidelity between their corresponding quantum states.
4.  **Training and Classification**: Feed the computed quantum kernel matrix into a classical SVM optimization algorithm (like `scikit-learn`'s SVC) to train the model.
5.  **Visualization**: Display the decision boundaries, margins, support vectors, and evaluate the prediction accuracy to see how well the quantum-enhanced model separates the classes compared to standard classical kernels.