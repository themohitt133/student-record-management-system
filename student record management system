# ..... STUDENTS RECORD MANAGEMENT SYSTEM ........

import csv
import os


class Student:
    all_students = []

    def __init__(self, name, student_ID, marks):
        self.name = name
        self.student_ID = student_ID
        self.marks = marks

    def update_marks(self, new_marks):
        self.marks = new_marks
        # print("Marks for {self.name} update to {self.marks}.")

    def show_details(self):
        print(f"\n Student Details : ")
        print(f"Name : {self.name}")
        print(f"Student Id : {self.student_ID}")
        print(f"Marks : {self.marks}")

    @classmethod
    def save_to_csv(cls):
        with open("student.csv", "w", newline="") as file:
            writer = csv.writer(file)
            writer.writerow(["Name" "Student_ID" "Marks"])
            for student in cls.all_students:
                writer.writerow([student.name, student.student_ID, student.marks])

    @classmethod
    def load_from_csv(cls):
        if not os.path.exists("student.csv"):
            return
        with open("student.csv", "r", newline="") as file:
            reader = csv.reader(file)
            next(reader, None)
            for row in reader:
                if len(row) == 3:
                    name, student_ID, marks = row
                    cls.all_students.append(cls(name, student_ID, marks))

    @classmethod
    def delete_student(cls, student_ID):
        student = cls.find_student_by_student_ID(student_ID)
        if student:
            cls.all_students.remove(student)
            cls.save_to_csv()
            print(f"Student {student.name} has been deleted successfully.")
        else:
            print("Student not found")

    @classmethod
    def find_student_by_student_ID(cls, student_ID):
        for student in cls.all_students:
            if student.student_ID == student_ID:
                return student
        return None

    @classmethod
    def add_students(cls):
        name = input("Enter student name : ")
        student_ID = input("Enter Student Id : ")
        marks = input("Enter student marks : ")
        if cls.find_student_by_student_ID(student_ID):
            print("Error:Student already exists!")
            return
        student = cls(name, student_ID, marks)
        cls.all_students.append(student)
        cls.save_to_csv()
        print(f"Student {name} added successfully !")

    @classmethod
    def update_student_marks(cls):
        student_ID = input("Enter student Id to update marks : ")
        student = cls.find_student_by_student_ID(student_ID)
        if Student:
            new_marks = int(input("Enter new marks : "))
            student.update_marks(new_marks)
            cls.save_to_csv()
            print(f"Marks for {student.name} updated successfully!")
        else:
            print("Student not found.")

    @classmethod
    def show_all_students(cls):
        if not cls.all_students:
            print("No student found.")
            return
        for student in cls.all_students:
            student.show_details()


def menu():
    while True:
        print(
            "\n ================== Welcome to Student Record Management System ===================="
        )
        print("1. Add Student")
        print("2. Update Marks")
        print("3. Show all Students")
        print("4. Delete Student")
        print("5. Exit")

        choice = input("Enter Your Option(1-5) : ")
        if choice == "1":
            Student.add_students()
        elif choice == "2":
            Student.update_student_marks()
        elif choice == "3":
            Student.show_all_students()
        elif choice == "4":
            student_ID = input("Enter Student ID to delete : ")
            Student.delete_student(student_ID)
        elif choice == "5":
            print("Exiting Student Record Management System.Thank You !")
            break
        else:
            print("Invalid Choice.Please try again.")


if __name__ == "__main__":
    Student.load_from_csv()
    menu()
