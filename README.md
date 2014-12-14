Proposal for Rain's coding standards
====================================

The following document provides guidelines for code formatting and documentation to all RAIN developers. 
Our goal is to keep code's style consistent across all RAIN repositories. We have an open door policy. Feel free to submit a pull request if you wish to contribute.

#####Topics covered
1. File Formatting
2. Naming Conventions
3. Coding Style
4. Inline Documentation

#####This document attempts to follow [RFC 2119's](http://www.ietf.org/rfc/rfc2119.txt) verbosity for indicating requirements.
- **MUST** and **MUST NOT** indicate non-optional requirements
- **SHOULD** and  **SHOULD NOT** indicate recommendations for which exceptions may exist
- **MAY** indicates truly optional requirements

#####Indentation
Indentation **MUST** consist of 4 spaces. Tabs **MUST NOT** be used for indentation.

#####Namespaces
Namespaces **SHOULD** be MixedCase, and acronyms used in namespaces **SHOULD** as well. As examples:
    
    - The namespace "Rain\PDF" would not be allowed, while "Rain\Pdf" is acceptable.
    - The namespace "Rain\JSON" would not be allowed, while "Rain\Json" is acceptable.

#####Acceptable File names
All files **MUST** only use alphanumeric characters, underscores, and the dash character ("-"). Spaces are strictly prohibited.

#####Functions and Methods
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

#####Variables
Variable names **MUST** contain only alphanumeric characters. Underscores are not permitted. Numbers are permitted in variable names but are discouraged in most cases.

As with function names, variable names **MUST** always start with a lowercase letter and follow the "camelCaps" capitalization convention.

Verbosity is encouraged. Variables should always be as verbose as practical to describe the data that the developer intends to store in them. Terse variable names such as "$i" and "$n" are discouraged for all but the smallest loop contexts. If a loop contains more than 20 lines of code, the index variables should have more descriptive names.

#####Arrays/Objects

When declaring an array, a trailing space **MUST** be added after each comma delimiter to improve readability.

    [a, b, c, d]
    
It is permitted to declare multi-line arrays. In this case, each successive line **MUST** be padded with spaces such that the beginning of each line is aligned with the initial element of the array

    [a, b, c, 
     d, e, f]
     
Alternately, the initial array item **MAY** begin on the following line. If so, it **MUST** be padded at one indentation level greater than the line containing the array declaration, and all successive lines **MUST** have the same indentation; the closing paren **MUST** be on a line by itself at the same indentation level as the line containing the array declaration.

    var letters = [
        a, b, c,
        d, e, f
    ]
    
#####Classes

The brace **MUST** be written on the line underneath the class name, at the same level of indentation as the class declaration.

Every class **MUST** have a documentation block.

All code in a class **MUST** be indented with four spaces additional to the level of indentation of the class declaration.

The following is an example of an acceptable class declaration

    
    /**
     * Documentation Block Here
     */
    class MyClass
    {
        // all contents of class
        // must be indented four spaces
    }
 
Classes that extend other classes or which implement interfaces **SHOULD** declare their dependencies on the same line when possible.


    class MyClass extends AbstractFoo implements Bar
    {
    }
    
If the class implements multiple interfaces and the declaration exceeds an average line length, break after each comma separating the interfaces, and indent the interface names such that they align.

    class MyClass implements
        BarInterface,
        BazInterface
    {
    }
    
#####Functions and Methods

Methods inside classes **MUST** always declare their visibility by using one of the private, protected, or public visibility modifiers.

As with classes, the brace **MUST** always be written on the line underneath the function name. Space **MUST NOT** be inserted between the function name and the opening parenthesis for the arguments.

Functions **SHOULD NOT** be declared in the global scope.

The following is an example of an acceptable function declaration in a class.


    /**
     * Documentation Block Here
     */
    class Foo
    {
        /**
         * Documentation Block Here
         */
        public function bar()
        {
            // all contents of function
            // must be indented four spaces
        }
    }
    
The following is an example of an unacceptable function declaration in a class.


    /**
     * Documentation Block Here
     */
    class Foo
    {
        /**
         * Documentation Block Here
         */
        public function bar(){ <--- Unacceptable
            // all contents of function
            // must be indented four spaces
        }
    }
    
