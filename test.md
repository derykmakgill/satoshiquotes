---
layout: default
title: Satoshi, WTF
---

### Commerce & Payments


A purely peer-to-peer version of electronic cash would allow online payments to be sent directly from one party to another without the burdens of going through a financial institution. - Cryptography Mailing List

Bitcoin is a new electronic cash system that uses a peer-to-peer network to prevent double-spending. - [bitcoin-list]

Receivers of transactions will normally need to hold transactions for perhaps an hour or more to allow time for this kind of possibility to be resolved. They can still re-spend the coins immediately, but they should wait before taking an action such as shipping goods. - Cryptography Mailing List

It's not a problem if transactions have to wait one or a few extra cycles to get into a block. - Cryptography Mailing List

Instantant non-repudiability is not a feature, but it's still much faster than existing systems. Paper cheques can bounce up to a week or two later. Credit card transactions can be contested up to 60 to 180 days later. Bitcoin transactions can be sufficiently irreversible in an hour or two. - Cryptography Mailing List

If you're selling something that doesn't merit a network-scale attack to steal [a transaction], in practice you could cut it closer [in block confirmations]. - Cryptography Mailing List

The race is to spread your transaction on the network first. Think 6 degrees of freedom -- it spreads exponentially. It would only take something like 2 minutes for a transaction to spread widely enough that a competitor starting late would have little chance of grabbing very many nodes before the first one is overtaking the whole network. During those 2 minutes, the merchant's nodes can be watching for a double-spent transaction. The double-spender would not be able to blast his alternate transaction out to the world without the merchant getting it, so he has to wait before starting.

If the real transaction reaches 90% and the double-spent tx reaches 10%, the double-spender only gets a 10% chance of not paying, and 90% chance his money gets spent. For almost any type of goods, that’s not going to be worth it for the scammer.

Information based goods like access to website or downloads are non-fencible. Nobody is going to be able to make a living off stealing access to websites or downloads. They can go to the file sharing networks to steal that. Most instant-access products aren’t going to have a huge incentive to steal.

If a merchant actually has a problem with theft, they can make the customer wait 2 minutes, or wait for something in e-mail, which many already do. If they really want to optimize, and it's a  large download, they could cancel the download in the middle if the transaction comes back double-spent. If it's website access, typically it wouldn't be a big deal to let the customer have access for 5 minutes and then cut off access if it's rejected. Many such sites have a free trial anyway.

I would be surprised if 10 years from now we're not using electronic currency in some way, now that we know a way to do it that won't inevitably get dumbed down when the trusted third party gets cold feet.

It could get started in a narrow niche like reward points, donation tokens, currency for a game or micropayments for adult sites. Initially it can be used in proof-of-work applications for services that could almost be free but not quite.

It can already be used for pay-to-send e-mail. The send dialog is resizeable and you can enter as long of a message as you like. It's sent directly when it connects. The recipient doubleclicks on the transaction to see the full message. If someone famous is getting more e-mail than they can read, but would still like to have a way for fans to contact them, they could set up Bitcoin and give out the IP address on their website. "Send X bitcoins to my priority hotline at this IP and I'll read the message personally."

Subscription sites that need some extra proof-of-work for their free trial so it doesn’t cannibalize subscriptions could charge bitcoins for the trial.

It might make sense just to get some in case it catches on. If enough people think the same way, that becomes a self fulfilling prophecy. Once it gets bootstrapped, there are so many applications if you could effortlessly pay a few cents to a website as easily as dropping coins in a vending machine.


- Cryptography Mailing List



Fees


Nodes will eventually be compensated by transaction fees alone when the total coins created hits the pre-determined ceiling.


- Cryptography Mailing List



When that [block reward] runs out, the system can support transaction fees if needed. It's based on open market competition, and there will probably always be nodes willing to process transactions for free.


- Cryptography Mailing List



Government

Governments are good at cutting off the heads of a centrally controlled networks like Napster, but pure P2P networks like Gnutella and Tor seem to be holding their own.


- Cryptography Mailing List


It's very attractive to the libertarian viewpoint if we can explain it properly.


- Cryptography Mailing List


Governance

The CPU power proof-of-work vote must have the final say. The only way for everyone to stay on the same page is to believe that the longest chain is always the valid one, no matter what.


- Cryptography Mailing List



The proof-of-work chain is itself self-evident proof that it came from the globally shared view. Only the majority of the network together has enough CPU power to generate such a difficult chain of proof-of-work. Any user, upon receiving the proof-of-work chain, can see what the majority of the network has approved. Once a transaction is hashed into a link that's a few links back in the chain, it is firmly etched into the global history.


- Cryptography Mailing List



Incentives

