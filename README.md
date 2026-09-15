import sys
import math
import random
import functools
 
print = functools.partial(print, flush=True)
 
#HELPER FUNCTIONS
def get_float(prompt):
    while True:
        try:
            print(prompt, end="", flush=True)
            sys.stdout.flush()
            return float(input())
        except ValueError:
            print(" >> Invalid input. Please enter a number (e.g.: 3, ,3.5 5, -2).")
        except EOFError:
            print("\n >> No input received. Exiting program.")
            raise SystemExit
 
 
def get_int(prompt):
    while True:
        try:
            print(prompt, end="", flush=True)
            sys.stdout.flush()
            return int(input())
        except ValueError:
            print(" >> Invalid input. Please enter a number (e.g.: 5, 3, -2, 0)")
        except EOFError:
            print("\n >> No input received. Exiting program.")
            raise SystemExit
 
def safe_input(prompt):
        try:
            print(prompt, end="", flush=True)
            sys.stdout.flush()
            return input()
        except EOFError:
            print("\n >> No input received. Exiting program.")
            raise SystemExit
       
def pause():
    safe_input("\nPress ENTER to return to the menu...")
 
 
def print_header(title):
    print("\n" + "=" * 70)
    print(f"{title}")
    print("=" * 70)
 
# SECTION 1 TRIGOMETRIC (CIRCULAR) FUNCTIONS
def trig_menu():
    print_header("TRIGONOMETRIC (CIRCULAR) FUNCTIONS")
    print("""
1. Show the value of pi
2. Convert degrees -> radians
3. Convert radians -> degrees
4. Compute sin, cos, tan of an angle (The user must enter a number in degrees)
5. Compute asin, acos, atan of a value (-1 to 1 for asin/acos)
0. Back to main menu
""")
 
    choice = safe_input("Enter your choice: ").strip()
 
    if choice == "1":
        print(f"\nmath.pi = {math.pi}")
 
    elif choice == "2":
        deg = get_float("Enter an angle in degrees: ")
        rad = math.radians(deg)
        print(f"\n{deg} degrees = {rad} radians")
 
    elif choice == "3":
        rad = get_float("Enter an angle in radians: ")
        deg = math.degrees(rad)
        print(f"\n{rad} radians = {deg} degrees")
 
    elif choice == "4":
        deg = get_float("Enter an angle in degrees: ")
        rad = math.radians(deg)
        print(f"\nAngle = {deg} degrees ({rad} radians)")
        print(f"sin({deg}) = {math.sin(rad)}")
        print(f"cos({deg}) = {math.cos(rad)}")
        print(f"tan({deg}) = {math.tan(rad)}")
 
    elif choice == "5":
        val = get_float("Enter a value: ")
        print()
        try:
            print(f"asin({val}) = {math.asin(val)} radians "
                  f"({math.degrees(math.asin(val))} degrees)")
        except ValueError:
            print("asin(x) needs -1 <= x <= 1. Skipped.")
 
        try:
            print(f"acos({val}) = {math.acos(val)} radians "
                  f"({math.degrees(math.acos(val))} degrees)")
        except ValueError:
            print("acos(x) needs -1 <= x <= 1. Skipped.")
        print(f"atan({val}) = {math.atan(val)} radians "
                f"({math.degrees(math.atan(val))} degrees)")
 
    elif choice == "0":
        return
 
    else:
        print("\nInvalid Choice.")
 
    pause()
 
# SECTION 2 HYPERBOLIC FUNCTIONS
def hyperbolic_menu():
    print_header ("HYPERBOLIC FUNCTIONS")
    print ("""
1. Compute sinh, cosh, tanh of a value
2. Compute asinh, acosh, atanh of a value (acosh needs x >= 1, atanh needs -1 < x < 1)
0. Back to main menu
""")
 
    choice = safe_input("Enter your choice: ").strip()
   
    if choice == "1":
        val = get_float("Enter a value x: ")
        print (f"\nsinh({val}) = {math.sinh(val)}")
        print (f"cosh({val}) = {math.cosh(val)}")
        print (f"tanh({val}) = {math.tanh(val)}")
 
    elif choice == "2":
        val = get_float("Enter a value x: ")
        print()
        print (f"asinh({val}) = {math.asinh(val)}")
        try:
            print (f"acosh({val}) = {math.acosh(val)}")
        except ValueError:
            print ("acosh(x) needs x >= 1. Skipped.")
        try:
            print (f"atanh({val}) = {math.atanh(val)}")
        except ValueError:
            print ("atanh(x) needs -1 < x < 1. Skipped.")
 
    elif choice == "0":
        return
 
    else:
        print ("\nInvalid Choice.")
 
    pause()
 
