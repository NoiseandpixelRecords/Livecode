Based on the information from the search results, here's an introduction to Sardine, incorporating details from its creator's GitHub repository:

## 🐟 Sardine: Python's Missing Algorave Module

Sardine is a versatile and user-friendly Python library designed for musical improvisation, algorithmic composition, and live coding performances. Created by Bubobubobubobubo, Sardine transforms your standard Python interpreter into a powerful musical instrument[4].

### 🌟 Key Features

1. **Musical Creativity**: Create and map melodic and rhythmic patterns to electronic instruments using MIDI, OSC, and SuperCollider[4].

2. **Time-Aware Python**: Employ temporal recursion to make Python code time and tempo-aware, allowing for precise musical timing[4].

3. **Audiovisual Performance**: Develop intricate audiovisual performances with MIDI and OSC I/O capabilities[4].

4. **Synchronization**: Easily synchronize with other computers and musical instruments using MIDI Clocks and the Link Protocol[4].

5. **SuperDirt Integration**: Utilize bindings for SuperDirt, a popular audio engine among live coders[4].

### 🚀 Installation

To install Sardine, ensure you have Python 3.10 or later, then run:

```bash
pip install sardine
```

### 🏊 The `swim` Function

While not explicitly mentioned in the search results, Sardine likely uses functions or decorators for creating musical patterns. Here's a hypothetical example of how a `swim` function might work in Sardine:

```python
from sardine import *

@swim
def bass_pattern(time, steps):
    N('c3', dur=1/4)
    N('e3', dur=1/4)
    N('g3', dur=1/4)
    N('b3', dur=1/4)
```

This example demonstrates how Sardine might allow you to define repeating musical patterns using Python functions.

### 🤝 Community and Contributions

Sardine is in its early stages of development and actively seeks contributors. Whether you're interested in code, documentation, or have ideas to share, the Sardine community welcomes your involvement. You can connect with the community through Discord, GitHub, or by sending a private message to the creator[4].

Sardine represents an exciting intersection of Python programming and live music performance, offering a powerful platform for exploring algorithmic composition and real-time musical creativity.

Sardine

# The Basics

Intro 

Of-course the documentation link [https://sardine.raphaelforment.fr](https://sardine.raphaelforment.fr/)

## Basic 120 bpm

```jsx
clock.tempo = 120;

@swim ()

def step1(p=0.5, i=0  ):

N1( "C" ,dur=1)

again(step1, p=1 ,i=i+1)
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/9ef856d1-a470-494b-b3aa-41937305b211/78bbf8db-3dd0-41c3-b56e-fd1082fd5561.png)

```jsx
clock.tempo = 120;

@swim ()

def step1( p=0,i=0  ):

N1( 'F .' ,i=i/4,dur=1)

N1( 'F0' ,i=i/2,dur=1)

again(step1, p=.25 ,i=i+1)
```

## timing and duration

clock.tempo = 120;

@swim ()

def step1( p=1,i=0  ):

N1( '( [F F . F]    )' ,i=i/P("2 2 1 4"),dur=".1 .1 1   2")

N1( 'F0' ,i=i/2,dur=1)

again(step1, p=.25 ,i=i+1)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/eef2d53c-d1ea-4862-8a06-74bf0a0c7f58/51e5f838-3334-4264-8587-1d72a8c5fe09.png)

clock.tempo = 120;
@swim ()

def step1( p=1,i=0  ):
N1( '[F F . F]!8 [.!4]   ' ,i=i/P("2 2 1 4"),dur=".1 .1 1   2")
N1( 'F0' ,i=i/2,dur=1)
again(step1, p=.25 ,i=i+1)

clock.tempo = 120;

@swim ()

def step1( p=1,i=0  ):

V.s1= P(" ( [10 0 1 0]*2) ",i=i/32)

N1( '[[{F0  C1}!2 . F2]+(getA s1)!8 [.!4]]!2 [F0 F0 . F1]!8',chan =2 ,i=i/P("[2 2 4 8]!8 [1!4]",i=i*8),dur="5 5 3   2")

N1( 'F0',i=i/2,dur=1)

again(step1, p=.25 ,i=i+1)

*#   8 bar = 8 bar in ableton*

*#intro 32 bar  / breakdown 16 / drop 16 /  drop variation 16 /*

*# breakdown  16 / drop / outro /*

### chords+arpegiator

```jsx

clock.tempo = 120; 
@swim ()  
def step1( p=1,i=0  ):
   V.s1= P(" ( [10 0 1 0]*2) ",i=i/32) #arpgiator
   N1( '[[{F0  C1}!2 . F2]+(getA s1)!8 [.!4]]!2 [F0 F0 . F1]!8',chan =2 ,i=i/P("[2 2 4 8]!8 [1!4]",i=i*8),dur="5 5 3   2")
   N1( 'F0',i=i/2,dur=1)
   again(step1, p=.25 ,i=i+1) 
   #   8 bar = 8 bar in ableton 
   #intro 32 bar  / breakdown 16 / drop 16 /  drop variation 16 /
   # breakdown  16 / drop / outro /&
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/c9f8ae08-d641-4a16-a653-135f234fa074/Untitled.png)

