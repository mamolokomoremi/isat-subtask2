import random

# Function 1: Decimal to Binary
def decimal_to_binary(decimal_num):
    """
    Converts an integer decimal number to its binary equivalent as a string.
    """
    if not isinstance(decimal_num, int):
        return "Invalid input: Please enter an integer."
    if decimal_num == 0:
        return "0"
    
    binary_str = ""
    temp_num = decimal_num
    while temp_num > 0:
        remainder = temp_num % 2
        binary_str = str(remainder) + binary_str
        temp_num //= 2
    return binary_str

# Function 2: Binary to Decimal
def binary_to_decimal(binary_str):
    """
    Converts a string of binary digits to its integer decimal equivalent.
    """
    if not isinstance(binary_str, str) or not all(c in '01' for c in binary_str):
        return "Invalid input: Please enter a valid binary string (containing only 0s and 1s)."
    
    decimal_num = 0
    power = 0
    for digit in reversed(binary_str):
        if digit == '1':
            decimal_num += 2 ** power
        power += 1
    return decimal_num

# Function 3: Decimal to Hexadecimal
def decimal_to_hexadecimal(decimal_num):
    """
    Converts an integer decimal number to its hexadecimal equivalent as a string.
    """
    if not isinstance(decimal_num, int):
        return "Invalid input: Please enter an integer."
    if decimal_num == 0:
        return "0"
    
    hex_digits = "0123456789ABCDEF"
    hex_str = ""
    temp_num = decimal_num
    while temp_num > 0:
        remainder = temp_num % 16
        hex_str = hex_digits[remainder] + hex_str
        temp_num //= 16
    return hex_str

# Function 4: Hexadecimal to Decimal
def hexadecimal_to_decimal(hex_str):
    """
    Converts a string of hexadecimal digits to its integer decimal equivalent.
    """
    if not isinstance(hex_str, str) or not all(c in "0123456789ABCDEFabcdef" for c in hex_str):
        return "Invalid input: Please enter a valid hexadecimal string."
    
    decimal_num = 0
    power = 0
    hex_map = {digit: value for value, digit in enumerate("0123456789ABCDEF")}
    
    for digit in reversed(hex_str.upper()): # Convert to upper for consistent mapping
        decimal_num += hex_map[digit] * (16 ** power)
        power += 1
    return decimal_num

# Menu Driven Command Line Interface
def display_menu():
    print("\nConversion Menu:")
    print("1. Convert Decimal to Binary")
    print("2. Convert Binary to Decimal")
    print("3. Convert Decimal to Hexadecimal")
    print("4. Convert Hexadecimal to Decimal")
    print("5. Demo (Generate and convert random integers to binary)")
    print("6. Exit")

def main():
    while True:
        display_menu()
        choice = input("Enter your choice (1-6): ")

        if choice == '1':
            try:
                dec_num = int(input("Enter a decimal number: "))
                binary_result = decimal_to_binary(dec_num)
                print(f"Binary representation: {binary_result}")
            except ValueError:
                print("Invalid input: Please enter a valid integer.")
        elif choice == '2':
            binary_input = input("Enter a binary number: ")
            decimal_result = binary_to_decimal(binary_input)
            if isinstance(decimal_result, str): # Check if it's an error message
                print(decimal_result)
            else:
                print(f"Decimal representation: {decimal_result}")
        elif choice == '3':
            try:
                dec_num = int(input("Enter a decimal number: "))
                hex_result = decimal_to_hexadecimal(dec_num)
                print(f"Hexadecimal representation: {hex_result}")
            except ValueError:
                print("Invalid input: Please enter a valid integer.")
        elif choice == '4':
            hex_input = input("Enter a hexadecimal number: ")
            decimal_result = hexadecimal_to_decimal(hex_input)
            if isinstance(decimal_result, str): # Check if it's an error message
                print(decimal_result)
            else:
                print(f"Decimal representation: {decimal_result}")
        elif choice == '5':
            random_num = random.randint(0, 99)
            print(f"Generated random integer: {random_num}")
            binary_rand = decimal_to_binary(random_num)
            print(f"Binary representation: {binary_rand}")
        elif choice == '6':
            print("Exiting the program.")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 6.")

if __name__ == "__main__":
    main()# Write your code here :-)
