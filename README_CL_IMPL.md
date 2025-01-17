# Implementation of Gilded Rose Inventory

This is my implementation of the Gilded Rose Inventory code kata, in Python.

See README_OriginalProblem.md for the problem description, requirements, and requested rules.

Assumptions made in my implementation:

* All strings are in English
* All strings are in ascii (no Unicode support for now)
* All string cases must match (important for category processing and item finding)
* "Once the sell by date has passed..." means that sell_in is < 0
* Since not explicitly mentioned in problem, the default quality adjustment is a decrease of 1 unit per day
* Made assumption: Edge case rule #3, "Aged Brie" actually increases in Quality the older it gets, 
  that aged brie continues increasing in quality even beyond sell date,
  hence not combining with Edge case rule #1
* While adding a new item...
    - String entries cannot be empty
    - Quality entry cannot be negative
    - The letter case you use will be retained
    - A negative sell in will be allowed (practically not a good idea, but not listed as requirement)
    - Aged Brie can be entered with any category, only as Food does it increase in value
    - A quality above 50 can be entered, for sulfuras, but for other items will be clamped to 50 when the day
      advances


## Version Information

ver 1.0 :: Initial release :: released 2021.09.01 :: git repo tag 'ver_100'

## Running the Gilded Rose Inventory

### On a system with Python 2 and Python 3 using command line:

`cd GildedRose/app`

`python3 main_app.py`


### Using Windows and Linux supplied binaries

Find the package corresponding to your OS in the /dist folder of this repository.

Extract the contents, both files, to the same folder.

Run the executable file as you would any other executable.

### Data file information

Upon first run the application will look for a `inventory.txt` in the same directory
as the executable (or main_app.py script). Once the user chooses the menu item that
saves data and exits, a new file `inventoryData.pickle` file is created, holding the
inventory data.  Upon a resume the application will look for this data file and will
load the inventory from there.

If the `inventoryData.pickle` file is not present with the application, it will revert
to the `inventory.txt` file.  If neither is present an error message is displayed. In this 
case simply recreate the `inventory.txt` file.

### Special run mode

A special application run mode is provided for the purpose of reimporting the original
inventory.txt file. Running the Python script in the command line method above, pass an 
argument of `-useinput` will instruct the app to use the inventory.txt file if it exists.

## Unit testing support

Unit testing is added via test cases included inside the app/test/ folder.

To run using PyTest...

`cd GildedRose`

`python -m pytest -vv`

## Future development notes
To add new special case functionality, add a new class derived from
InventoryItem and adjust the create_item factory method.

It is recommended to run unit tests after any change but especially
after changes to the daily adjustment functionality.
