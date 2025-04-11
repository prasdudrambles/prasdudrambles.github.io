---
title: "Pixie Dust Attack"
layout: post
---


tl;dr - An attack which leverages a QOL feature to hack into a WPS network.


![pixie dust](/assets/images/pixie_dust_1.webp){:height="300px" width="600px"}


<h1>WHAT IS WPS</h1>
WPS stands for Wi-Fi Protected Setup. It is a network standard created by Cisco in 2006. The main goal of WPS was to make life easier for normal users to setup their own home networks.

Setting up a Wi-Fi Protected Network can sometimes be daunting for less technically knowledgeable users, people who don't really care about how things work as long as it works, WPS was created for such users.

WPS eliminates the need for typing out complex passwords to connect to the network. On devices like televisions which have a lack of input device, it makes it easier for it to connect to the network.

The 2 most popular methods in WPS are either a WPS push button, where the user pushes a physical button on the back of the router to connect a device to it - theoretically, anyone could just gain access to the router and log onto the network.

The other method is more secure (but not really), where the user enters an 8 digit pin to connect the device.

This method is the target for Pixie Dust attacks.

---

<h1>THE PIXIE DUST ATTACK</h1>


![pixie dust](/assets/images/pixie_dust_2.png){:height="300px" width="600px"}

The working of the Pixie Dust attack occurs in 3 phases

Handshake Capture
---
The attacker sends a WPS request to the router. To the router, it looks like an innocent device trying to connect to the router via WPS.

The router and the attacker (the router does not know this) talk to each other sending various messages, but the only one we need for the attack are called M1 message and M2 message.

M1 Message - is the message sent from the attacker to the router, informing the router that it wants to connect. The attacker generates a nonce (random number) and a Diffie-Hellman key pair and shares the PKe (public key) to the router.

M2 Message - is the message sent from the router to the attacker, telling the router "Okay, let's connect!". The M2 message contains the routers nonce and its PKr.

The AuthKey is also sent. This key is used to prove authenticity of the handshake data.

Offline Cryptographic Attack
---
In this phase, the attacker takes the data collected from the previous phase and tries to use math to reconstruct the router's private key, and then use that to compute the WPS pin.

We are depending on the fact that some (or most old) routers reuse the same private key, or the nonce which is generated is of weak entropy (not truly random). Using this we can bruteforce the routers private key using PKr and the nonce. Finally we can test each guess against the captured AuthKey from the handshake phase. If a match is found, we have found the WPS pin!

---

<h1>DEFENSE AGAINT PIXIE DUST ATTACK</h1>
Just disable WPS in your router LOL.

But then again it comes back to people. Regular people don't care about all this because they lack awareness. This leads to majority of routers still having WPS enabled on their routers. So, in my opinion its upto the people who set up these networks to fully secure them.

---

<h1>Further Reading</h1>
- [Wi-FI Protected Setup](https://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup)
- [Pixie Dust explained](https://www.linkedin.com/pulse/wireless-vulnerabilities-practice-wps-pixie-dust-attack-hamdan-trrpf?trk=public_post_feed-article-content)



