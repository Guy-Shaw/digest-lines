# digest-lines

### Prefix each line of a text file with a unique ID number

A visual aid for comparing lines of text.

### Description

`digest-lines` prefixes each input line with a small unique ID number.

Input comes from files named on the command line or from standard input.

### The Problem

Sometimes what is desired is a comparison of individual lines
of text.  Sometimes all that is needed is comparison of lines
within a file, in which case only small unique content identifiers
are needed.  Those are easier to scan than message digests.

If individual lines are to be compared in a consistent way,
across files and across time, then some actual message digest
of each line comes in handy.


### Options

`--online`

means do not do two passes, and therefore do not
format the ID numbers with right justification, because we do
not know on the first pass how many ID numbers there will be.
While operating online, lines can be transformed and printed
immediately, and the input could be a potentially infinite
stream.

`--unique`

means do not print lines that we have seen before.

`--raw`

means prefix each line with its actual message digest,
rather than a small unique ID.  Usually, the much smaller IDs
are all that is needed.


### Example of use

I have shell history files that can be transcripts of some
rather long sessions, where, without planning ahead,
I end up building gradually longer and more complex scripts,
and go through many edit / build / test cycles.
Commands get repeated, typically by using some shell
history mechanism.  Well, that is, until I notice what is
happening and convert to a script, and then to a script
plus a make file, and so on.

Looking upon the history file, I notice that many events are
exact copies, but some are very similar but with some minor
fix or addition.  It can be pretty hard to tell visually
how many different variations there are.

Of course, I could use `sort` and `uniq` to eliminate the duplicate
lines.  But, that is not the same as seeing the history lines
in their original order.  This methods retains the lines,
in order, but adds the visual aid.

### Tip

Sometimes, you run into lines that look the same,
but differ only in white space, or in some other way that
is difficult to see.  This will tell you definitely that
such lines are different.  If the reason is still unclear,
you can run `digest-lines | cat --show-all`.


####

-- Guy Shaw

   gshaw@acm.org

