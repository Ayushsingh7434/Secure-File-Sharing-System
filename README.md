
# 📁 EZ Lab - Backend Intern Assignment

This repository contains the solution to the **Backend Internship Assessment** provided by **EZ Lab**. The project is a **secure file-sharing REST API** built using **FastAPI**. It features **role-based access control**, **JWT authentication**, and secure **one-time file download** functionality.

---

## 🛠 Tech Stack

- **Language**: Python 3  
- **Framework**: FastAPI  
- **Authentication**: JWT (OAuth2), Role-based (Ops, Client)  
- **Encryption**: Fernet (for secure email verification tokens)  
- **Data Storage**: In-memory (Python dictionaries)  
- **API Testing**: Postman (collection included)  
- **Package Management**: pip (`requirements.txt`)  

---

## 📁 Project Structure

```
secure_file_sharing/
├── main.py                              # Application logic
├── .env                                 # Environment variables (excluded from version control)
├── requirements.txt                     # Python dependencies
├── SecureFileSharingAPI.postman_collection.json  # Postman collection
└── README.md                            # Project documentation
```

---

## ✅ Features

- 🔐 User registration with role selection (`client`, `ops`)
- 📧 Email verification via Fernet-encrypted token (simulated)
- 🔑 JWT-based login and token authentication
- 📤 File upload (only for `ops`)
- 📂 File listing and downloading (only for verified `clients`)
- 🔗 Secure one-time download links
- 📝 Simulated download history tracking

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/ShivamGupta-16/secure_file_sharing.git
cd secure_file_sharing
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Set Up Environment Variables

Create a `.env` file in the project root with the following content:

```env
SECRET_KEY=your_jwt_secret_key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
FERNET_KEY=your_fernet_key_here
```

To generate a Fernet key, use this Python snippet:

```python
from cryptography.fernet import Fernet
print(Fernet.generate_key().decode())
```

### 4. Run the Application

```bash
uvicorn main:app --reload
```

Now open the API docs in your browser:  
📎 [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

---

## 📡 API Endpoints

| Method | Endpoint                         | Access Role | Description                          |
|--------|----------------------------------|-------------|--------------------------------------|
| POST   | `/signup`                        | Public      | Register a new user                  |
| GET    | `/verify-email/{token}`          | Public      | Simulate email verification          |
| POST   | `/login`                         | Public      | Login and receive access token       |
| POST   | `/upload`                        | Ops only    | Upload a file                        |
| GET    | `/list-files`                    | Client only | List available uploaded files        |
| GET    | `/download-file/{file_id}`       | Client only | Generate a secure download link      |
| GET    | `/secure-download/{token}`       | Client only | Download the file using token        |
| GET    | `/download-history`              | Client only | View simulated download history      |

---

## 🧪 API Testing with Postman

1. Open Postman and import `SecureFileSharingAPI.postman_collection.json`.
2. Use the following sequence to test the API:

   - ➕ **Sign Up** using `/signup`
   - ✅ **Verify Email** by copying the token and accessing `/verify-email/{token}`
   - 🔐 **Login** using `/login` and store the JWT token
   - 📤 **Upload Files** as `ops` user
   - 📂 **List & Download Files** as a `client` user

---

## 📬 Contact

For queries or follow-up regarding this project, feel free to connect.

---
