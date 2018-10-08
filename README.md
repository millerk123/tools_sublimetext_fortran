## SublimeFortran+

##### Adds Fortran support to Sublime Text 3.
Comprehensive syntax highlighting for Fortran in Sublime Text 3.

This is a fork+update of the _SublimeFortran_ package (see original _SublimeFortran_ repository is at [https://github.com/315234/SublimeFortran](https://github.com/315234/SublimeFortran) )

### Installation
Just 3 easy steps!
1. __If you previously installed the _Fortran_ package, you must uninstall it.__
2. __Add the _Fortran+_ repository to Sublime Text's package manager:__
3. __Install Fortran+__

If you are new to Sublime Text, see the _Installation Walkthrough_ section below for detailed instructions.

### Installation Walkthrough
1. __If you previously installed the _Fortran_ package, you must uninstall it.__
    * Open Command Palate (Mac: &#8984;-Shift-P or Windows: Ctrl-Shift-P)
    * Type 'remove package' then select the 'Package Control: Remove Package' item.
    * Scroll though the list and select the _Fortran_ item to uninstall it. (If you don't see an  _Fortran_ entry it's no big deal... it just means  _Fortran_ isn't installed which is what we were after anyway!)
    * ![](assets/remove_fortran.gif?raw=true)
2. __Add the _Fortran+_ repository to Sublime Text's package manager:__
    * Open Command Palate (Mac: &#8984;-Shift-P or Windows: Ctrl-Shift-P)
    * Type 'add repository' then select the 'Package Control: Add Repository' item.
    * Then paste in the value: `https://raw.githubusercontent.com/UCLA-Plasma-Simulation-Group/tools_sublimetext_fortran/master/info.json`
    * ![](assets/add_repo.gif?raw=true)
3. __Install Fortran+__
    * Open Command Palate (Mac: &#8984;-Shift-P or Windows: Ctrl-Shift-P)
    * Type 'install package' then select the 'Package Control: Install Package' item
    * Type 'Fortran+' then select the 'Fortran+' item
    * ![](assets/install_package.gif?raw=true)

###About
This is a fork of _SublimeFortran_ that fixes/handles a few things differently and in particular changes the generated parse tokens to work better with the Outline+ plugin. It also includes support for parsing F2003 derived types type-bound-procedures better as well as properly parsing the constituent 'module procedure' statements that make up a named module interface.

Note, the parsing done in _SublimeFortran_ is very incomplete and from the code you can tell they just gave up half way though (no judgment hahaha they did the right thing and got it to a 'good enough' state). In particular, Fortran statements/constructs are flat parsed rather then having any real nested contexts (except for a few cases like string literals and a few of the block constructs). This makes it hard to do really detailed tag processing (for example, the parser detects 'contains' statement.. but there cannot differentiate if the contains occurred within a module, function, derive type etc.. we have little info about surrounding context for most of the parsed stuff.)


Anyway, if you see parsing bugs, or have an idea/seen another tool with a nice quality-of-life feature for Fortran, write a quick note to Adam and we can fix things up. (One thing I would like, for example, is proper 'GoTo Defintion' symbol support for module procedures.. so that the type of the arguments is parsed and known and using this info the correct overloaded module procedure is selected and you are taken to that part of the code... this is possible f we use wRapacious as the parser rather then Sublime's parsing system)

(This is fork of _SublimeFortran_. The original _SublimeFortran_ repository is [here](https://github.com/315234/SublimeFortran). Look at this repository for more info about various fancy features (like LaTex) support within _SublimeFortran_)

### The original _README.md_ from _SublimeFortran_:
Features:

 - Linter based on `gfortran` (requires the package [SublimeLinter](https://github.com/SublimeLinter/SublimeLinter3) to work), highlights errors while you work:

    <img src="images/linter_example.png" width="271px">

 - Hover over inline latex in comments to see it rendered in a popup (requires build >= 3116):

    <img src="images/latex_example.png" width="351px">

 - Hover over intrinsic functions to see documentation in a popup (requires build >= 3116):

    <img src="images/docs_example.png" width="422px">

 - Code snippets

 - Indentation rules

 - Separate syntax definitions for fixed-format and modern Fortran.

 - Based on the new
   [sublime-syntax file format](http://www.sublimetext.com/docs/3/syntax.html)
   and therefore currently requires a recent [beta version](http://www.sublimetext.com/3)
   of Sublime Text 3 (minimum build number 3084).

Pull requests are welcome :)




## Installation ##

### Option 1: via Package Control (recommended) ###

1) Install [Package Control](https://packagecontrol.io/installation)

2) Open the command pallete via `ctrl+shift+p` (Win, Linux) or `cmd+shift+p` (OS X)

3) Choose `Package Control: Install Package`

4) Choose `Fortran`

5) The package will be installed and updated regularly by Package Control


### Option 2: clone the repository

1) In a terminal, `cd` into your Sublime Text Packages directory (which you can find via the menu option `Preferences → Browse Packages...`)

2) Clone the repository: `git clone https://github.com/315234/SublimeFortran.git Fortran` (note the local directory name at the end of the command line)

3) To update the package in future, return to the directory and run `git pull`



## Configuration ##

## Disabling documentation and latex popups ##

These can be turned on or off with the following settings:

```JSON
{
    "fortran_disable_docs": true,
    "fortran_disable_latex": true,
}

```

### Disabling rulers ###

The Fixed Form Fortran syntax included in this package sets some rulers to help code indentation and show where the 72 character limit is. If you find these distracting, they can be disabled by creating a language specific settings file.

To do this, create a file called `FortranFixedForm.sublime-settings` in your `Packages/User/` containing the following:
```JSON
{
    "rulers": []
}
```




### Using the linter ###

This package includes a linter based on SublimeLinter3. SublimeLinter user settings can be modified by selecting `SublimeLinter Settings - User` from the Command Palette.

You may need to tell SublimeLinter where `gfortran` is located by adding it to `paths` in SublimeLinter user settings:

```JSON
{
    "user": {
        "paths": {
            "linux": [],
            "osx": [
                "/usr/local/bin"
            ],
            "windows": []
        },
    }
}
```
Additional command line flags for `gfortran` may be also specified:
```JSON
{
    "user": {
        "linters": {
            "gfortranfixedform": {
                "@disable": false,
                "args": [
                    "-fdefault-real-8",
                    "-fdefault-double-8"
                ],
                "excludes": []
            },
            "gfortranmodern": {
                "@disable": false,
                "args": [
                    "-fdefault-real-8",
                    "-fdefault-double-8",
                    "-ffree-line-length-none"
                ],
                "excludes": []
            },
        },
    }
}
```
The default flags included are currently `-cpp -fsyntax-only -Wall`.
