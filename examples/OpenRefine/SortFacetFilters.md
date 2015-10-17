# OpenRefine Sorting, Faceting, &amp; Filtering
You'll need to have OpenRefine installed and running first. Go to the [OpenRefine website](http://www.openrefine.org/download.html) to get the installation instructions this if you don't have it.

The following show the options to sort, facet, filter then export the selected to a CSV.

## Starting OpenRefine

1. Start OpenRefine and if the window doesn't pop up, open http://127.0.0.1:3333 in your preferred web browser (not Internet Explorer).
2. Open an existing project or create a new project by going to Create Project > Uploading your data file. If you need more help creating a new project, check the [official OpenRefine documentation](https://github.com/OpenRefine/OpenRefine/wiki/Importers).
3. Once you're project is created, your data will open in the default project view. You can now run some faceting work/reports. OpenRefine works with your data in a tabular model - i.e., similar to a spreadsheet: you have rows, columns and cells – a cell is a field defined by a row and a column.

## Sorting Rows in OpenRefine
To sort the rows based on a specific column:

1. Click on the small downward arrow next to the column you wish to sort by, then choose “Sort…”. 
2. In the dialog box that appears, select what to sort the values by and then what the sorting order. 
3. Click “OK”. The interface should update to show your sort.
4. To undo a sort, click on the column arrow to see the menu again, then select “Sort...”, then “Remove sort”. The interface should update.

## Faceting Values in OpenRefine
To facet so that only certain rows are shown for a particular option:

1. Click on the arrow at the top of the column containing the values you want to facet by. Select “Facet”.
2. You can facet differently for text, numbers or dates (or write your own facet with GREL, shown below) – for library data work, we will generally be faceting by test.
3. This action opens a text facet window in the left-hand side of the OpenRefine interface, showing all the unique text values (facets) in that chosen column.
4. Now click on one of the choices, and the interface will show just the rows containing that value in the chosen column. You can hover over additional facets, and click on 'include' to add additional facets at the same time.
5. To remove a facet, hover over the facet and click 'exclude'. Or you can click 'reset' in the top right corner of the facets window.

## Creating a Custom Text Facet
To create a custom true/false facet:

1. Click on the arrow at the top of the column containing the values you want to facet by. Select “Facet”.
2. Choose 'Custom text facet...'.
3. In the box that appears, enter the [GREL (or Google Refine Expression Language) expression](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Functions) that you wish to facet by. For example: "value.contains('Tennessee')" will facet by values that contain Tennessee.
4. This action opens a text facet window in the left-hand side of the OpenRefine interface, showing True / False. True then shows all the rows where the value in that column matches the expression (i.e. all the rows that do contain the value 'Tennessee').

## Filtering Values in OpenRefine
To further facet the values that display, you can also use a text filter:

1. Click on the arrow at the top of the column containing the values you want to filter on. Select 'Text filter'.
2. A column text filter box will appear in the left-hand side of the OpenRefine interface. Type in the value you wish to filter by - the value that should appear in the cell in the rows that remain.
3. You can also use Regular Expressions in the text filter box.
4. This should automatically update the OpenRefine interface to show just the rows where that column contains the filtered-upon value.
5. To remove a filter, just close the Text filter box.

## Exporting Selected Rows from OpenRefine to CSV
With any of the above, when you have a subset showing either through facets or filters, you can then export just that subset of data from OpenRefine.

1. Leaving the facet and/or filter intact, go to the Export button in the top right corner of the OpenRefine interface.
2. Choose the format you wish to export to - CSV is normally used.
3. This will download just the subset to your computer.

