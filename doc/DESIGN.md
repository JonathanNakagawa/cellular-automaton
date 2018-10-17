# High Level Design

Visualization:

* The Main class contains nearly all the functionality for visualization. It defines the behavior for all aspects of the scene and stage of the game, including buttons, sliders, graphs, and panes. It also reads in all text in the GUI and displays it. It handles selection of the XML configuration file and ensures that the file is of the proper type. It then initializes the appropriate simulation with given parameters based on the configuration file and defines the appropriate behavior for updating the scene at each step.

Configuration:

* The configuration and initialization setup is laid out such that there is an Initializer class, a Handle class inheritance hierarchy (Handle itself is abstract), an XMLParser class, and a Grid class (Grid itself is abstract) inheritance hierarchy. 

* The Initializer class is used to select the proper Handle subclass based on the
simulation type it reads from the XML file, using reflection to obtain the
new instance of a Handle object

* The job of the created instance of a Handle class is to return an initialized Game class to the Main class. The XMLParser class is used throughout these classes in order to obtain grid dimensions, simulation type, grid initialization type, and simulation configuration parameters from the XML configuration file when needed. The Grid hierarchy (subclasses are based on what shape a cell is in the grid) is used in the initialization of the grid contained by a Game object.

Simulation:

* The highest level class in the simulation section is the Game superclass. This class holds an adjacency map of Nodes and implements a method to iterate through all the nodes and update them.Its children classes implements a function to check if the simulation is over and if so won't run anymore.

* The next structure is the Node superclass. It serves as the vertecies in the adjacency map. It holds a Cell object and implement some methods to allow for easy transversal of the map. It also has a replacement cell field that stores the cell that will replace the current cell in the next step. Its subclasses implement a update method that updates the current cell by passing it its neighborhood of cells and sets the according replacement cells.

* The bottom level structure is the Cell superclass. Each different type of automaton in each simulations was implemented as a different cell subclass. The main feature of the cell class is the update function which takes in a neighborhood of cells and sets the current cells replacement cell and in some cases passes back a map of other cells that need to be replaced.

# New Feature

* For the simulation create a new game class which extends the Game super. Implement endstate method that checks whether the simulation has ended. Create a new set of cell sub classes. For each implement the update cell method that takes a neighborhood of cells and sets the replacement cell for the current cell. If the cell needs to replace other cells, set in the my target map the cell being replaced as a key and replacement cell as a value. 

* In order to implement a new simulation from the configuration aspect, a Handle class that extends the Handle abstract class named such that it matches an identification string placed in the XMLParser file so that it can correctly check if the XML file is for an existing simulation must be created. It implements the methods "getConfigurationParameters()" and "initializeGrid()" methods, and I believe that the existing Handle subclasses serve as very straightforward examples for how you would implement a new Handle subclass.

* In order to implement a specific simulation file, see the below structure for an XML file:
```xml
 <?xml version="1.0" encoding="UTF-8"?>

<simulation simType = "Fire">
    <simAuthor> Ryan Piersma </simAuthor>
    <simTitle> Portfolio Weighted Random Showing </simTitle>

    <globalParam>
        <!-- Specific simulation parameters go here -->
        <!-- Fire: <probCatch> -->
        <!-- Seg: <percentSatisfaction> -->
        <!-- WaTor: <sharkLifetime> -->
        <!-- WaTor: <fishLifetime> -->
        <probCatch> .6 </probCatch>
    </globalParam>

    <grid>
        <gridSize>
            <xdim> 5 <!-- Initial grid x dimension--></xdim>
            <ydim> 5 <!-- Initial grid y dimension--> </ydim>
        </gridSize>

        <!-- ONLY ONE OF THE FOLLOWING INITIALIZATION TYPE BLOCKS CAN BE USED-->
        <!-- initializeType: specific (cells initialized based on a specific grid) -->
        <!-- EXAMPLE FOR SPECIFIC INITIALIZATION (using cells for Fire simulation)-->
        <beginGrid>
            <row1> T T B T T </row1>
            <row2> T U T U T </row2>
            <row3> U T T T U </row3>
            <row4> T T B B T </row4>
            <row5> T B U U U </row5>
        </beginGrid>

        <!-- initializeType: random (cells initialized based only on grid dimensions, do not need any more
        grid tags) -->

        <!-- initializeType: weightedrandom (cells initialized based on per cell type probabilities that
        should add to 1. For more precise probabilities, set "PROBABILITY_GRANULARITY" to some higher
        multiple of 10. Default = 100) -->
        <!-- EXAMPLE FOR WEIGHTED RANDOM INITIALIZATION>
        <initializeType> weightedrandom </initializeType-->
        <weightedrandom>
            <B> 0.01 </B> <!-- These letters are the cell identifier tags for the fire simulation -->
            <U> 0.0 </U>
            <T> 0.99 </T>
        </weightedrandom>
    </grid>

</simulation>
```


# Design Choices and Tradeoffs

* For the Cell classes, I decided to implement different classes for each type of cell. While on the one hand this plays into the idea of polymorphism and java's strengths, on the other is necessistated the creation of the node classs. If instead I just used a variable and array list of colors it would have been much easier to change the type of cell in a position.

* For the configuration classes, I decided to initialize the correct Handle subclass using reflection because it eliminated the need for an if-else tree to decide the right subclass initialization despite the fact that it introduced the constraint of having to leave Handle class constructors blank in order to facilitate "easy" code for initializing using reflection in Java.

* Grid was created as an inheritance hierarchy because it is meant to handle neighbor handling methods, which can be specified on a per-shape basis, lending to a concept of extending for each shape as a new type of grid. The tradeoff is that the methods specified as abstract in the overall Grid class must be implemented in the Grid subclasses

* Handle was created as an inheritance hierarchy so that each simulation could take advantage of common behaviors to run a simulation. I suppose another idea would have been to generalize the concept of a simulation to such a high level that simply initializing its instance variables in different ways would allow it to be a new simulation type, but this would have required extensive knowledge encompassing the entire field of cellular automata. The inheritance hierarchy lent itself to implementation on a per simulation type basis, but lent itself easily to duplicated code that would be very hard to get rid of based on behaviors that the Handle class interface does not handle as part of its description. Additionally, I feel that the Handle abstract superclass is fairly bloated with code that
could be further partitioned into different classes that encompass the functionality of a total simulation at smaller levels. However, I decided to implement the Handle hierarchy as I did because it facilitated an easily reproducible per simulation "Handle" file.

* For the main class, I stored all of the functionality for visualization within the Main class, which could have better been split into multiple classes each containing a distinct piece of functionality.

# Assumptions and Decisions

* Our Cell Society program uses extensive error checking to ensure that few assumptions were made about the contents of a game subclass or an xml file.