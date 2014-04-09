Note that the current code base does not necessarily follow this with 100% consistency. It will be an ongoing process to try and sanitize the existing code to match these guidelines.

Basically taken directly from http://geosoft.no/development/cppstyle.html  with some subtle changes and omissions.

##### Table of Contents
[1. Naming](#naming)  
[2. Files](#files)  
[3. Statements](#statements)  
[4. Layout and Comments](#layout)  

<a name="naming"/>
#1. Naming
##1.1. General Naming Conventions
####1.1.1. Names representing types must be in mixed case starting with upper case.  
    Coach, PenaltyBox

####1.1.2. Private class variables must be in mixed case prefixed with an underscore.  
    _puck, _team

####1.1.3. Local variables must be in mixed case (and NOT prefixed with an underscore).  
    redLine, icingFrequency
    
####1.1.4. Constants must be all uppercase using underscore to separate words.  
    MAX_RINK_LENGTH, COLOR_RED_LINE

####1.1.5. Methods or functions must be verbs and written in mixed case starting with lower case.  
    getPlayerNumber(), computeGoalsAgainstAverage()

####1.1.6. Names representing namespaces should be all lowercase.  
    puck::geometry, ice::math

####1.1.7. Names representing template types should be a single uppercase letter.  
    template<class R>, template<class B>, template<class K>
This makes template names stand out relative to all other names used.

####1.1.8. Abbreviations and acronyms must be uppercase when used in a name or lowercase when used at the beginning of a variable  
    showNHLStandings(); // not showNhlStandings();  
    exportASCIIStanleyCup(); // not exportAsciiStanleyCup();  
    UDPSocket udpSocket; // not UDPSocket uDPSocket;

####1.1.9. Global variables should always be referred to using the :: operator.  
    ::jumbotron.powerOn(), ::league.lockout();

####1.1.10. Generic variables should have the same name as their type.  
    void setPuckLogo(Logo* logo) // not void setPuckLogo(Logo* aLogo)
These will be discernible from class private variables since they are not prefixed with an underscore.

####1.1.11. All names should be written in English.  
    hockeyStick;   // NOT: bastonDeHockey

####1.1.12. The name of the object is implicit, and should be avoided in a method name.  
    puck.getDensity();    // NOT: puck.getPuckDensity();

##1.2 Specific Naming Conventions
####1.2.1. The terms get/set must be used where an attribute is accessed directly.  
    player.getNumber();  
    player.setNumber(number);  
    stick.getFlex();
    stick.setFlex(flex);

####1.2.2. The term compute can be used in methods where something is computed.  
    team->computerPowerPlayPercentage();    
    player->computePointsPerGame();
Give the reader the immediate clue that this is a potentially time-consuming operation, and if used repeatedly, he might consider caching the result. Consistent use of the term enhances readability.

####1.2.3. The term find can be used in methods where something is looked up.  
    net.findGoalLinePosition();  
    team.findHeaviestPlayer();
Give the reader the immediate clue that this is a simple look up method with a minimum of computations involved. Consistent use of the term enhances readability.

####1.2.4. The term initialize can be used where an object or a concept is established.  
    rink.initializePaintedLines();  
    video.initializeOnScreenScore();

####1.2.5. Variables representing GUI components should be suffixed by the component type name.  
    scoreboardText, mainWindow, fileMenu

####1.2.6. Plural form should be used on names representing a collection of objects.  
    vector<Player> players;  
    float savePercentages[];

####1.2.7. The prefix num should be used for variables representing a number of objects.  
    numGoals, numAssists

####1.2.8. The suffix Num should be used for variables representing an entity number.  
    playerNum, teamNum

####1.2.9.  Iterator variables should be called i, j, k etc.  
    for (int i = 0; i < numGoals); i++) {
        goals[i].playVideo();
    }

####1.2.10. The prefix is should be used for boolean variables and methods.  
    isGoodGoal, isRetired, isWinningTeam
Occasionally the has, can, should, and want prefixes will be better choices.

_Note: “want” should generally be used for optional items that are specified by some third party action, e.g. command line or menu options that enable additional functionality, or protocol versioning where negotiation occurs between client and server._  

    hasWonStanleyCup, canPlay, shouldPass, wantDebugLogging

####1.2.11. Complement names must be used for complement operations  
    get/set, add/remove, create/destroy, start/stop

####1.2.12. Abbreviations in names should be avoided.  
    computeGoalsAgainstAverage();  // NOT: compGlsAgstAvg();  

There are domain specific phrases that are more naturally known through their abbreviations/acronym. These phrases should be kept abbreviated.

Use `html` instead of `hypertextMarkupLanguage`.

####1.2.13. Naming pointers specifically should be avoided.
    Puck* puck; // NOT: Puck * puckPtr;
Many variables in a C/C++ environment are pointers, so a convention like this is almost impossible to follow. Also objects in C++ are often oblique types where the specific implementation should be ignored by the programmer. Only when the actual type of an object is of special significance, the name should emphasize the type.

####1.2.14. Negated boolean variable names must be avoided.
    bool isRetired; // NOT: isNotRetired or isNotPlaying
  
This is done to avoid double negatives when used in conjunction with the logical negation operator.

####1.2.15.  Enumeration constants can be prefixed by a common type name.
    enum Jersey {
      JERSEY_HOME,
      JERSEY_AWAY,
      JERSEY_ALTERNATE
    };

####1.2.16.  Exception classes should be suffixed with Exception.
    class GoalException {
      ...
    }

<a name="files"/>
#2. Files
##2.1 Source Files
####2.1.1. C++ header files should have the extension .h. Source files should have the extension .cpp.
    Puck.h, Puck.cpp

####2.1.2.  A class should always be declared in a header file and defined in a source file where the name of the files match the name of the class.
`class Puck` defined in `Puck.h`, `Puck.cpp`

####2.1.3. Most function implementations should reside in the source file.
    class Puck {
    public:
        // Not allowed!
        int calculateCircumference () {
            return PI * pow(_radius,2) ;
        } 

        // simple getters/setters should appear in the header file
        int getRadius() const { return _radius; };
        void setRadius(int radius) { _radius = radius; };
        ...
    private:
        int _radius;
    }
The header files should declare an interface, the source file should implement it. When looking for an implementation, the programmer should always know that it is found in the source file.

Simple getters and setters that just access private member variables should appear inline in the class definition in the header file.

####2.1.4. File content must be kept within 128 columns.

####2.1.5. Special characters like TAB and page break must be avoided.
Use four spaces for indentation.

####2.1.6. The incompleteness of split lines must be made obvious.
    teamGoals =  iginlaGoals + crosbyGoals +
                 malkinGoals;

    addToScoreSheet(scorer, directAssister,
                    indirectAssister);

    setHeadline("Crosby scores 4"
                " to force game 7.");

    for (int teamNum = 0; teamNum < numTeams;
         teamNum++) {
      ...
    }
Split lines occurs when a statement exceed the 128 column limit given above. It is difficult to give rigid rules for how lines should be split, but the examples above should give a general hint.

In general:
Break after a comma.
Break after an operator.
Align the new line with the beginning of the expression on the previous line.

##2.2 Include Files and Include Statements

####2.2.1. Header files must contain an include guard.
Include guards should be in the following format: hifi_$BASENAME_h.

    #ifndef hifi_VoxelAgentData_h
    #define hifi_VoxelAgentData_h
    
    ...
    
    #endif // _hifi_VoxelAgentData_h

####2.2.2. Include statements should be sorted and grouped. Sorted by their hierarchical position in the system with low level files included first. Leave an empty line between groups of include statements.
    #include <fstream>
    #include <cstring>
    
    #include <qt/qbutton.h>
    #include <qt/qtextfield.h>
    
    #include "Puck.h"
    #include "PenaltyBox.h"

####2.2.3. Include statements must be located at the top of a file only.

<a name="statements"/>
#3. Statements
##3.1. Types
####3.1.1. The parts of a class must be sorted public, protected and private. All sections must be identified explicitly. Not applicable sections should be left out.
The ordering is "most public first" so people who only wish to use the class can stop reading when they reach the protected/private sections.

####3.1.2.  Never rely on implicit type conversion. // NOT: floatValue = intValue;
#####3.1.2.1 Primitive types should use C style casting: 
    int foo = 1;
    float bar = (float)foo;
    // NOT this: float fubar = float(foo);

#####3.1.2.2 Class pointers must use C++ style casting:
    Player* player = getPlayer("forward");
    Forward* forward = static_cast<Forward*>(player);

For more info about C++ stype casting:
http://stackoverflow.com/questions/1609163/what-is-the-difference-between-static-cast-and-c-style-casting

##3.2 Variables
####3.2.1. Variables should be initialized where they are declared.
This ensures that variables are valid at any time. 

Sometimes it is impossible to initialize a variable to a valid value where it is declared:
 
    Player crosby, dupuis, kunitz;
    getLineStats(&crosby, &dupuis, &kunitz);

In these cases it should be left uninitialized rather than initialized to some phony value.

####3.2.2. Use of global variables should be minimized.
http://stackoverflow.com/questions/484635/are-global-variables-bad

####3.2.3. Class variables should never be declared public.
Use private variables and access functions instead. 

One exception to this rule is when the class is essentially a data structure, with no behavior (equivalent to a C struct). In this case it is appropriate to make the class' instance variables public.

Note that structs are kept in C++ for compatibility with C only, and avoiding them increases the readability of the code by reducing the number of constructs used. Use a class instead.

####3.2.4. C++ pointers and references should have their reference symbol next to the type rather than to the name.
    float* savePercentages; 
    // NOT: float *savePercentages; or float * savePercentages; 

    int& numCups;   
    // NOT: int &numCups; or int & numCups;
The pointer-ness or reference-ness of a variable is a property of the type rather than the name.

####3.2.5.  Implicit test for 0 should not be used other than for boolean variables or non-NULL pointers.
    if (numGoals != 0)  // NOT: if (numGoals)
    if (savePercentage != 0.0) // NOT: if (savePercentage)

    // Testing pointers for non-NULL is prefered, e.g. where
    // childNode is Node* and you’re testing for non NULL
    if (childNode) 

    // Testing for null is also preferred
    if (!childNode)

It is not necessarily defined by the C++ standard that ints and floats 0 are implemented as binary 0.

####3.2.6.  Variables should be declared in the smallest scope possible.
Keeping the operations on a variable within a small scope, it is easier to control the effects and side effects of the variable.

##3.3 Loops
####3.3.1.  Loop variables should be initialized immediately before the loop.

####3.3.2. The form while (true) should be used for infinite loops.
    while (true) {
      :
    }

    // NOT: 

    for (;;) {
      :
    }

    while (1) {
      :
    }

##3.4 Conditionals
####3.4.1. The nominal case should be put in the if-part and the exception in the else-part of an if statement 
    bool isGoal = pastGoalLine(position);

    if (isGoal) {
      ...
    } else {
      ...
    }
Makes sure that the exceptions don't obscure the normal path of execution. This is important for both the readability and performance.

####3.4.2. The conditional should be put on a separate line and wrapped in braces.
    if (isGoal) {
        lightTheLamp();
    }      

    // NOT: if (isGoal) lightTheLamp();

##3.5 Miscellaneous
####3.5.1. The use of magic numbers in the code should be avoided. Numbers other than 0 and 1 should be considered declared as named constants instead.
If the number does not have an obvious meaning by itself, the readability is enhanced by introducing a named constant instead. A different approach is to introduce a method from which the constant can be accessed.

####3.5.2. Floating point constants should always be written with decimal point and at least one decimal.
    double stickLength = 0.0;    // NOT:  double stickLength = 0;

    double penaltyMinutes;
    ...
    penaltyMinutes = (minor + misconduct) * 2.0;

####3.5.3. Floating point constants should always be written with a digit before the decimal point.
    double penaltyMinutes = 0.5;  // NOT:  double penaltyMinutes = .5;

<a name="layout"/>
#4. Layout and Comments
##4.1. Layout
####4.1.1. Basic indentation should be 4.
    if (player.isCaptain) {
        player.yellAtReferee();
    }
    
####4.1.2. Use inline braces for block layout
    while (!puckHeld) {
        lookForRebound();
    }

    // NOT:
    // while (!puckHeld) 
    // {
    //     lookForRebound();
    // }    

####4.1.3. The class declarations should have the following form:
    class GoalieStick : public HockeyStick {
    public:
        ...
    protected:
        ...
    private:
        ...
    }

####4.1.4.  Method definitions should have the following form:
    void goalCelebration() {
        ...
    }
    
####4.1.5.  The if-else class of statements should have the following form:
    if (isScorer) {
        scoreGoal();
    }

    if (isScorer) {
        scoreGoal();
    } else {
        saucerPass();
    }

    if (isScorer) {
        scoreGoal();
    } else if (isPlaymaker) {
        saucerPass();
    } else {
        startFight();
    }

####4.1.6.  A for statement should have the following form:
    for (int i = 0; i < GRETZKY_NUMBER; i++) {
        getActivePlayerWithNumber(i);
    }

####4.1.7. A while statement should have the following form:
    while (!whistle) {
        keepPlaying();
    }

####4.1.8. A do-while statement should have the following form:
    do {
       skate();
    } while (!tired)

####4.1.9. A switch statement should have the following form:
    switch (jerseyNumber) {
        case 87 :
            return crosby;
        case 66 :
            return lemieux;
        case 99 :
            return gretzky;
        default :
            return NULL; 
    }

####4.1.10. A try-catch statement should have the following form:
    try {
        tradePlayer();
    }
    catch (NoTradeClauseException& exception) {
        negotiateNoTradeClause();
    }

####4.1.11. Single statement if-else, for or while statements must be written with brackets.

##4.2 White space
####4.2.1. Conventional operators should be surrounded by a space character. 
    potential = (age + skill) * injuryChance; 
    // NOT: potential = (age + skill) * injuryChance;

#####4.2.2. C++ reserved words should be followed by a white space. 
    while (true)   
    // NOT: while(true) 
    
####4.2.3. Commas should be followed by a white space. 
    setLine(leftWing, center, rightWing, leftDefense, rightDefense);  
    // NOT: setLine(leftWing,center,rightWing,leftDefense,rightDefense);

####4.2.4. Semicolons in for statments should be followed by a space character.
    for (i = 0; i < 10; i++) {  // NOT: for(i=0;i<10;i++){

####4.2.5. Method names should not be followed by a white space
    setCaptain(ovechkin); // NOT: setCaptain (ovechkin);

####4.2.6.  Logical units within a block should be separated by one blank line.
    Team penguins = new Team();

    Player crosby = new Player();
    Player fleury = new Player();

    penguins.setCaptain(crosby);
    penguins.setGoalie(fleury);

    penguins.hireCoach();

####4.2.7. Avoid adding optional spaces across multi-line statements and adjacent statements.
Avoid the following:

    oddsToWin = (averageAge     * veteranWeight) +
                (numStarPlayers * starPlayerWeight) +
                (goalieOverall  * goalieWeight);

    theGreatOneSlapShotSpeed  = computeShot(stickFlex, chara);
    charaSlapShotSpeed        = computeShot(stickFlex, weber);

A change to the length of a variable in these sections causes unnecessary changes to the other lines.

####4.2.8 Multi-line statements must have all n+1 lines indented at least one level (four spaces).
Align all n+2 lines with the indentation of the n+1 line.

The following are all acceptable:
    
    shootOnNet(puckVelocity,
        playerStrength,
        randomChance);

    shootOnNet(puckVelocty,
               playerStrength,
               randomChance);
     
    if (longBooleanThatHasToDoWithHockey
        && anotherBooleanOnANewLine);

    isGoodGoal = playerSlapShotVelocity > 100
        ? true
        : false;

##4.3 Comments
####4.3.1.  All comments should be written in English
In an international environment English is the preferred language.

####4.3.2. Use // for all comments, including multi-line comments.
An exception to this rule applies for Doxygen comments where there are three slashes.

    // Comment spanning
    // more than one line.
There should be a space between the "//" and the actual comment

####4.3.3. Comments should be included relative to their position in the code
    while (true) {
        // crosby is always injured
        crosbyInjury();
    }     

    // NOT: 
    // crosby is always injured
    while (true) {
        crosbyInjury();
    }

####4.3.4 Source files (header and implementation) must include a boilerplate.
Boilerplates should include the filename, location, creator, copyright, and Apache 2.0 License information and be placed at the top of the file.

    //
    //  NodeList.h
    //  libraries/shared/src
    //
    //  Created by Stephen Birarda on 2/15/13.
    //  Copyright 2013 High Fidelity, Inc.
    //
    //  This is where you could place an optional one line comment about the file.
    //
    //  Distributed under the Apache License, Version 2.0.
    //  See the accompanying file LICENSE or http://www.apache.org/licenses/LICENSE-2.0.html
    //

##5. New rules to include
Other rules we’ve discussed....

LHS vs RHS...

// This
if (someVariable == 0)
// Not
if (0 == someVariable)...

consts vs #define
when/how to use consts vs defines, especial to avoid magic numbers
format of getters/setters, especially as the relate to “const” methods and references to const members.