# Library Management System

## Overview

This is a simple **Library Management System (LMS)** built using Python and the **Tkinter** library for the graphical user interface (GUI). It allows a librarian to manage books, users, and the borrowing/returning process within a library. The system supports the following features:

- Add, remove, and search books in the library.
- Borrow and return books with due date tracking.
- Manage user records and track overdue books.

The system is designed to be simple, intuitive, and easy to use, with basic error handling and modern visual elements through **ttk** styles.

## Features

1. **Add Book**: Add new books to the library with title, author, and ISBN information.
2. **Borrow Book**: Allows users to borrow books, setting a due date for 7 days.
3. **Return Book**: Users can return borrowed books, making them available again.
4. **Search Book**: Search for books by title, author, or ISBN.
5. **User Records Management**: View user records, including borrowed books and overdue items.
6. **Overdue Management**: The system automatically tracks overdue books and displays notifications for users with overdue books.

## Technologies Used

- **Python** (version 3.x)
- **Tkinter** for the graphical user interface
- **datetime** for date and time operations

## Installation

1. Clone the repository to your local machine:
    ```bash
    git clone https://github.com/your-username/Library-Management-System.git
    ```
2. Navigate to the project folder:
    ```bash
    cd Library-Management-System
    ```
3. Install the required dependencies (if any). In this case, Tkinter should already be included with Python, but ensure you have the latest Python version:
    ```bash
    pip install -r requirements.txt  # If any dependencies are listed.
    ```

## Running the Application

1. After installing the dependencies, run the main Python file:
    ```bash
    python library_management_system.py
    ```
2. The Library Management System GUI will open, and you can interact with it using the available features such as adding books, borrowing/returning books, and managing user records.

## How to Use

### 1. **Add a Book**
   - Enter the **Book Title**, **Author Name**, and **ISBN** in the respective fields.
   - Click the **Add Book** button to add the book to the library.

### 2. **Borrow a Book**
   - Enter the **User ID** and the **Book ISBN** in the respective fields.
   - Click the **Borrow Book** button. The system will check if the book is available and allow the user to borrow it. The book's due date will be set to 7 days from the current date.

### 3. **Return a Book**
   - Enter the **Book ISBN** of the book you wish to return.
   - Click the **Return Book** button. The system will check if the book was borrowed and then mark it as available again.

### 4. **Search for a Book**
   - Enter a search term (e.g., part of the book's title, author's name, or ISBN).
   - Click the **Search Book** button to display any books that match the search criteria.

### 5. **View User Records**
   - Click on **View User Records** to see a list of users with their borrowed books and any overdue books.

## Code Structure

The project is structured as follows:

