
Hello,

In episode 547 you read an article about GNU sed and you wondered what
the differences are with BSD sed. A few months ago I looked into it
because I wanted to write a blog post about sed[0] and I found a couple
of interesting ones, besides the difference in the -i option (inplace)
that you mentioned:

1. Escape sequences like \n for newline and \t for tab can be used
in regular expressions in both versions of sed, but only GNU sed
interprets them as special characters also in the replacement part of
an s command. For example:

echo 'a-b-c' | sed 's/-/\n/g'

returns

a
b
c

on GNU sed, but

anbnc

on OpenBSD sed (an escaped n is just a regular n, apparently). In BSD sed
one has to use *literal* tabs or newlines (if working on an interactive
shell, you can insert them by preceding them with Ctrl+V).

2. GNU sed offers shortcut for certain character sets in regular
expressions, such as \b for word boundary (POSIX [[:<:]] and [[:>:]])
or \s for whitespace (POSIX [:space:]).

3. GNU sed has some extra commands, see [1]


Overall, it looks like BSD sed is more minimal, offering little more
than what mandated by POSIX - I'll leave it for you to decide if this
is a good or a bad thing 🙂

Best regards,
Sebastiano

[0] https://sebastiano.tronto.net/blog/2023-12-03-sed
[1] https://www.gnu.org/software/sed/manual/sed.html#Extended-Commands