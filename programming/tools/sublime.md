#Sublime Text

## Theme
Sublime Text Material Theme

Install package control, use command line -> "Package Control: Install Package", and look for Material Theme.

Stored at Material-Theme.sublime-theme

## Open up command line
Shift Ctrl P

## Package Resource Viewer
Extracts packages, lets you view and edit them

## Search for file / method
- Ctrl P
	Browse any file in the system
	Ctrl P + @ = Ctrl R
	Default is the last file opened, good for switching back to the last file
- Ctrl R
	Go to symbol, find methods, etc in a file
	Note that to find a method in a file instantly, use Ctrl P, type in `file-name@method-name`

## Create new files
Use "advanced new files" - Ctrl Alt N
Put a colon in the front to create file in the same directory
In command line, advanced file (ANF) allows for deleting and renaming files

## Multiple cursors or seach for word
- Ctrl D
	Select whole word
	Keep adding Ctrl D to select the next same word at the same time
- Alt Fn F3 (Alt F3)
	Select all occurences of the same word in the file

##Snippet
Current snippet: 
- `met`, Tab -> (change public to protected) Tab -> function name & parameter, Tab -> done
	add new method
- `class`, Tab -> (change class name) done
	add new class
- `_c`, Tab -> (change paramter name), Tab -> done
	add new constructor

Save snippet as "snippet-name.sublime-snippet"

## PSR-2 Format
Use the package php-cs-fixer. Use following command in command line.
`$ php-cs-fixer fix [file-name] --level="psr2"`
or go to Tools -> Build System and choose PSR-2 (custom setting)

## Others
- Ctrl /
	Toggle comment / uncomment
- Use PHP Getters and Setters to gernerate getters and setters
	Shift Ctrl P open command line, use keyword `getter` or `setter`
	"Gernerate Getter for name" - generate specific getter
	"PHP: Generate Getters" - generate all getters, will read contructor properties and generate getters for them
- PHP Companion
	- F6 (Fn F6) to fully expand classname when importing
	- F7 (Fn F7) to auotmatically insert constructor into class
		press F7 (Fn F7) again to add another parameter in the same constructor