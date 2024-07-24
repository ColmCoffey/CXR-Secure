# CXR Secure: Federated Learning for COVID-19 Detection

## ✍️ Author(s) Details

- Colm Coffey MSc

- [LinkedIn](http://linkedin.com/in/colm-coffey/)

- [View Portfolio](https://drive.google.com/file/d/1JEqqHS_o56ehmzYib8gg85UB9U89VczC/view?pli=1)


## 📚 Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Architecture](#architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Technologies Used](#technologies-used)
- [Benchmarks](#benchmarks)
- [Contributing](#contributing)
- [License](#license)
- [Authors](#authors)
- [Acknowledgments](#acknowledgments)
- [References](#references)

## 🌟 Project Overview

This project implements a secure federated learning system for COVID-19 detection using chest X-rays. By leveraging homomorphic encryption and federated learning techniques, we enable collaborative model training across multiple healthcare institutions without compromising patient privacy. The system is built upon the COVID-Net model and optimized for performance in encrypted domains.

## 🔧 Features

- 🛡️ Privacy-preserving COVID-19 detection using chest X-rays
- 🏥 Federated learning across 3 simulated hospitals using AWS EC2 instances
- 🔒 Homomorphic encryption for secure weight sharing using TenSEAL
- ⚡ Optimized COVID-Net model for encrypted data processing
- 📊 Comprehensive evaluation metrics and benchmarking against published works

## 🏗️ Architecture

### Federated Learning Architecture

Our system follows a general federated learning architecture with the following key components:

1. 🏥 Local hospital environments (5 simulated using AWS EC2 instances)
2. 🔗 Central aggregator for secure weight aggregation
3. 🔒 Homomorphic encryption layer using TenSEAL for privacy preservation
4. 🧠 COVID-Net CXR model adapted for encrypted computations

## 🛠️ Installation

```bash
# Clone the repository
git clone https://github.com/ColmCoffey/cxr-secure-federated.git

# Navigate to the project directory
cd cxr-secure-federated

# Install dependencies
pip install -r requirements.txt

# Set up AWS CLI and configure credentials
aws configure



## 📈 Results

### Baseline Results (Covid Net CXR 2 tested on Plaintext)

```
## Test 1

Confusion matrix: 
[[194.   6.]
 [ 17. 183.]]
Sens Negative: 0.970, Positive: 0.915
PPV Negative: 0.919, Positive: 0.968
Accuracy = (True Positives + True Negatives) / (True Positives + True Negatives + False Positives + False Negatives)
Accuracy = 94.25%



## 🛠️ Technologies Used

- TensorFlow for model implementation
- TenSEAL for homomorphic encryption
- AWS EC2 for simulated hospital environments
- Python for scripting and data processing


## 🤝 Contributing

Contact: coffeycolm@gmail.com

Contributing Guidelines

Submitting Pull Requests: Follow our code style and include clear descriptions of your changes.
Reporting Issues: Provide detailed information about the issue and steps to reproduce it.
Requesting Features: Clearly explain the feature and its benefits.


## 📜 License

This project is licensed under the [MIT License](LICENSE.md).


## 🙏 Acknowledgments

- COVID-Net project for the initial model architecture
- TenSEAL developers for the homomorphic encryption library

## 📚 References

1. Wang, L., Lin, Z. Q., & Wong, A. (2020). COVID-Net: A Deep Convolutional Neural Network Design for Detection of COVID-19 Cases from Chest X-Ray Images. Scientific Reports, 10(1), 19549. https://arxiv.org/abs/2003.09871

2. Wood, A., Najarian, K., & Kahrobaei, D. (2020). Homomorphic Encryption for Machine Learning in Medicine and Bioinformatics. ACM Computing Surveys. https://eprint.iacr.org/2023/1320

3. Brand, M., & Pradel, G. (2023). Practical Privacy-Preserving Machine Learning using Fully Homomorphic Encryption. Cryptology ePrint Archive, Paper 2023/1320. https://eprint.iacr.org/2023/1320


---
