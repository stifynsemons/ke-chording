This file documents the mapping of characters to the equivalent names within Karabiner-Elements. A normal chords file is a list of chord definitions; each character in the definition corresponds to a key or to a special function. Keys that are represented in Karabiner-Elements as themselves, like "a", are represented in the chords file the same way. Keys without modifiers that correspond to a printing character are also represented by themselves.

Keys with modifiers are handled by the modifier prefix; for example, "!" is written as !1. Direct use of these characters is reserved for special functions, like "!" representing the shift modifier.

Whitespace is used to separate the chord from it's definition, so it cannot be used directly as a character either.

For these reasons, the other keys on the keyboard are represented by a select group of Unicode characters. So, to create a chord where you type quote followed by return_or_enter, and Karabiner-Elements should generate two double quotes and position the cursor between them, use a chord definition like this:

'↵   !'!'←

The list of currently supported chord characters, aside from the self-representing ones, is listed below:

```
⌫   delete_or_backspace
␣   spacebar
⎋   escape
↵   return_or_enter
←   left_arrow
→   right_arrow
↑   up_arrow
↓   down_arrow
↹   tab
⌘   left_command
⌥   left_option
⎈   left_control
⇧   left_shift
⇯   caps_lock
↾   right_shift
⌑   right_command
⌬   right_option
.   period
-   hyphen
,   comma
/   slash
;   semicolon
`   grave_accent_and_tilde
'   quote
=   equal_sign
[   open_bracket
]   close_bracket
\   backslash
```