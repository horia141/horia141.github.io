---
published: true
title: Gradual Security Claims
layout: post
date: 2017-03-08T16:16:05.000Z
categories: post
tags: infosec cryptography whatsapp signal wikileaks
comments: true
math: false
---
Wikileaks released the other day a treasure trove of documents describing the [CIAs hacking tools](https://news.ycombinator.com/item?id=13810015). There's a lot stuff in there, but at core it confirms the belief of many in the IT field, that most things one does on a connected device can be found out, even when the intention is not to. This includes phones and computers, but also more exotic devices such as smart TVs. Though not as cool as the [CIA's other toys](https://en.wikipedia.org/wiki/Lockheed_U-2), they are perhaps more fearsome. 

There's no hope of security if the "attacker" has control of the computing machine, either through backdoors, or exploits. In the end you have to _trust_ something, and if that trust is misplaced the whole construction falls apart. Absolute security is impossible.

To a certain extent, applications like [Signal](https://whispersystems.org/) or [WhatsApp](https://www.whatsapp.com/faq/en/general/28030015) which offer "security" as a feature are doing themselves a disservice by not qualifing their offering. Whenever something like this pops up, they are called out on their claims, and found to be lacking. Which is a shame, because they _do_ try, and their security offering is better than the alternatives.

It doesn't really make sense though to say things like: _"your communication is safe, unless somebody has compromised your device and is intercepting your keystrokes"_. There's a million such  tweaks which all result in the same result - the security guarantees not holding up. Worse, much like a product with a long, thorough and honest list of disclaimers, potential users will be confused and dissuaded from using a piece of software, preferring a "better marketed" alternative in its place.

Perhaps it might make sense to have a small set of security levels. These would succintly describe what sort of guarantees an application attempts to make. For example, we might have:

- No protection: your communication is visible to anybody on the Internet. Old-timey Yahoo Messanger! and IRC systems "offer" this.
- Third party protection: your communication is visible to you, and the maintainers of the chat application. Most chat applications, like Hangouts or Facebook Messanger offer this. Third parties will not see your communication, but it's still visible to "second parties".
- Corporate protection: your communication is visible to you, but not the maintaines of the chat application. Signal and WhatsApp offer this, with their end-to-end encryption.
- Nation-state protection: somebody with the resources of a whole country can't intercept or otherwise compromise your communication.

The builders need not do anything special to attain the first level. The second level requires some protection of the data in transit and in storage on the maintainer's central system. This is achieved via TLS/SSL for the transit part and regular old encryption for the storage part. The third level requires more sophisticated protocols, such as those employed by Signal and WhatsApp for end-to-end encryption. Finally, the fourth requires a holistic view of security, becuase such attackers can compromise bits outside of the application itself. So one would speak of actual devices or appliances at this point, rather than just an application. From the second level up, there needs to be a whole infrastructure for security.