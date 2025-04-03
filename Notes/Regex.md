#### Anchors
* `^ Start of line`
* `$ End of line`
* `\b` Start or end of word

#### Escape Character
* `\ is the escape character`

#### Characters
* `\d Digit`
* `\D Non-Digit`
* `\w Word Character`
* `\W Non-Word Character`
* `\s Whitespace Character`
* `\S Non-Whitespace Character`

#### Character Classes
* `. matches anything except line breaking`
* `[a-e]` matches a through e
* `^[4-6]` doesn't match 4-6

#### Repetition
* Any of these can be used after specifying something to match
* `A{3,5}` matches `A` if it repeats 3,4, or 5 times
* `[1-2]+` matches 1 or 2 if it occurs once or more

#### Captures Groups
* `(?<time>\d\d:\d\d:\d\d)`
	* This will pull out 12:43:52 and go into the field named "time"