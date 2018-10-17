#Refactoring: Lab 9.27.18
### Ryan Piersma (rrp17), Cell Society Group 7

In this lab, my main refactoring decisions were to modify the 
Handle inheritance hierarchy to get rid of large blocks of duplicated
code across the subclasses of Handle. In doing this I had to consider if these
methods would have to be moved again from the superclass in implementing new features
and decided that since they would not have to be moved, I could refactor them into the
superclass, thus changing the inheritance hierarchy. Alternatives would have been to
leave the duplicated code in expectation of new features displacing this from the
possibility of being put in the superclass. More likely, a better alternative would have
been to scrutinize the inner parts of the functionality of these methods and further
partition into generalized and specified methods.

In addition to this refactoring, I also made an effort to improve the error handling
involved with parsing from the XML file.