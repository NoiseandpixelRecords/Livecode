# The Basics

## Basic 120 bpm

clock.tempo = 120;

@swim ()

def step1(p=0.5, i=0  ):

N1( "C" ,dur=1)

again(step1, p=1 ,i=i+1)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70a150e2-b90f-442c-be6b-b361dc79a8e0/9ef856d1-a470-494b-b3aa-41937305b211/78bbf8db-3dd0-41c3-b56e-fd1082fd5561.png)

clock.tempo = 120;

@swim ()

def step1( p=0,i=0  ):

N1( 'F .' ,i=i/4,dur=1)

N1( 'F0' ,i=i/2,dur=1)

again(step1, p=.25 ,i=i+1)

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
