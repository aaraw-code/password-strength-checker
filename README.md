# password-strength-checker
 Python tool that checks the strength of a password

import string
print("🔒 PASSWORD CHECKER 🔍")

letters = string.ascii_letters
digits = string.digits
special = string.punctuation
common_passwords = ("123456", "password", "admin", "qwerty", "letmein", "abc123")


password = input("Enter password hear to check strength: ")

score = 0
tips = []

if len(password) >= 8:
    score += 1
else:
    tips.append("Make it at atleast 8 character long.")

if any(char.isupper() for char in password):
    score += 1
else:
    tips.append("Add at least one uppercase letter.")

if any(char.islower() for char in password):
    score += 1
else:
    tips.append("Add at least one lower case letter. ")

if any(char.isdigit() for char in password):
    score += 1
else:
    tips.append("Add at least one number.")

if any(char in special for char in password):
    score += 1
else:
    tips.append(f"Add special character eg: {special}")

if password.lower() not in common_passwords:
    score += 1
else:
    tips.append("Avoid common password")


if score == 6:
    level = "Strong"
elif 4 <= score < 6:
    level = "Medium"
else:
    level = "Weak"

print(f"Password Level is: {level}")
if tips:
    print('Suggestion to improve')
    for tip in tips:
        print(f"{tip}")
