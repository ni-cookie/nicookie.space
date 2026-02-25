# Personal Portfolio Website 

A fast, minimalist, and fully containerized personal portfolio website built with **FastAPI** and **Tailwind CSS**. Designed with a focus on clean code and automated deployment workflows.

## 🌟 Features

* **FastAPI Backend**: Lightweight and high-performance Python backend serving Jinja2 templates.
* **Minimalist UI**: Responsive, modern design using Tailwind CSS with built-in Dark/Light mode toggle.
* **Containerized**: Fully Dockerized application (FastAPI + Nginx) for consistent environments.
* **Reverse Proxy & SSL**: Nginx configured as a reverse proxy, seamlessly integrating with Let's Encrypt for automatic HTTPS.
* **CI/CD Pipeline**: Automated build and deployment to a remote server via GitHub Actions and GitHub Container Registry (GHCR).

## 🛠️ Tech Stack

* **Backend**: Python 3.11, FastAPI, Uvicorn, Jinja2
* **Frontend**: HTML5, Tailwind CSS (via CDN)
* **Infrastructure**: Docker, Docker Compose, Nginx
* **CI/CD**: GitHub Actions

## 📂 Project Structure

```text
.
├── .github/workflows/
│   └── docker-build.yml   # CI/CD pipeline configuration
├── static/
│   └── BW_Portrait.jpg    # Static assets (images)
├── templates/
│   └── index.html         # Jinja2 HTML template
├── docker-compose.yml     # Multi-container orchestration
├── Dockerfile             # FastAPI application image blueprint
├── main.py                # FastAPI application entry point
├── nginx.conf             # Nginx reverse proxy configuration
├── requirements.txt       # Python dependencies
└── README.md
```

## 💻 Local Development

1. **Clone the repository:**
   ```bash
   git clone https://github.com/ni-cookie/portfolio-app.git
   cd portfolio-app
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application:**
   ```bash
   uvicorn main:app --reload
   ```
   The website will be available at `http://localhost:8000`.

## 🚀 Deployment

This project uses **GitHub Actions** for Continuous Integration and Continuous Deployment (CI/CD). 

Upon pushing to the `main` branch, the pipeline will:
1. Build the Docker image.
2. Push the image to GitHub Container Registry (GHCR).
3. Connect to the production server via SSH.
4. Pull the latest image and restart the Docker containers without downtime.

### Prerequisites for CI/CD

To enable automated deployment, add the following **Repository Secrets** in your GitHub settings (`Settings > Secrets and variables > Actions`):

* `SERVER_HOST`: Your server's IP address or domain.
* `SERVER_USER`: SSH username (e.g., `root` or `ubuntu`).
* `SERVER_SSH_KEY`: The private SSH key for server access.

### Manual Server Setup (Initial)

If deploying for the first time on a fresh server:
1. Ensure Docker and Docker Compose are installed.
2. Generate Let's Encrypt SSL certificates.
3. Pull the repository and run:
   ```bash
   docker compose up -d
   ```

## 👤 Author

**Mykyta Lapin**
* System Administrator & Aspiring DevOps Engineer
* Website: [nicookie.space](https://nicookie.space)
* LinkedIn: [linkedin.com/in/mykytalapin](https://www.linkedin.com/in/mykytalapin)
* GitHub: [@ni-cookie](https://github.com/ni-cookie)