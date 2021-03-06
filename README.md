Proposal for Rain's coding standards
====================================

The following document provides guidelines for code formatting and documentation. Our goal is to keep code's style consistent across all RAIN repositories.

#####Topics covered
1. File Formatting.
2. Naming Conventions.
3. Coding Style.
4. Inline Documentation.

#####This document attempts to follow [RFC 2119's](http://www.ietf.org/rfc/rfc2119.txt) verbosity for indicating requirements.
- **MUST** and **MUST NOT** indicate non-optional requirements.
- **SHOULD** and  **SHOULD NOT** indicate recommendations for which exceptions may exist.
- **MAY** indicates truly optional requirements.

#####Indentation
Indentation **MUST** consist of 4 spaces. Tabs **MUST NOT** be used for indentation.

#####Namespaces
Namespaces **SHOULD** be MixedCase, and acronyms used in namespaces **SHOULD** as well. As examples.
    
    - The namespace "Rain\PDF" would not be allowed, while "Rain\Pdf" is acceptable.
    - The namespace "Rain\JSON" would not be allowed, while "Rain\Json" is acceptable.

#####Acceptable File names
All files **MUST** only use alphanumeric characters, underscores, and the dash character ("-"). Spaces are strictly prohibited.

#####Functions and Methods
Function names **MUST** contain only alphanumeric characters. Underscores are not permitted. Numbers are permitted in function names but are discouraged.

Function names **MUST** always start with a lowercase letter. When a function name consists of more than one word, the first letter of each new word **MUST** be capitalized. This is commonly called "camelCase" formatting.

Verbosity is encouraged. Function names should be as verbose as is practical to fully describe their purpose and behavior.

These are examples of acceptable names for functions.
    
    doSomething();
    ringTheBell();
    callUser();

The following are examples of unacceptable function names.
    
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
     
Alternately, the initial array item **MAY** begin on the following line. If so, it **MUST** be padded at one indentation level greater than the line containing the array declaration, and all successive lines **MUST** have the same indentation; the closing bracket **MUST** be on a line by itself at the same indentation level as the line containing the array declaration.

    var letters = [
        a, b, c,
        d, e, f
    ]
    
#####Classes

The brace **MUST** be written on the line underneath the class name, at the same level of indentation as the class declaration.

Every class **MUST** have a documentation block.

All code in a class **MUST** be indented with four spaces additional to the level of indentation of the class declaration.

The following is an example of an acceptable class declaration.

    
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
    
#####Control Statements (If/Else/Elseif)

Control statements based on the if and elseif constructs **MUST** have a single space before the opening parenthesis of the conditional and a single space after the closing parenthesis.

Within the conditional statements between the parentheses, operators **MUST** be separated by spaces for readability. Inner parentheses **SHOULD** be used to improve logical grouping for larger conditional expressions.

The opening brace **MUST** be written on the same line as the conditional statement if the conditional statement does not contain a line feed. The closing brace **MUST** be written on its own line. Any content within the braces **MUST** be indented using four spaces.

    if ($name != 'John') {
        //Your code goes here
    }
    
If the conditional statement causes the line length to exceed the maximum line length and has several clauses, you **MUST** break the conditional into multiple lines. In such a case, break the line prior to a logic operator, and pad the line such that it aligns under the first character of the conditional clause. The closing paren in the conditional will then be placed on a line with the opening brace, with one space separating the two, at an indentation level equivalent to the opening control statement.

    
    if (($name == 'John')
        && ($lastName == 'Doe')
        || ($name == 'Jane')
    ) {
        $fullName = $name . ' ' .$lastName;
    }

#####Inline Documentation

All class files **MUST** contain a "file-level" docblock at the top of each file and a "class-level" docblock immediately above each class. 

######Files
Every file **MUST** have a docblock at the top of the file.

    /**
     * RAIN (http://www.mediarain.com)
     *
     * @link      https://github.com/BruceLampson/codingstandars for the canonical source repository
     * @copyright Copyright (c) 2014 Media Rain USA Inc. (http://www.mediarain.com)
     * @license   https://github.com/BruceLampson/codingstandars MIT
     */

######Classes
    /**
     * Short description for class
     *
     * Long description for class (if any)...
     */

######Functions
Every function, including object methods, **MUST** have a docblock that contains at a minimum.
      
    - A description of the function
    - All of the arguments
    - All of the possible return values (even "void")
    - It is not necessary to use the @access annotation because the access level is already known from the public, private, or protected visibility modifier used to declare the function.
      
If a function or method may throw an exception, use @throws for all known exception classes.

    @throws exceptionclass [description]
    
    
We want to hear your thoughts on this initiative so feel free to fork this project and contribute!
