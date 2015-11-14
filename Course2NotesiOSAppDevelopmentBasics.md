
<!-- TOC depth:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Week 2 Further Introduction to XCode](#week-2-further-introduction-to-xcode)
	- [Running Code in an App](#running-code-in-an-app)
<!-- /TOC -->

# Week 2 Further Introduction to XCode

## Running Code in an App

To start a new project:

'Create a new XCode project' -> 'Single View Application'.

In the project hierarchy tree, the top 'Filterer' is the project file containing
project settings.

* Every app starts with `AppDelegate`
 	* Apps have live cycle: launch/close/leave and come back. We have to handle
	  these events.
	* `AppDelegate` helps with these.
* There is no `main` program in swift.
* `ViewController`
	* everything on the screen will be inside a `ViewController`.
	* All it does is load/display/disappear.
	* `viewDidLoad` is the first place where the view has been loaded.
	* We past the code from previous course to `viewDidLoad`.
	* remember to check 'copy item if needed' check box.
* `Asset.xcassets` to add image in it.
* top left part to run the code.
