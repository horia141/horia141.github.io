---
published: false
---

Wikileaks released the other day a treasure trove of documents describing the [CIAs hacking tools](https://news.ycombinator.com/item?id=13810015). There's a lot stuff in there, but at core it confirms the belief of many in the IT field, that most things one does on a connected device can be found out, even when the intention is not to. This includes phones and computers, but also more exotic devices such as smart TVs. Though not as cool as the [CIA's other toys](https://en.wikipedia.org/wiki/Lockheed_U-2), they are perhaps more fearsome. 

There's no hope of security if the "attacker" has control of the computing machine, either through backdoors, or exploits. In the end you have to _trust_ something, and if that trust is misplaced the whole construction falls apart. Absolute security is impossible.

To a certain extent, applications like [Signal](https://whispersystems.org/) or [WhatsApp](https://www.whatsapp.com/faq/en/general/28030015) which offer "security" as a feature are doing themselves a disservice by not qualifing their offering. Whenever something like this pops up, they are called out on their claims, and found to be lacking. Which is a shame, because they _do_ try, and their security offering is better than alternatives.

It doesn't really make sense though to say things like: _"your communication is safe, unless somebody has compromised your device and is intercepting your keystrokes"_. There's a million such  tweaks which all result in the same result - the security guarantees not holding up. Worse, much like a product with a long, thorough and honest list of disclaimers, potential users will be confused and dissuaded from using a piece of software, preferring a "better marketed" alternative in its place.

Perhaps it might make sense to have a small set of security levels. These would succintly describe what sort of guarantees an application attempts to make. For example, we might have:

- No protection: your communication is visible to anybody on the Internet. Old-timey Yahoo Messanger! and IRC systems "offer" this.
- Third party protection: your communication is visible to you, and the maintainers of the chat application. Most chat applications, like Hangouts or Facebook Messanger offer this. Third parties will not see your communication, but it's still visible to "second parties".
- Corporate protection: your communication is visible to you, but not the maintaines of the chat application. Signal and WhatsApp offer this, with their end-to-end encryption.
- Nation-state protection: somebody with the resources of a whole country can't intercept or otherwise compromise your communication. This also applies to the owners of said chat application not sharing the data with the state's government.