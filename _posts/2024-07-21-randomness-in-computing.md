---
title: "Randomness in Computing"
layout: post
---


tl;dr -Random numbers aren't really random. Well, sometimes they are, but not really, it depends wether you think we live in a deterministic universe or not. Does it really matter if a number is true random? Sometimes.


![randomness](/assets/images/it-never-was.jpg){:height="600px" width="600px"}


Would you believe me if I told you random numbers don't actually exist?
Numbers calculated by a computer through a deterministic process, cannot, by definition, be random.
It is difficult to get a computer to do something by chance. A computer follows its instructions blindly and is therefore completely predictable. (A computer that doesn't follow its instructions in this manner is broken.)

“One thing that traditional computer systems aren’t good at is coin flipping,” says Steve Ward, Professor of Computer Science and Engineering at MIT’s Computer Science and Artificial Intelligence Laboratory. “They’re deterministic, which means that if you ask the same question you’ll get the same answer every time. In fact, such machines are specifically and carefully programmed to eliminate randomness in results. They do this by following rules and relying on algorithms when they compute.”

---

<h1>Where do we need randomness?</h1>
Randomness is at the forefront of gambling, video games, statistical sampling, and most notably, cryptography. If they couldn’t be unpredictable, our devices would lack essential security features and be far more vulnerable to cyber-attacks.
Random numbers are useful for a variety of purposes, such as generating data encryption keys, simulating and modelling complex phenomena and for selecting random samples from larger data sets. They have also been used aesthetically, for example in literature and music, and are of course ever popular for games and gambling.

[wait, I just told you there is no such thing as random numbers, and now I listed a bunch of places where random numbers are used. So which is it?]

---

<h1>How computers compute randomness</h1>
Computers have 2 methods to generate “random numbers”, TRNG and PRNG.


![randomness](/assets/images/comic.gif){:height="600px" width="600px"}


<h3>TRNG</h3>
It stands for True Random Number Generator. 
They are also called hardware random number generators. These produce numbers by harvesting entropy. (sounds cool, right?)
A popular example is [www.random.org](https://www.random.org/) which uses atmospheric noise to generate random numbers.

However, when I used the site to generate values, I got the value 82 both times. Was that random? We will never know. (if you don't believe me, well I wouldn't either)

<h3>PRNG</h3>
It stands for Pseudo-Random Number Generator.
PRNGs rely on algorithms to generate sequences of numbers that appear to be random. As suggested by the prefix “pseudo”, the sequence isn’t actually random, it just looks it. The two main components of a PRNG are an initial value or seed, and a pre-set algorithm.

Here’s how it works. The generator must:

    • Receive an initial value or seed as input.
    • Generate a new number by applying a series of mathematical transformations to the seed.
    • Use the value obtained as the seed for the next iteration
    • Repeat the process until the desired length is achieved.

<h3>PRNGs are deterministic and periodic.</h3> 
They are deterministic because once the algorithm and seed are defined, nothing can change the numbers that are outputted. Each consecutive number in the sequence is related to previous ones; this is known as a recurrence relation. PRNGs are periodic, meaning they repeat themselves after a certain number of iterations. A good PRNG algorithm should have a long period.

Which means that they can't use a PRNG to encrypt your password. PRNGs usually use the system time as the seed, so if the attacker knows the approximate time your password was encrypted (account creation time, password change time), they can just generate a small range of passwords using that time range, and try all the generated passwords instead of having to generate all possible combinations allowed.


<h3>How can PRNGs be improved?</h3>
"A common way to improve PRNGs is to combine them with a TRNG. The PRNG seed is changed based on the slower TRNG result. For the time between TRNG values, the PRNG provides a rapid sequence. For that interval, the sequence is subject to analysis and possible prediction. After that interval, the sequence is changed based on the true randomness. Combined PRNGs and TRNGs can provide rapid sequences combined with enhanced security."
<br><em>-Carl Mikkelsen, LinkedIn</em>

<h3>Popular PRNG algorithms</h3>
This topic is much more deep than I had previously anticipated. Covering all the algorithms would turn this short blog into another textbook so I will provide resources at the end for further reading.
To do justice to the algorithm section, I shall make my own TRNG and PRNG hybrid soon, I shall call it [].
Part 2 coming soon!

---

<h1>Radioactive decay</h1>
When a nucleus is unstable, there is no way of predicting when it will decay. This makes it an ideal candidate as a source of entropy for true random number generation.

(Hey alexa, add 100 grams of uranium to my cart!)

---

<h1>Can computer generated “random data" truly be random?</h1>
let's get philosophical, does it even matter?
One characteristic that builders of TRNGs sometimes discuss is whether the physical phenomenon used is a quantum phenomenon or a phenomenon with chaotic behaviour. There is some disagreement about whether quantum phenomena are better or not, and oddly enough it all comes down to our beliefs about how the universe works. The key question is whether the universe is deterministic or not, i.e., whether everything that happens is essentially predetermined since the Big Bang. Determinism is a difficult subject that has been the subject of quite a lot of philosophical inquiry, and the problem is far from as clear-cut as you might think.

![randomness](/assets/images/does-it-matter.webp){:height="600px" width="600px"}

<i>(Whoa! Hey man, what do you mean quantum phenomenon, uranium , working of the universe I just want you to give me 2 random numbers for my coin flip app)</i>

## Further Reading

- [Random numbers, generated by radioactive decay](https://www.fourmilab.ch/hotbits/)
- [Cloudflare lava lamps](https://www.cloudflare.com/learning/ssl/lava-lamp-encryption/)
- [Mersenne twister](https://www.sciencedirect.com/topics/computer-science/mersenne-twister)
- [Middle square method](https://en.wikipedia.org/wiki/Middle-square_method)