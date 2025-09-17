# 🏕️ Project Camp Backend

A robust backend RESTful API for Project Camp, a collaborative tool for managing projects, tasks, notes, and teams with role-based access control.

![Project Camp API testing in Postman](https://i.imgur.com/gOq7z4L.png)

---

## ✨ Features

-   **User Authentication & Authorization:** Secure JWT-based authentication, email verification, password management, and token refresh.
-   **Role-Based Access Control (RBAC):** Three-tier permission system (Admin, Project Admin, Member) to manage user access securely.
-   **Complete Project Management:** Create, list, update, and delete projects.
-   **Team Management:** Invite users to projects, manage member roles, and remove members.
-   **Hierarchical Task Management:** Create tasks with assignees and track them through subtasks.
-   **Status Tracking:** Simple and effective task status system (Todo, In Progress, Done).
-   **Project Notes:** A dedicated space for project-wide notes and documentation.
-   **System Health Check:** An API endpoint for monitoring the application's status.

---

## 🛠️ Tech Stack

-   **Backend:** Node.js, Express.js
-   **Database:** MongoDB with Mongoose
-   **Authentication:** JSON Web Tokens (JWT), bcrypt.js
-   **Validation:** `express-validator`
-   **Email Service:** Nodemailer, Mailgen (with Mailtrap for development)
-   **File Handling:** Multer (as per PRD)

---

## ⚙️ Getting Started

Follow these instructions to get a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

-   [Node.js](https://nodejs.org/en/) (v18.x or higher)
-   [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)
-   [MongoDB](https://www.mongodb.com/try/download/community) instance (local or cloud)
-   [Git](https://git-scm.com/)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/project-camp-backend.git](https://github.com/your-username/project-camp-backend.git)
    ```

2.  **Navigate to the project directory:**
    ```bash
    cd project-camp-backend
    ```

3.  **Install dependencies:**
    ```bash
    npm install
    ```

4.  **Set up environment variables:**
    Create a `.env` file in the root of the project and add the following variables. Replace the placeholder values with your actual credentials.

    ```env
    # --- Server Configuration ---
    PORT=3000

    # --- Database Configuration ---
    MONGODB_URI=mongodb+srv://<user>:<password>@cluster.mongodb.net/your_db_name

    # --- JWT Configuration ---
    ACCESS_TOKEN_SECRET=your_super_secret_access_token_key
    ACCESS_TOKEN_EXPIRY=1d
    REFRESH_TOKEN_SECRET=your_super_secret_refresh_token_key
    REFRESH_TOKEN_EXPIRY=10d

    # --- Email (Mailtrap) Configuration ---
    MAILTRAP_SMTP_HOST=sandbox.smtp.mailtrap.io
    MAILTRAP_SMTP_PORT=2525
    MAILTRAP_SMTP_USER=your_mailtrap_user
    MAILTRAP_SMTP_PASS=your_mailtrap_password

    # --- CORS Configuration ---
    CORS_ORIGIN=*

    # --- Frontend URL for Password Reset ---
    FORGOT_PASSWORD_REDIRECT_URL=http://localhost:5173/reset-password
    ```

---

## 🚀 Running the Application

-   **Development Mode:**
    This will start the server with `nodemon`, which automatically restarts the server on file changes.
    ```bash
    npm run dev
    ```

-   **Production Mode:**
    This will start the server in a standard production environment.
    ```bash
    npm start
    ```

The server will be running at `http://localhost:3000`.

---

## 📚 API Endpoints

The API is structured with versioning under `/api/v1`. For detailed information on request bodies and responses, please refer to the Postman collection.

<details>
<summary><strong>Click to view API Endpoints</strong></summary>

#### Authentication Routes (`/api/v1/auth/`)
- `POST /register`
- `POST /login`
- `POST /logout` (secured)
- `POST /current-user` (secured)
- `POST /change-password` (secured)
- `POST /refresh-token`
- `GET /verify-email/:verificationToken`
- `POST /forgot-password`
- `POST /reset-password/:resetToken`
- `POST /resend-email-verification` (secured)

#### Project Routes (`/api/v1/projects/`)
- `GET /` (secured)
- `POST /` (secured)
- `GET /:projectId` (secured, role-based)
- and more...

#### Task Routes (`/api/v1/tasks/`)
- `GET /:projectId` (secured, role-based)
- `POST /:projectId` (secured, Admin/Project Admin)
- and more...

#### Note Routes (`/api/v1/notes/`)
- `GET /:projectId` (secured, role-based)
- `POST /:projectId` (secured, Admin only)
- and more...

</details>

---

## 📁 Project Structure

```
/
├── src/
│   ├── controllers/    # Request handling logic
│   ├── db/             # Database connection setup
│   ├── middlewares/    # Custom middleware (auth, validation)
│   ├── models/         # Mongoose schemas and models
│   ├── routes/         # API route definitions
│   ├── utils/          # Utility classes and functions
│   ├── validators/     # Request validation rules
│   └── index.js        # Main application entry point
├── public/             # Static assets
├── .env                # Environment variables (untracked)
├── .gitignore          # Files and folders to ignore
├── package.json        # Project dependencies and scripts
└── README.md           # This file
```

---

## 🤝 Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'feat: Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.
