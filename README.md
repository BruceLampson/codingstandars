Proposal for Rain's coding standards
====================================

The following document provides guidelines for code formatting and documentation to all RAIN developers. 
Our goal is to keep code's style consistent across all RAIN repositories. We have an open door policy. Feel free to submit a pull request if you wish to contribute.

##Topics covered
1. File Formatting
2. Naming Conventions
3. Coding Style
4. Inline Documentation

#### This document attempts to follow [RFC 2119's](http://www.ietf.org/rfc/rfc2119.txt) verbosity for indicating requirements.
- **MUST** and **MUST NOT** indicate non-optional requirements
- **SHOULD** and  **SHOULD NOT** indicate recommendations for which exceptions may exist
- **MAY** indicates truly optional requirements

####Indentation
Indentation **MUST** consist of 4 spaces. Tabs **MUST NOT** be used for indentation.

####Namespaces
Namespaces **SHOULD** be MixedCase, and acronyms used in namespaces **SHOULD** as well. As examples:
    
    - The namespace "Rain\PDF" would not be allowed, while "Rain\Pdf" is acceptable.
    - The namespace "Rain\JSON" would not be allowed, while "Rain\Json" is acceptable.

####Acceptable File names
All files **MUST** only use alphanumeric characters, underscores, and the dash character ("-"). Spaces are strictly prohibited.

####Functions and Methods
Function names **MUST** contain only alphanumeric characters. Underscores are not permitted. Numbers are permitted in function names but are discouraged.
Function names **MUST** always start with a lowercase letter. When a function name consists of more than one word, the first letter of each new word **MUST** be capitalized. This is commonly called "camelCase" formatting.
Verbosity is encouraged. Function names should be as verbose as is practical to fully describe their purpose and behavior.

These are examples of acceptable names for functions:
    
    doSomething();
    ringTheBell();
    callUser();

The following are examples of unacceptable function names:
    
    DoSomething();
    RINGTHEBELL();
    Call_user();

####Variables
Variable names **MUST** contain only alphanumeric characters. Underscores are not permitted. Numbers are permitted in variable names but are discouraged in most cases.

As with function names, variable names **MUST** always start with a lowercase letter and follow the "camelCaps" capitalization convention.

Verbosity is encouraged. Variables should always be as verbose as practical to describe the data that the developer intends to store in them. Terse variable names such as "$i" and "$n" are discouraged for all but the smallest loop contexts. If a loop contains more than 20 lines of code, the index variables should have more descriptive names.