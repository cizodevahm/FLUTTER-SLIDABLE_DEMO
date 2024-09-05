# Flutter SLIDABLE Demo

<p align="center">
<a href="mailto:hello@cizotech.com" target="_blank">Email: hello@cizotech.com</a>
<a href="https://cizotech.com" target="_blank">Visit us: www.cizotech.com</a>
</p>

# FLUTTER-SLIDABLE_DEMO

A Flutter implementation of slidable list item with directional slide actions that can be dismissed.

## Migration from 0.6.0

You can read this small guide to migrate from the 0.6 to the 1.0 version: https://github.com/cizodevahm/FLUTTER-SLIDABLE_DEMO/wiki/Migration-from-version-0.6.0-to-version-1.0.0

## Features

* Accepts start (left/top) and end (right/bottom) action panes.
* Can be dismissed.
* 4 built-in action panes.
* 2 built-in slide action widgets.
* 1 built-in dismiss animation.
* You can easily create custom layouts and animations.
* You can use a builder to create your slide actions if you want special effects during animation.
* Closes when a slide action has been tapped (overridable).
* Closes when the nearest `Scrollable` starts to scroll (overridable).
* Option to disable the slide effect easily.

## Install

In the `pubspec.yaml` of your flutter project, add the following dependency:

```yaml
dependencies:
  flutter_slidable: <latest_version>
```

In your library add the following import:

```dart
import 'package:flutter_slidable/flutter_slidable.dart';
```

## Getting started

Example:

```dart
Slidable(
  // Specify a key if the Slidable is dismissible.
  key: const ValueKey(0),

  // The start action pane is the one at the left or the top side.
  startActionPane: ActionPane(
    // A motion is a widget used to control how the pane animates.
    motion: const ScrollMotion(),

    // A pane can dismiss the Slidable.
    dismissible: DismissiblePane(onDismissed: () {}),

    // All actions are defined in the children parameter.
    children: const [
      // A SlidableAction can have an icon and/or a label.
      SlidableAction(
        onPressed: doNothing,
        backgroundColor: Color(0xFFFE4A49),
        foregroundColor: Colors.white,
        icon: Icons.delete,
        label: 'Delete',
      ),
      SlidableAction(
        onPressed: doNothing,
        backgroundColor: Color(0xFF21B7CA),
        foregroundColor: Colors.white,
        icon: Icons.share,
        label: 'Share',
      ),
    ],
  ),

  // The end action pane is the one at the right or the bottom side.
  endActionPane: const ActionPane(
    motion: ScrollMotion(),
    children: [
      SlidableAction(
        // An action can be bigger than the others.
        flex: 2,
        onPressed: doNothing,
        backgroundColor: Color(0xFF7BC043),
        foregroundColor: Colors.white,
        icon: Icons.archive,
        label: 'Archive',
      ),
      SlidableAction(
        onPressed: doNothing,
        backgroundColor: Color(0xFF0392CF),
        foregroundColor: Colors.white,
        icon: Icons.save,
        label: 'Save',
      ),
    ],
  ),

  // The child of the Slidable is what the user sees when the
  // component is not dragged.
  child: const ListTile(title: Text('Slide me')),
),
```

## Motions

Any `ActionPane` has a motion parameter which allow you to define how the pane animates when the user drag the `Slidable`.

### Behind Motion

The actions appear as if they where behind the `Slidable`:

![Behind Motion][behind_motion]

### Drawer Motion

Animate the actions as if they were drawers, when the `Slidable` is moving:

![Drawer Motion][drawer_motion]

### Scroll Motion

The actions follow the `Slidable` while it's moving:

![Scroll Motion][scroll_motion]

### Stretch Motion

Animate the actions as if they were streched while the `Slidable` is moving:

![Stretch Motion][stretch_motion]

### Controller

You can use ```SlidableController``` to open or close the actions programmatically:

```dart
final controller = SlidableController();

// ...

Slidable(
  controller: controller,
  // ...
);

// ...

// Open the actions
void _handleOpen() {
  controller.openEndActionPane();
  // OR
  //controller.openStartActionPane();
}

void _handleOpen() {
  controller.close();
}
```
# Contribute
If you want to contribute to this library, you're always welcome! See [Contributing Guidelines.](https://github.com/cizodevahm//FLUTTER-MVVM-DEMO/blob/master/CONTRIBUTING.md)

## Contact Us


Do you want to add more features? [Reach us out](https://https://cizotech.com/contact-us/)

# License
```MIT License

Copyright (c) 2024 CIZO

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```