# fullbomcreate
a simple bom creation tool for html written in awk

How to Install
==============

This is a fairly simple awk script for generation of html table objects. You'll want to install it at `/usr/local/bin/fullbomcreate`.

1. First clone the repository to your home folder or wherever's convenient. Go into the directory: `cd fullbomcreate`

2. Make sure that you can execute the script by typing `chmod 755 fullbomcreate`

3. Copy the script to `cp fullbomcreate /usr/local/bin/`

4. You should now be able to run the script as you would any other command line tool

5. Generally when you invoke the script you'll want to pipe the output to the clipboard. On a mac this would look like:

`$ fullbomcreate bom.txt | pbcopy`

Formatting input files for fullbomcreate
========================================

The input files should be tab delimited so quotes are not necessary. Look at fullbom.txt for an example. The first line of any bom should have the bom heading enclosed by stars followed by the heading background color as a hex value then the text color as a hex value.

The BOM entries should be formatted with the SKU first, quantity second and item description last. fullbomcreate will ignore any input past the first three fields

An empty row between BOM sections will trigger a </table> tag. Awk expects a newline at the end of a document so you must put two newlines at the very end of a bom text file to get proper output. This is a bit hackish, but it works.