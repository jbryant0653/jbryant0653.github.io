#writeups/BroncoCTF #writeups/2024 #writeups/medium #writeups/Stego
# The Challenge

--- start-multi-column: ID_hvcz

```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

* This is a Stego/Forensics Challenge in which you get given a <font color="#ff0000">png </font>and a hint that only makes sense in hindsight.
> Hint: Look inward, and you might find it at the intersection of Mario's color and the number of brothers.

> [!success]- Answer to Hint:
>Mario Color: <font color="#ff0000">Red</font>
>Number of Brothers: <font color="#ff0000">2</font>

--- column-break ---

![[Untitled 15.png|Untitled 15.png]]

--- end-multi-column

---

--- start-multi-column: ID_hqm5
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- Here is the png:

--- column-break ---

![[Untitled 1 7.png|400]]

--- end-multi-column

---

# Investigation

- I know how to solve this challenge because I read a shitty writeup, and now I understand it and will explain it in a better way to you guys.
- Start by always checking an image in online or local steganography tools.
    - There are too many tools to list all of them so it is up to you to learn them!
    - [AperiSolve](https://www.aperisolve.com/) & [StegOnline](https://georgeom.net/StegOnline/upload) are my go-to right now!
- Begin by looking through AperiSolve and going through both sites’ checklists.
    
    > [!quote]
    > Aperi'Solve is an online platform which performs layer analysis on image. The platform also uses zsteg, steghide, outguess, exiftool, binwalk, foremost and strings for deeper steganography analysis. The platform supports the following images format: .png, .jpg, .gif, .bmp, .jpeg, .jfif, .jpe, .tiff…

--- start-multi-column: ID_qxqb
```column-settings
Number of Columns: 2
Largest Column: Standard
Border: off
Alignement: Center
```

![[Untitled 2 8.png]]
![[Untitled 3 5.png|Untitled 3 5.png]]

--- column-break ---

![[Untitled 4 5.png|Untitled 4 5.png]]
![[Untitled 5 4.png|Untitled 5 4.png]]

--- end-multi-column

--- start-multi-column: ID_8f97
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- When I was looking at these photos when I went to solve the challenge, I was quickly drawn toward <font color="#ff0000">SuperImposed(1,3)</font> photo and the <font color="#ff0000">Red(1,3)</font> photo because of the obfuscated noisy pixels at the top of the screens.

> [!attention]  
> This is not normal and should be investigated further. If you know your stuff, you will now that each of these photos are outputs of what is called a bit plane.  

--- column-break ---

![[Untitled 6 4.png|Untitled 6 4.png]]

--- end-multi-column

---

# Aside on Bit planes!

- Every pixel in an image has RGB values.
    - It looks like a set like this (R, G, B), with each value in the set being a <font color="#ff0000">byte</font> or <font color="#ff0000">8 bits</font> long.
        > [!example]
        > (10100000, 00100000, 11110000): This is the color purple!


--- start-multi-column: ID_z57r
```column-settings
Number of Columns: 2
Largest Column: right
Border: off
```

- An image is just an n by m square of RGB values, representing many pixels.
    - Each image has <font color="#ff0000">3 different top-level planes</font>, with those being for <font color="#ff0000">RGB</font>.

--- column-break ---

![[Untitled.jpeg]]

--- end-multi-column

- We will deconstruct an image given the information above to understand what a bitplane is.
    - Each <font color="#ff0000">Top-level plane</font> is just a bunch of pixels with <font color="#ff0000">8-bit </font>numbers <font color="#ff0000">per pixel</font>.
        - Take one of the planes now and only take a <font color="#ff0000">single bit</font> from each pixel.
            - Each pixel will now only be a <font color="#ff0000">0 or 1</font> or black or white.
            - Now the image is just a black and white image.
            - This is a <font color="#ff0000">**bit plane!**</font> If you are in the <font color="#ff0000">Red top level plane</font> and looking at the <font color="#ff0000">LSB</font>(least significant bit)[0000000<font color="#ff0000">**1**</font>], that is bit plane <font color="#ff0000">R0</font>.
            - Each top-level plane has <font color="#ff0000">8-bit planes</font>
                - So, each RGB image has <font color="#ff0000">24-bit planes</font>.

> [!example] Bit Planes  
> ![[Untitled 1.jpeg]]
- This idea of showing images in bit planes is the basis for hiding encoded data in an image.
    - Binary has <font color="#ff0000">MSB</font>(most significant bits)[<font color="#ff0000">**1**</font>0000000] and LSB. The MSB is most significant because it represents the largest number, so <font color="#ff0000">$2^7$</font> for MSB.
    - If you encode data in the MSB, you will likely cause <font color="#ff0000">noise</font> in the original image, and your stenography will be garbage.
    - The opposite of this is LSB, where it is only <font color="#ff0000">$2^0$</font>, which is a 1-bit change, so if you encode data into the LSB plane of, let's say, R0, then the original image will not be edited almost at all. This is much harder to see visually.
        - Even better you can spread your encoded data across The LSB plane for each top-level domain.

---

# Back to solving

- As we can see now, There is messed up data in the R2 bit plane. This makes sense now that we know what we are looking at.
- Let’s take a look at the other website, <font color="#ff0000">StegOnline</font>, which can look at each bit plane individually and will extract files from certain bit planes if you know which plane to extract from.


--- start-multi-column: ID_pks0
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- To confirm, Browsing Bitplane R2 shows us this:

--- column-break ---

![[Untitled 7 4.png|Untitled 7 4.png]]

--- end-multi-column

--- start-multi-column: ID_z7db
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- Let’s try to use their extract tool to extract data from bit plane R2.

--- column-break ---

![[Untitled 8 3.png|Untitled 8 3.png]]

--- end-multi-column


--- start-multi-column: ID_3tf8
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- <font color="#ff0000">It found a hidden JPG!</font>

--- column-break ---

![[Untitled 9 3.png|Untitled 9 3.png]]

--- end-multi-column

---

--- start-multi-column: ID_6rrq
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- Downloading the jpeg gives an image of Marios and Warios. With 8 of them every single time. This is binary!
- Putting the values painfully into [CyberChef](https://gchq.github.io/CyberChef/) painfully gives you the flag!
- Deep link to Recipe: [Recipe](https://gchq.github.io/CyberChef/#recipe=From_Binary('Space',8)&input=MDExMDAwMTAgMDExMTAwMTAgMDExMDExMTEgMDExMDExMTAgMDExMDAwMTEgMDExMDExMTEgMDExMTEwMTEgMDExMDAwMTAgMDAxMTAwMDAgMDExMTAxMTEgMDExMTAwMTEgMDAxMTAwMTEgMDExMTAwMTAgMDEwMTExMTEgMDExMDAxMTEgMDAxMTAwMDAgMDExMTAxMDAgMDEwMTExMTEgMDExMTAxMDAgMDExMDEwMDAgMDAxMTAxMDAgMDExMTAxMDAgMDEwMTExMTEgMDExMDAxMDAgMDExMTAxMDEgMDExMDExMDEgMDExMTAwMDAgMDExMTEwMDEgMDExMTExMDEgMDAwMDEwMTAK)

> [!success]  Flag
> bronco{b0ws3r_g0t_th4t_dumpy}  

--- column-break ---

![[Untitled 2.jpeg]]

--- end-multi-column
