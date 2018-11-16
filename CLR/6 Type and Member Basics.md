# Chapter 6. Type and Member Basics

* Type members:
  * Constants: static members.
  * Fields: static/non-static, private first.
  * constructor
  * Type constructors: special method
  * Methods
  * Operator Overloads: non CLS, be careful.
  * conversion operators: non CLS
  * properties: setting & querying.
  * events: static/nonstatic event: -> to static/instance methods
  * types

* Type Visibility
  * File Scope visibility
    * internal
    * pulic
  * Friend Assemblies
    * indicate friends
    * [assembly:InternalsVisibleTo("Wintellect, PublicKey=12345678...90abcdef")]
    * use /out:<file> when compile the friend assembly.
    * use /t:module that going to become a friend assembly , you need /moduleassemblyname:<string> switch.

* Member Accessibility
  * 
