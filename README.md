# Python Deploy Automation

![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)

## About The Project

Python Deploy Automation is a proof-of-concept project demonstrating **Infrastructure as Code (IaC)** principles. It automates the provisioning, configuration, and deployment of a Python Flask web application using Ansible.

Instead of manual server configuration, this project uses a playbook to automatically setup the environment, install dependencies, configure security (firewall), and launch the application.

### Built With

*   **Automation**: Ansible
*   **Application**: Python, Flask
*   **Security**: UFW (Uncomplicated Firewall)

## Getting Started

To get this automation running, follow these steps.

### Prerequisites

*   **Ansible** installed on your control node (your machine).
*   **SSH Access** to the target server(s).
*   Target server running a Debian-based Linux (e.g., Ubuntu).

### Installation & Usage

1.  **Clone the repository**
    ```sh
    git clone https://github.com/your_username/python-deploy-automation.git
    cd python-deploy-automation
    ```

2.  **Configure Inventory**
    Edit the `ansible/inventory.ini` file to include your target server's IP address:
    ```ini
    [web_servers]
    your_server_ip ansible_user=root
    ```

3.  **Run Deployment**
    Execute the Ansible playbook to provision the server and deploy the app:
    ```sh
    cd ansible
    ansible-playbook -i inventory.ini deploy.yml
    ```

4.  **Verify Deployment**
    Open your browser and navigate to:
    `http://your_server_ip:5000`
    You should see the message: "Automation successful."

## Features

*   **Automated Provisioning**: Updates system packages and installs Python/Pip.
*   **Dependency Management**: Automatically installs Flask and other required libraries.
*   **Security Configuration**: Configures UFW firewall to allow SSH (22) and App (5000) traffic.
*   **Background Execution**: Deploys the application as a background process using `nohup`.

## Architecture

The project is structured to separate the application code from the deployment logic:
*   `/ansible` - Contains the deployment playbook (`deploy.yml`) and inventory.
*   `/app` - Contains the Flask application source code (`main.py`).
