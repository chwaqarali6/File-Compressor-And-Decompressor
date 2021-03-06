# File-Compressor-And-Decompressor

Project: Compressing Text Files, with fixed bit-length encoding

This project will be completed in parts.

Part 1

Given a text file, T, go through the text in T and count the number of unique characters. Then store these characters in a character array, C. Each character in C is a unique symbol from the file, and is to be assigned a "code", that is, a combination of 1 and 0 characters which shall be later packed as bits into bytes and dumped into a compressed file. Following is a list of things to do:

  1. Go through the file T, and create the table (array) of unique characters, called C. Note: C could be an array of size 256, however, you will only be using as many spaces as there are unique characters in T.

  2. Compute the length, n, of bit combinations (i.e. the minimum number of bits needed to store a symbol), by using the formula n=ceiling(log_2(k)), where k is the number of unique symbols. For example, if k=5, n=3. In this case, the character at index 0 of table C will get the code "000", the character at index 1 will get the code "001", and so on.

  3. Go through the file T again and print on the screen the pattern of bits that corresponds to the data in T. For example, if the text in T is FAABBBBHHHXXBX, then F, A, B, H, and X are the 5 unique characters stored in table C. They can be stored in any order, but let's say the order is the same as their order of appearance in the file. Then the output your program should show on the screen is: 000001001010010010010011011011100100010100. Note: this output is not actual bits but 1 and 0 characters printed on the screen. Later these will be packed into bytes, as actual bits.

Part 2

In this part, you will convert the stream of 0/1 characters, printed out in part 1, into a packed (compressed) stream of bits, and dump that into a compressed file. This file will be written usring binary filing in C++. Following is a list of things to do:

If there were n characters in the 0/1 output printed in part 1, now you create a dynamic array called "stream" and put all the 0/1 data (printed in Part 1) inside stream. The size of stream should be exactly n (the number of 0/1 characters).
Create another dynamic array called cstream (compressed stream), and using the packBits, and extendBy1 functions from class, pack the 0/1 data in this array at bit level. Note: the size of cstream will be equal to ceiling(n/8). Delete stream from memory.
Learn how to do binary filing in C++, here.
Create a binary file called "file_name.cmp" where file_name is the name of the original text file, and dump the data in cstream into this file, byte by byte.
Create another text file (not a binary file) called "info.cmp". In this file store the length of each binary code in Part 1, as well as the table C from Part 1. This file will be used during de-compression. Make this a hidden file.
Download the free hex editor. Open your file "file_name.cmp" in this editor and check that all the bits are written correctly in this file. Note: you will not be able to read this file in Notepad which is designed to treat the content as ASCII characters; you will see some garbage in notepad. Use the hex editor to comfirm that the data is correctly written.
The name of your program should be compress. In order to run your program, I should be able to type "compress" on the console followed by the name of the text file to be compressed. i.e >compress abc.txt, after this the program should produce the compressed file and the hidden info file in the same folder as the text file. Learn how to deal with command line arguments in C++ here.

Part 3

This is the third and final part. You will submit the complete compression and decompression code for the project. The decompression process is explained in the following list of points. Note: compress and decompress will be two different programs (exes), which we can run on text and binary files respectively from the command line.

Using the info file (a text file), read the information about the code-length, size of original text file, and the compression table C. From this information, you can compute the number of bytes to be read from the compressed file.
Using binary filing (the read function) and the size computed above, read all the compressed data into a dynamic unsigned char array cstream, which has exactly the same number of bytes as in the compressed file.
Using bit-maniputaion, unpack the bits in cstream and generate the array stream, containing 0/1 characters, just like in part 2.
Since you know the length of codes, you can go through stream 'code by code' and read-off the corresponding text characters (for each code) from the table C. In the same loop, you should write these characters into a text file, which will be your de-compressed file, with exactly the same content as the original text file.
Your programs will be used from the command line. For example, we will compress a file called "abc.txt" like this: >compress "abc.txt", this will produce a file "abc.cmp" in the same folder, as well as a hidden info file. We will then type on the command line: >decompress "abc.cmp", and this will reproduce the original "abc.txt" file in the same folder.
The compression program should also print the compression ratio on the console. This is a % value that will indicate the efficiency of your compression process. The compression ratio, r, is computed using the formula: r = ( 1 - m/n) * 100. Where m is the size in bytes of the compressed file, and n is the size in bytes of the decompressed (original) file. Test your program on various text files and see how this ratio varies. For example, copy all the text on this webpage and paste it in a text file and compress it. What is the compression ratio?
Plagiarism Policy

We will check the codes for plagiarism with each other, and codes from last year's class. Where detected, plagiarism is punishable by awarding zero in all assignments [25% absolute] at least.

Good Luck!
