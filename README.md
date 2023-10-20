# algorithm-for-file-updates-in-python

Python algorithm that updates a file to allow certain IP addresses to access content, and remove those that should not have access to that content within my imaginary organization.

## Project Description

In my organization, we manage restricted content access using an IP address allow list, which is tracked in the ```"allow_list.txt"``` file. We also maintain a distinct list for deactivating access to this content, which includes IP addresses that should no longer be granted entry. To enhance efficiency, I designed an algorithm for automating the process of updating the ```"allow_list.txt"``` file by removing IP addresses that are no longer authorized for access.

## Open the file that contains the allow list

In the first part of the algorithm, I opened the file ```“allow_list.txt”```. In order to do this, I first assigned this as a string to the variable ```import_file```:

![Import file](https://i.imgur.com/6lyIvFu.png)

After that, I used a ```with``` statement so that I could open the file:

![Statement to open file](https://i.imgur.com/6LZHrzD.png)

Within my algorithm, I employ the ```with``` statement in conjunction with the ```open()``` function, configured in read mode, to access and read the allow list file. This approach will allow me to retrieve the IP addresses that are stored in the file. The ```with``` keyword serves the additional purpose of resource management by automatically closing the file when exiting the ```with``` statement.

Inside the code ```with open(import_file, "r") as file:```, the ```open()``` function takes two parameters. The first parameter specifies the file to be imported, while the second parameter defines the desired operation, which, in this case, is ```"r"``` for reading. The ```as``` keyword is used to assign the output of the ```open()``` function to a variable named ```file```, which allows me to work with the file content within the ```with``` statement.

## Read the file contents

To access the file's content, I employed the ```.read()``` method, which transforms the contents of ```file``` into a string.

![Read file contents](https://i.imgur.com/7AzVooh.png)

By utilizing the ```.open()``` function with the ```"r"``` argument for reading, I can utilize the ```.read()``` function within the ```with``` statement. This method transforms the file into a string, enabling me to examine its contents. I invoked the ```.read()``` method on the ```file``` variable specified in the ```wit``` statement and stored the resulting string in the ```ip_addresses``` variable.

In other words, this code parses the contents of the ```"allow_list.txt"``` file, converting it into a string format that I can use at a later time to structure and extract data within my Python program.

## Convert the string into a list

To allow me to remove individual IP addresses from the allow list, I need the data to be in a list format. To achieve this, I proceeded by employing the ```.split()``` method, which converted the ```ip_addresses``` string into a list:

![Convert string to list](https://i.imgur.com/xkW7s4U.png)

To transform the string variable into a list, I invoked the ```.split()``` function. This operation involves converting the string's content into a list structure. The main objective behind splitting ```ip_addresses``` into a list is to simplify the process of removing specific IP addresses from the allow list.

By default, the ```.split()``` function divides the text into list elements wherever it encounters whitespace. In this particular algorithm, the ```.split()``` function operates on the data contained in the ```ip_addresses variable```, which is a string comprising individual IP addresses separated by whitespace. This function effectively transforms this string into a list of IP addresses. To preserve this list, I reassigned it to the ```ip_addresses``` variable.

## Iterate through the remove list

An essential component of my algorithm revolves around the need to iterate through the IP addresses listed within the ```remove_list```. To accomplish this task, I integrated a ```for``` loop:

![Iterate through remove list](https://i.imgur.com/pcIL5c3.png)

In Python, a ```for``` loop is utilized to execute a set of code instructions for a designated sequence. In a Python algorithm such as this one, the primary objective of the ```for``` loop is to implement specific code statements for each element within the sequence.

The ```for``` keyword initiates the ```for``` loop, followed by the loop variable, denoted as ```element```, and the ```in``` keyword. The ```in``` keyword signifies the iteration through the ```ip_addresses``` sequence, assigning each value in turn to the loop variable ```element```.

## Remove IP addresses that are on the remove list

To implement my algorithm, I needed to remove any IP address present in the ```ip_addresses``` allow list, which also appears in the ```remove_list```. Since there were no duplicate IP addresses within ```ip_addresses```, I successfully achieved this using the following code:

![Remove IP that are on remove list](https://i.imgur.com/oTFa7pG.png)

Initially, inside my ```for``` loop, I introduced a condition to check whether the loop variable, ```element```, existed within the ```ip_addresses``` list. This was necessary to avoid errors when using the ```.remove()``` method, as attempting to remove elements not present in ```ip_addresses``` would lead to issues.

Subsequently, within that conditional block, I employed the ```.remove()``` method on the ```ip_addresses list```. I used ```element```, the loop variable, as the argument to ensure that each IP address listed in ```remove_list``` would be successfully deleted from ```ip_addresses```.

## Update the file with the revised list of IP addresses

In the concluding phase of my algorithm, it was crucial to update the allow list file with the modified IP address list. To achieve this, the list had to be converted back into a string representation. To accomplish this conversion, I employed the ```.join()``` method as follows:

![Update the file with the revised list of IP addresses](https://i.imgur.com/QUDMPia.png)

The ```.join()``` method serves the purpose of merging all elements within an iterable into a single string. To use this method effectively, it is applied to a string that specifies the characters which will separate the iterable elements once they are combined into a string.

In the context of this algorithm, I employed the ```.join()``` method to transform the ip_addresses list into a string, which was then passed as an argument to the ```.write()``` method when updating the ```"allow_list.txt"``` file. To ensure each element appeared on a new line in the resulting text, I chose the string ```("\n")``` as the separator, instructing Python to maintain this formatting.

The next set of code that I implemented, I employed a with statement and the .write() method to update the file:

![Image](https://i.imgur.com/21pctgG.png)

Here, I utilized an additional argument, ```"w"```, when using the ```open()``` function within my ```with``` statement. This particular argument signifies my intention to open a file for the purpose of overwriting its existing content. By employing ```"w"```, I gained the ability to employ the ```.write()``` function within the ```with``` statement's block. The ```.write()``` function is instrumental in writing string data to a specified file and replacing any pre-existing content.

In this scenario, my objective was to write the updated allow list as a string to the file named ```"allow_list.txt."``` This approach ensures that the previously restricted content becomes inaccessible to any IP addresses that have been removed from the allow list. To achieve this, I added the ```.write()``` function to the file object, which I had defined within the with statement. As an argument, I passed the ```ip_addresses``` variable, thereby specifying that the contents of the file indicated in the with statement should be replaced with the data contained in this variable.

## Summary

I designed an algorithm to update the ```"allow_list.txt"``` file by removing any IP addresses present in a ```remove_list``` variable, which contains a list of unauthorized addresses. The algorithm consisted of several steps:

1. First, I opened the ```"allow_list.txt"``` file for manipulation.
2. Next, I converted the file's content into a string for further processing, and subsequently transformed this string into a list, storing it in a variable called ```ip_addresses```.
3. I proceeded to iterate through the IP addresses listed in the ```remove_list```. During each iteration, I examined whether the element was present in the ```ip_addresses``` list.
4. If the element was found in ```ip_addresses```, I employed the ```.remove()``` method to eliminate it from the list.
5. Finally, to update the ```"allow_list.txt"``` file, I utilized the ```.join()``` method to convert the ```ip_addresses``` list back into a string. This enabled me to overwrite the contents of the file with the revised list of IP addresses, ensuring that unauthorized addresses were no longer included in the allow list.