## Sample Sync and speed

For now sample selection is very annoying and take long time. This is not so friendly with live music. In sardine i find a way to loop sample. Its basic and need to feet the sample length. 

```jsx
   *#sample 4 sec not sync to the bpm worfine but not if we change the bpm* 
   #sample 4 sec dont work with sync
   
panic()

clock.tempo = 120; 
@swim ()  
def step1( p=1,i=0  ):
   N1( '0 . . . .' ,i=i/8,dur="1")
   print (clock.bar%8 , i%10 )
   again(step1, p=.25 ,i=i+1) 
   #   8 bar = 8 bar in ableton 
   #intro 32 bar  / breakdown 16 / drop 16 /  drop variation 16 /
   # breakdown  16 / drop / outro / 
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/8e5d1717-625c-4c96-8f7b-a72ea20f1dba/1d9a946b-8824-42dd-8d54-15801a878c5b.png)

# 

```jsx
   #sample work with sync but if we change the ableton bpm we need to update the 
   sardine bpm and it work 
   
panic()

clock.tempo = 120; 
@swim ()  
def step1( p=1,i=0  ):
   N1( '0 . . . ' ,i=i/8,dur="1")
   print (clock.bar%8 , i%10 )
   again(step1, p=.25 ,i=i+1) 
   #   8 bar = 8 bar in ableton 
   #intro 32 bar  / breakdown 16 / drop 16 /  drop variation 16 /
   # breakdown  16 / drop / outro / 
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/4b02eed6-81a0-4573-9315-bf48774878f0/a71d30ef-8152-4f42-a023-6f4fd48b594b.png)

# Lets try DNB

```jsx
#when you add +1 you selec the next sample and  with the sync you must find 
the best number of silence "."  to fit the sample 4.5 sec need 7 silence 
changing the two bpm let them sync / 
panic()

clock.tempo = 145; 
@swim ()  
def step1( p=1,i=0  ):
   N1( '0+1 . . . . . . . ' ,i=i/8,dur="1")
   print (clock.bar%8 , i%10 )
   again(step1, p=.25 ,i=i+1) 
   #   8 bar = 8 bar in ableton 
   #intro 32 bar  / breakdown 16 / drop 16 /  drop variation 16 /
   # breakdown  16 / drop / outro / 
```

```jsx
panic()

#jupiter organ preset  for konkat player vsti with etheral earth module
#rainedrops preset in pencil god 2 zip for synth 1 vsti
#Big city leaad preset in kvr zip 

#loop sample  Break Claves 92 bpm ableton library core 

clock.tempo = 151; 
@swim ()  
def step1( p=1,i=0  ):
   N1( '0+1 . . . . . . . ' ,i=i/8,dur="1")
   N1( '0+4 . . . . . . . ' ,i=i/16,dur="1")
   N1( '[ 1 . 2 .  4  . -2 . ]+C1+1' ,i=i/16,chan=1,dur=12)
   print (clock.bar%8 , i%10 )
   again(step1, p=.25 ,i=i+1) 
   #   8 bar = 8 bar in ableton 
   #intro 32 bar  / breakdown 16 / drop 16 /  drop variation 16 /
   # breakdown  16 / drop / outro / 
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/8985659d-609e-4428-90be-554e9607d616/26266505-b25a-46fb-8cc5-00a517f6c861.png)

[6-Audio 0001 [2024-07-08 211907] (online-audio-converter.com).mp3](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/645409ff-59d9-42b8-bf9c-956768922fd4/6-Audio_0001_2024-07-08_211907_(online-audio-converter.com).mp3)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/69037f04-5aae-4cbb-814e-b32ef2023f97/382e0f06-ea15-444a-b901-bf4c159612ba.png)

To take advantage of the MIDI note send and add density, 3 VSTi receive the note with different functions: one kind of short note or FX, the other the dreaming sound, and the last an arpeggiator giving rhythm. You can now group them and duplicate the groupe. With that you can change the preset and use ableton fader to switch between twoo mood for the same note in the code.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/0f043f62-b873-43bb-8a57-d17e8816fda0/Untitled.png)

# Blocking

I am new to this field and didn t see much about live code structure and aim at structuring tracks like classic EDM or dnb music. 32 16 and 8  are nice bars numbers to played with and tell a story. 

In pythin we can use a match and def to play what ever we want i ll love to make it shorter … still 

need to think how to do it. 

 

```jsx
panic()
#

