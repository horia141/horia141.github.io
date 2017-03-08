---
published: false
---

Wikileaks released the other day a treasure trove of documents describing the [CIAs hacking tools](https://news.ycombinator.com/item?id=13810015). There's a lot stuff in there, but at core it confirms the believe of many in the IT field, that most things one does on a connected device can be found out, even when the intention is not to. This includes phones and computers, but also more exotic devices such as smart TVs. Though not as fearsome as the [CIAs other toys](https://en.wikipedia.org/wiki/Lockheed_U-2), they are perhaps more fearsome. One can 

There's no hope of security if the "attacker" has control of the computing machine, either through backdoors, or exploits. In the end you have to _trust_ something, and if that trust is misplaced the whole construction falls apart. 

However, this is a given for security professionals. Absolute security is impossible.

To a certain extent, applications like [Signal](https://en.wikipedia.org/wiki/Signal_(software)) or [WhatsApp](https://www.whatsapp.com/faq/en/general/28030015) which offer "security" are doing themselves a disservice by not qualifing their offering.

It doesn't really make sense though to say things like: _"your communication is safe, unless somebody has compromised your device and is intercepting your keystrokes"_. There's a million such little tweaks which all result in the same result - the security guarantees not holding up. Worse, much like a product with a long, thorough and honest list of disclaimers, potential users will be confused and dissuaded from using a piece of software, preferring in its stead a "better marketed" alternative.

Perhaps it might make sense to have a small set of security levels. For example, for a chat application, we might have:

- No protection: your communication is visible to anybody on the Internet. Old-timey Yahoo Messanger! and IRC systems "offer" this.
- Third party protection: your communication is visible to you, and the maintainers of the chat application.
- Corporate protection: your communication is visible to you, but not the maintaines of the chat application.
- Nation-state protection: somebody with the resources of a whole country can't intercept or otherwise compromise your communication. This also applies to the owners of said chat application not sharing the data with the state's government.

A separate set of qualifiers could apply to whether the data is shared or not with external parties, and at what level.

- Public:
- Corporate sharing
- Nation-state sharing
- No sharing