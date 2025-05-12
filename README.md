Library Management System - MySQL Database

❤️‍🩹Overview
This is a comprehensive MySQL database solution for managing library operations. The system handles book cataloging, member management, loan tracking, reservations, fines, and staff administration in a fully normalized relational database structure.

🔥Database Features

🔥Core Functionality
- Member Management: Track library members with contact details and membership status
- Book Catalog: Manage book inventory with detailed information including authors, publishers, and categories
- Loan System: Record book loans with due dates and return tracking
- Reservation System: Handle book reservations with expiry dates
- Fine Management: Process late fees and payments
- Staff Administration: Manage library staff with different access levels

  ❤️‍🩹Technical Implementation
- 10 Normalized Tables with proper relationships (1-M, M-M)
- Data Integrity enforced through constraints (PK, FK, NOT NULL, UNIQUE, CHECK)
- Performance Optimization with strategic indexes
- Automated Processes via triggers for:
  - Available book count updates
  - Overdue loan detection
  - Status management

❤️‍🩹 Database Schema

  🔥Main Tables
1. members- Library patrons
2. authors - Book authors
3. publishers- Publishing companies
4. book_categories- Book classification
5. books- Book inventory
6. book_authors - M-M relationship between books and authors
7. loans- Book lending records
8. reservations - Book hold requests
9. fine_payments- Late fee transactions
10. staff - Library employees

❤️‍🩹 Installation

1. Save the SQL script as `library_management.sql`
2. Execute in MySQL:
   ```bash
   mysql -u [username] -p < library_management.sql
   ```
3. Enter your MySQL password when prompted

❤️‍🩹 Usage Examples

 🔥 Basic Queries
- Find available books:
  ```sql
  SELECT  FROM books WHERE available_copies > 0;
  ```

- Check overdue loans:
  ```sql
  SELECT FROM loans WHERE status = 'Overdue';
  ```

- Member loan history:
  ```sql
  SELECT b.title, l.loan_date, l.due_date 
  FROM loans l
  JOIN books b ON l.book_id = b.book_id
  WHERE l.member_id = [member_id];
  ```

  ❤️‍🩹Business Rules Implemented
1. Available copies automatically adjust when books are loaned/returned
2. Loans automatically mark as overdue when past due date
3. Members cannot borrow more books than available copies
4. Membership expiry dates must be after join dates
5. Book return dates cannot be before loan dates

  ❤️‍🩹Future Enhancements
1. Add stored procedures for common operations
2. Implement views for reporting
3. Add audit logging for sensitive operations
4. Extend with user authentication system

  ❤️‍🩹Support
For any questions or issues with the database implementation, please open an issue in the repository.