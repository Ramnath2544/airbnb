# Full-Stack Airbnb Style App

A full-stack property listing and booking-style web application built with **Node.js**, **Express**, **EJS**, **Tailwind CSS**, and **MySQL**.

The app uses an MVC structure with separate controllers, models, routes, EJS views, and static assets. Users can browse homes, view details, save favourites, and view bookings. Hosts can add, edit, and delete home listings.

## Features

### User Pages

- Browse all homes on the home page and homes list page.
- View details for a single home.
- Add homes to a favourites list.
- Remove homes from favourites.
- View a bookings page.
- See a custom 404 page for unknown routes.

### Host Pages

- Add a new home listing.
- View all host listings.
- Edit an existing home listing.
- Delete a home listing.

### Architecture

- MVC structure:
  - `controllers/` handles request logic.
  - `models/` handles data access.
  - `routes/` defines Express routes.
  - `views/` contains EJS templates and partials.
  - `public/` contains compiled CSS and image assets.
- Server-side rendering with EJS.
- Tailwind CSS for styling.
- MySQL database access through `mysql2`.

## Tech Stack

### Frontend

- HTML5
- EJS templates
- Tailwind CSS
- Static image assets

### Backend

- Node.js
- Express.js 5
- CommonJS modules
- Express URL-encoded body parsing

### Data Storage

- MySQL for home listing records.
- JSON file storage for favourites at `DB/data/favourite.json`.

### Development Tools

- npm
- Nodemon
- Tailwind CSS CLI
- PostCSS
- Autoprefixer

## Project Structure

```text
airbnb/
|-- README.md
`-- DB/
    |-- app.js
    |-- package.json
    |-- controllers/
    |-- data/
    |-- models/
    |-- public/
    |-- routes/
    |-- utils/
    `-- views/
```

## Routes

### Store Routes

| Method | Path | Description |
| --- | --- | --- |
| GET | `/` | Render the landing page. |
| GET | `/homes` | Render all available homes. |
| GET | `/homes/:homeId` | Render details for one home. |
| GET | `/favourites` | Render saved favourite homes. |
| POST | `/favourites` | Add a home to favourites. |
| POST | `/favourites/delete/:homeId` | Remove a home from favourites. |
| GET | `/bookings` | Render the bookings page. |

### Host Routes

| Method | Path | Description |
| --- | --- | --- |
| GET | `/host/add-home` | Render the add-home form. |
| POST | `/host/add-home` | Create a home listing. |
| GET | `/host/host-home-list` | Render host-managed listings. |
| GET | `/host/edit-home/:homeId` | Render the edit form for one home. |
| POST | `/host/edit-home` | Update a home listing. |
| POST | `/host/delete-home/:homeId` | Delete a home listing. |

## Getting Started

### 1. Open the app folder

```bash
cd DB
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure MySQL

The database connection is currently configured in `DB/utils/databaseUtil.js`:

```js
host: "localhost",
user: "root",
password: "root",
database: "airbnb"
```

Create a MySQL database named `airbnb`, then create a `homes` table with columns used by the app:

```sql
CREATE DATABASE IF NOT EXISTS airbnb;
USE airbnb;

CREATE TABLE IF NOT EXISTS homes (
  id INT AUTO_INCREMENT PRIMARY KEY,
  houseName VARCHAR(255) NOT NULL,
  price DECIMAL(10, 2) NOT NULL,
  location VARCHAR(255) NOT NULL,
  rating DECIMAL(2, 1) NOT NULL,
  photoUrl VARCHAR(500) NOT NULL,
  description TEXT
);
```

### 4. Run the app

```bash
npm start
```

This starts Nodemon for `app.js` and starts Tailwind in watch mode.

Open:

```text
http://localhost:3000
```

## Useful Scripts

| Command | Description |
| --- | --- |
| `npm start` | Start the Express app with Nodemon and Tailwind watch mode. |
| `npm run tailwind` | Rebuild `public/output.css` from `views/input.css` in watch mode. |

## Notes

- The Express server entry point is `DB/app.js`.
- The server listens on port `3000`.
- The app does not currently read environment variables; database credentials are hardcoded in `DB/utils/databaseUtil.js`.
- The `npm test` script is still a placeholder.
