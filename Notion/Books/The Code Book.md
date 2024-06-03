by Simon Singh

## Frequency Analysis

Simple Check list:

- Symbols or Alphabet?
- Spaces or no spaces?
- Letter frequencies!
- Di-grams, Tri-grams, and Quad-grams!
- Most common One, Two, Three, and Four letter words!
- Most common letters to Start and End words!
- Most common doubles!
- Frequency of letter pairs; Not the same as Di-grams!
- Note sometimes the key can be guessed if it uses a phrase!!!

> [!important]- [Language Detection](https://www.diva-portal.org/smash/get/diva2:1569329/FULLTEXT01.pdf)
>>[!faq] How to know if the cipher-text was written in another language?
> - Check the frequency of the cipher text to see what freq table of which language it lines up with best
>- Use the frequencies that are the most outliers such as e in English and the last 5 such as z which is below 1% chance!  

> [!NOTE] 
> Note: Try and adjust your frequency tables to context about your cipher-text, such as a poem based freq table or a military letter freq table which might skew data.

Links:

- [Best frequencys](https://www3.nd.edu/~busiforc/handouts/cryptography/cryptography%20hints.html)
- [Lots of Digrams and More](https://www3.nd.edu/~busiforc/handouts/cryptography/cryptography%20hints.html)
- [Letter Pairs](https://homepages.math.uic.edu/~leon/mcs425-s08/handouts/char_freq2.pdf)

> [!todo]-  Get this book!
> Get Cryptanalysis by Gaines, Helen Fouche for more freq tables!  

### Ways to make mono-alphabetic substitution better

- Add Null characters: alphabet to number 0-99 so the 73 other numbers are randomly added to cipher text. This messes up freq analysis.
- Misspell words on purpose to throw off freq analysis.
- Use code words in plain text then encrypt them. So “sing” might mean “run”.


> [!NOTE]
>Note: Deciphering a mono-alphabetic substitution cipher can be really difficult if good techniques are used such as: nulls, miss spellings, and code words are used.

### Poly-Alphabetic vs. Mono-Alphabetic

- Mono: One or more ciphertext characters correlate to Only one Plaintext character
- Poly: One ciphertext character correlates to Many Plaintext character
    - Ex: Vigenere cipher

### Homophonic Substitution cipher

Means Same sound, aka many cipher to the same plaintext character.

- It is a Mono-Alphabetic substitution cipher which uses multiple cipher texts for one plaintext
- Tries to make more options for a char if it has a higher frequency to make all the ciphertext characters be under 1% frequency.
- Can still be broke by realizing what characters appear next to other characters such as q and how u always follows q so 3 characters should always follow the char for q IF…..They set up the frequency to be below zero.