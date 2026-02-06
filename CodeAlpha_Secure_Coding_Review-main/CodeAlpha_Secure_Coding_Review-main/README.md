# CodeAlpha_Secure_Coding_Review

Secure Coding Review using C++ | CodeAlpha Cyber Security Internship

Programming Language: C++

Application Audited: Simple User Authentication System

This document presents a detailed secure coding review conducted as part of a
cybersecurity-focused learning project.

1. Vulnerable Code (Before Review):
   
#include <iostream>
#include <cstring>
using namespace std;
int main() {
 char username[10];
 char password[10];
 cout << "Enter username: ";
 cin >> username;
 cout << "Enter password: ";
 cin >> password;
 if (strcmp(username, "admin") == 0 && strcmp(password, "admin123") == 0) {
 cout << "Login successful!" << endl;
 } else {
 cout << "Login failed!" << endl;
 }
 return 0;
}

Identified Vulnerabilities:
• Buffer overflow due to fixed-size character arrays
• Hardcoded credentials
• Plaintext password handling
• No input validation

3. Secure Code (After Review):

#include <iostream>
#include <string>
using namespace std;
int main() {
 string username;
 string password;
 cout << "Enter username: ";
 cin >> username;
 cout << "Enter password: ";
 cin >> password;
 const string storedUser = "admin";
 const string storedPass = "admin123";
 if (username == storedUser && password == storedPass) {
 cout << "Login successful!" << endl;
 } else {
 cout << "Login failed!" << endl;
 }
 return 0;
}

4. Security Improvements Applied:
• Replaced unsafe character arrays with std::string
• Improved memory safety
• Cleaner and more secure input handling

5. Tools & Review Methods Used
• Manual code inspection
• Static analysis tools (Cppcheck, Clang Static Analyzer)

6. Recommendations & Best Practices
• Avoid hardcoded credentials
• Use password hashing techniques
• Validate all user inputs
• Perform regular static code analysis
• Follow secure coding standards