# SECTION 3 EXPONENTIATION AND LOGARITHMS FUNCTIONS
def exponent_menu():
    print_header ("EXPONENTIATION AND LOGARITHMS FUNCTIONS")
    print ("""
1. Show the value of e
2. Compute exp (x)
3. Compute the natural log, log10, log2 of a value
4. Compute log(x, base) with a custom base
5. Compute pow(x, y) - built-in vs math.pow
0. Back to main menu
""")
 
    choice = safe_input ("Enter your choice: ").strip()
 
    if choice == "1":
        print (f"\nmath.e = {math.e}")
 
    elif choice == "2":
        x = get_float("Enter x: ")
        print (f"nexp ({x}) = e^{x} = {math.exp(x)}")
 
    elif choice == "3":
        x = get_float("Enter a positive number x: ")
        try:
            print (f"\nlog({x}) = {math.log(x)} (natural log, base e)")
            print (f"log10({x}) = {math.log10(x)")
            print (f"log2({x}) = {math.log2(x)}")
        except ValueError:
            print ("Logarithms require x > 0. Please try again.")
 
    elif choice == "4":
        x = get_float("Enter x (must be > 0): ")
        b = get_float("Enter the base b (must be > 0 and != 1): ")
        try:
            print (f"\nlog({x}), base = {b} = {math.log(x, b)}")
        except (ValueError, ZeroDivisionError):
            print ("Invalid input for for a logarithm with that base.")
 
    elif choice == "5":
        x = get_float("Enter the base x: ")
        y = get_float("Enter the exponet y: ")
        print (f"Built-in pow({x}, {y}) = {pow(x, y)}")
        print (f"math.pow({x}, {y}) = {math.pow(x, y)}")
        print ("(Note: pow( can return an int for integer inputs); "
               "math.pow() always returns a float.)")
 
    elif choice == "0":
        return
 
    else:
        print ("\nInvalid Choice")
 
    pause()
 
    # SECTION 4 GENERAL-PURPOSE MATH FUNCTIONS
def general_menu():
    print_header("GENERAL-PURPOSE MATH FUNCTIONS")
    print("""
1. Compute ceil, floor, and trunc of a value
2. Compute a factorial
3. Compute the hypotenuse of a right triangle
0. Back to Main Menu
""")
 
    choice = safe_input("Enter your choice: ").strip()
 
    if choice == "1":
        x = get_float("Enter a decimal number x: ")
        print(f"\nValue = {x}")
        print(f"math.ceil({x}) = {math.ceil(x)}")
        print(f"math.floor({x}) = {math.floor(x)}")
        print(f"math.trunc({x}) = {math.trunc(x)}")
 
    elif choice == "2":
        n = get_int("Enter a non-negative whole number: ")
        try:
            print(f"\n.{n}! = {math.factorial(n)}")
        except ValueError:
            print("factorial() requires a non-negative integer.")
 
    elif choice == "3":
        x = get_float("Enter the length of side x: ")
        y = get_float("Enter the length of side y: ")
        print(f"\n.hypot({x}, {y}) = {math.hypot(x, y)}")
        print (f"(same idea as sqrt({x}**2 + {y}**2)"
        f"{math.sqrt(x**2 + y**2)}, but hypot() is more precise.)")
 
    elif choice == "0":
        return
 
    else:
        print("\nInvalid Choice.")
 
    pause()
# SECTION 5: THE RANDOM MODULE 
def random_menu():
    print_header ("THE RANDOM MODULE")
    print("""
1. Set a seed (so results can be repeated)
   2. Generate a number with randrange()
   3. Generate a number with randint()
   4. Pick a random item from a list with choice ()
   5. Draw several UNIQUE items from a list with sample() (like a lottery)
   0. Back to Main Menu
""")
    choice = safe_input("Enter your choice: ").strip()

    if choice == "1":
        pick = safe_input("Type 'time' to seed with current time, or type an "
                    "integer to seed manually: ").strip()
        if pick.lower() == "time":
            random.seed()
            print("\nSeed set using the current time. Every run will now "
                  "differ.")
        else:
            try:
                random.seed()
                print(f"\nSeed set to {int(pick)}. The random sequence"
                      f"produced from now on is repeatable.")
            except ValueError:
                print("\nInvalid integer. Seed not changed.")
     elif choice == "2":
         print("Choose a form:  1) randrange(end)  2) randrange (beg,end)" 
               "   3) randrange(beg, end, step)")
         form = safe_input("Form (1/2/3): ").strip()
         if form == "1":
             end = get_int("Enter end: ")
             print(f"\nrandom.randrange({end}.0) = (random.randrage(end)}")
         elif choice == "2"
             beg = get_int("Enter beg:")
             end = get_int("Enter end")
             print(f\nrandom.randrage({beg}), (end), {step}) +"
             f'(random.randrange(beg, end, step)}")

         else:
             print("\invalid form.")

         elif
             choice == "3":
             left = get_int ("Enter the left(lowest) bound:")
             right = get_int ("Enter the right (highest)")
             try:
              print(f"nrandom.randint ({left}, {right}) = "
              f"{random.randint({left}, {right})")
              print("(Both endpoints are possible outcomes.)")
             except ValueError:
              print("\nleft must be <= right.")

             elif choice == "4":
              raw = safe_input("Enter items sepearted byc commas (e.g., apple, banana,""cherry) ")
              if items:
                  print(f"nYour list: {items}")
                  print(f'nrandom.choice (list) picked: {random.choice(items)}")
              else:
                  print ("\nYou din't enter any items.")

              elif choice =="5":          
