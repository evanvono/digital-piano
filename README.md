# digital-piano

https://www.youtube.com/watch?v=_pbxFazwHDg&feature=youtu.be

As shown in the video, I decided to create a basic digital "piano" which allows the user to play any note in a c major scale. Each piano "key" is represented as a lit column on the LED matrix, and is organized left to right from pitch C4 to pitch C5. I obtained the frequencies of these pitches online, and stored them into the definitions as shown in the C code below. The controls of the piano consist of two buttons and the accelerometer. The upper button is pressed to "play" the key, and can be held for as long as desired. The lower button is used to cycle to the next key, which moves from left to right until it reaches C5, where it then cycles back to C4 (the beginning of the scale) if pressed again. 

Much of this logic is represented by if statements in the main while loop, and supplementary while loops have been used to wait for buttons to be released after having been pressed. If both buttons are pushed simultaneously, a key press is prioritized over a key cycle, as shown in the order of the if statements in the code. Each time a key is "pressed", the columns surrounding it on the LED matrix also light up, giving some extra visual feedback. This was controlled by the "keyPress" and "keyRelease" functions, which wrote to the corresponding pins to each column of the matrix surrounding the column for the key currently being pressed, which is represented by the index "selectedKey" for the "pins" array. Cycling to the next key increased the value of selectedKey by 1, unless it reached 7 in which case its next value would be to return to 0 at the start of the array. Note pitches are stored in a parallel array called notes.

The accelerometer acts as a third user input with a more analog feel, which allows them to tilt the "piano" left and right to bend the pitch lower and higher, respectively. I chose to divide the x tilt value by 800, in order to keep it in a moderate range that gives a nice effect, without being tripped by any sudden slight movements. Tilting it back and forth rapidly gives a "vibrato" effect that I thought sounded pretty cool (perhaps better in person than in the video).  

This code was written for the RED-V Thing Plus using PlatformIO's Freedom E SDK support.
