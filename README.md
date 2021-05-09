

This is a continuously changing community resource providing ideas and guides on how to best make use of xVASynth to get the best quality out of your voice lines.

To start with, this will mostly contain the raw notes from various people, until it all gets organized a bit better, as content grows. To contribute to this, either DM me links/text, post in [the discord server](https://discord.gg/nv7c6E2TzV) (let me know it's for the guide), or start a pull request directly.


## Tips from the author

Generating lines with [xVASynth](https://github.com/DanRuta/xVA-Synth) is sometimes good enough as-is. But most of the time, you can drastically improve the quality of audio lines through careful use of the pitch/duration editor. The more you use it, the better you will get at it - it's a skill (sometimes an art...). The kind of changes you need to make can vary between voices, depending on how well the models were trained.

 - Always use the bespoke HiFi-GAN if there is one available. Only on rare occasions does WaveGlow sound better, though you can still play around with it - just be careful if mixing the two, as the audio levels are different. You can use the ffmpeg amplitude settings to bring them to the same level. 
 - If a voice has trouble saying a particular word, try spelling it out phonetically. By that, I mean you should try to spell out the letter sounds, rather than the actual words.
 - Breaking a difficult word down into multiple smaller phonetically correct groups of letters, and shortening the pause between them away can help in some rare situations
 - If a letter sounds "tinny" using the HiFi-GAN, try shortening the offending letter's duration in the editor. For now, unusually long letters aren't converted into audio well enough sometimes
 - "s" sounds are very audible and don't need a long duration. It sometimes improves quality to shorten these letters, and you won't lose any speech sounds.


## Tips/guides from the community


### D0lphin

The program concatenates phonetic chunks spelled with a hyphen. So if he can't say literature, you could try lit-ra-cherr

The voices I work with most often are Joker and FemShep, however this tends to apply to most others, as well.
I find that words such as "you" often benefit from the y and o being extended quite a bit, unless for some reason you need the word to not be emphasized much.
When going for a change in tone to emphasize a word, try to "stairstep" the change in notes. Voices are like musical instruments and it isn't often that one letter is wildly out of place with others. (There are rare exceptions to this)

Be aware also that letters that don't have a vocal component, so things like "k," "b," "p," "t," etc do affect the "notes" of the vocal sounds around them and do have frequencies themselves. Delivery of words can be manipulated in this way to change the 'shape' of how a word sounds.
(EG. I got Joker to really emphasize the word "have" in "I can see! I have eyes!" by lengthening and lowering the h, then stair-stepping the rest of the word's letters upwards.)
Questions do not always go upwards in tone. They can sometimes be achieved by tweaking the final word to go partially up, then downwards at the end. This can give the impression of a questioning statement, or of emphasising the idea of the final word. "I thought you said we were authorized?" for example. Raising the beginning of the word then dragging it down changes the emphasis.

Try and get to know your actor's voice in ways other than just how it sounds. Pay attention to the performance in vanilla lines, what letters and sounds the actor emphasises in their own natural speech. Sometimes, I find I can get the line to read better by inferring how I think the actor would really say it, and working in concert with the AI's best guess with tonality.
For example, I wouldn't say Seth Green is a mushmouth of a speaker, but he does let certain sounds "crash" into each other, and I can mimic this by lengthening these sounds and then reducing the time between them.

By contrast, Jennifer Hale (FemShep) is a very breathy speaker, so I always pull her "th" "sh" and "h" and usually "r" sounds out.



### Shenzy

Be creative and break a difficult word into smaller, similar sounding words. For example, in words rarely spoken by the original voice, I often have trouble to get the sound "li" like in "literature" or "literally". When it happens, I tend to replace it with "lee" + the rest.

And don't forget the silence between words in xVA. It may not change the sound of a word, but it can impact the overall feeling of a sentence, without stretching the words themselves.
E.G, a micro-pause (stretching the the silence) before - and probably after - an important word, to make it stand apart. So you can still go on a monotonic tone but still give information on what is important.


### lillibattenberg

Don't feel constrained by the words you expect the AI to be able to pronounce! In my first ever Vilkas line, I had him ask (phonetically) "what have you done with cass see?", but found out later he can handle "Kassi" just as well. On the other hand, I had to spell "tragically" as "trajikly" to get the tone right, so experiment!

### Caden

Video demonstration of using the tool to generate lines for Skyrim CK: https://www.youtube.com/watch?v=KRFblv7uqtM
