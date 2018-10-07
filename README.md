##SublimeFortran+
==============

####Highly recommended that you also installed the Outline+ plugin found in the [Outline+ repository](https://github.com/UCLA-Plasma-Simulation-Group/tools_sublimetext_outliner)

###About
This is a fork of _SublimeFortran_ that fixes/handles a few things differently and in particular changes the generated parse tokens to work better with the Outline+ plugin. It also includes support for parsing F2003 derived types type-bound-procedures better as well as properly parsing the constituent 'module procedure' statements that make up a named module interface.

Note, the parsing done in _SublimeFortran_ is very incomplete and from the code you can tell they just gave up half way though (no judgment hahaha they did the right thing and got it to a 'good enough' state). In particular, Fortran statements/constructs are flat parsed rather then having any real nested contexts (except for a few cases like string literals and a few of the block constructs). This makes it hard to do really detailed tag processing (for example, the parser detects 'contains' statement.. but there cannot differentiate if the contains occurred within a module, function, derive type etc.. we have little info about surrounding context for most of the parsed stuff.)


Anyway, if you see parsing bugs, or have an idea/seen another tool with a nice quality-of-life feature for Fortran, write a quick note to Adam and we can fix things up. (One thing I would like, for example, is proper 'GoTo Defintion' symbol support for module procedures.. so that the type of the arguments is parsed and known and using this info the correct overloaded module procedure is selected and you are taken to that part of the code... this is possible f we use wRapacious as the parser rather then Sublime's parsing system)

(This is fork of _SublimeFortran_. The original _SublimeFortran_ repository is [here](https://github.com/315234/SublimeFortran). Look at this repository for more info about various fancy features (like LaTex) support within _SublimeFortran_)
