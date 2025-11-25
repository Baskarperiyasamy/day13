# day13

Creating Virtual Environment
Objective:
The objective of this task is to establish a clean, isolated development environment using a Python virtual environment and essential packages for development.
Create the Virtual Environment:
python3 -m venv my_python_env
t creates a virtual environment in a folder named my_python_env.
Activate the Environment:
my_python_env\Scripts\activate
This command activates Python virtual environment on Windows.
Install Required Packages:
pip install requests numpy
his installs two Python packages into currently active virtual environment.
Verify Installation:
pip list
This confirms the virtual environment and packages are correctly set up.
Scripting variables
Objective:
The objective here is to write a basic Python script that demonstrates the creation of variables, performing arithmetic operations, and explicitly converting data types.
Create Script:
num1 = 10         
num2 = 5.5         
text = "20"        
sum1 = num1 + num2
print("Sum of integer and float:", sum1)
num3 = int(text)
final_result = sum1 + num3
print("Final Result:", final_result)
print("Type of final result:", type(final_result))
Summary:
This script creates variables, performs arithmetic with integers and floats, converts a numeric string to an integer, and prints the final result along with its data type.
Building a Calculator
Objective:
The objective is to apply fundamental programming concepts to build a simple calculator.
Create Script:
num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))
op = input("Enter operator (+, -, *, /): ")

if op == "+":
    result = num1 + num2
elif op == "-":
    result = num1 - num2
elif op == "*":
    result = num1 * num2
elif op == "/":

    if num2 == 0:
        print("Error: Cannot divide by zero!")
        exit()
    else:
        result = num1 / num2
else:
    print("Invalid operator")
    exit()

print("Result:", result)
Summary:
This script takes two numbers and an operator as input, performs the corresponding arithmetic operation with error handling, and prints the final result.
Building a Calculator
Objective:
To write a script that iterates through a list of IP addresses and checks their reachability using a system command (like ping), practicing loops and subprocesses.
Create Script:
import subprocess

ip_list = ["192.168.1.1", "8.8.8.8", "10.0.0.1"]

for ip in ip_list:
    result = subprocess.run(["ping", "-n", "1", ip], stdout=subprocess.PIPE, stderr=subprocess.PIPE)
    if result.returncode == 0:
        print(f"IP address {ip} is reachable.")
    else:
        print(f"IP address {ip} is unreachable.")
Functions to compute Latency
Objective:
To build reusable functions that compute key statistical summaries (average, min, max) from a set of network performance data (e.g., latency values), focusing on functions and basic data analysis.
latency_values = [20, 35, 50, 40, 25, 45, 30, 55]
def calculate_average(data):
    return sum(data) / len(data)
def get_summary(data):
    summary = {
        'Min': min(data),
        'Max': max(data),
        'Average': calculate_average(data)
    }
    return summary
result = get_summary(latency_values)
print("Network Latency Summary:", result)
Menu Driven CLI Tool
Objective:
To combine user input, conditional logic (if/else), and loops to menu for the user to the user.
import sys
import os

def ip_reachability_tester():
    ip = input("Enter IP address to test: ")
    print(f"Pretending to ping {ip}... (IP Reachability Tester called)")
    

def calculate_average(data):
    return sum(data) / len(data)

def get_summary(data):
    summary = {
        'Min': min(data),
        'Max': max(data),
        'Average': calculate_average(data)
    }
    return summary


while True:
    print("\n=== Network Utility Menu ===")
    print("1. IP Reachability Tester")
    print("2. Latency Summary") 
    print("3. Exit")

    choice = input("Enter your choice (1/2/3): ").strip()

    if choice == '1':
        ip_reachability_tester()
    elif choice == '2':
        user_input = input("Enter comma-separated latency values (e.g., 20,35,50): ")
        try:
            values = [float(x.strip()) for x in user_input.split(',')]
            summary = get_summary(values)
            print(f"Latency Summary: {summary}")
        except ValueError:
            print("Error: Please enter valid numbers separated by commas.")
    elif choice == '3':
        print("Exiting. Goodbye!")
        break
    else:
        print("Invalid choice. Please select 1, 2, or 3.")
