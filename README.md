# Online Course System

A comprehensive Java-based online course management system that provides a robust framework for managing courses, students, instructors, and educational content. This system supports both online and interactive course formats with advanced features like quiz management, payment processing, and course content organization.

## 🎯 Features

### Core Functionality
- **Course Management**: Create and manage different types of courses (Online and Interactive)
- **User Management**: Handle students and instructors with detailed profiles
- **Content Organization**: Structured course content with chapters and modules
- **Quiz System**: Comprehensive quiz management with multiple question types
- **Payment Processing**: Support for paid courses and financial aid
- **Schedule Management**: Weekly schedules and course periods

### Course Types
- **Online Courses**: Fully digital courses with platform integration
- **Interactive Courses**: Physical location-based courses with limited seating

### Advanced Features
- **Validation System**: Comprehensive input validation and error handling
- **Comparable Interface**: Course comparison based on pricing
- **Payment Interface**: Flexible payment method handling
- **Exception Handling**: Robust error management throughout the system

## 🏗️ Architecture

### Class Hierarchy

```
Person (Abstract)
├── Student
└── Instructor

Course (Abstract)
├── OnlineCourse (implements Payable, Comparable)
└── InteractiveCourse (implements Payable, Comparable)

Quiz
├── Chapter (Inner Class)
└── Type (Enum: MCQ, WRITTEN, MIXED)

Payable (Interface)
```

### Key Components

#### Person Classes
- **Person**: Abstract base class with common attributes (name, contact, address, gender, nationality)
- **Student**: Extends Person with student-specific features (ID, course enrollment, status)
- **Instructor**: Extends Person with instructor-specific features (graduation details, experience, courses taught)

#### Course Classes
- **Course**: Abstract base class for all course types
- **OnlineCourse**: Digital courses with platform and pricing information
- **InteractiveCourse**: Physical courses with location and seating management

#### Supporting Classes
- **Quiz**: Comprehensive quiz management with multiple question types
- **Payable**: Interface for payment method handling
- **Test**: Demo class showing system usage

## 🚀 Getting Started

### Prerequisites
- Java 20 or higher
- Maven 3.6+
- IDE (IntelliJ IDEA, Eclipse, or VS Code recommended)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Online-Course-System-master
   ```

2. **Build the project**
   ```bash
   mvn clean compile
   ```

3. **Run the test class**
   ```bash
   mvn exec:java -Dexec.mainClass="Course.Test"
   ```

### Project Structure
```
Online-Course-System-master/
├── Course/
│   └── src/
│       └── Course/
│           ├── Course.java              # Abstract course base class
│           ├── OnlineCourse.java        # Online course implementation
│           ├── InteractiveCourse.java   # Interactive course implementation
│           ├── Person.java              # Abstract person base class
│           ├── Student.java             # Student class
│           ├── Instructor.java          # Instructor class
│           ├── Quiz.java                # Quiz management
│           ├── Payable.java             # Payment interface
│           └── Test.java                # Demo class
├── src/
│   └── main/
│       └── java/
│           └── com/
│               └── mycompany/
│                   └── online_course_system/
│                       ├── Person.java
│                       ├── Student.java
│                       ├── Instructor.java
│                       └── Test/
│                           ├── TestInstructor.java
│                           └── TestStudent.java
├── pom.xml                              # Maven configuration
└── README.md                            # This file
```

## 📖 Usage Examples

### Creating a Student
```java
Student student = new Student(
    "John Doe",           // name
    "+1234567890",        // phone number
    "123 Main St",        // address
    "male",               // gender
    "United States",      // nationality
    "STU001",             // student ID
    "middle"              // student status (rich/middle/poor)
);

// Add courses
student.addCourse("Java Programming");
student.addCourse("Data Structures");
```

### Creating an Instructor
```java
Instructor instructor = new Instructor(
    "Jane Smith",         // name
    "+0987654321",        // phone number
    "456 Oak Ave",        // address
    "female",             // gender
    "Canada",             // nationality
    2015,                 // graduation year
    "MIT",                // graduation university
    8                     // years of experience
);

// Add courses taught
instructor.addCourse("Java Programming");
instructor.addCourse("Advanced Algorithms");
```

### Creating an Online Course
```java
ArrayList<String> quizzes = new ArrayList<>();
quizzes.add("Quiz 1");
quizzes.add("Quiz 2");

ArrayList<String> instructors = new ArrayList<>();
instructors.add("Jane Smith");

ArrayList<String> students = new ArrayList<>();
students.add("John Doe");

ArrayList<String> content = new ArrayList<>();
content.add("Introduction to Java");
content.add("Object-Oriented Programming");

ArrayList<String> weeklyData = new ArrayList<>();
weeklyData.add("Week 1: Basics");
weeklyData.add("Week 2: OOP");

ArrayList<String> coursePeriod = new ArrayList<>();
coursePeriod.add("January 2024");
coursePeriod.add("February 2024");

