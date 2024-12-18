import tkinter as tk
from tkinter import messagebox
from tkinter import ttk
from datetime import datetime, timedelta

# Class to represent a Book
class Book:
    def __init__(self, title, author, isbn, available=True):
        self.title = title
        self.author = author
        self.isbn = isbn
        self.available = available
        self.due_date = None

# Class to represent a User
class User:
    def __init__(self, name, user_id):
        self.name = name
        self.user_id = user_id
        self.borrowed_books = []

    def borrow_book(self, book):
        if book.available:
            book.due_date = datetime.now() + timedelta(days=7)  # Set due date to 7 days from now
            self.borrowed_books.append(book)
            book.available = False
            return True
        return False

    def return_book(self, book):
        if book in self.borrowed_books:
            self.borrowed_books.remove(book)
            book.available = True
            book.due_date = None  # Clear due date when returned
            return True
        return False

    def check_overdue_books(self):
        overdue_books = [book for book in self.borrowed_books if book.due_date and book.due_date < datetime.now()]
        return overdue_books

# Main Library Management System Class with the GUI
class LibraryManagementSystem:
    def __init__(self, root):
        self.root = root
        self.root.title("Library Management System")
        self.root.geometry("600x600")  # Adjusted size for more space

        # Initialize book and user storage
        self.books = {}
        self.users = {}

        # Apply modern ttk styles
        self.style = ttk.Style()
        self.style.configure("TButton", padding=6, relief="flat", background="#4CAF50", foreground="white", font=("Helvetica", 10))
        self.style.configure("TLabel", font=("Helvetica", 12), padding=6)

        # Create the GUI elements
        self.create_widgets()

    def create_widgets(self):
        # Create frames for organization
        self.frame1 = ttk.LabelFrame(self.root, text="Add Book", padding=(20, 10))
        self.frame1.grid(row=0, column=0, padx=10, pady=10, sticky="ew", columnspan=2)

        self.frame2 = ttk.LabelFrame(self.root, text="Borrow Book", padding=(20, 10))
        self.frame2.grid(row=1, column=0, padx=10, pady=10, sticky="ew", columnspan=2)

        self.frame3 = ttk.LabelFrame(self.root, text="Return Book", padding=(20, 10))
        self.frame3.grid(row=2, column=0, padx=10, pady=10, sticky="ew", columnspan=2)

        self.frame4 = ttk.LabelFrame(self.root, text="Search Book", padding=(20, 10))
        self.frame4.grid(row=3, column=0, padx=10, pady=10, sticky="ew", columnspan=2)

        self.frame5 = ttk.LabelFrame(self.root, text="Manage User Records", padding=(20, 10))
        self.frame5.grid(row=4, column=0, padx=10, pady=10, sticky="ew", columnspan=2)

        # Add Book Section
        ttk.Label(self.frame1, text="Book Title:").grid(row=0, column=0, sticky="w")
        self.book_title_entry = ttk.Entry(self.frame1, width=30)
        self.book_title_entry.grid(row=0, column=1, padx=10)

        ttk.Label(self.frame1, text="Author Name:").grid(row=1, column=0, sticky="w")
        self.book_author_entry = ttk.Entry(self.frame1, width=30)
        self.book_author_entry.grid(row=1, column=1, padx=10)

        ttk.Label(self.frame1, text="ISBN:").grid(row=2, column=0, sticky="w")
        self.book_isbn_entry = ttk.Entry(self.frame1, width=30)
        self.book_isbn_entry.grid(row=2, column=1, padx=10)

        self.add_book_button = ttk.Button(self.frame1, text="Add Book", command=self.add_book)
        self.add_book_button.grid(row=3, column=0, columnspan=2, pady=10)

        # Borrow Book Section
        ttk.Label(self.frame2, text="User ID:").grid(row=0, column=0, sticky="w")
        self.user_id_entry = ttk.Entry(self.frame2, width=30)
        self.user_id_entry.grid(row=0, column=1, padx=10)

        ttk.Label(self.frame2, text="Book ISBN:").grid(row=1, column=0, sticky="w")
        self.book_isbn_borrow_entry = ttk.Entry(self.frame2, width=30)
        self.book_isbn_borrow_entry.grid(row=1, column=1, padx=10)

        self.borrow_book_button = ttk.Button(self.frame2, text="Borrow Book", command=self.borrow_book)
        self.borrow_book_button.grid(row=2, column=0, columnspan=2, pady=10)

        # Return Book Section
        ttk.Label(self.frame3, text="Book ISBN:").grid(row=0, column=0, sticky="w")
        self.book_isbn_return_entry = ttk.Entry(self.frame3, width=30)
        self.book_isbn_return_entry.grid(row=0, column=1, padx=10)

        self.return_book_button = ttk.Button(self.frame3, text="Return Book", command=self.return_book)
        self.return_book_button.grid(row=1, column=0, columnspan=2, pady=10)

        # Search Book Section
        ttk.Label(self.frame4, text="Search Term:").grid(row=0, column=0, sticky="w")
        self.search_book_entry = ttk.Entry(self.frame4, width=30)
        self.search_book_entry.grid(row=0, column=1, padx=10)

        self.search_book_button = ttk.Button(self.frame4, text="Search Book", command=self.search_book)
        self.search_book_button.grid(row=1, column=0, columnspan=2, pady=10)

        # Manage User Records Section
        self.view_user_button = ttk.Button(self.frame5, text="View User Records", command=self.view_user_records)
        self.view_user_button.grid(row=0, column=0, columnspan=2, pady=10)

    def add_book(self):
        title = self.book_title_entry.get()
        author = self.book_author_entry.get()
        isbn = self.book_isbn_entry.get()

        if title and author and isbn:
            new_book = Book(title, author, isbn)
            self.books[isbn] = new_book
            messagebox.showinfo("Success", f"Book '{title}' added successfully.")
        else:
            messagebox.showerror("Error", "Please fill in all fields.")

    def borrow_book(self):
        user_id = self.user_id_entry.get()
        isbn = self.book_isbn_borrow_entry.get()

        if user_id and isbn:
            if isbn in self.books:
                book = self.books[isbn]
                if user_id not in self.users:
                    self.users[user_id] = User(user_id, user_id)
                user = self.users[user_id]
                if user.borrow_book(book):
                    messagebox.showinfo("Success", f"Book '{book.title}' borrowed successfully.")
                else:
                    messagebox.showinfo("Error", "Book is not available.")
            else:
                messagebox.showerror("Error", "Book not found.")
        else:
            messagebox.showerror("Error", "Please fill in all fields.")

    def return_book(self):
        isbn = self.book_isbn_return_entry.get()

        if isbn:
            if isbn in self.books:
                book = self.books[isbn]
                for user in self.users.values():
                    if book in user.borrowed_books:
                        if user.return_book(book):
                            messagebox.showinfo("Success", f"Book '{book.title}' returned successfully.")
                            return
                messagebox.showerror("Error", "No such book borrowed.")
            else:
                messagebox.showerror("Error", "Book not found.")
        else:
            messagebox.showerror("Error", "Please enter a book ISBN.")

    def search_book(self):
        search_term = self.search_book_entry.get().lower()
        search_results = []
        for book in self.books.values():
            if search_term in book.title.lower() or search_term in book.author.lower() or search_term in book.isbn:
                search_results.append(book)

        if search_results:
            result_text = "\n".join([f"{book.title} by {book.author} (ISBN: {book.isbn})" for book in search_results])
            messagebox.showinfo("Search Results", result_text)
        else:
            messagebox.showinfo("Search Results", "No books found.")

    def view_user_records(self):
        user_records = []
        for user in self.users.values():
            overdue_books = user.check_overdue_books()
            overdue_books_info = "\n".join([f"{book.title} (due {book.due_date.strftime('%Y-%m-%d')})" for book in overdue_books])
            if overdue_books:
                overdue_info = f"Overdue Books:\n{overdue_books_info}\n"
            else:
                overdue_info = "No overdue books.\n"
            
            borrowed_books_info = "\n".join([f"{book.title} (due {book.due_date.strftime('%Y-%m-%d')})" for book in user.borrowed_books])
            user_records.append(f"User ID: {user.user_id}\nName: {user.name}\nBorrowed Books:\n{borrowed_books_info}\n{overdue_info}")
        
        messagebox.showinfo("User Records", "\n\n".join(user_records))

# Main code to run the application
if __name__ == "__main__":
    root = tk.Tk()
    app = LibraryManagementSystem(root)
    root.mainloop()
