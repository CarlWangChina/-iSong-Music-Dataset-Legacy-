# àimusic datasets
[download datasets](http://aige.midilib.com/%C3%A0imusic-datasets/%C3%A0imusic-datasets.zip)  
[view datasets](http://aige.midilib.com/%C3%A0imusic-datasets/datas/data-tone/)  
## dataset format description
``` python

We use three different parts of information to represent a song in our dataset, including 1) musical tonality and mode, 2)melody sequence, 3)chord sequence of the accompaniment. A brief example is as follows:

#Tonality of the file
C:KeyMode.MAJOR 
# melody sequence,every 4 notes correspond to a chord
[74,74,74,77,77,77,77,77,77,77,77,77,77,77,77,77,77,77,77,77,77,72,72,76,76,76,76,74,74,74,74,74,74,74,74,74,71,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,60,65,65,65,65,65,65,67,67,67,64,64,64,64,64,64,64,64,64,62,62,62,62,62,62,62,62,62,62,62,62,62,62,62,62,62,62,62] 
# chord sequence
[[38,41,45],[41,45,48],[41,45,48],[43,47,50],[43,47,50],[45,48,52],[45,48,52],[45,48,52],[45,48,52],[45,48,52],[45,48,52],[45,48,52],[45,48,52],[36,40,43],[36,40,43],[45,48,52],[45,48,52],[41,45,48],[41,45,48],[36,40,43],[36,40,43],[43,47,50],[43,47,50],[43,47,50],[43,47,50],[43,47,50],[43,47,50],[43,47,50],[43,47,50],[38,42,45]]

Musical tonality and mode 
are stored at the beginning of a piece of music data. For example, C:KeyMode.MAJOR means the music is in C major.

The melody sequence 
is a one-dimensional time series array, and the elements in the array are the MIDI pitch of the melody at the corresponding time. The melody sequence is sampled in units of sixteenth notes, that is, the time value of each element in the array is one quarter of a beat.

The chord sequence of accompaniment 
is also a one-dimensional timing array. The elements in the array are the chords at the corresponding time, which are expressed in the form of constituent tones. The chord sequence is sampled by quarter notes, that is, the time value of each element in the array is one beat.

```

## parse file
``` python
    file = open("./datas/data-tone/1.txt") # open file
    arr = file.read().split("\n") # read file
    tone = arr[0] # get Tonality
    print(tone)
    melody = arr[1].strip("[]").split(",") # get melody
    print(melody)
    chord = arr[2].lstrip("[").rstrip("]").split("],[") # get chord
    print(chord)
```
