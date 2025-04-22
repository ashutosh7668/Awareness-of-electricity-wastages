# Awareness-of-electricity-wastages
Awareness of electricity wastage
import csv

def collect_survey():
    fields = ['Name', 'Age', 'Are you aware of electricity wastage? (Yes/No)', 
              'What steps do you take to save electricity?', 
              'Do you think awareness needs to be increased? (Yes/No)']
    
    filename = "electricity_wastage_survey.csv"

    with open(filename, 'a', newline='') as csvfile:
        writer = csv.writer(csvfile)
        
        try:
            with open(filename, 'r') as checkfile:
                if checkfile.readline() == '':
                    writer.writerow(fields)
        except FileNotFoundError:
            writer.writerow(fields)

        while True:
            name = input("Enter your name: ")
            age = input("Enter your age: ")
            aware = input("Are you aware of electricity wastage? (Yes/No): ")
            steps = input("What steps do you take to save electricity?: ")
            increase_awareness = input("Do you think awareness needs to be increased? (Yes/No): ")

            writer.writerow([name, age, aware, steps, increase_awareness])

            cont = input("Do you want to add another response? (Yes/No): ").lower()
            if cont != 'yes':
                break

    print("Survey data saved successfully.")

collect_survey()
