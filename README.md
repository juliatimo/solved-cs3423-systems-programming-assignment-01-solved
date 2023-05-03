Download Link: https://assignmentchef.com/product/solved-cs3423-systems-programming-assignment-01-solved
<br>
: Shell Scripting







For this assignment, you will use <strong>bash </strong>create a simple inventory system. The system will store basic information about items and allow the user to create, read, update, delete, and total these items.

This assignment requires only the utilities used so far in the lecture notes. Further, you <strong><u>may not use </u></strong>sed, awk, find, grep, Python, perl, any programming language, scripting language, or other tools not otherwise permitted. The only external tool you <strong>may </strong>utilize is bc, which can be used to perform floating-point arithmetic.

<h1>Storing Item Information</h1>

Item information will be stored in text files (ending with the extension .item).

<ol>

 <li>Files will be stored in a directory named <strong>data</strong>, located within the same directory as your shell script.</li>

 <li>Each file will be named based on its unique item number, an integer (henceforth referred to as item_num) with exactly <strong>four </strong>digits, followed by the extension <strong>.item</strong>.</li>

 <li>An item file consists of exactly three lines, in the following format:

  <ul>

   <li>item_name <em>(string <strong>with no whitespace</strong>) </em>simple_name <em>(string)</em></li>

   <li>unit_price <em>(floating point number) </em>cur_qty <em>(unsigned integer) </em>max_qty <em>(unsigned integer)</em></li>

   <li>item_desc <em>(string)</em></li>

  </ul></li>

 <li>The following are the example contents of an item file named <strong>item</strong>:</li>

</ol>

<table width="577">

 <tbody>

  <tr>

   <td width="198">btl_water Bottled Water</td>

   <td width="134">(24/pk)</td>

   <td width="245"> </td>

  </tr>

  <tr>

   <td width="198">15.99 23 50Poland Springs natural</td>

   <td width="134">spring drinking</td>

   <td width="245">water</td>

  </tr>

 </tbody>

</table>

<h1>Script Execution</h1>

When the script is run, the following should occur.

<ol>

 <li>Upon running your script, the user should be presented with the following menu:</li>

</ol>

<strong>Enter one of the following actions or press CTRL-D to exit.</strong>

<strong>C – create a new inventory item</strong>

<strong>R – read an existing inventory item</strong>

<strong>U – update an existing inventory item</strong>

<strong>D – delete an existing inventory item</strong>

<strong>T – calculate total value of an inventory item</strong>

<ol start="2">

 <li>The user then enters a corresponding one-character selection (either upper or lowercase entries should be permissible), leading to one of the following actions:

  <ul>

   <li><strong>C</strong>: create a new inventory record (thus, also creating its associated data file)

    <ul>

     <li>From the terminal, read the following fields, one at a time, each separated on its own line:

      <ol>

       <li>Item number: <em>(four digit unsigned integer) </em>Example input: 3293 ii. Item name: <em>(string containing <strong>no whitespace</strong>) </em>Example input: btl_water iii. Simple name: <em>(string)</em></li>

      </ol></li>

    </ul></li>

  </ul></li>

</ol>

Example input: Bottled Water (24/pk) iv. Unit price: <em>(floating point number) </em>Example input: 15.99

<ol>

 <li>Current quantity: <em>(unsigned integer) </em>Example input: 23</li>

 <li>Maximum quantity: <em>(unsigned integer) </em>Example input: 50 vii. Description: <em>(string)</em></li>

</ol>

Example input: Poland Springs natural spring drinking water

<ul>

 <li>Using the values entered by the user, create a new file in the <strong>data </strong>subdirectory (which may or may not pre-exist) based on the file naming instructions above.</li>

 <li>Update <strong>data/queries.log </strong>by adding the following line:</li>

</ul>

<strong>[<em>date</em>] CREATED: <em>item_num </em>– <em>item_name </em>– <em>cur_qty </em>/ <em>max_qty </em></strong>where:

