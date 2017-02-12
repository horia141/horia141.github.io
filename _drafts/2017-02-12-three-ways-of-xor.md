---
published: false
---
We all know exclusive or or XOR. It's the cousin of NOT, AND and OR. Like AND and OR, it is a binary boolean function. Cryptographers love it and machine learning folks fear it. 

The first way of XOR is that it is true when both arguments are different and false when they are the same. So, to paraphrase the description of logical OR, `a XOR b` is true when either `a` is true or `b` is true, but not both. This is the understanding most common in programming languages. Sadly, XOR doesn't appear as an equivalent to NOT, AND and OR, as a logical operator on booleans, being relegated to just a bitewise operator. This not such a great loss however. XOR doesn't play well with short-circuiting and can lead to bugs in code.[1]

The second way of XOR is that it is a controller negator. The second argument is processed, while the first controlls whether the second is negated or not. This is the understanding most common in cryptography. XOR appears as a basic building block in one-time pads and stream ciphers. The key is used to control the negation, while the plaintext is what is processed.

The third way of XOR is that it is the most "complex" binary boolean function. There are `2^2^2=16` distinct boolean functions of two operators. Half of them are the negation of another function, so let's list the `8` which are distinct.

| Name | 0 0 | 0 1 | 1 0 | 1 1 |
|------|-----|-----|-----|-----|
| zero |  0  |  0  |  0  |  0  |
| and  |  0  |  0  |  0  |  1  |
| a!b  |  0  |  0  |  1  |  0  |
| a    |  0  |  0  |  1  |  1  |
| !ab  |  0  |  1  |  0  |  0  |
| b    |  0  |  1  |  0  |  1  |
| xor  |  0  |  1  |  1  |  0  |
| or   |  0  |  1  |  1  |  1  |

We can see XOR is the only function which has two zeros and two ones. It has the highest entropy amongst the set. The extra complexity has manifested itself in the fact that, geometrically, the function is not linearly separable. It was in fact _the_ example used against perceptrons / one layer neural networks to highlight their limitations and weaknesses. It more-or-less lead to the AI winter.

Quite the punch for such a small function.

---
[1] To elaborate on this point...
