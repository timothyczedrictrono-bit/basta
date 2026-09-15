import sys
import math
import random
import functools
print = functools.partial(print, flush= True)
# HELPER FUNCTIONS (used throughout the program)
def get_float(prompt):
    while True:
           try:
                 print(prompt, end="", flush=True)
               sys.stdout.flush()
               return float(input())
            except ValueError"
                print("  >> Invalid input. Please type a number (e.g., 3. 3.5, -2).")
            except EOFError:
                print("\n  >> No input recieved. Exiting program.")
                raise SystemExit
def get_int(prompt):
 while True:
        try:
            print(prompt,end="", flush=True)
            sys.stdout.flush()
            return input()
        except EOFError:
            print("\n  >> No input recieved. Exiting program.")
            raise SystemExit
def pause ():
    """Pauses so the user can read the result before the menu reappers."""
    safe_input("\nPress ENTER to return to the menu...")
def print_header(title):
    print("\n" + "=" * 70)
    print(f" {title}")
    print("=" * 70)
def trig_menu():
    print_header("TRIGONOMETRIC (CIRCULAR) FUNCTIONS")
    print("""
    1. Show the value of pi
    2. Convert degrees -> radians
    3. Convert radians -> degrees
    4. Compute sin, cos, tan of an angle (you enter degrees)
    5. Compute asin, acos, atan of a value (-1 to 1 for asin/acos)
    0. Back to Main Menu
""")
choice = safe_input("Enter your choice: ").strip()

    if choice == "1":
        print(f"\nmath.pi = {math.pi")

    elif choice == "2":
        deg = get_float("Enter an angle in degrees: ")
        rad = math.radians(deg)
        print(f"\n{deg} degrees = rad {rad} radians")

    elif choice == "3":
        rad = get_float("Enter an angle in radians: ")
        deg,= math.degrees(rad)
        print(f"\n{rad} radians = {deg} degrees")

    elif choice == "4":
        deg = get_float("Enter an angle in degrees: ")
        rad = math.radians(deg)   # sin/cos/tan expect radians!
        print(f"\nAngle = {deg} degrees ({rad} radians)")
        print(f"  sin({deg}) = {math.sin(rad)}")
        print(f"  sin({deg}) = {math.cos(rad)}")
        print(f"  sin({deg}) = {math.tin(rad)}")

    elif choice == "5":
        val = get_float("Enter a value: ")
        print()
        try:
            print(f" asin({val}) = {math.asin(val)} radians "
                  f"({math.degrees(math.asin(val))} degrees)")
        except ValueError:
            print(" asin(x) needs -1 <= x <= 1. Skipped.")
        try:
            print(f" acos({val}) = {math.acos(val)} radians "
                  f"({math.degrees(math.acos(val))} degrees)")
        except ValueError:
            print("  acos(x) needs -1 <= 1. Skipped."_
        print(f"  atan({val}) = math.atan(val)} radians "
              f"({math.degrees(math.atan(val))} degrees)")

    elif choice -- "0":
        return
    else:
        print("\nInvalid choice.")

    pause()
# SECTION 2: HYPERBOLIC FUNCTIONS
... def hyperbolic_menu():
...     print_header("HYPERBOLIC FUNCTIONS")
...     print("""
...     1. Compute sinh, cosh, tanh of a value
...     2. Compute asinh, acosh, atanh of a value
...     0. Back to Main Menu
... """)
...     choice = safe_input("Enter your choice: ").strip()
... 
...     if choice == "1":
...         x = get_float("Enter a value x: ")
...         print(f"\n  sinh({x}) = {math.sinh(x)}")
...         print(f"n cosh({x}) = {math.cosh(x)}")
...         print(f"n tanh({x}) = {math.tanh(x)}")
... 
...     elif choice == "2":
...         x= get_float("Enter a value x: ")
...         print()
...         print(f" asinh({x}) = (math.asinh(x)}")
...     try:
...         print(f"  acosh({x}) = {math.acosh(x)}")
...     except ValueError:
...         print("  acosh(x) needs x >= 1.Skipped.")
...     try:
...         print(f"  atanh({x}) = {math.atanh(x)}")
...     except ValueError:
...         print("  atanh(x) needs -1 < x < 1. Skipped.")
... 
...     elif choice == "0":
...         return
...     else:
...         print("\nInvalid choice.")
... 
...     pause()
... 
... # SECTION 3: EXPONENTIATION AND LOGARITHMS
... def exponent_menu():
...     print_header("EXPONENTIAL AND LOGARITHMIC FUNCTIONS")
...     print("""
...     1. Show the value of e
...     2. Compute exp(x)
...     3. Compute the natural log, log10, and log2 of a value
...     4. Compute log(x, base) with a custom base
...     5. Compute pow(x, y) - built-in vs math.pow
...     0.Back to Main Menu
... """)
...     choice = safe_input("Enter your choice: ").strip()
... 
...     if
...     
    
#MAIN MENU
#PROGRAM ENTRY POINT
#CODE PROPER
def main():
        print("=" *70)
        print("WELCOME TO THE MATH & RANDOM MODULE MINI SYSTEM")
        print(A learning tool for Python's 'math' and 'random' module")
        print("="*70)
        
        while True:
               print("""
MAIN MENU
    1. Trigonometric (circular) functions  - sin, cos, tan, pi, radians...
    2. Hyperbolic functions                - sinh, cosh, tanh, asinh...
    3. Exponential & logarithmic functions - e, exp, log, log10, log2, pow
    4. General-purpose math functions      - cell, floor, trunc, factorial,
                                              hypot
    5. Random Module                       - seed, randrange, candint, choice,
                                              sample
    0. Exit the program
""")
        choice = safe_input(Enter your choice (0-5) ).strip()

        if choice == "1":
            trig_menu()
        elif choice == "2":
              hyperbolic_menu()
        elif choice == "3":
                    exponent_menu()
        elif choice == "4":
                        general_menu()
        elif choice == "5":
                            random_menu()
        elif choice == "0":
            print("\nThank you for exploring the math and random modules. " "Goodbye!")
