This page is the definition of NF-e Team's coding standards and patterns for the Java™ Programming Language. 

# Summary

- [Package Structure](#package-structure)
- [Code Style](#code-style)
- [Source Code Design](#source-code)
- [Unit Test Design](#unit-test)
- [Integration Test Design](#integration-test)
- [Third Party Libraries](#third-party-libraries)

# Package Structure

* config 
* service
* enums ("enum" is a reserved word);
* exception 
* constant
* creator
* messaging
* model
  * restapi
  * message
* transformer (used only in specific cases, prefer creators)
* converter (for handling enums on data access or request layer)

# Code Style

The code style is based on [Spring Framework Style](https://github.com/spring-projects/spring-framework/wiki/Code-Style) and enforced by the checkstyle [plugin](https://github.wdf.sap.corp/NF-e-Documentation/Wiki/blob/master/Java/codeFormatting/readme.md#checkstyle) and [scheme](https://github.wdf.sap.corp/NF-e-Documentation/Wiki/blob/master/Java/codeFormatting/readme.md#code-formatting-in-ide) (NF-e Checkstyle Conventions). 

# Design
Here are some guidelines for writing consistent code following NF-e team agreed patterns.

## Source Code

### DO use Creators
Whenever you use new() in a model object, use the Creator pattern.

#### good
Creator object creating a model object with content. Easy to read and easy to unit test.
![image](https://github.wdf.sap.corp/storage/user/39301/files/19411ea9-fdad-4fdb-ab2d-99cd5d283cad)

#### bad
Model object created inside the business logic code flow. Bad for readability and bad for unit testing.
![image](https://github.wdf.sap.corp/storage/user/39301/files/2cc43038-84ce-4e14-b9e6-6648791359ca)

### PREFER only one create() method per Creator
When you need to create the same object model, but from different parameters or with different content, use different Creators instead of more create() methods inside the same object.

#### good
Two Creators with only one create() method each, which creates the same object but with different content. Good for readability and code clarity.  
![image](https://github.wdf.sap.corp/storage/user/39301/files/a0afc0af-6901-4c4a-8164-1741ddbb1547)

#### bad
One Creator with two create() methods. In time this can become horrible for readability if you need more types of create(). Imagine this class with 5 create() methods.  
![image](https://github.wdf.sap.corp/storage/user/39301/files/ed042b52-021f-4d18-ab08-037a6db4aeb6)

## Unit Test

## Integration Test

# Third Party Libraries
General guidelines when using specific third party libraries.

## Lombok

Lombok must be used only for models and enums, with all annotations being allowed. For all other classes, the use is forbidden.

Also, do not configure Lombok differently in any project before talking with anyone from the Tech Council group. All configuration definitions should be discussed before being put into practice.
