DocsGPT is an open-source solution that streamlines the process of finding information in project documentation. With its integration of the powerful <strong>GPT</strong> models, developers can easily ask questions about a project and receive accurate answers.
  
Say goodbye to time-consuming manual searches, and let <strong>DocsGPT</strong> help you quickly find the information you need. Try it out and see how it revolutionizes your project documentation experience. Contribute to its development and be a part of the future of AI-powered assistance.

## Project structure
- Application - flask app (main application)

- Extensions - chrome extension

- Scripts - script that creates similarity search index and store for other libraries. 

- frontend - frontend in vite and

## QuickStart

Note: Make sure you have docker installed

1. Open dowload this repository with `git clone https://github.com/arc53/DocsGPT.git`
2. Create .env file in your root directory and set your OPENAI_API_KEY with your openai api key and  VITE_API_STREAMING to true or false if you dont want streaming answers
3. Run `docker-compose build && docker-compose up`
4. Navigate to http://localhost:5173/

To stop just run Ctrl + C

## Development environments

Spin up only 2 containers from docker-compose.yaml (by deleting all services except for redis and mongo)

Make sure you have python 3.10 or 3.11 installed

1. Navigate to `/application` folder
2. Run `docker-compose -f docker-compose-dev.yaml build && docker-compose -f docker-compose-dev.yaml up -d`
3. Export required variables              
`export CELERY_BROKER_URL=redis://localhost:6379/0`   
`export CELERY_RESULT_BACKEND=redis://localhost:6379/1`
`export MONGO_URI=mongodb://localhost:27017/docsgpt`
4. Install dependencies
`pip install -r requirements.txt`
5. Prepare .env file
Copy .env_sample and create .env with your openai api token
6. Run the app
`python wsgi.py`
7. Start worker with `celery -A app.celery worker -l INFO`

To start frontend
1. Navigate to `/frontend` folder
2. Install dependencies
`npm install`
3. Run the app
4. `npm run dev`


[How to install the Chrome extension](https://github.com/arc53/docsgpt/wiki#launch-chrome-extension)



