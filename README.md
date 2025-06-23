
================================================================================
📚 LIBRARY MANAGEMENT SYSTEM DATABASE
================================================================================

🛠 TOOL USED: DBeaver (SQL Client Tool)
Compatible with: MySQL, PostgreSQL, SQLite, Oracle, etc.

--------------------------------------------------------------------------------
🎯 OBJECTIVE:
To design a relational database system for managing a library's users, books,
staff, issuing/returning process using Primary Keys and Foreign Keys to ensure
data integrity and efficient retrieval.


================================================================================
📂 DATABASE STRUCTURE OVERVIEW
================================================================================

This system includes 7 tables:

1. Users
2. Books
3. Librarians
4. IssuedBooks
5. ReturnedBooks
6. BookCategories
7. BookCategoryMapping

Each table uses PRIMARY KEY to uniquely identify records.
Foreign Keys link tables to maintain referential integrity.

================================================================================
🗂 TABLE DESCRIPTIONS
================================================================================

🔹 USERS
- Purpose: Stores details of library members.
- Columns: user_id (PK), name, email (unique), phone

🔹 BOOKS
- Purpose: Stores book details available in the library.
- Columns: book_id (PK), title, author, publisher, isbn (unique)

🔹 LIBRARIANS
- Purpose: Stores information about library staff.
- Columns: librarian_id (PK), name, email (unique)

🔹 ISSUEDBOOKS
- Purpose: Records which user issued which book and when.
- Columns:
  - issue_id (PK)
  - user_id (FK) → Users.user_id
  - book_id (FK) → Books.book_id
  - issue_date
  - due_date

🔹 RETURNEDBOOKS
- Purpose: Stores data about returned books and fine details.
- Columns:
  - return_id (PK)
  - issue_id (FK) → IssuedBooks.issue_id
  - return_date
  - fine

🔹 BOOKCATEGORIES
- Purpose: Stores different genres/categories of books.
- Columns: category_id (PK), category_name

🔹 BOOKCATEGORYMAPPING
- Purpose: Handles many-to-many relation between books and categories.
- Columns:
  - book_id (FK) → Books.book_id
  - category_id (FK) → BookCategories.category_id
  - Composite Primary Key: (book_id, category_id)

================================================================================
🔗 RELATIONSHIPS SUMMARY
================================================================================

| Table               | Linked With              | Key Type       | Description                              |
|--------------------|--------------------------|----------------|------------------------------------------|
| IssuedBooks         | Users, Books             | Foreign Keys   | Tracks who issued which book             |
| ReturnedBooks       | IssuedBooks              | Foreign Key    | Tracks returned books and fines          |
| BookCategoryMapping | Books, BookCategories    | Foreign Keys   | Maps books to one or more categories     |

================================================================================
🧪 SAMPLE DATA INSERTION (EXAMPLE)
================================================================================

INSERT INTO Users VALUES (1, 'SaiSri', 'saisri@example.com', '9999999999');
INSERT INTO Books VALUES (101, 'Clean Code', 'Robert C. Martin', 'Pearson', '9780132350884');
INSERT INTO IssuedBooks VALUES (1, 1, 101, '2025-06-20', '2025-07-05');

================================================================================
✅ PRIMARY KEY & FOREIGN KEY USAGE BENEFITS
================================================================================

✔ PRIMARY KEYS
- Ensure each record (user, book, issue) is unique.
- Prevent duplicate data entries.

✔ FOREIGN KEYS
- Link related data across tables (e.g., who issued which book).
- Enforce data consistency.
- Prevent deletion of data that is still in use.

================================================================================
🚀 FUTURE ENHANCEMENTS
================================================================================

- Add book reservation and waitlist system
- Auto-fine calculation using triggers
- Add login system with roles (Admin, User)
- Generate reports using SQL Views or BI tools

================================================================================
👩‍💻 AUTHOR
================================================================================

Created by: SaiSri  
Project: Library Management System Database  
Use: Academic or practical SQL database practice

================================================================================
