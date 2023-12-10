# Update a file through a Python algorithm Lab


## Project description

This was a lab for the Google Cybersecurity Certificate. The prompt was to create an Algorithm using what we had learned in Python to read and update an allow list. 

We were given an allow list of IP addresses which has access to restricted content, `“allow_list.txt”`. We were then given a remove list which identifies IP addresses that should no longer have access to the restricted content. I automated updating of the `“allow_list.txt”` to remove IP addresses that should no longer have access using a Python algorithm. 

## Environment/Code:

- Jupyter notebook
   
- Python

## Open the file that contains the allow list
The first part of the project I was tasked with opening the allow list file.
I assigned <code>"allow_list.txt"</code> as a string to the variable <code>import_file</code>:


<img src="https://i.imgur.com/Hw3AKTz.png" height="70%" width="70%" alt="Open file"/>


To open the file I used a <code>with</code> statement:


<img src="https://i.imgur.com/Hw3AKTz.png" height="70%" width="70%" alt="Open file"/>

The purpose of this code is to open the allow list file, access the IP addresses stored in the file,  and then save the output as the variable `file` outside the statement. 
`with` is used to manage resources.
`open()` is the function to open files  
(import_file, “r”) are the parameters for my `open()` function. `import_file`, the name of the file to be opened, and `”r”`the parameter for read.
`as` `file` - `as` keyword assigns `file` variable  to reference the `open()` function output.

## Read the file contents
I use `.read()` to convert `file` into the string.

<img src="https://i.imgur.com/ln5BP1C.png" height="70%" width="70%" alt="Read"/>

Purpose of this code is to convert `“allow_list.txt”` into a string format that I can later use to organize and extract data. I assigned the string to the variable `ip_addresses` .

`.read()` - can convert a file into a string. `.read()` function can be called in the body of a statement when the `.open()` function is used  with read argument `”r”`.


## Convert the string into a list

Used `.split()` to make a list from the `ip_addresses` string. 

<img src="https://i.imgur.com/3Y7VnJG.png" height="70%" width="70%" alt="Convert"/>

Purpose of this code was to create a list of IP addresses that I could remove addresses from. I converted the string into a list then assigned it back to the `ip_addresses` variable
`.split()` - converts a string to a list.

## Iterate through the remove list

A `for` loop was used to check the IP addresses for those that are in the `remove_list`.

<img src="https://i.imgur.com/HiPXbjz.png" height="50%" width="70%" alt="Iterate through remove list"/>

`for` - Create a `for` loop which is needed to iterate through a specified sequence. 
`element` - the loop variable
`in remove_list`  -  iterate through and assign values to the loop variable.


## Remove IP addresses that are on the remove list

My algorithm requires removing any IP address from the allow list, ip_addresses, that is also
contained in remove_list. 

<img src="https://i.imgur.com/oStuOoT.png" height="70%" width="70%" alt="Remove IP addresses"/>

Within the loop body I created a conditional to see if the element variable was found in the list of ip addresses.
I then used `.remove()` with the loop variable `element` passed through it on `ip_addresses` so that every IP on the `remove_list` would be removed. 

## Update the file with the revised list of IP addresses

I used `.join()` to convert the list back to a string so that I could update the allow list.

<img src="https://i.imgur.com/49ZaEH4.png" height="70%" width="70%" alt="Update file"/>

I used `”\n”` to give each IP address a new line.


I then used a `with`statement  followed by a `.write()` to update the allow list.

<img src="https://i.imgur.com/uE73azg.png" height="70%" width="70%" alt="Update file"/>

## Full code:

```Python
with open(import_file, "r") as file:

    ip_addresses = file.read()

ip_addresses = ip_addresses.split()


for element in remove_list:
    
    if element in ip_addresses:

        ip_addresses.remove(element)


ip_addresses = "\n".join(ip_addresses)


with open(ip_addresses, "w") as file:
    
  file.write(ip_addresses)
```
