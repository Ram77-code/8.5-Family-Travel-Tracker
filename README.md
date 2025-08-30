# 🌍Family Travel Tracker

A full-stack **Node.js + Express.js + PostgreSQL** web app that lets users track countries they have visited.
Users can add themselves, choose a color theme, and maintain their personal visited-country list with persistence in the database.

## 🚀 Features

* 👥 **Multi-user support** – each user can have their own travel list.
* 🗺️ **Track visited countries** – search for a country by name and add it to your list.
* 🎨 **Custom user colors** – personalize your profile with a chosen theme color.
* 📊 **Database-backed** – data stored persistently using PostgreSQL.
* 🖥️ **Dynamic UI** – powered by EJS templating for rendering server-side views.

## 🛠️ Tech Stack

* **Backend:** Node.js, Express.js
* **Frontend:** EJS templating engine
* **Database:** PostgreSQL
* **Middleware:** body-parser
* **Styling:** Custom CSS (served via `public/`)

## 📂 Project Structure

```
├── index.js          # Main server file
├── queries.sql       # Database schema & sample data
├── package.json      # Dependencies & scripts
├── package-lock.json # Lock file
├── .gitignore        # Ignored files
└── views/            # EJS templates (index.ejs, new.ejs, etc.)
```

## 🗄️ Database Setup

Run the following SQL commands from `queries.sql` to set up your database:

```sql
CREATE TABLE users(
  id SERIAL PRIMARY KEY,
  name VARCHAR(15) UNIQUE NOT NULL,
  color VARCHAR(15)
);

CREATE TABLE visited_countries(
  id SERIAL PRIMARY KEY,
  country_code CHAR(2) NOT NULL,
  user_id INTEGER REFERENCES users(id)
);
```

Sample data included in `queries.sql`.

## ⚙️ Installation & Setup

1. **Clone the repo**

   ```bash
   git clone https://github.com/your-username/travel-tracker.git
   cd travel-tracker
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Configure PostgreSQL**
   Update your DB credentials inside `index.js` (or `solution.js`):

   ```js
   const db = new pg.Client({
     user: "postgres",
     host: "localhost",
     database: "world",
     password: "your_password",
     port: 5432,
   });
   ```

4. **Run database setup**

   ```bash
   psql -U postgres -d world -f queries.sql
   ```

5. **Start the server**

   ```bash
   node index.js
   ```

   Server runs on 👉 [http://localhost:3000](http://localhost:3000).

## ✨ Usage

* Open the app in your browser.
* Select a user or create a new one.
* Add countries you’ve visited.
* See your personal travel map update dynamically.

## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you’d like to change.

## 📜 License

This project is licensed under the **ISC License**.