clock.tempo = 151; 
@swim ()  
def step1( p=1,i=0  ):
   def a(): N1( '0+1 . . . . . . . ' ,i=i/8,dur="1")
   def b():N1( '0+4 . . . . . . . ' ,i=i/16,dur="1")
   def c():N1( '[ 1 . 2 .  4  . -2 . ]+C1+1' ,i=i/16,chan=1,dur=12)
   def d():N1( '0 . . . . . . . ' ,i=i/16,chan=3,dur="1")
   #last_value =listener1.get("//p") #control par osc
   #last_value =0;#P("[0]",i/1350)
   #track= last_value['args'][0]
   track=P("[1!16 2!16 ] [3!8 1!4 0!4 ] ",i=(i/4)/4) # last_value['args'][0] 
#This part is where building blocks are organized on the timeline
# I need to be divided by 4 to be in sync with the number of bars
# Because p=0.25 and i=1, we divide i by 4 and everything is in sync
   match track:
    case 0:   1;
    case 1:c()
    case 2:a(),c()
    case 3:c(),d()   
    case 11:panic()
   print ( ((i/4)/4)%32 )
   again(step1, p=0.25 ,i=i+1) 
   #   8 bar = 8 bar in ableton 
   #intro 32 bar  / breakdown 16 / drop 16 /  drop variation 16 /
   # breakdown  16 / drop / outro / clock.bar%32 

```

So with a bit of work we get this basic structure  that play a 3.40 min track 

```jsx
panic(   )

clock.tempo = 151; 
@swim ()  
def step1( p=1,i=0  ):
   def a(): N1( '[0+1 . . . . . . . ]' ,i=i/8,dur="1")
   def b():N1( '0+4 . . . . . . . ' ,i=i/16,dur="1")
   def c():N1( '[ 1 . 2 .  4  . -2 . ]+C1+1' ,i=i/16,chan=1,dur=12)
   def d():N1( '0 . . . . . . . ' ,i=i/16,chan=3,dur="1") #vocal
   def e():N1( '2 . . . . . . . ' ,i=i/16,chan=3,dur="1") #rise sample
   def f(): N1(  "("+"mask"+D1 +" [ 1 0 1 0 0 1 0 1 1 ]"+")!16 " ,vel=111.31,chan=2  , i=i/2,dur=8)   #bass    tada da   
   def g():1
   def h():1
   def ii():1
   int, br, dr = "[1!16 2!16]", "[2!15 4!8 0!4] [3!4]", "[5!16 0]"
   br2, dr2, out = "[2!15 4!8 ][3!4]", "[5!16 0]", "[1!16][11]"
   track=P(int+br+dr+br2+dr2+out,i=(i/4)/4) #P("[1!16 2!16 ] [3!8 1!4 0!2 ] [1!16 2!16 ] ",i=(i/4)/4) # last_value['args'][0]
   match track:
    case 0:   pass;
    case 1:c() ;
    case 2:a(),c();
    case 3:c(),d()   ;
    case 4:a(),c(),e()  ;
    case 5:f() ,a()
    case 6:f() ,a()
    case 11:panic();
   #print ( ((i/4)/4)%32 )
   again(step1, p=0.25 ,i=i+1) 
   #   8 bar = 8 bar in ableton 
   #intro 32 bar  / breakdown 16 / drop 16 /  drop variation 16 /
   # breakdown  16 / drop2 16 / outro 16 / clock.bar%32 

```

[testdnblight.mp3](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/510e549d-122d-4f0b-a0dd-5697a0d9b657/testdnblight.mp3)

```jsx
panic(   )

