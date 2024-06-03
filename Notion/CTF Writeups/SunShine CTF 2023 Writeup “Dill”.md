# The Challenge

- We begin with the challenge description and the downloadable file shown below.

![[Untitled 13.png|Untitled 13.png]]

Challenge Description

- The first thing that I do when looking at a file with no extension or an extension that I don’t know, I use the `file` command on it.

![[Untitled 1 5.png|Untitled 1 5.png]]

# Recon

- When doing this challenge I had already known about .pyc files and how to de-compile them. But you guys may not, so what you should do first is begin researching what a `.pyc` file is.

> [!important]  
> Using google or chatgpt: you should learn that .pyc is what is created when you run a .py file to make execution of the code faster.  
  
> [!important]  
> The next question should be, can I de-compile this file, since we are in the reverse engineering category. Google or chatgpt will tell you about a few programs that are created to de-compile .pyc files.  
  
> [!important]  
> Ive done the research on the best tools: pydumpck, pycdc/decompyle++, decompyle3, uncompyle6, pydeinstaller(windows), unpyc3, uncompile2, and an online toolhttps://www.lddgo.net/en/string/pyc-compile-decompile).  

# Code Review

- after decompiling using the online tool which using both pycdc or uncompyle6 we get this:

> [!important]  
> Note: pycdc and uncompyle6 get slightly different results, but both codes run the same.  

```Python
# Visit https://www.lddgo.net/en/string/pyc-compile-decompile for more information
# Python 3.8.0 (3413)



class Dill:
    prefix = 'sun{'
    suffix = '}'
    o = [5, 1, 3, 4, 7, 2, 6, 0]

    def __init__(self) -> None:
        self.encrypted = 'bGVnbGxpaGVwaWNrdD8Ka2V0ZXRpZGls'

    def validate(self, value: str) -> bool:
        return value.startswith(Dill.prefix) and value.endswith(Dill.suffix) or False
        value = value[len(Dill.prefix):-len(Dill.suffix)]
        if len(value) != 32:
            return False
        c = [value[i:i + 4] for i in range(0, len(value), 4)]
        value = ''.join([c[i] for i in Dill.o])
        if value != self.encrypted:
            return False
        return True
```

- Here is the pseudo code for the above code:

```Python
"""
define varibles

show encrypted flag (bGVnbGxpaGVwaWNrdD8Ka2V0ZXRpZGls)

validate ctfflag via this function:
	check for ctf prefix and suffix
	get rid of prefix and suffix
	check length for 32 char base64 string
	c array is set to chucks of 4 of the 32 char string
	in the order specificed by the varible 'o', rerange the chunks from array 'c'
	if the new order is = to the encrypted flag then that is the ctf flag.
"""
```

# Solution

> [!important]  
> Since we know the order that the flag was scrambled in we should be able to easily de-scramble in reverse. Lets split the current encrypted text into the 4 chunks and list there array order which is specified by the variable o .  

==bGVn== ==bGxp== ==aGVw== ==aWNr== ==dD8K== ==a2V0== ==ZXRp== ==ZGls==  
5 1 3 4 7 2 6 0  

> [!important]  
> We want to change this to be in the order of 0,1,2,3,4,5,6,7. So lets do that!  

0 1 2 3 4 5 5 7  
  
==ZGls== ==bGxp== ==a2V0== ==aGVw== ==aWNr== ==bGVn== ==ZXRp== ==dD8K==

> [!important]  
> Remember, based on the code, this is the flag. We can confirm this by running the flag through cyber chefs magic:  

![[Untitled 2 6.png|Untitled 2 6.png]]

- So the since the flag format is sun{}. The flag should be `sun{``==ZGlsbGxpa2V0aGVwaWNrbGVnZXRpdD8K}==`
- If you were to run this flag through the checker it would come out as true.