# North Metro Software Python Coding Standards

## Introduction

These coding standards are designed for beginner Python students at North Metro Software. They are based on PEP 8, the official style guide for Python code, with some specific rules to help you write clean, readable, and consistent code.

## General Guidelines

1. Follow PEP 8 guidelines whenever possible. You can find the full PEP 8 documentation [here](https://www.python.org/dev/peps/pep-0008/).
2. Use 4 spaces for indentation. Do not use tab characters (the tab key is generally fine!).
3. Limit all lines to a maximum of 79 characters for code and 72 for comments and docstrings.
4. Use UTF-8 encoding for your Python files.

## Naming Conventions

1. Variables and Functions:
   - Always use lowercase for variables and functions.
   - Use underscores to separate words in multi-word names (snake_case).
   - Examples:

     ```python
     user_name = "Sandeep"
     def calculate_total_price():
         pass
     ```

2. Constants:
   - Use all uppercase letters for constants.
   - Use underscores to separate words.
   - Example:

     ```python
     MAX_ATTEMPTS = 3
     PI = 3.14159
     ```

3. Classes:
   - Use CamelCase (capitalize the first letter of each word) for class names.
   - Example:

     ```python
     class UserAccount:
         pass
     ```

## Naming Best Practices

1. Functions should start with a verb:

   ```python
   def calculate_average():
       pass

   def print_report():
       pass
   ```

2. Variables should be nouns:

   ```python
   total_score = 0
   user_input = input("Enter your name: ")
   ```

3. Use English words and avoid contractions:

   ```python
   # Good
   number_of_users = 10
   is_valid = True

   # Avoid
   num_users = 10
   isValid = True
   ```

4. Choose descriptive and unambiguous names:

   ```python
   # Good
   elapsed_time_in_seconds = 5

   # Avoid
   et = 5
   ```

## Whitespace and Formatting

1. No spaces between a function name and its invocation parentheses:

   ```python
   # Correct
   print('Hello, World!')

   # Incorrect
   print ('Hello, World!')
   ```

2. Use spaces around operators and after commas:

   ```python
   # Correct
   x = 5
   y = x + 1
   numbers = [1, 2, 3, 4]

   # Incorrect
   x=5
   y=x+1
   numbers=[1,2,3,4]
   ```

3. Leave two blank lines before top-level classes and functions, and one blank line before method definitions inside a class.

## Magic Numbers

Magic numbers are numeric literals that appear in your code without explanation. They can make your code harder to understand and maintain. Instead of using magic numbers, define constants with descriptive names.

1. Avoid using magic numbers directly in your code:

   ```python
   # Incorrect
   if user_age >= 18:
       print("You are eligible to vote.")

   # Correct
   VOTING_AGE = 18
   if user_age >= VOTING_AGE:
       print("You are eligible to vote.")
   ```

2. Use all-uppercase names for constants, as mentioned in the Naming Conventions section.

3. Group related constants together at the top of your file or in a separate constants module.

## Boolean Functions and Variables

Boolean functions and variables represent true/false conditions. Following these conventions will make your code more readable and self-explanatory.

1. Naming Boolean Functions:
   - Start with verbs like `is_`, `has_`, `can_`, or `should_`.
   - The name should sound like a yes/no question when read aloud.

   ```python
   def is_adult(age):
       return age >= 18

   def has_permission(user, action):
       # Check if the user has permission to perform the action
       pass

   def can_vote(user):
       return user.age >= VOTING_AGE and user.is_registered
   ```

2. Naming Boolean Variables:
   - Use similar prefixes as boolean functions, or phrase them as adjectives.

   ```python
   is_logged_in = True
   has_subscription = False
   eligible_for_discount = total_purchases > 1000
   ```

3. Using Boolean Functions in Conditional Statements:
   - When using boolean functions in conditionals, don't compare them to True or False explicitly.

   ```python
   # Incorrect
   if is_adult(user.age) == True:
       print("You can enter.")

   # Correct
   if is_adult(user.age):
       print("You can enter.")

   # For negative conditions, use 'not'
   if not has_permission(user, 'delete'):
       print("Access denied.")
   ```

4. Avoid Double Negatives:
   - They can be confusing. Instead, rephrase your condition or variable name.

   ```python
   # Confusing
   if not is_not_valid:
       process_data()

   # Clear
   if is_valid:
       process_data()
   ```

Remember, the goal of these naming conventions is to make your code as readable and self-documenting as possible. When another programmer (or you in the future) reads `if is_adult(user.age):`, the intent is immediately clear without needing to look at the function's implementation.

## Comments and Docstrings

1. Use inline comments sparingly. They should explain why, not what.
2. Write docstrings for all public modules, functions, classes, and methods.
3. Use triple quotes for docstrings, even if they're only one line.

Example:

```python
def calculate_area(length, width):
    """
    Calculate the area of a rectangle.

    Args:
        length (float): The length of the rectangle.
        width (float): The width of the rectangle.

    Returns:
        float: The area of the rectangle.
    """
    return length * width
```

## Error Handling

1. Use try/except blocks to handle exceptions.
2. Be specific about the exceptions you're catching.

Example:

```python
try:
    number = int(input("Enter a number: "))
except ValueError:
    print("That's not a valid number!")
```

## Final Notes

1. Consistency is key. Always prioritize maintaining consistency with the existing codebase. If in doubt, ask a senior developer for guidance. Generally, refactoring solely for style consistency is not recommended.
2. Recommended: use tools like `ruff` to check your code against these standards.
3. Remember, these guidelines are meant to help you write better code, not to restrict your creativity. There may be situations where breaking a rule leads to more readable code.

Happy coding!
