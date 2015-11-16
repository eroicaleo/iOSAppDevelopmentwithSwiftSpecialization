
<!-- TOC depth:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Week 2 Further Introduction to XCode](#week-2-further-introduction-to-xcode)
	- [Running Code in an App](#running-code-in-an-app)
	- [Creating Interfaces](#creating-interfaces)
	- [Using Buttons](#using-buttons)
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

## Creating Interfaces

We want to display images on the App, we would go to 'launchscreen.storyboard'.
Also right side panel, 'Show the object library' -> filter, type 'image' ->
then drag the image to 'view controller' -> double click it -> at the top of right
panel, click 'show the attributes inspector' -> Change the background color.

Then open assistant editor, place the 'ViewController' and the code side by side.
Press the `ctrl` and right click the image, drag it to the `ViewController` class.
It must be outside the `viewDidLoad` function. And give it the name `viewImage`

Then the `viewImage` becomes a property of the class. We can put the following
code in our `viewDidLoad` function.

```swift
viewImage.image = result
```

## Using Buttons

We add button by click ctrl and drag to the `ViewController` class.
For a button, we need to add it twice: one for the button itself and one for click
by changing the `Connection` to `Action` and `Type` to `UIBotton`.


A button has 4 states:

* Default
* Highlighted
* Selected
* Disabled

We could change the text for one button in the `main.storyboard`'s attribute
inspector. Or we could do it with the following code.

```swift
imageToggle.setTitle("show previous image", forState: .Selected)
```
