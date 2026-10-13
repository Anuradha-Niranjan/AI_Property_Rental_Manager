# AI_Property_Rental_Manager

A full-stack MERN web application for listing, browsing and renting properties, with AI-powered features built on Google Gemini. It has three roles (User, Owner and Admin), each with its own dashboard and permissions.

Features
User (Renter)
Browse properties with search, category filter, price range and pagination
AI Search: describe what you need in plain English (e.g. "2BHK near Andheri under 20000") and the filters are set automatically
AI Recommendations: property suggestions based on your past rental requests
AI Summary: one-line summary of any property description
Send rental requests to owners with an optional message
Track the status of requests (pending, approved, rejected)
Manage your profile and photo
Owner
Add, edit and delete properties with up to 5 images
AI Description Generator: generate a listing description from the property details
View rental requests for your properties and approve or reject them
Approving a request marks the property as rented and rejects other pending requests for it
Dashboard with property and request statistics
Admin
Platform dashboard with user, category, property and request statistics
Manage users (view, filter by role, delete)
Manage property categories (add, edit, delete)
View all properties and all rental requests across the platform
Analytics with status breakdown bars
Tech Stack

Frontend

React 19 with Vite
React Router v7
Tailwind CSS v4
Axios, React Toastify, React Icons

Backend

Node.js and Express 5
MongoDB with Mongoose
JWT authentication and bcrypt password hashing
Multer for image uploads
Google Gemini API (@google/genai) for AI features
Project Structure
AI_Property_Rental_Manager/
├── client/                 # React frontend
│   └── src/
│       ├── components/     # Navbar
│       ├── pages/          # auth, user, owner, admin, shared
│       ├── routes/         # ProtectedRoute, UserRoute, OwnerRoute, AdminRoute
│       └── services/       # Axios instance
└── server/                 # Express backend
    └── src/
        ├── config/         # db, multer, gemini
        ├── controllers/
        ├── middlewares/    # authentication and authorization
        ├── models/
        ├── routes/
        ├── utils/          # validators
        ├── uploads/        # uploaded images
        └── server.js
Getting Started
Prerequisites
Node.js 20.19+ or 22.12+
A MongoDB database (local or MongoDB Atlas)
A Gemini API key from Google AI Studio
1. Clone the repository
bash
git clone https://github.com/Anuradha-Niranjan/AI_Property_Rental_Manager.git
cd AI_Property_Rental_Manager
2. Backend setup
bash
cd server
npm install
mkdir src/uploads

Create server/.env:

env
PORT=4000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET_KEY=your_long_random_secret
GEMINI_API_KEY=your_gemini_api_key

Start the server:

bash
npm run dev

The API runs at http://localhost:4000.

3. Frontend setup
bash
cd client
npm install

Create client/.env:

env
VITE_BASE_URL=http://localhost:4000

Start the app:

bash
npm run dev

Open http://localhost:5173.

4. Create an admin account

The signup page only offers the User and Owner roles. To create an admin, register a normal account, then change its role field to admin in your database (for example in MongoDB Atlas or Compass) and log in again.

Environment Variables
Variable	Location	Description
PORT	server	Port the API listens on
MONGO_URI	server	MongoDB connection string
JWT_SECRET_KEY	server	Secret used to sign JWT tokens
GEMINI_API_KEY	server	Google Gemini API key
VITE_BASE_URL	client	Backend base URL (no trailing slash)

Never commit .env files. Both are listed in .gitignore.

API Overview
Base path	Purpose
/users	Signup, login, profile, user management (admin)
/categories	Property categories
/properties	Property CRUD, search, filter and pagination
/rental-requests	Send, track, approve and reject requests
/admin	Dashboard stats, all properties, all requests
/ai	Description generation, summary, requirement analysis, recommendations
/uploads	Static uploaded images

Protected routes expect an Authorization: Bearer <token> header and are restricted by role.

Password and Input Rules
Password: 8-20 characters with an upper-case letter, a lower-case letter, a digit and one of @.#$!%*?&
Phone: Indian mobile number
Images: JPG, PNG or WEBP, up to 2 MB each
Author

Anuradha Niranjan
