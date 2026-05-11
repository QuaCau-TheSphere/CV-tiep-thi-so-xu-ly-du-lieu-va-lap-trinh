---
share: true
created: 2023-10-30T14:29
updated: 2026-05-10T21:42
---
Khái niệm:: 

[](https://stackoverflow.com/posts/4491290/timeline)

Maybe it's easier to understand what Security-by-Obscurity is about, by looking at something that is in some sense the _opposite_: _Auguste Kerckhoffs's Second Principle_ (now simply known usually as _Kerckhoffs's Principle_), formulated in 1883 in two articles on _La Cryptographie Militaire_:

> [The cipher] must not be required to be secret, and it must be able to fall into the hands of the enemy without inconvenience.

Claude Shannon reformulated it as:

> The enemy knows the system.

And Eric Raymond as:

> Any security software design that doesn't assume the enemy possesses the source code is already untrustworthy.

An alternative formulation of that principle is that

> The security of the system must depend _only_ of the secrecy of the key, not the secrecy of the system.

So, we can simply define Security-by-Obscurity to be any system that does not follow that principle, and thus we cleverly out-defined the password :-)

There are two basic reasons why this Principle makes sense:

1. Keys tend to be much smaller than systems, therefore they are easier to protect.
2. Compromising the secrecy of a key only compromises the secrecy of all communications protected by that key, compromising the secrecy of the system compromises _all_ communications.

Note that it doesn't say anywhere that you can't keep your system secret. It just says you shouldn't depend on it. You may use Security-by-Obscurity as an _additional_ line of defense, you just shouldn't assume that it actually works.

In general, however, cryptography is _hard_, and cryptographic systems are complex, therefore you pretty much _need_ to publish it, to get as many eyeballs on it as possible. There are only very few organizations on this planet that actually have the necessary smart people to design cryptographic systems in secrecy: in the past, when mathematicians were patriots and governments were rich, those were the NSA and the KGB, right now it's IBM and a couple of years from now it's gonna be the Chinese Secret Service and international crime syndicates.

Trích từ:: [Isn't a password a form of security through obscurity?](https://stackoverflow.com/a/4491290/3416774)