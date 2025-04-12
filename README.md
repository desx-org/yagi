# YAGI 

An a next generation data exchage format

Yagi is a next generation data excange format that 
Basic functionality looks earily familiar to :

'''json
{
  "name": "smith",
  "age" : 50,
  "occupation" : "virologist"
}
'''

# Novel YAGI components:
 1. Binary Format: Don't use text files to talk to computers
 2. Multi dimensional: Life has many dimentions, so should your data
 3. World References: Store and retrieve with impunity 
 4. Types: Strong and  
 5. Functions


## Binary Format

Formats such as json and yaml use text as a data storage format, with the justifiaction that it allows existing tooling (text editors) to edit and debug the data. This comes at the cost of pretty much every other desirable attribute you would want in a data storage format. Any json or yaml parser has to parse throug evry symbol in a json file to look for start and end delimiters and exclude check escape sequences. Any basic binary format would not just be faster to process, but far less comples to implement in code. Also the data efficincty for storing data in text form is abysmal. "1000" takes up four bytes of data where it should only take up two using the basic numeric encoding emplemented in yagi.

The key downside of binary format is that you can not use your basic text editior to edit. If you are on a system that does not have a yagi editor you are out of luck to view or modify yagi files. The solution to this is to make the yagi editor absurdly easy to aquire:

 1. Install it with our package manager
 2. The yagi editor only depends on libc: Find a precompiled binary and just copy it to your system
 3. If there is no precompiled binary (there probably is) then copy the source and run "make install" (you need gnu make and g++ installed)
 4. the yagi editor is so simple that we are makeing a busybox version to include in lighweight linux systems

## Multi dimemensional 

Arrays are the core data type of yagi, and the dimentionality of arrays are just an atribute of that array. Zero dimentional array has one value, one dimentional two dimentional is like a table. Its hard to justify this design choice becuse considering arrays of having dimentionality as an attribuyte simpifies the system.

## World References



## Software Components

 1. Yagi lib: core c++ library for creating/manipualting yagi
 1. language bindings: use yagi lib in youre favoritatle language 
 1. Yagi cli editor
 1. 


 # The future we want  
  1. Yagi cli editor is available in all the major package manageres
  1. Yagi is installed by default in most linux distros
  1. Yage files are the easiest tool used to confiure software 
  1. Deploy a busybox implentation of yagi
  1. Yagi lib is easily used on microprocessors 