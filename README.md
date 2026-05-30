# Course Registration Portal

A full-stack web application for managing course registrations with role-based access for students, professors, and administrators. Built with Java servlets, PostgreSQL, and modern web technologies.

## 🎯 Overview

The Course Registration Portal is an enterprise-ready platform designed to streamline course management and student registration processes. It provides distinct interfaces and capabilities for different user roles, enabling students to browse and register for courses, professors to manage their course sections, and administrators to oversee the entire system.

## ✨ Features

### For Students
- **Course Catalog Browsing**: View all available courses with advanced filtering capabilities
  - Filter by department, credit hours, and professor
  - Search functionality to quickly find courses
- **Course Registration**: Register for available courses using course codes
- **Enrolled Courses Management**: View currently enrolled courses with detailed scheduling information
- **Grade Tracking**: Access result cards displaying grades for completed courses
- **Course Drop**: Unregister from enrolled courses with a dedicated interface
- **Session Management**: Secure login and logout functionality

### For Professors
- **Professor Dashboard**: Manage course sections and student rosters
- **Grade Management**: Input and update student grades
- **Course Information**: View and manage course details

### For Administrators
- **User Management**
  - Add new students and professors
  - Delete user accounts
  - View all users filtered by role
- **Course Management**
  - Add new courses to the catalog
  - Delete courses from the system
  - View and manage all courses
  - Assign professors to courses
- **Grade Administration**: Remove grades as needed
- **System Configuration**: Full control over course offerings and user accounts

## 🏗️ Architecture

### Technology Stack

| Layer | Technologies |
|-------|--------------|
| **Frontend** | HTML5, CSS3, JavaScript (Vanilla) |
| **Backend** | Java, Apache Tomcat, Servlets |
| **Database** | PostgreSQL |
| **Build Tool** | Maven |
| **JSON Processing** | org.json library |

### Project Structure

```
src/
├── main/
│   ├── java/com/courseportal/
│   │   ├── LoginServlet.java              # Authentication handler
│   │   ├── StudentDashServlet.java        # Student operations
│   │   ├── ProfessorDashServlet.java      # Professor operations
│   │   ├── AdminDashServlet.java          # Admin operations
│   │   ├── AdminServlet.java              # Admin access control
│   │   └── LogoutServlet.java             # Session termination
│   └── webapp/
│       ├── index.html                     # Login page
│       ├── student-dash.html              # Student interface
│       ├── professor-dash.html            # Professor interface
│       ├── js/
│       │   ├── index.js                   # Login form handling
│       │   ├── student-dash.js            # Student dashboard logic
│       │   └── [...other JS files]
│       └── css/
│           └── [...styling files]
```

### Language Composition
- **Java**: 33% - Backend logic and servlet implementations
- **JavaScript**: 31.6% - Frontend interactivity and API communication
- **HTML**: 20.8% - Page structure and layout
- **CSS**: 14.6% - Styling and responsive design

## 🚀 Getting Started

### Prerequisites

- Java Development Kit (JDK) 8 or higher
- Apache Tomcat 9.0 or higher
- PostgreSQL 12 or higher
- Maven 3.6 or higher
- Modern web browser

### Installation & Setup

1. **Clone the Repository**
   ```bash
   git clone https://github.com/c0gnit00/Course-portal.git
   cd Course-portal
   ```

2. **Database Setup**
   - Create a PostgreSQL database named `courseportal`
   - Create a database user:
     ```sql
     CREATE USER portaluser WITH PASSWORD 'portalpass';
     GRANT ALL PRIVILEGES ON DATABASE courseportal TO portaluser;
     ```
   - Initialize the database schema (schema file to be created)

3. **Build the Application**
   ```bash
   mvn clean package
   ```

4. **Deploy to Tomcat**
   - Copy the generated WAR file to Tomcat's `webapps/` directory
   - Restart Tomcat

5. **Access the Application**
   - Navigate to `http://localhost:8080/course-portal/`

### Configuration

Update database connection details in servlet initialization if needed:
```java
jdbc:postgresql://localhost:5432/courseportal
User: portaluser
Password: portalpass
```

Update Tomcat server URL in form actions (currently set to `http://localhost:8080/course-portal/`)

## 📋 Usage Guide

### Student Workflow

