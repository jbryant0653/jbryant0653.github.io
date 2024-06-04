#writeups/reversing #writeups/BitsCTF #writeups/easy #writeups/2024 
- This challenge is a Reversing Challenge and only gave a single file.

--- start-multi-column: ID_kid0
```column-settings
Number of Columns: 1
Largest Column: Large
Border: off
```

![Untitled 14](attachments/Untitled%2014.png)

--- end-multi-column

- As I have said before, If I get a file and I don’t know what it is, I always run the <font color="#ff0000">file</font> command on it.

--- start-multi-column: ID_aut9
```column-settings
Number of Columns: 1
Largest Column: Full
Border: on
```

![Untitled 1 6.png](attachments/Untitled%201%206.png)

--- end-multi-column

- As excepted from reversing challenges, it is a binary aka an executable.
- Always try and run it first to see what your goal is:
    - In Linux in order to make a binary runnable, you must use <font color="#ff0000">chmod +x binaryname</font>.

--- start-multi-column: ID_ssez
```column-settings
Number of Columns: 1
Largest Column: Large
```

![Untitled 2 7.png](attachments/Untitled%202%207.png)

--- end-multi-column

- Im now thinking, okay I must input some string which will give me the flag, or the string that is inputted is the flag.
- Regardless, We should try <font color="#ff0000">strings</font> on the binary to see what language this was compiled in or to find the flag possibly. Remember that if there is too many strings use <font color="#ff0000">strings -n 10</font> to limit the output to strings equal to or greater than 10.

--- start-multi-column: ID_xcot
```column-settings
Number of Columns: 2
Largest Column: Right
Border: off
```
- Along side other programing aids, there is a section that says baby-rev.c which shows this is a c program. C programs are reversible using dozens of programs. I like to use this site to quickly size up how hard the challenge is and to see the code de-compiled in different ways.
- The website is [https://dogbolt.org/](https://dogbolt.org/):

--- column-break ---

> [!info] Terminal
> ![Untitled 3 4.png](attachments/Untitled%203%204.png)

--- end-multi-column

---

- The site has many decompilers built in with the most normal to read being the <font color="#ff0000">angr</font> decompiler. Here is a list of the compilers:
![cropthis](attachments/cropthis.png)
- The way that I solved this was I just skimmed through the code to find where the <font color="#ff0000">:P</font> was entered into the console by the program and when I found it I found this section of the code:

--- start-multi-column: ID_uo6b
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
Alignment: Center
```

![250](attachments/Untitled%205%203.png)

--- column-break ---

![250](attachments/Untitled%206%203.png)

--- end-multi-column

- So I saw that my <font color="#ff0000">:P</font> string is at the top and so I never made it through all the else if statements to make it to the <font color="#ff0000">Yippee :3</font> statement which likely means I entered the correct flag into the program.
- Then I realized that each number that is happening in the comparisons are definitely ASCII value.
- Originally I Grab each value in order and put it in CyberChef but realized after I had already converted all the values that they are out of order.
- This is obvious when you look at the comparisons being made. The second comparisons of the array <font color="#ff0000">a0</font> is <font color="#ff0000">a0[4] != 76</font> . This shows that the values that they are being compared to are out of order.
    - Just read the ASCII decimal values in order from <font color="#ff0000">a0[0] </font>to <font color="#ff0000">a0[22]</font>. Put it in [CyberChef](https://gchq.github.io/CyberChef/) using <font color="#ff0000">from decimal</font>.

![Untitled 7 3.png](attachments/Untitled%207%203.png)

> [!success]  Flag
> BITSCTF{w3lc0me_t0_r3v}CyberChef