Even if a bad guy does overpower the network, it's not like he's instantly rich. All he can accomplish is to take back money he himself spent, like bouncing a check. To exploit it, he would have to buy something from a merchant, wait till it ships, then overpower the network and try to take his money back. I don't think he could make as much money trying to pull a carding scheme like that as he could by generating bitcoins. With a zombie farm that big, he could generate more bitcoins than everyone else combined.

The Bitcoin network might actually reduce spam by diverting zombie farms to generating bitcoins instead.


- Cryptography Mailing List



The incentive value when a node finds a proof-of-work for a block could be the total of the fees in the block.


- Cryptography Mailing List




With the transaction fee based incentive system… nodes would have an incentive to include all the paying transactions they receive.


- Cryptography Mailing List




Would be cheaters can try and simultaneously double-spend all they want, and all they accomplish is that within a few blocks, one of the spends becomes valid and the others become invalid.


- Cryptography Mailing List




There will be transaction fees, so nodes will have an incentive to receive and include all the transactions they can.


- Cryptography Mailing List




Bitcoin is at its most vulnerable in the beginning when the total network CPU power is small.  That's offset by the fact that the incentive to attack it is also low when it's small.

- Dustin Trammel Emails



Inflation

As computers get faster and the total computing power applied to creating bitcoins increases, the difficulty increases proportionally to keep the total new production constant. Thus, it is known in advance how many new bitcoins will be created every year in the future.


- Cryptography Mailing List



Total circulation will be 21,000,000 coins. It'll be distributed to network nodes when they make blocks, with the amount cut in half every 4 years.


- Cryptography Mailing List


Escape the arbitrary inflation risk of centrally managed currencies! Bitcoin's total circulation is limited to 21 million coins.

- [bitcoin-list]


Network Nodes

Long before the network gets anywhere near as large as that, it would be safe for users to use Simplified Payment Verification to check for double spending, which only requires having the chain of block headers, or about 12KB per day. Only people trying to create new coins would need to run network nodes. At first, most users would run network nodes, but as the network grows beyond a certain point, it would be left more and more to specialists with server farms of specialized hardware. A server farm would only need to have one node on the network and the rest of the LAN connects with that one node.


- Cryptography Mailing List




I made the proof-of-work difficulty ridiculously easy to start with, so for a little while in the beginning a typical PC will be able to generate coins in just a few hours. It'll get a lot harder when competition makes the automatic adjustment drive up the difficulty.


- Cryptography Mailing List





Privacy

A bit of privacy may be lost if [an] address is used multiple times, but it is a useful alternative if both users can’t be online at the same time or the recipient can't receive incoming connections.


- Cryptography Mailing List



Pseudonymity 

It's not pseudonymous in the sense of nyms identifying people, but it is at least a little pseudonymous in that the next action on a coin can be identified as being from the owner of that coin.


- Cryptography Mailing List



Satoshi

I actually did this kind of backwards. I had to write all the code before I could convince myself that I could solve every problem, then I wrote the paper.


- Cryptography Mailing List




I'm better with code than with words…


- Cryptography Mailing List



I believe I've worked through all [the] little details over the last year and a half while coding it, and there were a lot of them.

- Cryptography Mailing List


Scaling

The bandwidth might not be as prohibitive as you think. A typical transaction would be about 400 bytes (ECC is nicely compact). Each transaction has to be broadcast twice, so lets say 1KB per transaction. Visa processed 37 billion transactions in FY2008, or an average of 100 million transactions per day. That many transactions would take 100GB of bandwidth, or the size of 12 DVD or 2 HD quality movies, or about $18 worth of bandwidth at current prices.


If the network were to get that big, it would take several years, and by then, sending 2 HD movies over the Internet would probably not seem like a big deal.


- Cryptography Mailing List




Spam

Another factor that would mitigate spam if POW tokens have value: there would be a profit motive for people to set up massive quantities of fake e-mail accounts to harvest POW tokens from spam. They'd essentially be reverse-spamming the spammers with automated mailboxes that collect their POW and don't read the message. The ratio of fake mailboxes to real people could become too high for spam to be cost effective.

The process has the potential to establish the POW token's value in the first place, since spammers that don't have a botnet could buy tokens from harvesters. While the buying back would temporarily let more spam through, it would only hasten the self-defeating cycle leading to too many harvesters exploiting the spammers.

Interestingly, one of the e-gold systems already has a form of spam called "dusting". Spammers send a tiny amount of gold dust in order to put a spam message in the transaction's comment field. If the system let users configure the minimum payment they’re willing to receive, or at least the minimum that can have a message with it, users could set how much they're willing to get paid to receive spam.


- Cryptography Mailing List




Value

Hal sort of alluded to the possibility that [Bitcoin] could be seen as a long-odds investment. 

- Dustin Trammel Emails
