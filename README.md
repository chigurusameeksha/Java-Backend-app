# **BlueWave Store Demonstration Application**

The **BlueWave Store** is a demonstration application designed to showcase the integration of modern technologies in building a secure, scalable, and user-friendly e-commerce platform. This application is composed of:

- **Java REST API** built using **Spring Boot**
- **Database** for managing product inventory, customer data, and orders
- **React-based shopping cart** for an intuitive user experience
- **NGINX reverse proxy** implementing HTTPS for secure communication
- **Payment gateway** to simulate certificate management and secure transactions

---

## **Requirements**

This example leverages features in **Docker 17.05 CE Edge** or higher. Ensure Docker is installed and configured on your system to run this application successfully.

---

## **Building and Running the BlueWave Store**

### **Secrets Management**

The BlueWave Store uses **Docker secrets** to secure sensitive information, such as certificates and payment gateway credentials. Follow these steps to set up the secrets:

1. **Create Certificates**  
   To secure the reverse proxy, generate a certificate and store it as a secret:
   ```bash
   mkdir certs

   openssl req -newkey rsa:4096 -nodes -sha256 -keyout certs/domain.key -x509 -days 365 -out certs/domain.crt

   docker secret create revprox_cert certs/domain.crt
   docker secret create revprox_key certs/domain.key
   docker secret create postgres_password certs/domain.key


Create Payment Gateway Secret
To set up a secret for staging the payment gateway, run: