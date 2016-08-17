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

Formatting Input Files For fullbomcreate
========================================

The input files should be tab delimited so quotes are not necessary. Look at fullbom.txt for an example. The first line of any bom should have the bom heading enclosed by stars followed by the heading background color as a hex value then the text color as a hex value.

The BOM entries should be formatted with the SKU first, quantity second and item description last. fullbomcreate will ignore any input past the first three fields

An empty row between BOM sections will trigger a `</table>` tag. Awk expects a newline at the end of a document so you must put two newlines at the very end of a bom text file to get proper output. This is a bit hackish, but it works.

Example
_______

`*Core Components Kit*	#383838	#fff
25286-19	4	Button Head Cap Screw M5 x 12
25287-08	1	M5 Flat Washer

*750mm Drag Chain Kit*	#8A52A1	#fff
30681-01	1	Drag Chain Support Arm
25281-05	2	T-Slot Nut M5 Pre-Assembly`

Gives us this table:

<table>
  <tr>
    <td style="color:#fff;background: #383838" colspan="3">
      <b>Core Components Kit</b>
    </td>
  </tr>
  <tr>
    <td>
      <b>SKU</b>
    </td>
    <td>
      <b>Name</b>
    </td>
    <td>
      <b>Quantity</b>
    </td>
  </tr>
  <tr>
    <td>
      25286-19
    </td>
    <td>
      Button Head Cap Screw M5 x 12
    </td>
    <td>
      4
    </td>
  </tr>
  <tr>
    <td>
      25287-08
    </td>
    <td>
      M5 Flat Washer
    </td>
    <td>
      1
    </td>
  </tr>
</table>
<table>
  <tr>
    <td style="color:#fff;background: #8A52A1" colspan="3">
      <b>750mm Drag Chain Kit</b>
    </td>
  </tr>
  <tr>
    <td>
      <b>SKU</b>
    </td>
    <td>
      <b>Name</b>
    </td>
    <td>
      <b>Quantity</b>
    </td>
  </tr>
  <tr>
    <td>
      30681-01
    </td>
    <td>
      Drag Chain Support Arm
    </td>
    <td>
      1
    </td>
  </tr>
</table>