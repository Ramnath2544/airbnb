# 🏡 Full‑Stack Airbnb Style

A modern **full-stack property booking web application** built with **EJS templating (frontend)** and **Node.js + Express + MySQL (backend)**.  
Supports **browsing homes**, managing **favourites**, **bookings**, and comprehensive **host management** (add, edit, and delete listings) with a robust MVC architecture.

---

**<h2>Table of Contents</h2>**

### •	 <ins>Features</ins>

### •	 <ins>Documentation</ins>

### •	 <ins>Usage</ins>

### •	 <ins>Tech Stack</ins>

### •	 <ins>Project Structure</ins>

### •	 <ins>Getting Started</ins>

### •	 <ins>Environment Variables</ins>

### •	 <ins>Commit History Highlights</ins>

### •	 <ins>Future Enhancements</ins>

### •	 <ins>Contributing</ins>

### •	 <ins>Contact</ins>

---

## ✨ Features

### 🖥️ Frontend (EJS + Tailwind CSS)
- Server-side rendered views using **EJS templates** and reusable **partials** for consistent layouts.
- Fully styled responsive user interface utilizing **Tailwind CSS**.
- Intuitive navigation across Home, Properties, Favourites, and Bookings.
- Dynamic property details pages with rating images and descriptive UI.
- Custom **404 Error pages** for invalid paths.

### ⚙️ Backend (Node.js + Express)
- RESTful routing implemented via **Express.js**.
- Strict **MVC (Model-View-Controller)** architecture to separate data logic from routing.
- Dedicated routers for different user roles:
  - `storeRouter`: For user-facing pages (index, homes, favourites, bookings).
  - `hostRouter`: For property management (add, edit, delete homes).
- Request body parsing and middleware integration for seamless data flow.

### 📦 Persistence & Database
- Fully integrated with **MySQL** for robust, relational data persistence.
- Models designed for `Home`, `Favourites`, and `Bookings`.
- Automated cascading deletes (e.g., deleting a home automatically removes it from favourites).
- *Legacy Support:* Originally built with File System (JSON) persistence before successfully migrating to a SQL database.

### 🏠 Property & Booking Management
- **Host Dashboard:** Create new home listings, populate edit-home forms with existing data, and handle edit/delete requests.
- **User Dashboard:** View detailed home listings, save homes to a favourites list, and track requested bookings.

---

## Documentation
Here's a list of all the primary routes you can use with this application and what each path does.

**Store / User Routes**
- [GET /](#get-)
- [GET /homes](#get-homes)
- [GET /homes/:id](#get-homesid)
- [GET /favourites](#get-favourites)
- [POST /favourites](#post-favourites)
- [GET /bookings](#get-bookings)

**Host / Management Routes**
- [GET /host/add-home](#get-hostadd-home)
- [POST /host/add-home](#post-hostadd-home)
- [GET /host/edit-home/:id](#get-hostedit-homeid)
- [POST /host/edit-home](#post-hostedit-home)
- [POST /host/delete-home](#post-hostdelete-home)
  
### GET /
Renders the landing/index page of the application.

### GET /homes
Renders a list of all available property listings.

### GET /homes/:id
Displays detailed information, rating images, and specifics for a single home.

### GET /favourites
Renders the user's list of saved/favourite properties.

### POST /favourites
Adds a selected property to the user's favourites database.

### GET /bookings
Renders the user's active property bookings.

### GET /host/add-home
Displays the form for a host to list a new property.

### POST /host/add-home
Parses the request body and creates a new home record in the MySQL database.

### GET /host/edit-home/:id
Displays the edit skeleton pre-populated with the existing home data for modification.

### POST /host/edit-home
Submits and updates the modified property details in the database.

### POST /host/delete-home
Deletes a property from the database and automatically cleans up related records (like favourites).

---

## Usage
- **Users** can browse available homes on the main page, view specific property details, and save items to their favourites.
- **Users** can book properties and view their booking history.
- **Hosts** can navigate to the host dashboard to add new properties.
- **Hosts** can click the edit or delete buttons on their listings to manage property data safely.

---

## 🚀 Tech Stack

**Frontend:**  
- HTML5 / CSS3
- Tailwind CSS (Utility-first styling)
- EJS (Embedded JavaScript Templating)

**Backend:**  
- Node.js (CommonJS modules)
- Express.js (Routing, Middleware, parsing)
- MySQL (Relational Database)

**Other Tools:**  
- Nodemon (Development hot-reloading)
- npm (Package management)

---

## 📂 Project Structure

### Overview

The application follows the Model-View-Controller (MVC) architecture pattern for better code organization, maintainability, and separation of concerns.

### Directory Structure

airbnb/<br>
├── models/                 # Data models (Home, Favourites - MySQL logic)<br>
├── controllers/            # Business logic layer (handling CRUD operations)<br>
├── views/                  # Presentation layer (EJS templates & partials)<br>
├── routes/                 # URL routing layer (storeRouter, hostRouter)<br>
├── utils/                  # Helper functions (e.g., path core modules)<br>
├── public/                 # Static assets (Tailwind CSS, images)<br>
├── server.js               # Application entry point & Express setup<br>
└── package.json            # Project dependencies and scripts


##🔧 Getting Started

### 1. Install dependencies

npm install

### 2. Setup Tailwind CSS (if building custom styles)

npx tailwindcss -i ./public/css/input.css -o ./public/css/output.css --watch

### 3. Run the development server

npm run dev
# or
nodemon server.js

The server will typically start on http://localhost:3000 (or your configured port).

##🌐 Environment Variables

| Variable    | Description             | Example      |
| ----------- | ----------------------- | ------------ |
| PORT        | Server port             | 3000         |
| DB_HOST     | MySQL Database Host     | localhost    |
| DB_USER     | MySQL Database username | root         |
| DB_PASSWORD | MySQL Database password | secret       |
| DB_NAME     | MySQL Database name     | airbnb_clone |

## 📈 Commit History Highlights
- **Foundation:** Started with raw Node.js HTTP servers, manual chunk buffering, and request redirection.
- **Framework Adoption:** Integrated Express.js for routing, middleware parsing, and modularized code.
- **UI/UX:** Implemented EJS templating with partials and added Tailwind CSS for a modern design.
- **Architecture:** Transitioned to an MVC structure by moving data logic out of routes into controllers.
- **Data Evolution:** Built a complete local File System (JSON) CRUD before migrating the entire application to a production-ready MySQL database.

---

## 🛠️ Future Enhancements
- 🔐 User authentication (Sign Up / Login / JWT).
- 👤 Role-based authorization (distinct Host vs. Guest accounts).
- ⭐ User reviews and dynamic rating calculations.
- 💳 Checkout and payment gateway integration for bookings.

---

## 🤝 Contributing
Contributions are welcome. Please fork the repository and open a pull request. For major changes, open an issue first to discuss what you would like to change.

---

## 📧 Contact
For support or inquiries, please open an issue or email: [ramnath2544@gmail.com](mailto:ramnath2544@gmail.com).
