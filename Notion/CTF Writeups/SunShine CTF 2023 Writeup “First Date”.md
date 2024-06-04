# The Challenge

- We begin with the challenge description and the downloadable file shown below.

![Untitled 10.png](attachments/Untitled%2010.png)

- Since we are given a `.zip` file we will `unzip` the file.

![Untitled 1 4.png](attachments/Untitled%201%204.png)

- As usual, if given files with file extensions that you don’t know, you should use the `file` command.

![Untitled 2 5.png](attachments/Untitled%202%205.png)

- Let's use the cat command to see what's in the text file to see if it is important.

> [!important]  
> Remember, Reversing challenges are meant to figure out what is going on in the background of a program to then solve the challenge.  

![Untitled 3 3.png](attachments/Untitled%203%203.png)

- This doesn't have any significance to us at the moment, so we can focus on figuring out what is the executable `Playdate`.

# Research

- Let's look up what playdate is first: [https://play.date/](https://play.date/)

![Untitled 4 3.png](attachments/Untitled%204%203.png)

- Okay, so it is a Gameboy-like device. Given some thought, the file we are given is probably for a program that runs on this playdate. Let’s figure out how to open it now:

![Untitled 5 2.png](attachments/Untitled%205%202.png)

- After reading through either of these links, you will find something called the `playdate simulator`. You can download the SDK and figure out how to download it after a quick Google search, which runs you through the entire simulator setup, which takes a bit of time.([https://play.date/dev/](https://play.date/dev/))
- Also, after looking through the docs, you will learn that to open the .pdz file, you have to open the .pdx folder, which includes both the pdxinfo file and the .pdz file.
- If you try and open the .pdx folder with playdate, this window of the simulator will pop up:

---

![Untitled 6 2.png](attachments/Untitled%206%202.png)

- Many random letters and numbers will pass the screen quickly with a Press a button! Symbol.
- The program is limited and not very interesting. Remember, the point of reversing is to find out about what is going on in the background. Let's do more research on this playdate simulator by searching `playdate reversing`.

![Untitled 7 2.png](attachments/Untitled%207%202.png)

  

> [!important]  
> Boom, we found where we need to go, and hopefully, we will exploit this! Let's look into the GitHub real quick:  

![Untitled 8 2.png](attachments/Untitled%208%202.png)

- The first thing that catches my eye is the `[pdz.py](http://pdz.py)` file, which will unpack all the files from the container! This is exciting now.

> [!important]  
> Something to note is that this Python script runs using arguments given to the program via the terminal. Without the arguments, you will get an error.  

![Untitled 9 2.png](attachments/Untitled%209%202.png)

- Run `python` `[pdz.py](http://pdz.py)` `main.pdz ./` or `pdz.py main.pdz ./` for windows. This should give you a `main.luac` file shown below.

![Untitled 10 2.png](attachments/Untitled%2010%202.png)

- After looking up what a `.luac` file is, you can find on [fileinfo.com](http://fileinfo.com) that it is a compiled version of a lua file. As reversing goes, you have to decompile it.
- If we return to GitHub, where we got the pdz program, we can also find a luac decompiler.

![Untitled 11](attachments/Untitled%2011.png)

- Either download the `.jar` file or `unluac.sh`. I used the .jar file and ran the command `java -jar unluac.jar -o file.lua main.luac`.
- Finally, this outputs sexy Lua code!!!

---

> [!important]  
> There is a lot of code, but there are only two essential sections that I will show you: The playdate.update() function and the generateOrder() function.  

```Lua
index = ""
lastPressed = "Press a button!"
function playdate.update()
	gfx.clear(gfx.kColorWhite)
	counter = counter + 1
	gfx.drawTextAligned(generateFlag(), 200.0, 120.0, kTextAlignment.center)
	for i = 1, \#buttons do
		if playdate.buttonJustPressed(buttons[i]) then
			pressedButtons = pressedButtons .. i
			lastPressed = buttons[i]
		end
	end
	gfx.drawTextAligned(lastPressed, 200.0, 160.0, kTextAlignment.center)
	gfx.drawTextAligned(makeTextDisplayable(pressedButtons), 200.0, 180.0, kTextAlignment.center)
	gfx.drawTextAligned("Rotate the crank to reset the challenge.", 200.0, 200.0, kTextAlignment.center)
	if pressedButtons == generateOrder() then
		print("Pin entered correctly!")
		gfx.setFont(gfx.font.kVariantBold)
		cleaned = clean(pressedButtons)
		print("Flag: sun{" .. cleaned .. "}")
		gfx.drawTextAligned([[
Flag: 
sun{]] .. cleaned .. "}", 200.0, 80.0, kTextAlignment.center)
	end
end
```

```Lua
function generateOrder()
	local pinSeed = ""
	for i = 1, 20 do
		pinSeed = pinSeed .. i
	end
	return pinSeed
end
```

> [!important]  
> Note the generateFlag() function could be cracked because we are given the seed for math.random(). But there is a more straightforward solution.  

---

- Based on the playdate.update(), we need our pressedButtons to be equal to the output of the generateOrder() function.
- generateOrder() is just the string `1234567891011121314151617181920`. So, if we can edit pressedButtons variable to be equal to generateOrder(), then we can win.

> [!important]  
> We can't just press the buttons via the playdate simulator because there are only 6 buttons, which means only 6 possible numbers, and there are 10 numbers needed in this input.  

- When I was painfully trying to figure out this challenge, I got very good at using the playdate simulator and found all of its features, such as the `lua memory tab, lua memory sampler, malloc log, and the debug console`. My first thought before realizing that you can edit the pressedButtons variable was to use the debug console to call functions because I had tried this previously, and it worked. With Tim's help, we could edit the variable and get the flag like this.
- Run this command `pressedButtons = '1234567891011121314151617181920'`, and this will output into the console:  
      
    `Pin entered correctly! Flag: sun{MIEANBLVFPZJTDOA}`

![Untitled 12](attachments/Untitled%2012.png)

  

BITSCTF2024 Writeup “baby-rev” Reversing