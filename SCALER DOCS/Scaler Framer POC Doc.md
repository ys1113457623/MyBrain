## Questions

- How to handle state management in the framer 

## Framer Features

- Plugins
- Fetch
- Code Components
- Code Overides
- Custom Side Overides

## Framer Limitations

- Limited support to logics and complexity 
- We have to copy paste the logic every-time we are creating a new page(Either we can duplicate the project)
- Importing npm package is currently experimental 
- State management is little complecated here and it might lead to error as framer and custom component both will be using the state
- Even for homepage framer tries to load 40-50mbs of javascript 
- ![[Pasted image 20250911111859.png]]

## PLUGINS

### NODES

- TEXT NODE 
- UNKNOWN NODE 
- CODE COMPONENT NODE
- SVG NODE
- FRAMER NODE 

### CODE COMPONENTS

**CORE FEATURES**
- PROPERTY CONTROLS
	- WE CAN MAKE A PROP CONFIGURABLE FROM THE INTERFACE USING `addPropertyControls`
	- **CONTROL TYPES**
		- ControlType.String
		- ControlType.Boolean
		- ControlType.Array
		- ControlType.Image
		- ControlType.ComponentInstance
		- ControlType.Object
		- ControlType.Color
		- ControlType.Date
		- ControlType.Enum
		- ControlType.Eventhandler
		- ControlType.File
		- ControlType.ResponsiveImage
		- ControlType.Number
		- ControlType.Transition
		- ControlType.Link
		- ControlType.Padding
		- ControlType.BorderRadius
		- ControlType.BoxShadow
		- ControlType.Border
- AUTO SIZING
	- There are 4 setting for code component layout (auto, fixed any and any-prefer-fixed and default is auto)
- SHARING

|Smart Component and Code Components has a unique URL that can be shared


### Overrides Example

**We Can Overrides the following attributes**

- **CUSTOM IDs And Attributes**
  ![[Screenshot 2025-08-19 at 7.26.15 PM.png]]
- **Click Tracking**
  ![[Screenshot 2025-08-19 at 7.26.29 PM.png]]
- **Text Content**
  ![[Screenshot 2025-08-19 at 7.26.37 PM.png]]
