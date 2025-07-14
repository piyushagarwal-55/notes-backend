# Express Backend for Notebook Application

This is the backend API server for the Notebook application built with Express.js and MongoDB.

## Features

- **Authentication**: JWT-based user authentication with secure HTTP-only cookies
- **Notes Management**: Create, read, update, and delete notes
- **Bookmarks Management**: Manage bookmarks with auto-title fetching
- **Search & Filtering**: Search notes and bookmarks by content and tags
- **Favorites**: Mark notes and bookmarks as favorites
- **Security**: CORS protection, input validation, and error handling

## Quick Start

### Prerequisites

- Node.js (v16 or higher)
- MongoDB (local or cloud instance)

### Installation

1. **Clone and navigate to the backend folder:**
   ```bash
   cd express-backend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Set up environment variables:**
   Copy `.env.example` to `.env` and update the values:
   ```bash
   cp .env.example .env
   ```

4. **Update the .env file with your configuration:**
   ```env
   MONGODB_URI=mongodb://localhost:27017/notebook
   JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
   JWT_EXPIRE=7d
   COOKIE_EXPIRE=7
   PORT=5000
   NODE_ENV=development
   FRONTEND_URL=http://localhost:3000
   ```

5. **Start the development server:**
   ```bash
   npm run dev
   ```

6. **For production:**
   ```bash
   npm start
   ```

The server will be running at `http://localhost:5000`

## API Routes

### Authentication
- `POST /api/auth/register` – Register new user
- `POST /api/auth/login` – Login existing user
- `GET /api/auth/me` – Get current logged-in user
- `POST /api/auth/logout` – Logout user

### Notes
- `GET /api/notes` – Get all notes
- `POST /api/notes` – Create new note
- `GET /api/notes/:id` – Get single note
- `PUT /api/notes/:id` – Update note
- `DELETE /api/notes/:id` – Delete note
- `PATCH /api/notes/:id/favorite` – Toggle favorite status

### Bookmarks
- `GET /api/bookmarks` – Get all bookmarks
- `POST /api/bookmarks` – Create new bookmark
- `GET /api/bookmarks/:id` – Get single bookmark
- `PUT /api/bookmarks/:id` – Update bookmark
- `DELETE /api/bookmarks/:id` – Delete bookmark
- `PATCH /api/bookmarks/:id/favorite` – Toggle favorite status

### System
- `GET /api/health` – Check server status

## Project Structure

```
express-backend/
├── config/
│   └── database.js          # MongoDB connection
├── middleware/
│   └── auth.js              # Authentication middleware
├── models/
│   ├── User.js              # User schema
│   ├── Note.js              # Note schema
│   └── Bookmark.js          # Bookmark schema
├── routes/
│   ├── auth.js              # Authentication routes
│   ├── notes.js             # Notes routes
│   └── bookmarks.js         # Bookmarks routes
├── .env                     # Environment variables
├── .env.example             # Environment template
├── package.json             # Dependencies and scripts
└── server.js                # Main server file
```

## Deployment

### Deploy to Render

1. **Create a new Web Service on Render**
2. **Connect your GitHub repository**
3. **Set the following:**
   - Build Command: `npm install`
   - Start Command: `npm start`
   - Environment: `Node`
   - Root Directory: `express-backend`

4. **Add environment variables in Render dashboard:**
   ```
   MONGODB_URI=your-mongodb-atlas-connection-string
   JWT_SECRET=your-production-secret-key
   JWT_EXPIRE=7d
   COOKIE_EXPIRE=7
   NODE_ENV=production
   FRONTEND_URL=https://your-frontend-domain.com
   PORT=10000
   ```

5. **Deploy!** Render will automatically deploy your backend.

### Deploy to Railway

1. **Create a new project on Railway**
2. **Connect your GitHub repository**
3. **Set the root directory to `express-backend`**
4. **Add the same environment variables as above**
5. **Deploy!**

### Deploy to Heroku

1. **Create a Heroku app:**
   ```bash
   heroku create your-app-name
   ```

2. **Set environment variables:**
   ```bash
   heroku config:set MONGODB_URI=your-mongodb-atlas-connection-string
   heroku config:set JWT_SECRET=your-production-secret-key
   heroku config:set NODE_ENV=production
   heroku config:set FRONTEND_URL=https://your-frontend-domain.com
   ```

3. **Create a Procfile in the express-backend directory:**
   ```
   web: npm start
   ```

4. **Deploy:**
   ```bash
   git subtree push --prefix express-backend heroku main
   ```

## Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `MONGODB_URI` | MongoDB connection string | `mongodb://localhost:27017/notebook` |
| `JWT_SECRET` | Secret key for JWT tokens | `your-secret-key` |
| `JWT_EXPIRE` | JWT expiration time | `7d` |
| `COOKIE_EXPIRE` | Cookie expiration (days) | `7` |
| `PORT` | Server port | `5000` |
| `NODE_ENV` | Environment mode | `development` or `production` |
| `FRONTEND_URL` | Frontend URL for CORS | `http://localhost:3000` |

## Security Notes

- Always use strong, unique values for `JWT_SECRET` in production
- Use HTTPS in production
- Set `NODE_ENV=production` for production deployments
- Use environment variables for all sensitive data
- Consider using MongoDB Atlas for production database

## Development

```bash
# Install dependencies
npm install

# Start development server with auto-reload
npm run dev

# Start production server
npm start
```

## License

This project is licensed under the ISC License.
