Ryan Piersma (rrp17), Tahj Starr (tms62)

Our role in completing CellSociety is working with reading the XML file and
using it to initialize a speific simulation

## Part 1

1. My design incorporates the decision to encapsulate the different parameters needed for different
simulations by providing a universal "initializeSim()" method in an inheritance hierarchy that
can handle initialization for each type of simulation. 

2. I intend to build an inheritance hierarchy that allows for the initialization of different 
simulation types. This is based around the different behavior needed to handle the initial state
of a simulation given its different simulation parameters.

3. I am trying to close the mechanism by which a simulation is initialized, while leaving open
the ability to add new simulations to the handler.

4. Exceptions might occur when a certain type of Game object is initialized but not given 
the correct number of arguments in its initialization- this will throw an exception called
"WrongArgumentException"

5. I think this design idea is good because it allows for the main visualization code to run
and initialize a simulation while being oblivious to the XML configuration file itself, as well as the
specific code that was run to initialize the game.


## Part 2

1. The results of the initialization process from the XML file go to the "visualization" area
of the project, and my code will link between parsing the XML file and creating the different
Cell objects that encapsulate the different behaviors of the different simulations.

2. These dependencies are based on the other class's implementation.
By the way we defined the divisions between the classes, my hierarchy of initialization
classes must perform functions using the Cell hierarchy -> which is dependence on
implementation, because this isn't reliance on the Cell behavior, but rather how
the cells are being represented.

3. These dependencies could be minimized by making the interaction surface between
the Initializer and Cell hierarchies as small as possible, though there must be an
interaction surface by definition. The interaction surface could be minimized by
placing the correct fields within Cells and the correct handling code in the Initalizers

4. Superclass (Interface?) : Initializer (Things in common = method to handle initialization of
specific simulation)
   Subclass: LifeInitializer (Variation = how this method is implemented for a 
   Game of Life simulation)


## Part 3

1. Use cases:

* Creating grids of different sizes
* Handling when XML global parameters for a simulation do not match the simulation
type
* Translating grid data in the XML file to specific instances of Cells
* Using XML fields to initialize the proper simulation type
* Making sure the initialized grid is equipped to handle stepping

2. I am excited to figure out how to use the XML data to create a specific instance
of the correct simulation

3. I am worried about correctly interacting with the Cell class during initialization
