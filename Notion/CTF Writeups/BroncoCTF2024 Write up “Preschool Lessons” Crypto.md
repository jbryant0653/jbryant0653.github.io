#writeups/BroncoCTF #writeups/easy #writeups/2024 #writeups/crypto 
# Investigation/Code Review

--- start-multi-column: ID_6l93

```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- This challenge is a Crypto challenge, and all that is given is a bunch of a’s, b’s, and c’s.

--- column-break ---

![[Untitled 9.png|Untitled 9.png]]

--- end-multi-column

---

--- start-multi-column: ID_jco0
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- At first, I thought this was a cipher, so I ran it through my favorite cipher identifiers and tried to decrypt the ciphertext. Here is a list of some of the most used identifiers:

--- column-break ---

[https://www.dcode.fr/cipher-identifier](https://www.dcode.fr/cipher-identifier)
[https://www.boxentriq.com/code-breaking/cipher-identifier](https://www.boxentriq.com/code-breaking/cipher-identifier)
[https://www.cryptool.org/en/cto/ncid](https://www.cryptool.org/en/cto/ncid)
[https://www.cachesleuth.com/multidecoder/](https://www.cachesleuth.com/multidecoder/)
[https://ciphertools.co.uk/#/crack](https://ciphertools.co.uk/#/crack)

--- end-multi-column

---

--- start-multi-column: ID_z917
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- Using dcode you get these results

--- column-break ---

![[Untitled 1 3.png|Untitled 1 3.png]]

--- end-multi-column

--- start-multi-column: ID_woc7
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- Dcode is convinced it is 99% bacon Cipher, Let’s see.

--- column-break ---

![[Untitled 2 4.png|Untitled 2 4.png]]

--- end-multi-column
- It comes out to nothing. After further investigation into the bacon cipher, this couldn't be the bacon cipher because it requires chucks of 5 a’s or b’s, which correlate to the alphabet.

> [!lightbulb]  
> The text we were given has <font color="#ff0000">8 a’s or b’s</font>………..and the character <font color="#ff0000">c in between each 8 ab’s</font>.  

- What has 8 of something, and that something can only be 2 values???????
- <font color="#ff0000">BINARY!!!!!</font>
---

--- start-multi-column: ID_wy6p
```column-settings
Number of Columns: 2
Largest Column: Right
Border: off
```

- Now I decided to open [CyberChef](https://gchq.github.io/CyberChef/) and use the <font color="#ff0000">From Binary</font> and <font color="#ff0000">Find / Replace</font> Tool to get the flag:

Link for CyberChef Recipe: [Recipe](https://gchq.github.io/CyberChef/#recipe=Find_/_Replace(%7B'option':'Regex','string':'a'%7D,'0',true,false,true,false)Find_/_Replace(%7B'option':'Regex','string':'b'%7D,'1',true,false,true,false)Find_/_Replace(%7B'option':'Regex','string':'c'%7D,'%20',true,false,true,false)From_Binary('Space',8)&input=YWJiYWFhYmFjYWJiYmFhYmFjYWJiYWJiYmJjYWJiYWJiYmFjYWJiYWFhYmJjYWJiYWJiYmJjYWJiYmJhYmJjYWJiYWJhYWJjYWJhYmJiYmJjYWJiYWJiYWJjYWFiYmFhYWJjYWJiYmFhYmJjYWJiYmFhYmJjYWJhYmJiYmJjYWJiYmFhYWFjYWJiYmFhYmFjYWFiYmFhYmJjYWJiYmFhYmJjYWJiYWFhYmJjYWJiYWJhYWFjYWJiYWJiYmJjYWFiYmFhYWFjYWJiYWJiYWFjYWJiYmJiYWI)

--- column-break ---

![[Untitled 3 2.png|Untitled 3 2.png]]

--- end-multi-column

![[Untitled 4 2.png|Untitled 4 2.png]]

> [!success]  Flag
> bronco{i_m1ss_pr3scho0l}