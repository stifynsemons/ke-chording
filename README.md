# ke-chording
Extend Karabiner-Elements to support chording

The ke-chording project generates configuration files for Karabiner-Elements that add chording support to a Mac Keyboard. With typical keyboard software, re-mapping for keys is one-for-one. You type one key, you get one key. Some support modifiers, which give multiple meanings to a key; and it is not uncommon for these to outputs to be words (or other sequences of characters). Karabiner-Elements allows a very generic extension to this concept - remapping pairs of keys, or triplets, or larger sequences, into words or phrases or other sequences. 

ke-chording simplifies the configuration by generating the required complex manipuation JSON entries from a simple two-column list of chord and meaning.

While chording keyboards in software are not unique (consider Plover, for instance), Karabiner-Elements is the only generic solution. These chords can be not only to assist with speed-typing, but also in reducing the number of keypresses or reducing the workload of specific fingers, which can be a great boon to those with finger pain, etc. With a modest number of chords, the number of keypresses can be reduced to 67% for typing English text. (Support for other languages would require a different frequency table reference). As the number of chords is expanded, 50% is achievable, and with phrases, 33%.

How does this work? By typing in "words", fewer keys are needed to type more characters. For example, "the" has three letters, and we can use "th" to represent it. If you slur T and H - that is, don't let up on T before you press H, you get the chord, and have typed three characters for the price of two. Better yet, we can auto-add the space, as in "the ", so you get four for the price of two. From a speed perspective, many of the chords are faster to type than separated keystrokes - it is what you do any way when typing. From an over-use perspective, it is half the work.

Regular single keypresses still work, so if you can't remember a chord, you can always spell it out and you are no worse off than if you were before.

At present, ke-chording provides support for pairs and triplet chords, with conflict detection. 

To build it:
>  clone this project into your ~/.config/karabiner directory
>  edit the chord.components file to the list of .chords files that you want to include
>  edit ke.header and ke.footer to include the other features of Karabiner-Element that you want - it needs to split so that ke.header includes all of your complex manipulators, and ke.footer contains the rest of your standard file. This is a priority to cleanup - build_chords should determine these from your existing file.
>  run ./build_chords

This will update the karabiner.json file which karabiner will automatically re-read. The build script will use the simplified file list to estimate the effectiveness of your chord set for typing English, as well as generate a list of common words that you don't support in the missing.table. If you would like to try this against another language or a better English source, update frequency.table.

For a simplified list for English, look at english.chords
