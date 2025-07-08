# Library Management System

A comprehensive Library Management System built with ASP.NET MVC, Entity Framework Core, and modern web technologies. This system provides a complete solution for managing books, authors, and borrowing transactions in a library environment.

## 🚀 Features

### Author Management
- **CRUD Operations**: Add, edit, delete, and list authors
- **Unique Validation**: Ensures author names and emails are unique
- **Comprehensive Profile**: Full name (4 names minimum), email, website, bio
- **Book Tracking**: Read-only list of books associated with each author

### Book Management
- **Complete Book Database**: Title, genre, description, and author association
- **Genre Classification**: 15 predefined genres (Adventure, Mystery, Thriller, Romance, SciFi, Fantasy, Biography, History, SelfHelp, Children, YoungAdult, Poetry, Drama, NonFiction, Unknown)
- **Author Integration**: Dropdown selection for book-author relationships

### Library Operations
- **Real-time Status Tracking**: View all books with availability status
- **Advanced Filtering**: Filter by status, borrow date, and return date
- **Borrowing System**: Secure book checkout with date tracking
- **Return Management**: Simple return process with automatic status updates
- **Conflict Prevention**: Prevents borrowing of already checked-out books

### Interactive Features
- **Dynamic Updates**: JavaScript-powered real-time availability status
- **Responsive UI**: Modern, user-friendly interface
- **Pagination**: Efficient data browsing (bonus feature)
- **Partial Views**: Modular UI components for better maintainability

## 🏗️ Architecture

This project follows a clean **n-tier architecture** pattern:

```
┌─────────────────────────────────────┐
│        Presentation Layer                  │
│     (ASP.NET MVC Controllers)       │
├─────────────────────────────────────┤
│         Business Layer                        │
│    (Services & Business Logic)        │
├─────────────────────────────────────┤
│          Data Layer                              │
│   (Entity Framework & Models)      │
└─────────────────────────────────────┘
```

### Key Architectural Principles
- **Separation of Concerns**: Each layer has distinct responsibilities
- **Dependency Injection**: Loose coupling between components
- **Service-Oriented**: All business logic resides in dedicated services
- **Controller Responsibility**: Controllers only handle HTTP requests/responses

## 🛠️ Technology Stack

- **Backend**: ASP.NET MVC (.NET Core)
- **ORM**: Entity Framework Core (Code-First approach)
- **Database**: In-Memory Database (for development and testing)
- **Frontend**: HTML5, CSS3, JavaScript, jQuery
- **Architecture**: N-tier with Dependency Injection
- **Design Pattern**: Repository Pattern, Service Layer Pattern

## 📋 Prerequisites

- .NET 6.0 or higher
- Visual Studio 2022 or Visual Studio Code
- Git for version control

## 🚀 Getting Started

### Clone the Repository
```bash
git clone https://github.com/yourusername/library-management-system.git
cd library-management-system
```

### Install Dependencies
```bash
dotnet restore
```

### Run the Application
```bash
dotnet run
```

The application will be available at `https://localhost:5001` or `http://localhost:5000`

## 📊 Database Schema

### Core Entities

#### Author
- `Id` (Primary Key)
- `FullName` (Required, Unique, 4 names minimum)
- `Email` (Required, Unique, Email validation)
- `Website` (Optional)
- `Bio` (Optional, max 300 characters)
- `Books` (Navigation property)

#### Book
- `Id` (Primary Key)
- `Title` (Required)
- `Genre` (Required Enum)
- `Description` (Optional, max 300 characters)
- `AuthorId` (Foreign Key)
- `Author` (Navigation property)

#### BorrowingTransaction
- `Id` (Primary Key)
- `BookId` (Foreign Key)
- `BorrowedDate` (Required)
- `ReturnedDate` (Optional)
- `Book` (Navigation property)

## 🎯 Usage Examples

### Adding an Author
1. Navigate to Authors section
2. Click "Add New Author"
3. Fill in required fields (full name with 4 parts, email)
4. Optionally add website and bio
5. Submit to create the author

### Borrowing a Book
1. Go to Library section
2. Select an available book
3. Click "Borrow Book"
4. Confirm borrowing action
5. Book status automatically updates to "Checked Out"

### Returning a Book
1. Find the borrowed book in the library
2. Click "Return Book"
3. Return date is automatically set
4. Book status updates to "Available"

## 🔧 Configuration

### Database Seeding
The application includes sample data seeding:
- 3 sample authors with complete profiles
- 10 sample books across various genres
- Sample borrowing transactions for testing

### Environment Settings
Configure the application in `appsettings.json`:
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "InMemoryDatabase"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

## 🧪 Testing

### Manual Testing Scenarios
1. **Author Management**: Test CRUD operations and validation
2. **Book Management**: Verify genre selection and author association
3. **Borrowing Flow**: Test complete borrow/return cycle
4. **JavaScript Features**: Verify dynamic status updates
5. **Validation**: Test all form validations and constraints

### Data Validation Tests
- Unique author names and emails
- Required field validation
- Email format validation
- Character limits for bio and description fields

## 📁 Project Structure

```
LibraryManagementSystem/
├── Controllers/
│   ├── AuthorsController.cs
│   ├── BooksController.cs
│   └── LibraryController.cs
├── Models/
│   ├── Author.cs
│   ├── Book.cs
│   ├── BorrowingTransaction.cs
│   └── ViewModels/
├── Services/
│   ├── IAuthorService.cs
│   ├── AuthorService.cs
│   ├── IBookService.cs
│   ├── BookService.cs
│   ├── IBorrowingService.cs
│   └── BorrowingService.cs
├── Data/
│   ├── LibraryContext.cs
│   └── DataSeeder.cs
├── Views/
│   ├── Authors/
│   ├── Books/
│   ├── Library/
│   └── Shared/
├── wwwroot/
│   ├── css/
│   ├── js/
│   └── lib/
└── Program.cs
```

## 🎨 UI Features

### Modern Interface
- Clean, responsive design
- Intuitive navigation
- Real-time feedback
- Mobile-friendly layout

### Interactive Elements
- Dynamic dropdowns
- Real-time status updates
- Form validation feedback
- Loading indicators

## 🔒 Business Rules

### Author Constraints
- Full name must contain exactly 4 names
- Each name must be at least 2 characters
- Email must be unique across all authors
- Bio limited to 300 characters

### Book Constraints
- Title is required
- Genre must be from predefined enum
- Description limited to 300 characters
- Must be associated with an existing author

### Borrowing Rules
- Books can only be borrowed if available
- Borrowing date is automatically set
- Books cannot be borrowed multiple times simultaneously
- Return date is automatically set when returned

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Contribution Guidelines
- Follow existing code style and patterns
- Ensure all business logic remains in services
- Add appropriate validation and error handling
- Update documentation for new features

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Entity Framework Core team for excellent ORM functionality
- ASP.NET MVC team for the robust web framework
- jQuery team for DOM manipulation capabilities
- The open-source community for continuous inspiration
---

**Built with ❤️ by Donia**