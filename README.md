---

# 🧑‍🎓 Student and Grade Management System

This Python project demonstrates fundamental concepts of **Object-Oriented Programming (OOP)** by creating a simple system to manage student information and their grades. You can define students, add grades, calculate averages, and check passing status using custom classes.

---

## How It Works

The project consists of two core classes:

* **`Student` Class:**
    * **`__init__(self, name, year)`**: Initializes a new student with a `name`, their `year` level, and an empty list to store their `grades`.
    * **`add_grade(self, grade)`**: Adds a `Grade` object to the student's list of grades, ensuring only valid `Grade` objects are added.
    * **`get_average(self)`**: Calculates and returns the student's average grade.
    * **`add_grades(self, scores)`**: A convenient method to add multiple grades at once by taking a list of scores and creating `Grade` objects for each.
    * **`__str__(self)`**: Provides a user-friendly string representation of the `Student` object, including their name, year, and average grade.

* **`Grade` Class:**
    * **`minimum_passing`**: A class variable set to `65`, representing the minimum score required to pass.
    * **`__init__(self, score)`**: Initializes a new grade with a `score`.
    * **`is_passing(self)`**: Returns `True` if the grade's score meets or exceeds the `minimum_passing` score, otherwise `False`.

The script then creates instances of `Student` and `Grade` classes, adds some sample grades, and prints the student information, showcasing the functionality of the classes.

---

## Getting Started

### Prerequisites

You'll only need **Python 3** installed on your computer to run this script.

### Installation

No special installation is required. Just save the code to a `.py` file.

1.  **Save the code:** Copy the entire code block provided and save it as `school_system.py` (or any other name ending with `.py`) on your computer.

---

## Usage

1.  **Open your terminal or command prompt.**
2.  **Navigate to the directory** where you saved `school_system.py`.
    ```bash
    cd path/to/your/project
    ```
3.  **Run the script** using Python:
    ```bash
    python school_system.py
    ```
4.  The script will print the details of the three sample students (`Pieter`, `Sandro`, and `Roger`), including their names, years, and calculated average grades.

---

## Code

Here's the full code for the Student and Grade Management System:

```python
class Student():
  def __init__(self, name, year):
    self.name = name
    self.year = year
    self.grades = []

  def add_grade(self, grade):
    # Ensure that only instances of the Grade class can be added
    if type(grade) is Grade:
      self.grades.append(grade)

  def get_average(self):
    if not self.grades: # Handle case where there are no grades
      return 0
    total = sum(grade.score for grade in self.grades)
    return total / len(self.grades)

  def __str__(self):
    # Format average grade to two decimal places
    return f"{self.name}, Year: {self.year}, Average Grade: {self.get_average():.2f}"

  def add_grades(self, scores):
    # Helper method to add multiple scores easily
    for score in scores:
      self.add_grade(Grade(score))

class Grade():
  minimum_passing = 65 # Class variable for minimum passing score

  def __init__(self, score):
    self.score = score

  def is_passing(self):
    # Check if the individual grade is passing
    return self.score >= Grade.minimum_passing

# --- Example Usage ---

# Create student instances
roger = Student('Roger van der Weyden', 10)
sandro = Student('Sandro Botticelli', 12)
pieter = Student('Pieter Bruegel the Elder', 8)

# Add grades to students using the convenient add_grades method
pieter.add_grades([100, 90, 80])
sandro.add_grades([90, 80, 70])
roger.add_grades([65, 65, 55])

# Print student details (uses the __str__ method)
print(pieter)
print(sandro)
print(roger)

# You could also manually add grades:
# new_grade_for_roger = Grade(70)
# roger.add_grade(new_grade_for_roger)
# print(f"Roger's new average: {roger.get_average():.2f}")

# Check if a specific grade is passing
# sample_grade = Grade(60)
# print(f"Is 60 a passing grade? {sample_grade.is_passing()}")
```

---

## Learning Context & Credits

This project was developed as part of the **"Learn Python 3"** (specifically focusing on Object-Oriented Programming) curriculum on [Codecademy](https://www.codecademy.com/). It provided hands-on experience with:

* **Classes and Objects:** Defining custom data types (`Student`, `Grade`) and creating instances of them.
* **Constructors (`__init__`)**: Initializing object attributes.
* **Instance Methods:** Functions that operate on object instances (e.g., `add_grade`, `get_average`, `is_passing`).
* **Class Variables:** Attributes shared across all instances of a class (`minimum_passing`).
* **Special Methods (`__str__`)**: Customizing how objects are represented as strings.
* **Encapsulation:** Bundling data (attributes) and methods that operate on the data within a single unit (the class).

---

## Future Enhancements (Ideas for Improvement)

This is a great foundation for a more comprehensive school management system. Here are some ideas for how you could expand upon it:

* **School/Course Class:** Create a `School` or `Course` class to manage multiple `Student` objects, or assign students to specific courses.
* **Grade Book:** Implement a way to store and retrieve grades for specific subjects or assignments.
* **File Persistence:** Save and load student and grade data to/from a file (e.g., CSV, JSON) so that data isn't lost when the program exits.
* **User Interface:** Create a command-line interface (CLI) or a simple graphical user interface (GUI) to interact with the system.
* **Error Handling:** Add more robust error handling, such as validating input scores to be within a reasonable range.
* **Reporting:** Generate more detailed reports, such as a list of all failing students, or top performers.

---
