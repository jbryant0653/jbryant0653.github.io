[https://broncoctf.xyz/challenges](https://broncoctf.xyz/challenges)

> [!info] Discord - A New Way to Chat with Friends & Communities  
> Discord is the easiest way to communicate over voice, video, and text.  
> [https://discord.com/channels/1160887571698700358/1160887572130701373](https://discord.com/channels/1160887571698700358/1160887572130701373)  

### Forensics

- Medieval Beats:
    
    Learn FFmpeg: The solution was to extract video from YouTube, create an image for each frame per second, find all the black frames, and delete them to see the full flag.
    
    Solution Commands:
    
    ```Bash
    ffmpeg -i flag.mp4 -vf "fps=1" output_%04d.png
    find . -type f -size 284c -exec rm {} +
    ```
    
    [https://ffmpeg.org/about.html](https://ffmpeg.org/about.html)
    
    [https://gist.github.com/KeigoAlexTanaka/eb3953742f00fa6a10709f5bdbc9b845](https://gist.github.com/KeigoAlexTanaka/eb3953742f00fa6a10709f5bdbc9b845)
    
- Wario Party:
    
    Image had encoded data in bits: how to detech, use aperisovle and look for weird scrambled data. Use stegsolve.jar to find file. What other tools will do that. Thne it was just binary. What are bitplanes and explore more steg information.
    
      
    
- Boom:
- Mystery Sound:
- LAN Party:

Image had encoded data in bits: how to detech, use aperisovle and look for weird scrambled data. Use stegsolve.jar to find file. What other tools will do that. Thne it was just binary. What are bitplanes and explore more steg information.

  

### OSINT

- Side Quest
- Lost Valentine

### Misc

- Voldy Kills the Vibe

### Crypto

- Oh, Danny
- Birthday Bash

### Reversing

- MZ
- Serpent’s Pass

### Web

- ACM Borg Members
- All I Do Is
- Blue Herring