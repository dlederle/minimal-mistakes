--- 
title: Music in Jason Rohrer's Gravitation
category: engl457
layout: single
---

Jason Rohrer describes his [*Gravitation*](http://hcsoftware.sourceforge.net/gravitation/) as "a video game about mania, melancholia, and the creative process".
One of the key components of the game's atmosphere is the music, which keeps pace with the game's shifting mood.
I hope to explore the ways in which the music factors in to the overall experience of *Gravitation* by exploring the game's source code.
~

Firstly, if you have not played *Gravitation*, please go do so, it takes less than ten minutes and is one of the more moving works of electronic literature I know.

*Spoilers Below*

The game opens with your character in a small box of visibility, surrounded by blackness.
A small child avatar begins throwing a red ball to you.
If you bat the ball back, a heart appears over the child's head, but if you don't and the ball hits the ground, tears sprout from the child.
As you play ball, the visible box grows larger, and the area within becomes more colorful and brightly lit.
At a certain point, when your "mood" raises high enough, your head appears to catch fire and you can jump incredible distances.
Jumping above your initial level reveals stars, which fall downwards when touched.

Your "mania" only lasts a short time, afterwhich your view closes up and the colors darken.
Unable to jump higher, you navigate your way down to the original level, where the stars have become blocks of ice with point values.
The points start at 9 and count slowly backwards.
Pushing the blocks of ice into a small kiln at the far right edge of the screen adds the current point value to your total.
The child continues to throw the ball when you return, and the blocks of ice can cut you off from him until they are cleared off.

In the beginning of the game, the music is slow and mournful.
As your mania increases, the initial music becomes overlayed with other tracks, which fade out as your mood darkens. 
The volume and tempo increases and the music becomes dischordant as your mood intensifies.

Rather than .ogg or .mp3, the game's music is encoded in a .tga file, an extension typically used for image files.
In fact, if you open the file with an image viewer, it reveals waves that appear to represent six different musical tracks.

  ![Gravitation Music](/images/music.png "Gravitation Music")

The thicker white horizontal lines delimit the different tracks.
The first track has long yellow lines that correspond to the slow, low brass sounding initial track.
The second track has red dots, that sound like a xylophone.
The third green track is the initial melody. 
The next three tracks are activated during mania, and its build up.
The two tracks with many small dots spaced at regular close intervals to each other appear to be the game's drum tracks.
The last track has yellow dots which I believe only play during the height of mania, and provide a rapid, high pitched counterpoint to the initial melody.

I am still working through the code which constructs sound from this file, but it is fascinating.
An initial foray into the musicPlayer.cpp file confirmed my hypothesis: 

``` c
    // smoothly fade in particular tracks based on player emotion
    // low emotion plays only first track... high emotion plays all tracks
    extern double playerEmotion;
``` 

Rohrer's comment precedes his loading of the floating point variable "playerEmotion", which represents the avatar's emotional state.
It operates on a scale with 0 being total melancholia and 1 being total mania.
It is used later as a multiplier for fading tracks in and out.
  
``` c
    // factor in player emotion

    // level from 0..(numTimbres-1)
    double trackFadeInLevel = playerEmotion * (numTimbres-1);
```

It is interesting that in this code Rohrer is treating the "playerEmotion" to be state of the game player's avatar, not the player themselves, which would be much more difficult to assess.
However, the discordant music will affect the human player's mood.
By tying the music to the avatar's emotion, Rohrer attempts to connect the player mood with the avatar mood.
