# xrwvm-fullstack_developer_capstone

**Repository name:** xrwvm-fullstack_developer_capstone

**Project name:** Best Cars Dealership - Full Stack Dealership Review Application

## About the project

Best Cars is a national car retailer with dealerships across the United States. This
full-stack web application lets customers:

- browse all dealerships, or filter them by state
- view a dealer's details and the reviews other customers have left
- sign up, log in and post their own reviews of a dealer
- see the sentiment (positive, neutral or negative) of each review

## Architecture

| Component | Technology | Purpose |
|-----------|------------|---------|
| Django application | Python, Django | Main web app, user management, car makes and models, proxy to the services |
| React frontend | React | Dealers list, dealer details, post review, login and register pages |
| Static pages | HTML, Bootstrap | Home, About Us, Contact Us |
| Dealers and reviews API | Node.js, Express, MongoDB | Stores and serves dealerships and reviews |
| Sentiment analyzer | Python, Flask, NLTK | Analyzes review sentiment, deployed on IBM Cloud Code Engine |
| CI/CD | GitHub Actions | Lints the Python and JavaScript code on every push |
| Deployment | Docker, Kubernetes | Runs the application in IBM Cloud |

## Running locally

```bash
# Dealers and reviews API (needs MongoDB, see server/database/docker-compose.yml)
cd server/database && docker build . -t nodeapp && docker-compose up

# Sentiment analyzer
cd server/djangoapp/microservices && python3 -m flask --app app run --port 5050

# React frontend
cd server/frontend && npm install && npm run build

# Django application
cd server
pip install -r requirements.txt
python3 manage.py makemigrations && python3 manage.py migrate
python3 manage.py runserver
```
