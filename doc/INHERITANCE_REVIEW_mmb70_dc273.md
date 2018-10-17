#Part 1


* What is an implementation decision that your design is encapsulating (i.e., hiding) for other areas of the program?

Splitting up the cell and game classes from the main class, which handles visualization using JavaFX.

* What inheritance hierarchies are you intending to build within your area and what behavior are they based around?

The Game class is extended by several subclasses representing the different kinds of CAs, and the cell class is extended by severall subclasses representing the different kinds of cells within the CAS

* What parts within your area are you trying to make closed and what parts open to take advantage of this polymorphism you are creating?

Since the Main class simply takes in the results of the other classes my teammates have built, there is not a great deal of OO design that goes into making the visualization.

* What exceptions (error cases) might occur in your area and how will you handle them (or not, by throwing)?

IOException or FileNotFoundError for missing XML configuration files.

* Why do you think your design is good (also define what your measure of good is)?

Our design adheres to the OO principles which we've learned about in class so far, making use of inheritance, abstract classes, and polymorphism, among other things.

#Part 2


* How is your area linked to/dependent on other areas of the project?

My area is wholly dependent on other areas of the project, as my job is to visualize the implementation of other areas of the project.

* Are these dependencies based on the other class's behavior or implementation?

These dependencies are based on the other class's behavior.

* How can you minimize these dependencies?

There is no need to minimize these dependencies, as it is part of the nature of the class.

4. Go over one pair of super/sub classes in detail to see if there is room for improvement.

There is only one class I'm working on.

5. Focus on what things they have in common (these go in the superclass) and what about them varies (these go in the subclass).

N/A


#Part 3

* Come up with at least five use cases for your part (most likely these will be useful for both teams).

Pausing, playing, autoplaying, restarting, loading new game, etc.

2. What feature/design problem are you most excited to work on?

Creating the JavaFX game window.

3. What feature/design problem are you most worried about working on?

Issues with IntelliJ not compiling/building the project properly.