---
title: "CPU"
author: "jaydenn71"
description: "Making my own CPU, first online and then irl!!"
created_at: "Jul 9, 2026"
note: "This journal is imported from Macondo"
---

# Started out of the project 2h 30m
I did a bunch of progress but didn't really document it since I kinda put it off until later.

https://lapse.hackclub.com/timelapse/nYJCGsTGZe1D 
I made all of the logic gates using only NAND after doing a lot of trial and error. I chose this simulator because it was the first thing I saw

<img width="818" height="719" alt="image" src="https://github.com/user-attachments/assets/c6dc9d61-b2ed-46df-b15d-b1cca1fafca8" />

(This was on the airplane so this was not recorded, but I didn't include it in the time just to be safe) Following the mattbatwings video playlist, (downloaded the ALU video) https://www.youtube.com/watch?v=osFa7nwHHz4&list=PL5LiOvrbVo8nPTtdXAdSmDWzu85zzdgRT I made the ALU, but it took me a while to figure out that my Cin was on the lowest bit instead of the highest bit, then I inputted the bits in reverse order, but I eventually figured out the adder part.

A pretty common thing I'd do was connect the wrong wires, flip it, or anything like that because of messy wiring. When I discovered you could click and like control how the wires flow, everything was a lot cleaner.

https://lapse.hackclub.com/timelapse/lNILn3eZ_3sw This part has some parts working on adder

It took me some trial and error trying to figure out how to make a latch myself, but I eventually gave up and just looked it up.

From there I made a basic memory register

http://lapse.hackclub.com/timelapse/Np7U85oJ2MKF Here I finished up the memory register and made it output based off the addresses you gave in. I also started working on the memory

The whole process was pretty straightfoward and didn't really have that many struggles, other than messing up the bits on the google sheet


# Remake register file 1h 6m
After watching Sebastian Lague's video about RAM, it made me realize I could easily make 16 registers. I did this by making a 4 bit address which translates into a row and column, which inputs into every 8 bit latch where they both need to be on to be enabled.

Something that made me stuck was trying to connect all of the outputs into one bus, which kept flashing. After doing some research, I realized that using a tri-state buffer was actually useful, turning off an output instead of using an enable. I found that simulating that was a good idea, since in real life 0 goes to ground, which would affect bus signals, compared to just disconnected, which wouldn't.

After this discovery, I had to restart my register because having the write signal also control the read signal was also not my intent. I did this by adding a 4 bit column and row (similar to before) structure and also made the 8-bit enable to have tri-state buffers instead of a bunch of AND gates, outputting "disconnected" instead of "0".
<img width="869" height="562" alt="image" src="https://github.com/user-attachments/assets/6ef22dc3-a9f2-4922-9af2-a5ba2895a847" />
<img width="854" height="448" alt="image" src="https://github.com/user-attachments/assets/05907101-ec23-429f-a732-c35e3948cb6f" />
<img width="866" height="529" alt="image" src="https://github.com/user-attachments/assets/7ce5fb18-eb72-4640-afa2-dee99c398a4f" />

# Control ROM 1 hr
https://lapse.hackclub.com/timelapse/Um0NA_AAu0c- (i accidentally left it on but I corrected my hours to be correct)

Following my google sheet I just wired up the control ROM, continue using the the column and grid structure. I used an AND gate, connected to both of the inputs for tri-state buffer for all 16 instructions so all I had to do was to connect it to the correct bus at the bottom. I chose to make a DISABLE and just NOT that signal to make it easier and I don't have to connect as much.
<img width="857" height="404" alt="image" src="https://github.com/user-attachments/assets/a4bbd82f-e7f6-48db-8d66-72b5de28f8de" />

# Program Counter + Increment 42m
https://lapse.hackclub.com/timelapse/wyl1HNTy6TsB
I basically made this by just having an 8 bit mux where the two inputs is itself and the new input.
I don't really remember much so sorry for the dry journal 😢
<img width="243" height="141" alt="image" src="https://github.com/user-attachments/assets/0db11c30-f757-4a89-8f0d-cafb9615fad2" />

# Compiler 1h 27m
I made the compiler from my own assembly to binary code. It's debugging is very limited, as all it basically does is replace keywords with binary.
This made me think that my program counter was glitching, but in fact it was working (only like 20% of the time if I was lucky), but in reality something like
`ADI r3 6` would compile to `1010 0011 0000 0110` which would add 48 to register 6
One of the struggles I had at the beginning was trying to get the clock signal to only output one tick, since the program counter kind of just spammed to 255 without properly clocking everything.
<img width="849" height="343" alt="image" src="https://github.com/user-attachments/assets/a3f24478-825d-48bd-aca4-7cf33d82fc42" />

# Flags and Branching 1h 23mins
I made the flags from the ALU and the branching. 
Honestly, I also don't remember much so sorry again. 
What I do remember that I couldn't really tell if it was working or not, since the clock is still really broken.
I also remember that I had to shift around the rivals a bunch because of my messy wiring.
<img width="1872" height="925" alt="image" src="https://github.com/user-attachments/assets/7a862629-89ed-4eab-b035-c3de76213106" />