1. **Login**: Enter your student credentials on the login page
2. **Browse Catalog**: View available courses with optional filters
3. **Register**: Use the course code to register for a course
4. **View Enrollment**: Check your enrolled courses and schedules
5. **Check Grades**: Review your result card after semester completion
6. **Drop Course**: Unregister from courses before the deadline

### Professor Workflow

1. **Login**: Enter your professor credentials
2. **Access Dashboard**: View assigned courses and student rosters
3. **Manage Grades**: Input and update student grades
4. **Logout**: Exit your session

### Admin Workflow

1. **Authenticate**: Enter admin password (security note: change default credentials)
2. **User Management**: Add/delete students and professors
3. **Course Management**: Create, update, and delete courses
4. **Grade Management**: Remove grades as needed
5. **Monitor System**: View all users and courses

## 🔐 Security Notes

### Current Implementation
- Session-based authentication using Java HTTP sessions
- Role-based access control (Student/Professor/Admin)
- SQL prepared statements to prevent SQL injection

### Recommendations for Production
- ⚠️ **Change hardcoded admin password** in `AdminServlet.java`
- Implement HTTPS/SSL encryption
- Add input validation and sanitization
- Implement password hashing (bcrypt/SHA-256)
- Add CSRF token validation
- Enable SQL parameter binding in all queries
- Implement rate limiting and brute-force protection
- Use environment variables for database credentials
- Add comprehensive logging and audit trails

## 📊 Database Schema

### Key Tables
- **users**: Student and professor accounts
- **courses**: Course catalog and information
- **enrollments**: Student course registrations
- **grades**: Student academic grades
- **departments**: Academic departments
- **schedules**: Course meeting times and locations

## 🔄 API Endpoints

### Student Endpoints
- `GET /StudentDashServlet?action=session` - Get current session info
- `GET /StudentDashServlet?action=enrolled` - Get enrolled courses
- `GET /StudentDashServlet?action=results` - Get grade results
- `GET /StudentDashServlet?action=dropList` - Get courses available for drop
- `POST /StudentDashServlet?action=registerByCode` - Register for a course
- `POST /StudentDashServlet?action=drop` - Drop a course

### Admin Endpoints
- `POST /add-course` - Add new course
- `POST /delete-course` - Delete course
- `GET /view-courses` - List all courses
- `POST /add-users` - Add new user
- `POST /delete-users` - Delete user
- `GET /view-users` - List users by role
- `POST /remove-grade` - Remove student grades

### Authentication Endpoints
- `POST /login` - User authentication
- `POST /logout` - Session termination
- `POST /admin` - Admin access

## 🧪 Testing

Currently no automated test suite. Recommended additions:
- Unit tests for servlet logic (JUnit)
- Integration tests for database operations
- End-to-end tests for user workflows
- API endpoint testing

## 🐛 Known Limitations

- Hardcoded localhost URLs in HTML forms
- Admin password hardcoded in servlet
- Limited error handling and validation
- No password strength requirements
- Missing database schema file
- No transaction rollback mechanisms
- Limited audit logging

## 📈 Future Enhancements

- [ ] RESTful API redesign
- [ ] Spring Boot migration
- [ ] JWT authentication
- [ ] React/Vue frontend
- [ ] Real-time notifications
- [ ] Advanced analytics dashboard
- [ ] Mobile application
- [ ] Payment integration
- [ ] Automated email notifications
- [ ] Course prerequisites management
- [ ] Waitlist functionality
- [ ] Schedule conflict detection

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the MIT License. See the LICENSE file for details.

## 👨‍💻 Author

**c0gnit00** - [GitHub Profile](https://github.com/c0gnit00)

Created: June 18, 2025

## 📞 Support

For issues, questions, or suggestions, please:
- Open an issue on the [GitHub repository](https://github.com/c0gnit00/Course-portal/issues)
- Review the project documentation
- Check existing issues for similar problems

## 📚 Resources

- [Apache Tomcat Documentation](https://tomcat.apache.org/tomcat-9.0-doc/)
- [Java Servlets Tutorial](https://docs.oracle.com/javaee/6/tutorial/doc/bnafd.html)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Web Development Best Practices](https://developer.mozilla.org/en-US/)

---

**Status**: Active Development | **Last Updated**: June 2025
