# Orbit — Task Management Application

Full-stack internship starter project with a premium dark black / purple / blue design.

## Included
- Register, login, logout
- bcrypt password hashing; JWT stored in an HTTP-only cookie
- Login session restored after refresh
- Create, view, edit, complete/reopen, search, sort, and delete tasks
- Priority and optional due dates
- Per-user task isolation enforced by the backend
- Responsive mobile/desktop interface
- Express rate limiting, Helmet security headers, server-side input validation

## Stack
HTML, CSS, vanilla JavaScript • Node.js • Express • MongoDB/Mongoose • bcryptjs • JWT

## Run it locally
1. Install Node.js 18+ and have MongoDB available (local install or MongoDB Atlas).
2. Extract this ZIP and open the folder in VS Code.
3. Open VS Code Terminal in the project folder and run `npm install`.
4. Copy `.env.example` to a new file named `.env`.
5. In `.env`, set `MONGODB_URI` and `JWT_SECRET`. Keep `.env private and never upload it.
   - Local MongoDB example: `mongodb://127.0.0.1:27017/task_manager`
   - Atlas: paste the Node.js connection string from Atlas, replace username/password placeholders.
   - `JWT_SECRET` must be a long random string of at least 32 characters.
6. Run `npm run dev` (or `npm start`).
7. Open `http://localhost:3000`.
8. Register a test account, create tasks, refresh the browser, then sign out/in to test persistence.

## MongoDB Atlas quick steps
- Create a free cluster and a database user.
- In Network Access, allow your current IP address.
- Choose Connect → Drivers and copy the Node.js URI into `MONGODB_URI`.
- Replace the password placeholder (URL-encode special characters if necessary), save `.env`, restart server.

## API
| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/auth/register` | Create account |
| POST | `/api/auth/login` | Sign in |
| POST | `/api/auth/logout` | Sign out |
| GET | `/api/auth/me` | Restore current session |
| GET | `/api/tasks` | List own tasks |
| POST | `/api/tasks` | Create task |
| PATCH | `/api/tasks/:id` | Update own task |
| DELETE | `/api/tasks/:id` | Delete own task |
| GET | `/api/health` | Health check |

## Security and limitations
- Never commit `.env`, database credentials, or real user passwords.
- The cookie is HTTP-only and SameSite=Strict; production mode also enables Secure cookies, so production should use HTTPS.
- Every task query/update/delete includes the authenticated user's ID. This prevents users from accessing another user's tasks through normal API requests.
- This starter has not been deployed or independently security-audited. Password reset, email verification, and optional WebSockets/live updates are not included.
- Serve the frontend and API from the same Express app for the simplest setup.

## Suggested internship demo
1. Register a test account and create tasks with different priorities/due dates.
2. Complete one task and search for a keyword.
3. Refresh the browser and show that the session and tasks persist.
4. Sign out and sign back in.
5. Create a second test account and confirm it sees only its own tasks.
