import csv
import os

DATA_FILE = "budget_data.csv"
HEADER = ["Date", "Category", "Type", "Amount"]

def initialize_data_file():
    if not os.path.exists(DATA_FILE):
        with open(DATA_FILE, mode="w", newline="") as file:
            writer = csv.writer(file)
            writer.writerow(HEADER)

def add_entry():
    date = input("Enter the date (DD-MM-YYYY): ")
    category = input("Enter the category: ")
    entry_type = input("Enter type (Income/Expense): ").capitalize()
    amount = float(input("Enter the amount: "))

    with open(DATA_FILE, mode="a", newline="") as file:
        writer = csv.writer(file)
        writer.writerow([date, category, entry_type, amount])
    print("Entry added successfully.")

def calculate_budget():
    income = 0
    expenses = 0

    with open(DATA_FILE, mode="r") as file:
        reader = csv.DictReader(file)
        for row in reader:
            if row["Type"] == "Income":
                income += float(row["Amount"])
            elif row["Type"] == "Expense":
                expenses += float(row["Amount"])

    budget = income - expenses
    return budget

def analyze_expenses():
    expenses_by_category = {}

    with open(DATA_FILE, mode="r") as file:
        reader = csv.DictReader(file)
        for row in reader:
            if row["Type"] == "Expense":
                category = row["Category"]
                amount = float(row["Amount"])
                if category in expenses_by_category:
                    expenses_by_category[category] += amount
                else:
                    expenses_by_category[category] = amount

    return expenses_by_category

initialize_data_file()

while True:
    print("\nPersonal Budget Tracker")
    print("1. Add Entry")
    print("2. Calculate Budget")
    print("3. Analyze Expenses by Category")
    print("4. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        add_entry()
    elif choice == "2":
        budget = calculate_budget()
        print(f"Your current budget is: ${budget:.2f}")
    elif choice == "3":
        expenses_by_category = analyze_expenses()
        print("\nExpenses by Category:")
        for category, amount in expenses_by_category.items():
            print(f"{category}: ${amount:.2f}")
    elif choice == "4":
        print("Exiting the Budget Tracker. Goodbye!")
        break
    else:
        print("Invalid choice. Please choose a valid option.")
