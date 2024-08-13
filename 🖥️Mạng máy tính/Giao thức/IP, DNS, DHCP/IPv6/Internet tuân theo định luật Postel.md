---
share: true
created: 2023-10-30T14:29
updated: 2024-08-06T21:46
---
Which brings us to Postel's Law, which I always bring up when I write about networks. When I do, invariably there's a slew of responses trying to debate whether Postel's Law is "right," or "a good idea," as if it were just an idea and not a force of nature.

Postel's Law says simply this: be conservative in what you send, and liberal in what you accept. Try your best to correctly handle the bugs produced by the other end. The most successful network node is one that plans for every "impossible" corruption there might be in the input and does something sensible when it happens. (Sometimes, yes, "something sensible" is to throw an error.)

[Side note: Postel's Law doesn't apply in every situation. You probably don't want your compiler to auto-fix your syntax errors, unless your compiler is javascript or HTML, which, kidding aside, actually were designed to do this sort of auto-correction for Postel's Law reasons. But the law does apply in virtually every complex situation where you need to communicate effectively, including human conversations. The way I like to say it is, "It takes two to miscommunicate." A great listener, _or_ a skilled speaker, can resolve a lot of conflicts.]

Postel's Law is the principle the Internet is based on. Not because Jon Postel was such a great salesperson and talked everyone into it, but because that is the only winning evolutionary strategy when internets are competing. Nature doesn't care what you think about Postel's Law, because the only Internet that happens will be the one that follows Postel's Law. Every other internet will, without exception, eventually be joined to The Internet by some goofball who does it wrong, but just well enough that it adds value, so that eventually nobody will be willing to break the connection. And then to maintain that connection will require further application of Postel's Law.

Nguồn:: [202007 - apenwarr](https://apenwarr.ca/log/?m=202007#:~:text=Internets%20are%20fundamentally%20sloppy)