<ol>

 <li>date is the formatted output from the shell’s <strong>‘date “+[%Y-%M-%d %H:%m:%S]”‘</strong></li>

</ol>

command,

<ol>

 <li>item_num represents the item’s internal identification number (e.g. 3293),</li>

</ol>

<ul>

 <li>item_name represents the item’s internal identification string (e.g. btl_water), and</li>

</ul>

<ol>

 <li>cur_qty represents the item’s initial quantity as of its entry into this inventory system (e.g. 20).</li>

 <li>max_qty represents the item’s maximum allowable inventory quantity (e.g. 50).</li>

</ol>

<ul>

 <li>If the item number already exists, abandon the “Create” operation and print the following example error message, then continue with the script. For example: <strong>ERROR: item <em>3293 </em>already exists</strong></li>

</ul>

<ul>

 <li><strong>R</strong>: read and display an existing item’s inventory information</li>

</ul>

<ul>

 <li>Prompt the user for an inventory item’s number:</li>

</ul>

<strong>Enter an item number:</strong>

<ul>

 <li>Search for the specified inventory item using the item number provided.</li>

 <li>Print the item’s inventory information in the following format:</li>

</ul>

<strong>Item Number:        <em>item_num</em></strong>

<strong>Item Name:            <em>item_name</em></strong>

<strong>Simple Name:        <em>simple_name</em></strong>

<strong>Unit Price:              <em>unit_price</em></strong>

<strong>Quantity:                  <em>cur_qty </em></strong>/ <strong><em>max_qty</em></strong>

<strong>Description:          <em>item_desc</em></strong>

<ul>

 <li>If the item is not found, print the following example error and continue with the script.</li>

</ul>

<strong>ERROR: item <em>3293 </em>not found</strong>

<ul>

 <li><strong>U</strong>: update an existing inventory record

  <ul>

   <li>Prompt the user for the following fields one at a time:

    <ol>

     <li>Item number <em>(four digit unsigned integer)</em></li>

     <li>Item name <em>(string containing <strong>no whitespace</strong>)</em></li>

    </ol></li>

  </ul></li>

</ul>

<ul>

 <li>Simple name <em>(string) </em> Unit price <em>(floating point number)</em></li>

</ul>

<ol>

 <li>Current quantity <em>(unsigned integer)</em></li>

 <li>Maximum quantity <em>(unsigned integer)</em></li>

</ol>

<ul>

 <li>Description <em>(string)</em></li>

</ul>

<ul>

 <li>Using the values entered by the user, search for the specified item in the <strong>data </strong>subdirectory using the given item number.</li>

 <li>Update each of the corresponding fields based on the user’s input. <strong>If the user input is blank for a particular field (except for the item number), keep the existing value currently utilized within the file.</strong></li>

 <li>Update <strong>data/queries.log </strong>by adding the following line:</li>

</ul>

<strong>[<em>date</em>] UPDATED: <em>item_num </em>– <em>item_name </em>– <em>cur_qty </em>/ <em>max_qty </em></strong>where:

<ol>

 <li>date is the formatted output from the shell’s <strong>‘date “+[%Y-%M-%d %H:%m:%S]”‘</strong></li>

</ol>

command,

<ol>

 <li>item_num represents the item’s internal identification number (e.g. 8299),</li>

</ol>

<ul>

 <li>item_name represents the item’s internal identification string (e.g. btl_water), and iv. cur_qty represents the item’s currently-stocked quantity (e.g. 12).</li>

</ul>

<ol>

 <li>max_qty represents the item’s maximum allowable inventory quantity (e.g. 85).</li>

</ol>

(e) If the item number <strong>does not </strong>already exist, abandon the “Update” operation and print the following example error message, then continue with the script. For example: <strong>ERROR: item <em>8299 </em>not found</strong>

<ul>

 <li><strong>D</strong>: delete an existing item’s inventory record

  <ul>

   <li>Prompt the user for an item number:</li>

  </ul></li>

</ul>

<strong>Enter an item number:</strong>

