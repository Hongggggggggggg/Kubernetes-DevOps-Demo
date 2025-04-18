<!-- filepath: /Users/ryan900911/Desktop/Github/Kubernetes-DevOps-Demo/README.md -->
## Microservice Architecture (Click on the image to enlarge)
<img width="919" alt="image" src="https://github.com/user-attachments/assets/7991fa70-dc82-4fff-af3b-7d4591b08e5f" />

#### This project was completed through collaboration among multiple developers. All services listed below can be deployed and tested within this project.

### Developed by me
- **Product-Catalog**: Product catalog service, manages product information  
- **Ad**: Advertising service, manages platform ad delivery  
- **Recommendation**: Product recommendation service, provides personalized recommendations  

### Developed by other developers
- **Cart**: Shopping cart service, handles user cart operations  
- **Checkout**: Checkout process service, handles order generation workflow  
- **Payment**: Payment processing service, handles transactions and payment flows  
- **Shipping**: Shipping service, handles logistics and transportation management  
- **Email**: Email notification service, responsible for system email delivery  
- **Currency**: Currency conversion service, handles multi-currency support  
- **Fraud-Detection**: Fraud detection service, identifies suspicious transactions  
- **Image-Provider**: Image provider service, manages product image resources  
- **Quote**: Quotation service, provides dynamic pricing  
- **Accounting**: Accounting service, handles finances and bookkeeping  
- **React-Native-App**: Mobile frontend service, provides mobile experience
- **Kafka**: Event message queue service, enables inter-service communication  
- **Load-Generator**: Load testing service, simulates user traffic  
- **Prometheus**: Time series database, collects and stores monitoring metrics  
- **Grafana**: Data visualization dashboard, displays system metrics  
- **OTel-Collector**: OpenTelemetry collector, handles telemetry data collection  

---

## Technology Stack

### DevOps Tools
- **Containerization**: Docker  
- **Orchestration**: Kubernetes  
- **Version Control**: Git / GitHub  
- **CI/CD**:  
  - GitHub Actions (Continuous Integration)  
  - Argo CD (Continuous Deployment)

---

## DevOps Process (Click on the image to enlarge)
![DevOps Process-2025-03-29-113549](https://github.com/user-attachments/assets/2a35aaf3-e947-4f18-b3b6-d5b810d2765b)

### This project implements a one-stop CI/CD automation process, from code submission to deployment without manual intervention:
1. **Developer Code Submission**  
   - Push changes to GitHub repository
   - Submit Pull Request 
2. **Trigger GitHub Actions**  
   - Execute code quality checks  
   - Build container images  
   - Push images to container repository  
   - Update Kubernetes Deployment configuration files  
3. **Argo CD Monitor Image Updates**  
   - Detect changes in GitHub repository every three minutes  
   - Automatically update Kubernetes resources and apply new deployment configurations  

---

## Quick Start

### Local Development Environment

1. **Clone Repository**  
   ```bash
   https://github.com/Hongggggggggggg/Kubernetes-DevOps-Demo.git
   cd Kubernetes-DevOps-Demo
   ```
2. **Start Local Environment with Docker Compose**  
   ```bash
   docker-compose up
   ```

### Kubernetes Deployment

1. **Apply Kubernetes Resources**  
   ```bash
   kubectl apply -f kubernetes/complete-deploy.yaml
   ```
2. **Access the Application**  
   ```bash
   kubectl port-forward svc/opentelemetry-demo-frontendproxy 8080:8080
   ```
   Open [http://localhost:8080](http://localhost:8080) in your browser

---

## Code Source

- [opentelemetry.io](https://opentelemetry.io/)
