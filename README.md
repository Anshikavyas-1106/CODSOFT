# CODSOFT
''''__________TASK 1 - TO-DO LIST APPLICATION__________
import tkinter as tk
from tkinter import messagebox

class ToDoList:
    def __init__(self, root):
        self.root = root
        self.tasks = []
        self.task_number = 0

        self.task_entry = tk.Entry(root, width=50)
        self.task_entry.pack()

        self.add_button = tk.Button(root, text="Add Task", command=self.add_task)
        self.add_button.pack()

        self.tasks_frame = tk.Frame(root)
        self.tasks_frame.pack()

    def add_task(self):
        task_description = self.task_entry.get()
        if task_description:
            self.tasks.append(task_description)
            self.display_tasks()
            self.task_entry.delete(0, tk.END)
        else:
            messagebox.showwarning("Warning", "Task description cannot be empty.")

    def display_tasks(self):
        for widget in self.tasks_frame.winfo_children():
            widget.destroy()

        for i, task in enumerate(self.tasks):
            task_frame = tk.Frame(self.tasks_frame)
            task_frame.pack(fill=tk.X)

            tk.Label(task_frame, text=task).pack(side=tk.LEFT)
            tk.Button(task_frame, text="Done", command=lambda task_number=i: self.mark_as_done(task_number)).pack(side=tk.RIGHT)
            tk.Button(task_frame, text="Delete", command=lambda task_number=i: self.delete_task(task_number)).pack(side=tk.RIGHT)

    def mark_as_done(self, task_number):
        self.tasks[task_number] = f"[Done] {self.tasks[task_number]}"
        self.display_tasks()

    def delete_task(self, task_number):
        del self.tasks[task_number]
        self.display_tasks()

def main():
    root = tk.Tk()
    root.title("To-Do List")
    todo = ToDoList(root)
    root.mainloop()

if __name__ == "__main__":
    main()

**************************************************************************************************************************************************************************
'''______________TASK - 2 CALCULATOR PROGRAM______________'''
def add(x,y):
    return x + y
def subtract(x,y):
    return x - y
def multiply(x,y):
    return x * y
def divide(x,y):
    if y == 0:
        return "Error! Division by zero."
    return x / y
def calculator():
    print("Simple Calculator")
    print("1. Addition")
    print("2. Subtraction")
    print("3. Multiplication")
    print("4. Division")
    choice = input("Enter your choice (1/2/3/4): ")
    if choice in ['1', '2', '3', '4']:
        num1 = float(input("Enter first number: "))
        num2 = float(input("Enter second number: "))
        if choice == '1':
           print(f"{num1} +{num2} = {add(num1, num2)}")
        elif choice == '2':
             print(f"{num1} - {num2} = {subtract(num1, num2)}")
        elif choice == '3':    
             print(f"{num1} * {num2} = {multiply(num1, num2)}")
        elif choice == '4':
             print(f"{num1} / {num2} = {divide(num1, num2)}")
    else:
        print("Invalid choice.Please try again.")
def main():
    calculator()
    again = input("Do you want to perform another calculation? (yes/no): ")
    if again.lower() == 'yes':
        main()
    else:
        print("Goodbye!")
if __name__ == "__main__":
    main()

****************************************************************************************************************************************************************************
'''__________________TASK - 3 PASSWORD GENERATOR__________________'''
import random
import string

length = int(input("Enter the length of the password: "))

lower = string.ascii_lowercase
upper = string.ascii_uppercase
numbers = string.digits
special = string.punctuation

all_characters = lower + upper + numbers + special
temp = random.sample(all_characters, length)
password = "".join(random.sample(all_characters, length))
print("Generated password:", password)

