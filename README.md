# Louder AI

Live demo: https://louderai.onrender.com

Louder AI is an AI-powered event planning web app. A user can sign up, describe an event in plain English, and get a structured venue recommendation with location, estimated cost, and a short explanation of why that option fits the request.

This project shows full-stack product work:
- authentication with secure cookies
- persistent chat history per user
- AI response generation with Mistral through LangChain
- modern React frontend with animated UI
- Express and MongoDB backend deployment

## What You Should Know

This is not just a UI demo. I built a complete application where:
- users create an account and log in
- each user gets their own saved planning chats
- the backend sends user prompts to an LLM
- the LLM returns structured event suggestions
- the frontend renders those suggestions as clean proposal cards

The product use case is simple: instead of manually researching venues and rough budgets, a user can type something like:

`Team offsite for 20 engineers in Goa for 2 days under Rs 2 lakh`

and the app returns a concise event recommendation.

## Main Features

- AI event planning assistant for venue and budget suggestions
- user registration and login
- cookie-based authentication with JWT
- chat history saved in MongoDB
- new chat title generation from the first prompt
- responsive dashboard UI
- Socket.IO server and client setup for real-time capabilities

## Tech Stack

**Frontend**
- React
- Vite
- Tailwind CSS
- Framer Motion
- Axios
- React Router

**Backend**
- Node.js
- Express
- MongoDB + Mongoose
- JWT
- bcryptjs
- Socket.IO
- LangChain
- Mistral AI

## Project Structure

```text
LouderAi/
|- frontend/   # React client
|- backend/    # Express API, MongoDB models, AI services
\- README.md
```

## How It Works

1. The user signs up or logs in.
2. The frontend sends the event prompt to the backend.
3. The backend stores the user message in MongoDB.
4. The backend sends recent chat context to the Mistral model using LangChain.
5. The AI returns structured output:
   - venue name
   - location
   - estimated cost
   - why it fits
6. The response is saved and shown in the dashboard.

## Running Locally

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd LouderAi
```

Replace the GitHub URL above with your public repository URL before pushing.

### 2. Install dependencies

```bash
cd backend
npm install
cd ../frontend
npm install
cd ..
```

### 3. Create backend environment variables

Create a file at `backend/.env` using `backend/.env.example` as reference.

Required variables:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
MISTRAL_API_KEY=your_mistral_api_key
GOOGLE_USER=your_email@gmail.com
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_REFRESH_TOKEN=your_google_refresh_token
```

Notes:
- `MONGO_URI`, `JWT_SECRET`, and `MISTRAL_API_KEY` are required for the app to work.
- Google mail variables are only needed if you want the email service flow.

### 4. Run the backend

Open a terminal:

```bash
cd backend
npm run dev
```

The backend runs on:



this is deployed on backend folder for cost cutting so you will see the project runs on `http://localhost:3000` 


## Production / Deployment Note

The backend serves the built frontend from `backend/public`, which is how the deployed app works. The live version is available here:

https://louderai.onrender.com

## Important Implementation Notes

- user passwords are hashed with `bcryptjs`
- authentication is handled with JWT stored in cookies
- chat history is linked to each authenticated user
- the AI is constrained to event-planning use cases and returns `"NOT RELEVANT"` for unrelated prompts

## Possible Improvements

- stronger input validation on all auth routes
- emit real-time chat events through Socket.IO
- improve error handling and loading states
- add automated tests
- support multiple AI providers through config

## Author

Built by [FARDEEN](https://github.com/fardeen-99>)
