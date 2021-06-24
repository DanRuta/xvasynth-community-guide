

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

### Elscrux

Follow this guide for how to easily extract dialogue from Skyrim via xEdit, straight into the correct format for the batch synthesis mode:
https://docs.google.com/document/d/13rN4yzgE_7UDj9qzURJyKQufxrwev1bzsrSmB437nNI

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


### Para - Reducing Static and tinny artifacts for SKVA generated voices (for Skyrim SE)

<ol>
 <li>Generate SKVA sample; adjust; save wav to something that makes sense.</li>
 
 <li>Now take this same utterance with the same exact settings and add random punctuation in the middle of it to force a pause. This pause will be filled with some audio artifacts / white noise / static that SKVA generates. </li>
 <ul>
  <li>Note: this is especially useful if you’re modifying the global pitch of the utterance from the voiceset’s baseline by decreasing/increasing it when you generate your file in step 1. The white noise will be specific to the pitch at which you’re working for the voice set. For example, if the default voice is at higher pitch and you’re working by decreasing overall pitch in SKVA (by clicking the Decrease button on the whole sentence, rather than each individual phoneme), you will want to match your noise profile to that pitch. This will also depend somewhat on the content of the sentence itself. If your sentence has a lot of sibilants (s sounds), the “tin” noise will likely be on higher frequencies.</li>
 </ul>
 <li>Save that file and name it something that makes sense: for example [CharacterName_NoiseProfile.wav]</li>
 <li>Load both files from step 1 and step 2 into Audacity or the audio processing program of your choice.</li>
 <li>Go into your noise file from Step 3, and select the blank section where you get static but no vocals. Go to Effects > Noise Reduction, and with that section of white noise still selected/highlighted, click “get profile” or equivalent for your audio program. Save that preset to something that makes sense, for example “SKVA_CharacterName_NoiseBaseline”</li>
 <li>Go to the wav file generated in Step 1 (the one you’ll be working on). Select all, go to Effects > Noise Reduction and choose the profile you just saved. Click “preview” and listen to the audio. You should have quite a bit of “tin” removed, but you can play around with settings to see what sounds best. Once you’re happy, click Apply.</li>
 </li>At this point, you might still be getting some unwanted metallic sounds. Those generally will be of two types: low frequency artifacts that make it sound like your character is speaking from the bottom of a metallic cistern, or high frequency “tinny” sounds that make it sound like a walkie talkie. Those unwanted artifacts can be at both low and high frequencies, and while you might not be able to filter them out entirely from speech frequencies without “thinning” the voice too much, you can reduce them a bit by running a Bandpass, where you cutoff everything below 60 Hz and above 10000 Hz (or a little higher or lower depending on how high/low the voice’s baseline pitch is, you can play around with these values to see what sounds best for your specific case)</li>
 <li>Once you’re satisfied, it’s time to Normalize the audio. This step is important for making sure all your audio files sound the same. If you’re adding just one line of dialogue, then go ahead and Normalize here. Go to Effects > Normalize, click the “Remove DC before Normalizing” and click apply. I run it at something like -3db.</li>
 <li>Note: If you’re working with multiple files to create a collection of dialogues to plug into your mod, you will want to put them all into one audio track before processing them, then break them apart before preparing them to add to CK.</li>
 <ul>
  <li>It helps to generate silences between each clip you’re adding. Go to Generate > Silence, and pick something not too short, like 0.5s. It will make your life easier once you’re ready to parse them back up into individual files. </li>
  <li>It also helps to keep an eye out for the overall pitch settings you’re using. For example, if you are systematically lowering or raising the pitch from the default model in SKVA, you’ll want to use the same “noise” profile for all your files in that “pitch” collection. You will run through the above steps, but on the whole collated audio file, using the same process on all of them. This will help standardize them, otherwise you will end up with variation between tracks, which you want to avoid if you’re going to plug them into the game.</li>
  <li>After you’ve collated all your voice set files into one track and removed as much tin as you can, go ahead and do step 8. You might need to adjust the setting (If you’re making voices to use in CK for a mod, you’ll likely be working in the -4db to -2db range to make the loudness approximate the game audio, but see what works for your setup).</li>
 <ul>
</ol>


### Shenzy

Be creative and break a difficult word into smaller, similar sounding words. For example, in words rarely spoken by the original voice, I often have trouble to get the sound "li" like in "literature" or "literally". When it happens, I tend to replace it with "lee" + the rest.

And don't forget the silence between words in xVA. It may not change the sound of a word, but it can impact the overall feeling of a sentence, without stretching the words themselves.
E.G, a micro-pause (stretching the the silence) before - and probably after - an important word, to make it stand apart. So you can still go on a monotonic tone but still give information on what is important.


### lillibattenberg

Don't feel constrained by the words you expect the AI to be able to pronounce! In my first ever Vilkas line, I had him ask (phonetically) "what have you done with cass see?", but found out later he can handle "Kassi" just as well. On the other hand, I had to spell "tragically" as "trajikly" to get the tone right, so experiment!

### Scroody

If people don't like the way the dialogue comes out, they can create the WAV using one of the voice types that sounds better. Then take the WAV and JSON from the better sounding voice type, and then regenerated it with the voice they wanted....It does require some cutting nad pasting and some manual editing of the JSON, but it does produce a better sound in many cases....For example. The following line sounds better comming from Female Commander than it does Female Even Tone. "Come on. Let's go. Move it."

Default FemaleEvenToned: `audio/scroody_femaleeventoned_default.wav`

Default FemaleCommander: `audio/scroody_femalecommander.wav`

Commander sounds better. Using commander's JSON and editing it for Even tone and regenerating the file, makes Lydia sound a little better.
(with some polishing): `audio/scroody_final.wav`


### Caden

If some sentences sound screwed up with any word that end in "ING", just have then remove the "G", example "Trying" sometimes sounds better and continues to the next word better by Typing "Tryin" into the synth. 
 
[via the "Keep editor state on voice change" setting] Sometimes if the line isnt coming out right, I will generate it in another voice, and once it generates right in another voice I go back to the voice I want and it generates close to the same but in the voice that I want
 
Video demonstration of using the tool to generate lines for Skyrim CK: https://www.youtube.com/watch?v=KRFblv7uqtM
