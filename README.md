### library_system

Here’s a **MongoDB README.md for a Library Management System** you can directly use in your project 👇

---

# 📚 Library Management System (MongoDB)

A simple **Library Management System** built using **MongoDB** to manage books, users, and issue/return records.

---

## 🚀 Features

* Add, update, delete books
* Manage users (students/admin)
* Issue and return books
* Track due dates and availability
* Search books by title/author

---

## 🛠️ Tech Stack

* Database: MongoDB
* Backend: Node.js (optional)
* API Testing: Postman / Thunder Client

---

## 📂 Database Structure

### 1. 📘 Books Collection

```json
{
  "_id": ObjectId,
  "title": "The Alchemist",
  "author": "Paulo Coelho",
  "isbn": "1234567890",
  "availableCopies": 5,
  "totalCopies": 10,
  "category": "Fiction"
}
```

---

### 2. 👤 Users Collection

```json
{
  "_id": ObjectId,
  "name": "Nanju",
  "email": "nanju@email.com",
  "role": "student",
  "issuedBooks": []
}
```

---

### 3. 📖 Transactions Collection

```json
{
  "_id": ObjectId,
  "userId": ObjectId,
  "bookId": ObjectId,
  "issueDate": "2026-05-01",
  "returnDate": "2026-05-10",
  "status": "issued"
}
```

---

## ▶️ Setup Instructions

### 1. Start MongoDB

```bash
mongod
```

---

### 2. Open Mongo Shell

```bash
mongosh
```

---

### 3. Create Database

```js
use libraryDB
```

---

## 📌 Basic Operations

### 📘 Add Book

```js
db.books.insertOne({
  title: "The Alchemist",
  author: "Paulo Coelho",
  isbn: "1234567890",
  availableCopies: 5,
  totalCopies: 10,
  category: "Fiction"
})
```

---

### 👤 Add User

```js
db.users.insertOne({
  name: "Nanju",
  email: "nanju@email.com",
  role: "student",
  issuedBooks: []
})
```

---

### 📖 Issue Book

```js
db.transactions.insertOne({
  userId: ObjectId("USER_ID"),
  bookId: ObjectId("BOOK_ID"),
  issueDate: new Date(),
  returnDate: null,
  status: "issued"
})

db.books.updateOne(
  { _id: ObjectId("BOOK_ID") },
  { $inc: { availableCopies: -1 } }
)
```

---

### 🔄 Return Book

```js
db.transactions.updateOne(
  { _id: ObjectId("TRANSACTION_ID") },
  { $set: { status: "returned", returnDate: new Date() } }
)

db.books.updateOne(
  { _id: ObjectId("BOOK_ID") },
  { $inc: { availableCopies: 1 } }
)
```

---

### 🔍 Search Books

```js
db.books.find({ title: "The Alchemist" })
```

---

## 📁 Project Structure

```
library-management/
│── models/
│── routes/
│── controllers/
│── config/
│── app.js
│── package.json
│── README.md
```

---

## ⚙️ Environment Variables

Create `.env` file:

```
MONGO_URI=mongodb://localhost:27017/libraryDB
```

---

## 🧪 Run Project

```bash
node app.js
```

---

## 📌 Future Improvements

* Add authentication (JWT)
* Fine calculation for late return
* Admin dashboard
* Book reservation system

* ## 📄 License

<img width="962" height="726" alt="Screenshot 2026-05-05 151943" src="https://github.com/user-attachments/assets/c96cd4ce-1a7a-411a-8812-e2fc66f727d0" />
<img width="1600" height="840" alt="WhatsApp Image 2026-05-05 at 3 26 15 PM" src="https://github.com/user-attachments/assets/facf9565-9fc9-4f73-a73e-c0d95d6bf0df" />
<img width="1013" height="736" alt="Screenshot 2026-05-05 151813" src="https://github.com/user-attachments/assets/e69cd671-3802-4e6f-888a-b1e2292f43c6" />
