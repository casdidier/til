Text strings look simple, but they are actually kind of complicated underneath. There are a lot of different ways that computers can represent text in memory and on the network.

Older software — including older versions of Python — tended to assume that each character takes up only one byte of memory. That works fine for some human languages, like English and Russian, but it doesn't work at all for other human languages, like Chinese; and it really doesn't work if you want to handle text from multiple languages in the same program.

These words all mean cat:
gato قط 猫 گربه кіт बिल्ली ねこ

The Web is international, so browsers and servers need to support all languages. This means that the old one-byte assumption is completely thrown out. But when programs use the network, they need to know how long a piece of data is in terms of bytes. That has to be figured out unambiguously at some point in time. The way Python does this is by making us encode strings into bytes objects when we want to send them over a binary channel (such as an HTTP connection).

This Japanese word for cat is two characters long. But when it's encoded in binary, it's six bytes long:

> > > len('ねこ')
> > > 2
> > > len('ねこ'.encode())
> > > 6
> > > The most common encoding these days is called UTF-8(opens in a new tab). It is supported by all major and minor browsers and operating systems, and it supports characters for almost all the world's languages. In UTF-8, a single character may be represented as anywhere from one to four bytes, depending on language.

English text with no accent marks still takes up one byte per character:

> > > len('cat')
> > > 3
> > > len('cat'.encode())
> > > 3
> > > UTF-8 is the default encoding in Python. When you call the encode method on a string without passing it another encoding, it assumes you mean UTF-8. This is the right thing to do, so that's what the code in this course does.
