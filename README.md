# ke-chording
## Extend Karabiner-Elements to support chording

**Note: this document and the software is a work in progress. The pieces can be made to work, but the software and docs are not competely in sync yet**

The ke-chording project generates configuration files for Karabiner-Elements that add chording support to a Mac Keyboard. With typical keyboard software, re-mapping for keys is one-for-one. You type one key, you get one key. Some support modifiers, which give multiple meanings to a key; and it is not uncommon for these to outputs to be words (or other sequences of characters). Karabiner-Elements allows a very generic extension to this concept - remapping pairs of keys, or triplets, or larger sequences, into words or phrases or other sequences. 

ke-chording simplifies the configuration by generating the required complex manipuation JSON entries from a simple two-column list of chord and meaning.

While chording keyboards in software are not unique (consider Plover, for instance), Karabiner-Elements is the only generic solution. These chords can be not only to assist with speed-typing, but also in reducing the number of keypresses or reducing the workload of specific fingers, which can be a great boon to those with finger pain, etc. With a modest number of chords, the number of keypresses can be reduced to 67% for typing English text. (Support for other languages would require a different frequency table reference). As the number of chords is expanded, 50% is achievable, and with phrases, 33%.

How does this work? By typing in "words", fewer keys are needed to type more characters. For example, "the" has three letters, and we can use "th" to represent it. If you slur T and H - that is, don't let up on T before you press H, you get the chord, and have typed three characters for the price of two. Better yet, we can auto-add the space, as in "the ", so you get four for the price of two. From a speed perspective, many of the chords are faster to type than separated keystrokes - it is what you do any way when typing. From an over-use perspective, it is half the work.

Regular single keypresses still work, so if you can't remember a chord, you can always spell it out and you are no worse off than if you were before.

At present, ke-chording provides support for pairs and triplet chords, with conflict detection. 

## Installation

To build it:
```
clone this project into your ~/.config/karabiner directory
edit the chord.components file to the list of .chords files that you want to include
edit ke.header and ke.footer to include the other features of Karabiner-Element that you want - it needs to split so that ke.header includes all of your complex manipulators, and ke.footer contains the rest of your standard file. This is a priority to cleanup - build_chords should determine these from your existing file.
run ./build_chords
```

This will update the karabiner.json file which karabiner will automatically re-read. The build script will use the simplified file list to estimate the effectiveness of your chord set for typing English, as well as generate a list of common words that you don't support in the missing.table. If you would like to try this against another language or a better English source, update frequency.table.

For a simplified list for English, look at english.chords

## Learning to use chords

In order for chords to be effective, they must be easy to remember, common words, and easy on the hands. We'll use the basic english.chords as an example. To make them memorable, they normally start with the first letter of the word and finish with the most distinctive letter that is not already taken.

### Group 1: Two Letter Words
For two letter words - this is easy. Use both letters and that's it. It is only a 3 for 2 exchange with the space added, but it is still worthwhile. The two letter words are:
```
an as at be by do go he if in it me my no of on or so to up us we
```
### Group 2: First-Second Pairs
```
>0.6% THe BUt  HIs WIth
>0.2% ALl HAve OUt SAid SHe 
```
### Group 3: First-Last Pairs
```
>0.6% AnD      FoR  HaD     NoT                 WaS  YoU 
>0.2% ArE BeeN FroM HeR HiM TheM THeY ThiS WhaT WheN WhO WoulD
```
### Group 4: First-Middle Pairs
```
>1.0% ThAt
>0.2% TheIr TheRe WeRe WhiCh 
```
### Group 5: Letter-Number Pairs
```
o1: ONE
```
### Editing chords

Remember that each of these words comes with an attached space after it. You may be wondering at this point, what happens when you need to finish a sentence with a period, or use other punctuation. There is a remedy: the edit chords. Suppose you type a sentence,
```
HE␣HaD␣YoU␣AT␣GO␣
```
Notice the space separator, which is a unicode symbol. The same character is used when defining chords. Not a lot of savings (10/17), because it is all made of short words from the list. But it is wrong, because you need a period after the GO, not a space. In this case type the chord: delete-period, or ⌫., which erases the trailing space, adds a period, then puts the trailing space back. After a two letter word, it is not much help. You could have type GO.␣ instead of GO⌫. And, with longer chords, it starts to add up. You'll find this much more effective with endings like, ⌫g, which appends 'ing' to the end and restores the space.

