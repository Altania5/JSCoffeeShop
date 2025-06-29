# Coffee Shop App

## Description

Welcome to the Coffee Shop App! This application aims to provide a seamless experience for customers to browse our menu, place orders, and for staff to manage inventory and customer requests.

This project is built using Node.js and is designed for deployment on Heroku.

## Table of Contents

* [Features](#features)
* [Technologies Used](#technologies-used)
* [Prerequisites](#prerequisites)
* [Setup and Local Installation](#setup-and-local-installation)
* [Running the Application Locally](#running-the-application-locally)
* [Deployment to Heroku](#deployment-to-heroku)
* [API Endpoints (Optional)](#api-endpoints-optional)
* [Contributing](#contributing)
* [License](#license)

## Features

* User registration and authentication
* Browseable coffee and food menu
* Online ordering system
* Order history for users
* Admin panel for menu management
* Admin panel for order fulfillment

## Technologies Used

* **Backend:** Node.js, Express.js
* **Frontend:** CSS, JavaScript, React
* **Database:** MongoDB
* **Version Control:** Git
* **Deployment Platform:** Heroku
* **Package Manager:** npm 

## Prerequisites

Before you begin, ensure you have the following installed on your local machine:

* [Node.js](https://nodejs.org/) (which includes npm) or [Yarn](https://yarnpkg.com/)
* [Git](https://git-scm.com/)
* [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
* (***Add your specific database if it needs local installation, e.g., PostgreSQL, MongoDB server***)

## Setup and Local Installation

1.  **Clone the repository:**
    ```bash
    git clone <your-repository-url>
    cd <repository-name>
    ```

2.  **Install dependencies:**
    * If using npm:
        ```bash
        npm install
        ```
    * If using yarn:
        ```bash
        yarn install
        ```

3.  **Set up environment variables:**
    Create a `.env` file in the root of your project. This file will store sensitive information and configuration settings that should not be committed to Git. Add the following variables (adjust based on your project's needs):
    ```env
    PORT=3000
    DATABASE_URL=<your_local_database_connection_string>
    SESSION_SECRET=<a_very_strong_secret_key>
    # Add other environment variables like API keys, etc.
    ```
    *Ensure `.env` is listed in your `.gitignore` file!*

4.  **Database Setup (if applicable):**
    * Example for PostgreSQL:
        ```bash
        # psql -U your_username
        # CREATE DATABASE coffee_shop_db;
        # \q
        # npm run migrate # (if you have a migration script)
        # npm run seed   # (if you have a seed script)
        ```

## Running the Application Locally

* If using npm:
    ```bash
    npm start
    ```
    (Or `npm run dev` if you have a development script configured in your `package.json`)

* If using yarn:
    ```bash
    yarn start
    ```
    (Or `yarn dev`)

The application should now be running on `http://localhost:PORT` (e.g., `http://localhost:3000`).

## Deployment to Heroku

1.  **Log in to Heroku (if you haven't already):**
    ```bash
    heroku login
    ```

2.  **Create a Heroku app (if you haven't already):**
    From your project's root directory:
    ```bash
    heroku create your-coffee-shop-app-name
    ```
    (If you omit `your-coffee-shop-app-name`, Heroku will generate a random one.)

3.  **Provision a database (if needed):**
    * Example for Heroku Postgres:
        ```bash
        heroku addons:create heroku-postgresql:hobby-dev
        ```
    Heroku will set a `DATABASE_URL` config var automatically.

4.  **Set Heroku Config Vars:**
    Set any environment variables your app needs in Heroku (similar to your `.env` file, but **do not commit your `.env` file**).
    ```bash
    heroku config:set MY_VARIABLE="some_value"
    heroku config:set ANOTHER_VARIABLE="another_value"
    # Example: heroku config:set SESSION_SECRET="a_different_very_strong_secret_for_production"
    ```
    You can also do this through the Heroku Dashboard under your app's "Settings" tab.

5.  **Ensure your `package.json` has a `start` script and an `engines` section:**
    ```json
    {
      "name": "coffee-shop-app",
      "version": "1.0.0",
      "main": "server.js", // or your main entry file
      "scripts": {
        "start": "node server.js", // Ensure this command starts your app
        "test": "echo \"Error: no test specified\" && exit 1"
        // Add other scripts like "dev", "migrate", "seed"
      },
      "engines": {
        "node": "18.x" // Specify the Node.js version Heroku should use (check Heroku's supported versions)
      },
      "dependencies": {
        // your dependencies
      },
      "devDependencies": {
        // your dev dependencies
      }
    }
    ```

6.  **Ensure your `Procfile` is correct:**
    While Heroku can often infer the `start` script, explicitly defining a `Procfile` is more robust. Create a file named `Procfile` (no extension) in the root directory:
    ```Procfile
    web: node server.js
    ```
    (Replace `server.js` with your app's entry point if different.)

7.  **Push your code to Heroku:**
    ```bash
    git add .
    git commit -m "Prepare for Heroku deployment"
    git push heroku main # or master, depending on your branch name
    ```

8.  **Run database migrations/seeds on Heroku:**
    ```bash
    heroku run npm run migrate
    heroku run npm run seed
    ```
    (Adjust the commands based on your `package.json` scripts.)

9.  **Open your app in the browser:**
    ```bash
    heroku open
    ```

10. **Check logs if something goes wrong:**
    ```bash
    heroku logs --tail
    ```

## API Endpoints

**Example:*

* **Users**
    * `POST /api/users/register` - Register a new user
    * `POST /api/users/login` - Login an existing user
* **Menu Items**
    * `GET /api/menu` - Get all menu items
    * `GET /api/menu/:id` - Get a specific menu item
* **Orders**
    * `POST /api/orders` - Create a new order
    * `GET /api/orders/user/:userId` - Get orders for a specific user

| Method | Endpoint             | Description                     |
| :----- | :------------------- | :------------------------------ |
| `GET`  | `/api/menu`          | Retrieve all menu items         |
| `POST` | `/api/orders`        | Place a new coffee order        |
| ...    | ...                  | ...                             |

## Contributing

Contributions are welcome! If you'd like to contribute, please follow these steps:

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE.txt` for more information

---

# 1. (Save files in editor)
# 2. Check status (optional)
git status

# 3. Stage changes
git add . # Or specific files

# 4. Commit changes
git commit -m "Your commit message"

# 5. Push to GitHub/GitLab (optional but recommended)
# git push origin main

# 6. Push to Heroku to deploy
git push heroku main # Or master:main, or just master

# 7. Check logs
heroku logs --tail --app your-heroku-app-name

# 8. Open and test live app
heroku open --app your-heroku-app-name