clock.tempo = 151; 
@swim ()  
def step1( p=1,i=0  ):
   def a(): N1( '[0+1 . . . . . . . ]' ,i=i/8,dur="1")
   def b(): N1( '0+4 . . . . . . . ' ,i=i/16,dur="1")
   def c(): N1( '[ 1 . 2 .  4  . -2 . ]+C1+1' ,i=i/16,chan=1,dur=12)
   def d(): N1( '0 . . . . . . . .' ,i=i/16,chan=3,dur="1") #vocal
   def e(): N1( '2 . . . . . . . ' ,i=i/16,chan=3,dur="1") #rise sample
   def f(): N1(  "("+"mask"+D1 +" [ 1 0 1 0 0 1 0 1 1 ]"+")!16 " ,vel=111.31,chan=2  , i=i/2,dur=8)   #bass    tada da   
   def g(): N1(  "[ C .   C . E  .]+5+"+str(P('0 3 5', i/(32*4))),vel=111.31,chan=4, i=i/3,dur=4 )  #_tops 
   def h(): N1(  "[ C .   C . E  .]+5+"+str(P('0 3 5', i/(32*4))),vel=111.31,chan=4, i=i,dur=4 )  #_tops 
   def ii():1
   def j(): N1(  "("+"mask"+D1 +M1+")!2+" +str(P('20 -2  3 3', i/(128))),vel=111.31,chan=5 , i=i/8,dur=32 )   #_pad
   int, br, dr = "[1!16 2!16]", "[2!15 4!8 0!2 3!8]", "[5!14 6!2 0]"
   br2, dr2, out =  "[2!15 4!8 0!2 3!8]", "[6!14 7!2 0]", "[1!16][11]"
   track=P(br);
   track=P(int+br+dr+br2+dr2+out,i=(i/4)/4) #P("[1!16 2!16 ] [3!8 1!4 0!2 ] [1!16 2!16 ] ",i=(i/4)/4) # last_value['args'][0]
   match track:
    case 0:   pass;
    case 1:c() ; j()
    case 2:a(),c();g();
    case 3:d()   ;
    case 4:a(),c(),e()  ; g()
    case 5:f() ,a() ,j()
    case 6:f() ,a(),h()
    case 7:c(); 
    case 8:d() , g()  ; j()
    case 11:panic();
   #print ( ((i/4)/4)%32 )
   again(step1, p=0.25 ,i=i+1) 
   #   8 bar = 8 bar in ableton 
   #intro 32 bar  / breakdown 16 / drop 16 /  drop variation 16 /
   # breakdown  16 / drop2 16 / outro 16 / clock.bar%32  #processing #unreal #lighting

```

[TESTDNBblock_1.mp3](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/99801b30-e5a3-46e9-8fc6-85679946c828/TESTDNBblock_1.mp3)

So from there we can add stabs and fx … variation in the drums and vocals and clean the drop  and volumes. its 

[step2TESTDNB_1.mp3](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/aff93d21-8dda-4b4b-9045-23b038b40810/step2TESTDNB_1.mp3)

# Melodie and complexe patern

this is a midi part for a high pitched not put on top of everything 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/95abb8ab-f303-4d00-8f86-429db744a4a2/8831f026-c62b-4382-87b1-e3923f3668f7.png)

Still need to test and work this line and putting silence 

```jsx
N1("[[F4 G4 F4 ] B4 {C5 D4 } {C5 B4 } {B5 A4 } {D5 A4 } ]+ [0!(16)  1!16   2!(16) 3!(16)  ] ",i=i/(16*4),dur=P(" ( [18]) ",i/128)    ), #16*4

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/14ca6713-43e0-4d2a-a2cf-5b9e7b490ebd/ad94e0cc-0693-4630-9e5d-28892427ae06.png)

So after simplification and sound design 

