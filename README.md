import json

class Student:
    def _init_(self, name, subject, grade):
        self.name = name
        self.subject = subject
        self.grade = grade
    
    def display(self):
        print(f"{self.name} -> {self.subject}: {self.grade}")

students = {}
def save_to_file():
    file = open("students.txt", "w")
    json.dump(students, file)
    file.close()
    print("Data saved to file.")
def load_from_file():
    try:
        file = open("students.txt", "r")
        students = json.load(file)
        file.close()
        print("Loaded student records from file.")
    except:
        print("No previous records found. Starting fresh.")
def add_student():
    name = input("Enter student name: ")
    subject = input("Enter subject: ")
    grade = input("Enter grade: ")
    students[name] = (subject, grade)

def display_records():
    print("Student Records:")
    for name in students:
        subject, grade = students[name]
        print(f"{name} -> {subject}: {grade}")

load_from_file()
add_student()
save_to_file()
display_records()