<ul>

 <li>Delete the specified item’s file from the <strong>data </strong></li>

 <li>Update <strong>data/queries.log </strong>by adding the following line:</li>

</ul>

<strong>[<em>date</em>] DELETED: <em>item_num </em>– <em>item_name </em>– <em>simple_name </em>– <em>cur_qty </em></strong>where:

<ol>

 <li>date is the formatted output from the shell’s <strong>‘date “+[%Y-%M-%d %H:%m:%S]”‘</strong></li>

</ol>

command,

<ol>

 <li>item_num represents the item’s internal identification number (e.g. 8299),</li>

</ol>

<ul>

 <li>item_name represents the item’s internal identification string (e.g. btl_water), and</li>

</ul>

<ol>

 <li>simple_name represents the item’s short-form description (e.g. Bottled Water (24/pk)).</li>

 <li>cur_qty represents the item’s currently-stocked quantity (e.g. 12).</li>

</ol>

(d) If the item number <strong>does not </strong>already exist, abandon the “Delete” operation and print the following example error message, then continue with the script. For example: <strong>ERROR: item <em>8299 </em>not found</strong>

<ul>

 <li><strong>T</strong>: calculate total value of current inventory items

  <ul>

   <li>Prompt the user for an item number:</li>

  </ul></li>

</ul>

<strong>Enter an item number:</strong>

<ul>

 <li>Calculate the total value currently in inventory for this specific item (e.g. unit price <em>× </em>current quantity).</li>

 <li>Print the following message with the item’s number, simple name, and total value: <strong><em>item_num </em></strong><strong>– <em>simple_name </em>– $(<em>unit_price</em></strong><em>×<strong>cur_qty</strong></em><strong>) total</strong></li>

 <li>If the given item number <strong>does not exist</strong>, abandon the “Total” operation and print the following example error message, then continue with the script. For example: <strong>ERROR: item <em>8299 </em>not found</strong></li>

</ul>

<ul>

 <li>If an invalid character is entered at the main menu, print the following error message and continue with the script:</li>

</ul>

<strong>ERROR: invalid option</strong>

<ol start="3">

 <li>After an action is completed, display the menu again. This should go on indefinitely until <strong>CTRL-D </strong>or the end of a file is reached.</li>

</ol>

<h1>Assignment Data</h1>

An initial data set can be found in <strong>/usr/local/courses/ssilvestro/cs3423/Spring20/assign1</strong>. Copy this to your own assignment’s directory when you are prepared to begin initial testing. You should not, under any circumstances, rely solely on this data as the only data set with which to test the functionality of your script.

<h1>Script Files</h1>

Your program should consist of six bash files:

<ul>

 <li><strong>bash </strong>– the main file which is to be initially invoked</li>

 <li><strong>bash </strong>– logic for the create option</li>

 <li><strong>bash </strong>– logic for the read option</li>

 <li><strong>bash </strong>– logic for the update option</li>

 <li><strong>bash </strong>– logic for the delete option</li>

 <li><strong>bash </strong>– logic for the calculating total value in inventory of a given item</li>

</ul>

<h1>Verifying Your Program</h1>

Your program must <strong><em>at least </em></strong>function correctly with the input provided in <strong>a1Input.txt</strong>. It is extremely important to note that this is <strong><em>NOT </em></strong>the only input your script will be tested with. Thus, think carefully of corner cases and work diligently to test your scripts with large scale input and debug them accordingly, if necessary.

<ol>

 <li>Verify that your assignment folder has a <strong>data </strong>directory with the initial data set.</li>

 <li>Execute your script and <em>redirect </em><strong>txt </strong>into it. You should <strong>not </strong>be copying or typing the contents of <strong>a1Input.txt </strong>into your terminal. File redirection <strong>must </strong>work.</li>

</ol>

For example, the following must work: <strong>./assign1.bash &lt; a1Input.txt</strong>

<ol start="3">

 <li>Verify that both the printed output and data files are as expected.</li>

</ol>


