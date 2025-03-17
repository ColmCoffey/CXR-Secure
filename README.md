# Privacy-Preserving Federated Learning for COVID-19 Detection

<p align="center">
  <img src="https://github.com/user-attachments/assets/c896af81-706f-4064-a907-6fd1253203e9" alt="image">
</p
This project implements a secure federated learning system for COVID-19 detection using chest X-rays. By leveraging homomorphic encryption and federated learning techniques, we enable collaborative model training across multiple healthcare institutions without compromising patient privacy. The system is built upon the COVID-Net model and optimized for performance in encrypted domains.

## 🔍 Overview

Our privacy-preserving federated learning system allows hospitals to collaborate on training a COVID-19 detection model without sharing sensitive patient data. The project is designed with healthcare privacy compliance in mind, following a defense-in-depth security approach with encrypted model weights, secure communication, and proper access controls.

## 🔧 Features

- Privacy-preserving COVID-19 detection using chest X-rays
- Federated learning across multiple simulated hospitals using AWS EC2 instances
- Homomorphic encryption for secure weight sharing using TenSEAL (CKKS scheme)
- Optimized COVID-Net model for encrypted data processing
- Comprehensive evaluation metrics and benchmarking against published works
- HIPAA considerations built into the design
- Scalable architecture that can start small locally and scale to multi-institution deployment

## 🏗️ Architecture

### Federated Learning Architecture

Our system follows a general federated learning architecture with the following key components:

1. **Local Hospital Environments**: Simulated using AWS EC2 instances
2. **Central Aggregator**: For secure weight aggregation
3. **Homomorphic Encryption Layer**: Using TenSEAL for privacy preservation
4. **COVID-Net CXR Model**: Adapted for encrypted computations

### Federated Learning Process

1. **Model Initialization**: Base COVID detection model created
2. **Local Training**: Hospitals train on local patient data
3. **Secure Aggregation**:
   - Local model updates encrypted using homomorphic encryption
   - Encrypted updates sent to aggregation server
   - Server performs addition on encrypted data
   - Result decrypted and applied to global model
4. **Model Distribution**: Updated global model distributed to hospitals
5. **Iteration**: Process repeats for multiple rounds

### AWS Infrastructure

| Component | AWS Service | Purpose |
|-----------|------------|---------|
| Compute   | EC2 (t3.large) | Model training and aggregation |
| Storage   | S3 with SSE | Model weights, checkpoints |
| Encryption| KMS | Key management for homomorphic encryption |
| Access Control | IAM | Fine-grained permissions |
| Security Groups | EC2 | Network isolation and protection |

### Deployment Topology

- 1 central server EC2 instance for federated aggregation
- Multiple client EC2 instances representing hospital nodes
- S3 bucket for encrypted model exchange
- KMS for encryption key management

## 🚀 Implementation Stages

The project follows a staged implementation approach with clear checkpoints:

1. **Local Prototype** - Simple classification model on medical images
2. **Basic Federated Learning** - Implementation of federated architecture
3. **COVID Detection Model** - Scale up to COVID-19 X-ray images
4. **Privacy Implementation** - Add homomorphic encryption for secure aggregation
5. **AWS Deployment** - Full system deployment with monitoring

## 🔒 Security Features

- **Homomorphic Encryption**: Model weights encrypted with CKKS scheme
- **Server-Side Encryption**: S3 objects protected with AES-256
- **Network Isolation**: Security groups limiting communication
- **IAM Roles**: Principle of least privilege access
- **KMS Integration**: Centralized key management

### Homomorphic Encryption

The project uses the CKKS (Cheon-Kim-Kim-Song) scheme implemented in TenSEAL:

- **Parameters**:
  - Polynomial modulus degree: 8192
  - Coefficient modulus bit sizes: [60, 40, 40, 60]
  - Scale: 2^40

- **Operations**:
  - Encrypted addition of model weights
  - Scale-factor multiplication for averaging

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
```

### Prerequisites

- AWS Account with appropriate permissions
- Python 3.8+
- TensorFlow 2.5+
- TenSEAL 0.3.0+
- Boto3

## 📁 Project Structure

```
cxr-secure-federated/
├── client/                     # Client-side code
│   ├── model.py                # COVID detection model
│   ├── training.py             # Local training logic
│   └── encryption.py           # Encryption utilities
├── server/                     # Server-side code
│   ├── aggregator.py           # Secure aggregation logic
│   └── distribution.py         # Model distribution
├── deployment/                 # AWS deployment resources
│   ├── terraform/              # IaC for AWS resources
│   ├── scripts/                # Deployment scripts
│   └── config/                 # Configuration files
├── data/                       # Sample data (not patient data)
│   └── sample_images/          # Example X-ray images
└── docs/                       # Documentation
    ├── architecture.md         # Detailed architecture
    ├── security.md             # Security considerations
    └── performance.md          # Performance benchmarks
```

## 📈 Results & Performance

### Baseline Results (Covid Net CXR 2 tested on Plaintext)

```
Confusion matrix: 
[[194.   6.]
 [ 17. 183.]]
Sens Negative: 0.970, Positive: 0.915
PPV Negative: 0.919, Positive: 0.968
Accuracy = 94.25%
```


## 📊 Performance Considerations

- **Encryption Overhead**: Benchmarks for homomorphic operations
- **Communication Efficiency**: Minimizing bandwidth usage
- **Model Compression**: Techniques to reduce model size
- **Scaling Strategies**: Horizontal and vertical scaling options

## 🛠️ Technologies Used

- TensorFlow for model implementation
- TenSEAL for homomorphic encryption
- AWS EC2 for simulated hospital environments
- AWS S3 for secure storage
- AWS KMS for key management
- Python for scripting and data processing


## 🤝 Contributing

Contact: coffeycolm@gmail.com

### Contributing Guidelines

- **Submitting Pull Requests**: Follow our code style and include clear descriptions of your changes.
- **Reporting Issues**: Provide detailed information about the issue and steps to reproduce it.
- **Requesting Features**: Clearly explain the feature and its benefits.

## 📜 License

This project is licensed under the [MIT License](LICENSE.md).

## 🙏 Acknowledgments

- COVID-Net project for the initial model architecture
- TenSEAL developers for the homomorphic encryption library
- TensorFlow Federated team
- OpenMined for the TenSEAL library

## 📚 References

1. Wang, L., Lin, Z. Q., & Wong, A. (2020). COVID-Net: A Deep Convolutional Neural Network Design for Detection of COVID-19 Cases from Chest X-Ray Images. Scientific Reports, 10(1), 19549. https://arxiv.org/abs/2003.09871

2. Wood, A., Najarian, K., & Kahrobaei, D. (2020). Homomorphic Encryption for Machine Learning in Medicine and Bioinformatics. ACM Computing Surveys. https://eprint.iacr.org/2023/1320

3. Brand, M., & Pradel, G. (2023). Practical Privacy-Preserving Machine Learning using Fully Homomorphic Encryption. Cryptology ePrint Archive, Paper 2023/1320. https://eprint.iacr.org/2023/1320

---

*This project was developed as part of a research initiative to improve privacy-preserving machine learning in healthcare settings.*