OnlineCourse course = new OnlineCourse(
    "Java Programming",           // name
    "CSE231",                     // course ID
    "Learn Java programming",     // description
    quizzes,                      // quizzes
    instructors,                  // instructors
    students,                     // students
    content,                      // content
    weeklyData,                   // weekly schedule
    coursePeriod,                 // course periods
    99.99,                        // price
    "Coursera"                    // platform
);
```

### Creating a Quiz
```java
ArrayList<Chapter> chapters = new ArrayList<>();
chapters.add(new Chapter());
chapters.add(new Chapter());

Quiz quiz = new Quiz(
    LocalDate.now(),      // creation date
    chapters,             // content chapters
    20,                   // number of questions
    true                  // is set
);

// Change quiz type
quiz.setType(Quiz.Type.MIXED);
```

## 🔧 Configuration

### Maven Configuration
The project uses Maven for dependency management and build configuration. Key settings in `pom.xml`:

- **Java Version**: 20
- **Encoding**: UTF-8
- **Main Class**: `com.mycompany.online_course_system.Online_Course_System`

### Validation Rules

#### Person Validation
- **Name**: Must contain only letters and spaces, no digits
- **Phone Number**: Must contain only digits, optionally starting with '+'
- **Address**: Must be non-empty
- **Gender**: Must be either 'male' or 'female'
- **Nationality**: Must be from predefined list

#### Student Validation
- **Student ID**: Must be non-empty
- **Student Status**: Must be 'rich', 'middle', or 'poor'

#### Instructor Validation
- **Graduation Year**: Must be between 1900 and 2023
- **University Name**: Must be non-empty
- **Experience**: Must be non-negative

#### Course Validation
- **Course ID**: Must be non-empty
- **Price**: Must be non-negative
- **Platform/Location**: Must be non-empty

## 🧪 Testing

The project includes test classes demonstrating system functionality:

- **Test.java**: Main demo class showing course creation and usage
- **TestStudent.java**: Student-specific functionality tests
- **TestInstructor.java**: Instructor-specific functionality tests

Run tests using:
```bash
mvn test
```

## 🔒 Error Handling

The system implements comprehensive error handling with:

- **Input Validation**: All user inputs are validated with meaningful error messages
- **Exception Handling**: Custom exceptions for invalid data
- **Null Checks**: Protection against null pointer exceptions
- **Business Logic Validation**: Domain-specific validation rules

## 📝 API Documentation

### Core Methods

#### Course Management
- `addChapterToContent(String chapter)`: Add new chapter to course
- `removeChapterFromContent(String chapter)`: Remove chapter from course
- `getChapterNumber(String chapterName)`: Get chapter position
- `changeWeeklyPeriod(ArrayList<String> newPeriod)`: Update course schedule

#### Student Management
- `addCourse(String course)`: Enroll in a course
- `removeCourse(String course)`: Drop a course
- `getCourses()`: Get enrolled courses list

#### Instructor Management
- `addCourse(String course)`: Assign course to instructor
- `removeCourse(String course)`: Remove course assignment
- `getCoursesExplained()`: Get courses taught by instructor

#### Quiz Management
- `addQuestion(int count)`: Add questions to quiz
- `removeQuestion(int count)`: Remove questions from quiz
- `addChapter(Chapter chapter)`: Add chapter to quiz
- `changeType(Type type)`: Change quiz type
- `changeQuizTime(int year, int month, int day)`: Update quiz date

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Authors

For any inquiries or support, please contact:

<table>
<tr>
  <!-- Khalid Doma -->
    <td align="center" style="word-wrap: break-word; width: 170.0; height: 170.0">
        <a href= https://github.com/KHALIDDOMA >
            <img src=https://avatars.githubusercontent.com/u/77086956?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt= Khalid Doma/>
            <br />
            <sub style="font-size:14px"><b>Khalid Doma</b></sub>
        </a>
    </td>
  <!-- Kareem Mostafa -->
    <td align="center" style="word-wrap: break-word; width: 170.0; height: 170.0">
        <a href= https://github.com/KareemMostafa1 >
            <img src=https://avatars.githubusercontent.com/u/167640929?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt= Kareem Mostafa/>
            <br />
            <sub style="font-size:14px"><b>Kareem Mostafa</b></sub>
        </a>
    </td>
  <!-- Mohamed Hussien Mansour -->
    <td align="center" style="word-wrap: break-word; width: 170.0; height: 170.0">
        <a href= https://github.com/MohamedHussienMansour >
            <img src=https://avatars.githubusercontent.com/u/115054256?v=4 width="100;"  style="border-radius:50%;align-items:center;justify-content:center;overflow:hidden;padding-top:10px" alt= Mohamed Hussien                Mansour/>
            <br />
            <sub style="font-size:14px"><b>Mohamed Hussien Mansour</b></sub>
        </a>
    </td>
   
</tr>
</table>

## 🙏 Acknowledgments

- Java Collections Framework for data structures
- Maven for build management
- Object-oriented programming principles
- Design patterns implementation

## 📞 Support

For support and questions:
- Create an issue in the repository
- Contact the development team
- Check the test classes for usage examples

---

**Note**: This system is designed for educational purposes and demonstrates advanced Java programming concepts including inheritance, polymorphism, interfaces, and exception handling.
