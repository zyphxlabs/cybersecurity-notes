## CyberChef Basics
Cyberchef is basically a web based tool that helps with all sorts of cyber related tasks right inside your browser, think of it like a swiss army knife for data, a toolbox full of different tools each doing their own specific job. It can do simple stuff like base64 or xor encoding all the way up to complex stuff like aes encryption or rsa decryption. The whole tool works around the idea of recipes which is basically a series of operations run one after another on your data

You can access it two ways, either just open it online through a browser with internet, or download the latest release and run it locally offline on windows or linux, downloading the most stable version is usually the safer bet

## Interface Areas
Cyberchef has four main areas that make up the interface

Operations area is basically a big repository of every operation the tool can do, all categorized so you can find stuff easily, theres also a search bar to quickly find a specific operation. Hovering over any operation shows a quick description or example along with a wiki link

Recipe area is where the actual magic happens, you drag operations here arrange them in order and set their arguments to customize how they behave. It has options to save a recipe load a previously saved one or clear it entirely. At the bottom theres a bake button that processes the data through your recipe, or you can tick auto bake so it processes automatically without you clicking every time

Input area is where you paste type or drag in your data. It also lets you open a new input tab to work with different values side by side, open an entire folder as input, open a single file as input, or clear everything and reset the layout back to default

Output area shows you the result of whatever operations you ran on the input. You can save the output to a file, copy the raw output straight to clipboard, replace the input with the output to keep chaining operations, or maximise the output pane for a better view

## Common Operation Categories
Extractors category pulls specific patterns out of a block of data

- Extract IP addresses — pulls any valid ipv4 or ipv6 address from the input
- Extract URLs — pulls urls out but the protocol like http or ftp needs to be present otherwise it gets way too many false positives
- Extract email addresses — pulls out anything matching the format of something@domain.com

Date and time category deals with converting timestamps. A unix timestamp is basically a 32 bit number representing seconds since january 1st 1970 utc which is called the unix epoch. To unix timestamp converts a readable date into that number, and from unix timestamp does the reverse and turns it back into something readable

## Data Format and Base Encoding
Data format operations handle converting between different encoding formats

- From Base64 — decodes a base64 string back into its raw readable form
- URL Decode — converts percent encoded characters in a url back to their raw values, since utf-8 is the default charset in html5 you'll commonly see things like colon becoming %3A slash becoming %2F dot becoming %2E equals becoming %3D and hash becoming %23
- From Base85 — similar idea to base64 but usually more efficient, decodes a string back to raw data
- From Base58 — like base64 but removes characters that are easy to misread like l uppercase I 0 and O, makes it more human readable
- To Base62 — encodes data using a restricted set of symbols, higher base means shorter strings compared to decimal or hex

All these base encodings work on the same basic idea, they take binary data and turn it into a text representation using a specific set of ascii characters

Lets manually walk through converting the letters THM into base64 to actually understand whats happening under the hood. First you convert each letter to its 8 bit binary using the ascii table, T is 01010100, H is 01001000, M is 01001101. Concatenate all three together and you get a 24 character binary string 010101000100100001001101

Next you split that string into groups of 6 bits each since base64 works on 6 bit chunks, giving you four groups 010101 000100 100001 001101. Convert each of those to decimal and you get 21 4 33 13

Last step is matching each of those decimal numbers to its corresponding character in the base64 index table, 21 maps to V, 4 maps to E, 33 maps to h, 13 maps to N. Put those together and you get VEhN which is THM encoded in base64

## Thought Process for Using CyberChef
There's basically a four step approach when working with cyberchef. First set a clear objective, ask yourself what you actually want to accomplish, like finding out if a gibberish string found during an investigation is hiding a message. Second put that data into the input area. Third pick the right operations based on what you suspect the data might be, if it looks like it could be encoded try stuff under the encryption or encoding category like rot13 base64 base85 or rot47. Fourth check the output and see if it actually matches what you were trying to achieve, if not you go back and try a different combination of operations until it clicks