```jsx

 """
  _________.__                
 /   _____/|  | _____  ___.__.
 \_____  \ |  | \__  \<   |  |
 /        \|  |__/ __ \\___  |
/_______  /|____(____  / ____|
        \/           \/\/     

 """

def ini () : 
   your_midi_port = ["sardine1", "sardine2", "sardine3","sardine4","sardine5","sardine5","sardine6","sardne7","sardne8", "SardineControl1","sardineDrum1","sardineSample1"]
   for port in range(len(your_midi_port)):
      your_midi.append(MidiHandler(port_name=your_midi_port[port]))
      bowl.add_handler(your_midi[port]);
##

ini()
N1  = your_midi[0].send  # For sending MIDI Notes    
N2  = your_midi[1].send  # For sending MIDI Notes 
N3  = your_midi[2].send  # For sending MIDI Notes    
N4  = your_midi[3].send  # For sending MIDI Notes    
N5  = your_midi[4].send  # For sending MIDI Notes    
N6  = your_midi[5].send  # For sending MIDI Notes    
N7  = your_midi[6].send  # For sending MIDI Notes   PP
N8  = your_midi[7].send  # For sending MIDI Notes   PP
N9  = your_midi[8].send  # For sending MIDI Notes   PP
N10 = your_midi[9].send  # For sending MIDI Notes   PP
PC1 = your_midi[0].send_program  # For MIDI Program changes
CC1 = your_midi[9].send_control  # For MIDI Control Change messages 

#Code by vjblind / krease 

##magenta
from random import *
from re &import *
import random
from alive_progress.styles import showtime
[0 if i % 2 == 0 else 1 for i in range(16)]
clock.tempo = 156
listener1 = OSCInHandler(
    ip="127.0.0.1",
    port=44441,
    name="Listener1",
    loop=osc_loop
)
your_midi  = [ ]
your_midi2 = [ ]
your_midi_port = ["sardine1", "sardine2", "sardine3","sardine4","sardine5","sardine5","sardine6","sardne7","sardne8", "SardineControl1","sardineDrum1","sardineSample1"]
your_midi.append(MidiHandler(port_name="sardine1"))
bowl.add_handler(your_midi[0]);
N1  = your_midi[0].send  # For sending MIDI Notes    
N2  = your_midi[1].send  # For sending MIDI Notes 
N3  = your_midi[2].send  # For sending MIDI Notes    
N4  = your_midi[3].send  # For sending MIDI Notes    
N5  = your_midi[4].send  # For sending MIDI Notes    
N6  = your_midi[5].send  # For sending MIDI Notes    
N7  = your_midi[6].send  # For sending MIDI Notes   PP
N8  = your_midi[7].send  # For sending MIDI Notes   PP
N9  = your_midi[8].send  # For sending MIDI Notes   PP
N10 = your_midi[9].send  # For sending MIDI Notes   PP
PC1 = your_midi[0].send_program  # For MIDI Program changes
CC1 = your_midi[9].send_control  # For MIDI Control Change messages 
##
##black   ##
##green
""" track1____) 
  """ 
V.r=  1; #51-1; #  (getA r)  # sample  G#1   selection
V.l=    7  # 2  or 7  ``15zzz: 
SI8 ,SI4 ,SI2 ="[.!8 ]!8" , "[.!8 ]!4" ,"[.!8 ]!2"
SI1="[.!8 ]" 
SI="[.!2 ]!4"
TR1= "[ (getA r ) .!(getA l )   ]!2 "        #"[ 0 .!15    ]!1  [ 1 .!7  ]!8 [ 5 .!15  ]!2 [ 6 .!7  ]!8  [  6 .!7  ]!8  " ; "[ C#2 .!2   ]!8 "    
TR= "[ 0 .!15    ]!1 "        #"[ 0 .!15    ]!1  [ 1 .!7  ]!8 [ 5 .!15  ]!2 [ 6 .!7  ]!8  [  6 .!7  ]!8  " ;
D1="[C1 C1 C1 C1 C1 C1 C1 C1 C1 C1 C1 C1 C1 C1 C1 C1 C1 C1 C1 C1   ]+12"#  [. C1 D1 . .  [D1 D1 D1]    ]!2 " ;
M1=  "[0 0 0 0 0 0 1 0 0 0 0 0 0 0 0 1]"
M2=  "[0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1]"
pat1="[0 0 0 1 0 0 0 0 0 0 0 0 0 0 0 1]"
bowl.add_handler(listener1)  
listener1.attach('/stop', panic)
#track
 ##

panic()  

V.tLine1= "lll"#"<__________________________________________________________________________________________________________________>"# block 384 =4*96 _-----

def mt(position, char):
  position=int(position/4)
  return V.tLine1[:position] + char +V.tLine1[position + 1:]

clock.tempo = 151; 
@swim ()  
def step1( p=1,i=0  ):
   def a(): N1(  '[0+1 . . . . . . . ]' ,i=i/8,dur="1") # drum
   def b(): N1(  '0+4 . . . . . . . ' ,i=i/16,dur="1") # drum
   def c(): N1(  '[ 1 . 2 .  4  . -2 . ]+C1+1' ,i=i/16,chan=1,dur=12) #synth
   def d(): N1(  '0 . . . . . . . .' ,i=i/16,chan=3,dur="1") #vocal
   def e(): N1(  '2 . . . . . . . ' ,i=i/16,chan=3,dur="1") #rise sample
   def f(): N1(  "("+"mask"+D1 +" [ 1 0 1 0 0 1 0 1 1 ]"+")!16 " ,vel=111.31,chan=2  , i=i/2,dur=8)   #bass    tada da   
   def g(): N1(  "[ 32  .  ]+C0+"+str(P('-1 -2 1  ', i=i/(8*4))),vel=111.31,chan=4, i=i/P('1 3 3 3 ', i/(16*4)),dur=8 )  #bass stutter call 
   def h():{ N1(  "[[ 34 . 47  . B4 .{C5 D4 }. {C5 B4 }  . . {B5 B4 }. {D5 A4 } ]/3  ]+"+str(P('-1 -2 10 ', i=i/(1*4))),chan=7, i=i/P('16', i/(16*4)),dur=6 )  #_tops 
            ,N1(  '[7 .!7 ]' ,i=i/8,dur="1"), N1(  '[8 .!32 ]' ,i=i/8,dur="1") }  #key 
   def ii():N1(  '2 . . . . . . . ' ,i=i/16,chan=6,dur="1") #rise sample
   def j(): N1(  "("+"mask"+D1 +M1+")!2+" +str(P('20 -2  3 3', i/(128))),vel=111.31,chan=5 , i=i/8,dur=32 )   #_pad
   def k(): N1(  "[ 32  .  ]+C0+"+str(P('-1 -2 1 ', i=i/(32*4))),vel=111.31,chan=8, i=i/P('1 3 3 3 ', i/(16*4)),dur=8 )  #reponse 
   def fx():{ N1(  "[.!8] 4 [.!30] 7 "+SI2,i=(i/4)/4,chan=3,dur="1"),
              N1("[.!8] 9 [.!16] 6!8 ",i=(i/4)/4,chan=3,dur="1") ,
              N1("[.!4] 5 "+SI,i=(i/4)/4,chan=3,dur="1") ,N1(SI+" 9 [.!4] 9 [.!4] 9 [.!4] 9 ",i=(i/4)/4,chan=3,dur="1") }#fx
   def mel():N1(" .!4 [  B4 {C5 D4 } {C5 B4 } {B5 A4 } {D5 A4 } ]+ [0!(16)  2!(16)   ] ",
                i=i/(16*4),chan =9,dur=P(" ( [18]) ",i/128)    ), #16*4
   int, br, dr   = "[1!16]", "[ 2!16 4!8 0 3!8 ]", "[5!20 7!3 8!2 0]"
   br2, dr2, out = "[8!4 2!12 4!8 0!2 3!6]", "[6!8 7!2  5!16]", "[1!8][11]"
   track=P(br+dr,i=(i/4)/4)
   track=P(int+br+dr+br2+dr2+out,i=(i/4)/4)
   match track:   
    case 0:   pass;
    case 1:c() ; j()
    case 2:a(),c();g(); mel()
    case 3:d()  ;
    case 4:a(),c(),e()  ; g() ;mel()
    case 5:f() ,a() ,j(),h(); 
    case 6:f() ,a(),g()
    case 7:c(); 
    case 8:d() , g()  ; j()
    case 11:panic();
   fx();
   tr=track
   print ( mt(i/4, '\/'), ((i/4)/4), "/120",tr )
   V.tLine1=mt(i/4, str(tr))
   again(step1, p=0.25 ,i=i+1) 
   #   8 bar = 8 bar in ableton 
   #intro 32 bar  / breakdown 16 / drop 16 /  drop variation 16 /
   # breakdown  16 / drop2 16 / outro 16 / clock.bar%32  #processing #unreal #lighting 0#
```

Still add vocals and correction  more melodic sens

https://soundcloud.com/kreasevision-dump/akrylik


Citations:
[1] https://github.com/Bubobubobubobubo/livecodingfr
[2] https://github.com/livecode/livecode/blob/develop/docs/guides/LiveCode%20Builder%20Language%20Reference.md
[3] https://github.com/livecode/atom-language-livecode
[4] https://github.com/Bubobubobubobubo/sardine
[5] https://github.com/topics/livecode-builder
