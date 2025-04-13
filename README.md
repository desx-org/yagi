# YAGI 
Note: all this is a planning doc, notheing has been implemented 

An a next generation binary data exchage format

Yagi is a data excange format that 
Basic functionality looks earily familiar to :

```json
{
  "name": "smith",
  "age" : 50,
  "occupation" : "virologist"
}
```
# implementation 

The yagi editor is a single c file about 5 thousand lines long that will comipile on pretty much any system with the folowing command:

`gcc yagi.c -o yagi`

`


# Novel YAGI components:
 1. Binary Format: Don't use text files to talk to computers
 2. Multi dimensional: Life has many dimentions, so should your data
 3. World References: Store and retrieve with impunity 
 4. Types: Strong and  
 5. Functions

# Example 
Each value has four componets
`<name>:<type>=<value>;<expression>`

```
{
  name         : 
    first : txt = Billy ; 
    last  : txt = Swag  ;
  dob          : date  = 05/01/1995
  now          : date  = 03/02/2025
  age          : years = 29         ; minus(.now,.dob).year
  occupation   : txt   = virologist
  speed_ave    : mi/hr = 9.92       ; ave(.races.time) 
  speed_m/s    : m/s   =            ; to_m/s(.speed_ave)
  races 0xde01 : =
    0xfedf:date, time:mi/hr, place:int
       10/01/23, 10.01     ,         4
       12/01/23,  9.98     ,         5 
       01/01/24, 10.09     ,         8
       03/01/24,  9.90     ,        11
       04/01/24,  9.91     ,         3
}
```

## Binary Format

Formats such as json and yaml use text as a data storage format, with the justifiaction that it allows existing tooling (text editors) to edit and debug the data. This comes at the cost of pretty much every other desirable attribute you would want in a data storage format. Any json or yaml parser has to parse throug evry symbol in a json file to look for start and end delimiters and exclude check escape sequences. Any basic binary format would not just be faster to process, but far less comples to implement in code. Also the data efficincty for storing data in text form is abysmal. "1000" takes up four bytes of data where it should only take up two using the basic numeric encoding emplemented in yagi.

The key downside of binary format is that you can not use your basic text editior to edit. If you are on a system that does not have a yagi editor you are out of luck to view or modify yagi files. The solution to this is to make the yagi editor absurdly easy to aquire:

 1. Install it with our package manager
 2. The yagi editor only depends on libc: Find a precompiled binary and just copy it to your system
 3. If there is no precompiled binary (there probably is) then copy the source and run "make install" (you need gnu make and g++ installed)
 4. the yagi editor is so simple that we are makeing a busybox version to include in lighweight linux systems

## Multi dimemensional 

Arrays are the core data type of yagi, and the dimentionality of arrays are just an atribute of that array. Zero dimentional array has one value, one dimentional two dimentional is like a table. Its hard to justify this design choice becuse considering arrays of having dimentionality as an attribuyte simpifies the system.
## Types

The lack of an easy way to store and send a typed data field susch as "meters per seconds" is extremely anoying. Yagi solves this by having a strong typing system. Not only are a wide set of builtin types available, but they are easily extendable by defining your own types. 

Key elements of types are:
 - Serialization/de-serialization functions
 - Are hyarichcal and composable. m/s refrences the meter(m) and the seconds(s) type, as well as the divide function(/) and is a "number" type

## Functions 

Functions are a 

## World References

Yagi files include not just data, but functions and type definitions. The goal is to make these

## Software Components

 1. Yagi lib: core c library for creating/manipualting yagi
 1. language bindings: use yagi lib in youre favoritatle language 
 1. Yagi cli editor
 1. Yagi network resolver

 # The future we want  
  1. Yagi cli editor available in all the major package manageres
  1. Yagi is installed by default in most linux distros
  1. Yage files are the easiest tool used to confiure software 
  1. Deploy a busybox implentation of yagi
  1. Yagi lib is easily used on microprocessors 

## Builtin types
 1. second:time
 1.	metre:	length
 1. kg:kilogram	mass
 1. A:ampere	electric current
 1. K: kelvin	thermodynamic temperature
 1. mol:mole	amount of substance
 1. cd: candela
 1. Basic Netwrok types: ipv4/ipv6 address, port
 1. Text types
 1. Text
 1. Version
 1. Local reference
 1. Hash Reference
 1. YRI referece 
 1. Function
 1. Type
 1. Number
 1. Boolean
 1. Null
 1. Bytes 
 1. Bits
 1. Enum
 1. int