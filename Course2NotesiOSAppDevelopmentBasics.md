
<!-- TOC depth:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Week 2 Further Introduction to XCode](#week-2-further-introduction-to-xcode)
	- [Running Code in an App](#running-code-in-an-app)
	- [Creating Interfaces](#creating-interfaces)
	- [Using Buttons](#using-buttons)
- [Week 3 UIKit and the Interface Builder](#week-3-uikit-and-the-interface-builder)
	- [Beginning Auto Layout](#beginning-auto-layout)
	- [In-Depth Auto Layout](#in-depth-auto-layout)
	- [Basic UI Elements](#basic-ui-elements)
	- [UIStackView](#uistackview)
- [Week 4 Advanced UI Concepts](#week-4-advanced-ui-concepts)
	- [Modifying the View Hierarchy in Code](#modifying-the-view-hierarchy-in-code)
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

# Week 3 UIKit and the Interface Builder

## Beginning Auto Layout

To scale the simulator: select 'window' -> 'scale' -> '33%'.
To select another device: select 'hardware' -> 'device' -> 'iphone'

We can see the size and origin of the image by clicking 'show the size inspector'
at the right panel.

If we want to adjust the location of the button, click it and at the right bottom,
find the 'pin'. Then we can select the top/left/bottom/right constraint. After we
adding them, in the `ViewController` tree, the constraints will show up. You can also
find it at the right panel.

We can also add constraint for the button like `height`.

Two ways to auto fix the constraints issue:

* At the left pane scene, right to the `View Controller Scene`, click the yellow
  or red arrow. Then we could fix the constraints issue by clicking the warnings
  and then `fix the misplacement`.
* At the right bottom of `ViewController`, click `Resolve Auto Layout Issues`.

Put a UI Element at the center of the `ViewController`:

* click the element, go to right pane, `Show the Size Inspector`.
* `Arrange`, selects `Center horizontal/Vertical`.

**Very important**: remember to uncheck the *constrain to margins*. Otherwise
your image cannot fill out the screen. Can refer to stackoverflow article
[here](http://stackoverflow.com/questions/25807545/what-is-constrain-to-margin-in-storyboard-in-xcode-6)

## In-Depth Auto Layout

* To delete some constraints:
	* click the object, e.g. bottom or image
	* go to right panel, click the ruler shape icon at the top, 'show the size inspector'
	* scroll down, there is a section for 'constraints'
* Container view is convenient when have 5 buttons at the bottom.
	* right panel, in 'filter', type `uiview`
* Let the contents, e.g. the button, of the view decides the height.
	* Just set the constraints as last section, but this time, only left/top/bottom and height.
	* Fix the view: left panel, click warnings, click `view`,
	  check `apply to all views in the container`, click `fix misplacement`
* Make 4 buttons:
	* `ctrl-c` `ctrl-v` 3 times
	* set the top/bottom space to be 0
* Now adjust the space between the 4 bottoms
	* `ctrl+click` the left most buttom and drag to the buttom next to it
	* Then select `horizontal spacing`, set it to 0
	* right most botton, select `trailing space to container`, set it to 0.
	* To make them equal width, `ctrl+click` and select `equal width`
	* Then just `fix misplacement`

## Basic UI Elements

* Other UI elements
	* click `main.storyboard`, then right panel.
* `Label` and `Button` are sub class of UI View.
* `Button` has control
	* Alignment in enabled/selected/Highlighted.
* `Segmented Control`: iOS version of radio button.
	* How many segments
* `Text Field`:
	* Can use `Placeholder`.
* `Slider`
* `Switch`
* `Activity Indicator View`:
	* `Animating`
	* `Hides when Stopped`
* `Image View`
* `Text View`
	* subclass of scope
* `Scroll View`
* `Visual Effect with Blur`

## UIStackView

Make the 4 buttons super easy.

* select all 4 the buttons we created, then press the leftmost of the 4 icons in
  the right bottom corner of `View Controller Scene`.
* Click `Stack View` in the left pane and then `attribute inspector`.
* Most important part is `Alignment` and `Distribution`, which we use `Fill equally`.
	* `Fill equally`: what we want.
	* `Equal spacing`: The space between buttons are the same.
	* `Equal center`: The center of each button are distributed.
* We can add `Image View` and new `Buttom` in, and they are still equally filled.
* We can stack one step further by stacking the image and the 4 buttons together.
* We can also a top bar and delete them.

# Week 4 Advanced UI Concepts

## Modifying the View Hierarchy in Code

We are going to make a pop up menu when we press `Filter`. The stack view doesn't
make sense, because it will top image view become smaller. Secondary view will
overlay.

* We move the `ImageView` and the `View` of 4 buttons out of the vertical stack view.
* Added the top/left/right/bottom constraints for button view and top/left/right
  constraints for image view. Then auto fix the constraint issue.
* Delete the behavior by right clicking the button like `Share` or `Compare`,
  click the cross to remove the function associated with the button.
* Add a `View` outside the `View Controller`
	* First search 'uiview' in the search bar of object library, and drag it to
	  the `View Controller`.
	* Then drag it outside the `View Controller` in the left pane.
* Add a `Horizontal Stack View` to the new `View`, set the top/left/right/bottom constraints,
  fix the constraints problem by using the bottom right icon `Resolve Auto Layout Issues`.
  Set the `Distribution` to `Fill equally`.
* Add 5 buttons to the `Stack View`.
* Delete the code for the `Button` and the code inside `viewDidLoad`.
* Hold `alt` and click the `Main.Storyboard` to bring up the Storyboard in
  Secondary view.
* `ctrl+click` to bring outlet of secondary menu, filter button and bottom menu
  to the code. Like we did in last lecture.
* Also add an action for `filter` button, with the following code:

```swift
view.addSubview(secondaryMenu)
```

* Make sure the following [here](http://stackoverflow.com/questions/26442414/libcabi-dylib-terminating-with-uncaught-exception-of-type-nsexception-lldb),
go to Main.storyboard, RIGHT click on the yellow
box icon (view controller) at the top of the phone outline and DELETE the
outlet(s) with yellow flags.

* The final code looks like this:

```swift
override func viewDidLoad() {
	super.viewDidLoad()
	// Do any additional setup after loading the view, typically from a nib.
	secondaryMenu.translatesAutoresizingMaskIntoConstraints = false
	secondaryMenu.backgroundColor = UIColor.whiteColor().colorWithAlphaComponent(0.5)

}

@IBAction func onFilter(sender: UIButton) {
	if (sender.selected) {
		hideSecondaryMenu()
		sender.selected = false
	} else {
		showSecondaryMenu()
		sender.selected = true
	}
}

func showSecondaryMenu() {
	view.addSubview(secondaryMenu)

	let bottomConstraint = secondaryMenu.bottomAnchor.constraintEqualToAnchor(bottomMenu.topAnchor)
	let leftConstraint = secondaryMenu.leftAnchor.constraintEqualToAnchor(view.leftAnchor)
	let rightConstraint = secondaryMenu.rightAnchor.constraintEqualToAnchor(view.rightAnchor)

	let heightConstraint = secondaryMenu.heightAnchor.constraintEqualToConstant(44)

	NSLayoutConstraint.activateConstraints([bottomConstraint, leftConstraint, rightConstraint, heightConstraint])

	view.layoutIfNeeded()

}

func hideSecondaryMenu() {
	secondaryMenu.removeFromSuperview()
}
```

## Basic Animations

We can add some animations in the showSecondaryMenu and hideSecondaryMenu function.

```swift
func showSecondaryMenu() {
	view.addSubview(secondaryMenu)

	let bottomConstraint = secondaryMenu.bottomAnchor.constraintEqualToAnchor(bottomMenu.topAnchor)
	let leftConstraint = secondaryMenu.leftAnchor.constraintEqualToAnchor(view.leftAnchor)
	let rightConstraint = secondaryMenu.rightAnchor.constraintEqualToAnchor(view.rightAnchor)

	let heightConstraint = secondaryMenu.heightAnchor.constraintEqualToConstant(44)

	NSLayoutConstraint.activateConstraints([bottomConstraint, leftConstraint, rightConstraint, heightConstraint])

	view.layoutIfNeeded()

	self.secondaryMenu.alpha = 0
	UIView.animateWithDuration(0.5, animations: {
		self.secondaryMenu.alpha = 1.0
	})
}

func hideSecondaryMenu() {
	UIView.animateWithDuration(0.4, animations: {
		self.secondaryMenu.alpha = 0
		}, completion: { completed in
			if completed == true {
				self.secondaryMenu.removeFromSuperview()
			}
	})
}
```

**Here I don't understand what the completed does**
