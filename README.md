# DSFDropFilesView

![](https://github.com/dagronf/dagronf.github.io/blob/master/art/projects/DSFDropFilesView/screenshot.png?raw=true)

A simple view class for dropping files onto.

![](https://img.shields.io/github/v/tag/dagronf/DSFDropFilesView) ![](https://img.shields.io/badge/macOS-10.11+-red) ![](https://img.shields.io/badge/Swift-5.0-orange.svg)
![](https://img.shields.io/badge/License-MIT-lightgrey) [![](https://img.shields.io/badge/spm-compatible-brightgreen.svg?style=flat)](https://swift.org/package-manager)


## Why

I've need something like this many times. So here's a module to make my future life easier maybe.

## Installation

### Swift Package Manager

Add `https://github.com/dagronf/DSFDropFilesView` to your project.

## Usage

### Via Interface Builder

Add a new `NSView` instance using Interface Builder, then change the class type to `DSFDropFilesView`

### Programatically

```swift
let dropView = DSFDropFilesView(frame: .zero)
```

## Delegation

To receive callbacks from the control, set the `dropDelegate` to your view controller.

```swift
@objc optional func dropFilesViewWantsSelectFiles(_ sender: DSFDropFilesView)
```
An optional method that gets called if the user clicks the 'Select files...' button on the control.

```swift
func dropFilesView(_ sender: DSFDropFilesView, validateFiles: [URL]) -> NSDragOperation
```
Called when the drag enters the view. Return the drag operation (or an empty array) to indicate how the drag is to proceed. Use this function to filter out if the 'wrong' types of files are dropped. (for example, if you only want to receive PDFs).

```swift
func dropFilesView(_ sender: DSFDropFilesView, didDropFiles files: [URL]) -> Bool
```
Called with the files when the user actually drops the files.

## Customizations

### Properties

These properties can all be configured via Interface Builder or programatically.

#### Allowed drop counts

* `allowMultipleSelect` : Allow multiple files/folders to dropped

#### Select files button (optional)

* `selectFilesButtonLabel` : Embed a clickable button for accessibility with the specified label. If empty, doesn't display the button (default)
* `selectFilesButtonIsLink` : If the select files button is display, show the button as a hyperlink (blue underlined text) instead of a button.

#### Icon

* `showIcon` : Should we display an icon
* `icon` : The icon to display. A default icon is supplied

#### Label

* `label` : The text of the label. If empty, the label is hidden.
* `lineWidth` : The line width for the dotted border
* `cornerWidth` : The radius for the corners

## History and changes

### `1.1.0`

#### Select files button

* Added `selectFilesButtonLabel` to allow the user to specify the 'select files' text. Removes the need for the package to provide its own localizations -- the user can provide them if needed.
* Removed the `selectFiles` property, as it can now be inferred from the `selectFilesButtonLabel` content.
* Added `selectFilesButtonIsLink` to display the 'select files' button in a hyperlink style (blue underlined) or a standard button.

#### Multiple select

* Renamed `multipleSelect` to `allowsMultipleSelect` for code clarity.

#### General

* Removed localizations file (no longer needed)

### `1.0.0`

* Initial release

## License

```
MIT License

Copyright (c) 2020 Darren Ford

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
