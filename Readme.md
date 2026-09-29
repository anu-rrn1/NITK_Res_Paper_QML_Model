# Hybrid Quantum-Classical Sentiment Analysis for only SST-2 Glue (We would like to evaluate on only one dataset, SST-2 Glue.)

## Aim

The aim of this work is to study whether a **hybrid quantum-classical model** can be used for sentiment classification and how its performance compares with classical models. We use the **SST-2 Glue dataset** and convert text embeddings into a small quantum representation before classification.

## Model

The model takes **768-dimensional BERT embeddings** and uses a trainable projection network to reduce them to **8 values**, which are used as inputs to an **8-qubit quantum circuit**. The circuit has **4 variational layers, trainable rotations, and cyclic CZ connections**, followed by a small classical classifier for the final sentiment prediction.

## Workflow

```text
SST-2 Glue Dataset
      ↓
BERT Embeddings
      ↓
Train / Validation / Test Split
      ↓
Standardization
      ↓
Trainable Projection
768 → 128 → 64 → 8
      ↓
8-Qubit Quantum Circuit
4 Variational Layers
      ↓
Pauli-Z Measurements
      ↓
Classical Classifier
8 → 16 → 1
      ↓
Sentiment Prediction
      ↓
SST-2 Glue Predictions
      ↓
SST-2.tsv
```

The model uses only **8 qubits and 96 trainable quantum parameters**, keeping the quantum part small and manageable. The trainable projection reduces the original 768-dimensional embeddings to just 8 values before they are passed to the quantum circuit.
