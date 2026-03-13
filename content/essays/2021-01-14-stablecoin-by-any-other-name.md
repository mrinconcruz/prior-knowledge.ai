---
hidden: true
title: "A Stablecoin by Any Other Name: Value, Risk, Loss, and Gain"
date: 2021-01-26T15:50:17-07:00
---
hidden: true
***TL;DR\: Journalists and analysts have not proposed a coherent logical definition of the word stablecoin, as evidenced by their inability to reliably identify stablecoin projects. The confusion is strongest when it comes to discussions of “algorithmic stablecoins,” and arises when commentators use “stablecoin” both as a historical name for specific projects and as a logical descriptive definition for a special class of tokens.***

***To clarify this confusion, I provide a well-founded description of value as “value in terms of a measurement unit,” which then allows me to classify all digital assets by their risk of loss, or the probability of realizing a decrease in value, and risk of gain, or the probability of realizing an increase in value. This allows us to precisely and descriptively define stablecoins—assets where \\(\\ p(gain)=p(loss)=0\\) . Using this definition, it is clear that today’s “algorithmic stablecoins” by design have no risk of gain but retain a risk of loss. Yikes! It is also clear that Ampleforth is like Bitcoin or Ethereum—it has a risk of gain and a risk of loss.***

*Note: Thanks to Noah Jessop, Christopher Chow, Michael Schmatz, and Evan Kuo for providing comments and feedback. An abridged version of this essay as published earlier on CoinTelegraph.*


{{% epigraph %}}
'Tis but thy name that is my enemy;
Thou art thyself, though not a Montague.
What's Montague? It is nor hand, nor foot,
Nor arm, nor face, nor any other part
Belonging to a man. O, be some other name!
What's in a name? That which we call a rose
By any other name would smell as sweet;
So Romeo would, were he not Romeo call'd,
Retain that dear perfection which he owes
Without that title. Romeo, doff thy name,
And for that name which is no part of thee
Take all myself. 

*– Juliet[^1]*
{{% /epigraph %}}

[^1]: Romeo and Juliet, Act 2, Scene 2. http://shakespeare.mit.edu/romeo_juliet/romeo_juliet.2.2.html

## Introduction to the problem
We are so early in the crypto revolution that we still suffer from confusions in naming and definition. Saul Kripke argued in his famous 1970s lectures that proper names are rigid designators that pick out the same object or person in all possible worlds where they exist.[^2] He was arguing against a view advanced by Bertrand Russell and others that treated names as abbreviated descriptions or definitions.[^3] One of his main contentions is that descriptions very rarely specify the object that speakers refer to. So while Russell might have thought that when he said “Nixon” he really meant “the man who won the 1960 presidential election,” when Kripke said “Nixon” he meant Nixon the person, even in those counterfactual situations (aka possible worlds) where Nixon never ran for office. The core difference is whether one takes a historical or a logical approach to naming. In other words, Kripke’s rose by any other name smells just as sweet. It simply refers to this specific type of flower here, which some community baptized with the name in the distant past. Russell’s rose also smells just as sweet because the name logically refers to any sweet smelling flower of similar looks, even if it belongs to a different species, like a Lisianthus or Camelia.
[^2]: Saul Kripke. *Naming and Necessity.* Cambridge: Harvard University Press, 1980. The original lectures were given at Princeton, starting on January 20, 1970. 
[^3]: The most famous essay on this matter is Bertrand Russell. “On Denoting,” *Mind*. Oxford: Oxford University Press, 1905. 479–493.

{{< figure src="/2021-01-14-stablecoin-by-any-other-name/rose.jpeg" title="Kripkean or Russellian roses? Flowers from the families Rosaceae and Gentianaceae." width="100%" >}}

Sometimes, “stablecoins” and variants like “algorithmic stablecoins” function like historical names—they refer to projects that call themselves stablecoins, like Basis Cash, Elastic Set Dollar, FRAX, and their clones. Sometimes, “stablecoin” is used as a logical [description]( https://decrypt.co/resources/stablecoins) for “a cryptocurrency designed to have low price volatility” or currencies that are “stores of value or units of account,” or “[a new type of cryptocurrency](https://cointelegraph.com/explained/stablecoins-explained) that often have their value pegged to another asset… designed to tackle the inherent volatility seen in cryptocurrency prices,” or a [currency](https://www.investopedia.com/terms/s/stablecoin.asp) that can “act as a medium of monetary exchange and a mode of storage of monetary value, and its value should remain relatively stable over longer time horizons”. On the more metaphysically speculative end, some [writers](https://haseebq.com/stablecoins-designing-a-price-stable-cryptocurrency/) have defined a stablecoin as “an asset that prices itself, rather than an asset that is priced by supply and demand. This goes against everything we know about how markets work.”

  {{< figure src="/2021-01-14-stablecoin-by-any-other-name/hasseb.png" title="Hasseb Qureshi's classifcation of stablecoins (www.hassebq.com)." width="100%" >}}


Circularity is the core issue, as I see it. The alleged deficiency of Bitcoin as money and a vague definition originally inspired a host of stablecoin projects. Design features of these projects have now in turn been incorporated back into the stablecoin definition. Commentators and analysts since have struggled to reconcile the conceptual morass. 

For example, Hasseb Qureshi defines a stablecoin as simply a price peg. Yet, it is not obvious that anything with a peg should bear the name of stablecoin. Ampleforth has a “peg” and journalists call it a stablecoin. The founding team routinely clarifies that it is no such thing. Who is right? Another example, just what exactly is “stable” in a stablecoin—the peg or its value? Wrapped Bitcoin (wBTC) is perfectly pegged to Bitcoin—one wBTC will always be one BTC. Is that a stablecoin? According to the original motivations for creating stablecoins in the first place, BTC is not a stable means of exchange, even though Bitcoin is the canonical “store of value” asset.

Having clarified the problem—that no one knows how to define or recognize a stablecoin—the rest of this essay outlines a solution. It provides a well-defined description of value as a relational property, namely, “value in terms of a measurement unit.” Using this description, I then comprehensive classify all digital assets along two dimensions—risk of loss, or the probability of realizing a decrease in value, and risk of gain, or the probability of realizing an increase in value. We can then precisely and logically define stablecoins—assets where the risk of loss and risk of gain are both zero. That is, \\(\\ p(gain)=p(loss)=0\\). I call this a risk-defined stablecoin. 

It is clear that today’s “algorithmic stablecoins” have risk of loss but no risk of gain. Thus, not only are they not stablecoins, they are terrible financial assets. I finish by considering whether it makes sense to expand the concept of risk-defined stablecoin to a more general concept centered on expected value; an expected-value stablecoin is one where the probabilities of loss and gain, weighed by the magnitude of loss and gain, are perfectly offset and net out to zero. I conclude that the complexity and ergodicity of such a concept rules it out as a useful stablecoin definition.

## What is value? 

What “value” means is not entirely clear, as evidenced by continuing debates about the “true” rate of inflation. One way to clarify the issue is to ask “value in terms of what?” That is, we decide to treat value as a relational property between the object being measured, and the thing doing the measuring. It is like asking for height—do you want it in inches or centimeters? For our purposes, can we define a function that maps an *asset* to a set of number values in a chosen *unit*. Call it Value. For example, if the chosen unit is the US dollar, and the item is a bag of chips, \\(\\ Value_{USD}(chips)=$5\\). We could just as well have written \\(\\ Height_{inches}(table)=35in\\).

## Risk of loss, risk of gain

Yet, as we all know, the value of an asset changes over time. Thus, we can expand our Value function to reflect the idea of “the value of an asset, in terms of a unit, at a certain time.” We can do this easily by adding the time \\(\\t\\) at which we are measuring value, \\(\\ Value_{unit}^t(asset)=x\\) .
We can now think about the risk of loss or the risk of gain of an asset. Conditional on your owning the asset, we can define these risks as the probability that, at a randomly chosen time in the future, the Value function would show a decrease or increase in value. In practical terms, this means that if I convert the asset into my chosen unit, I would realize a loss or a gain. 

## A risk-defined stablecoin

We now have enough to create a well-defined description for “stablecoin.” A stablecoin is an asset where the risk of loss and the risk of gain are both zero. That is, \\(\\ p(gain)=p(loss)=0 \\). In practical terms, this means that if I sell the stablecoin asset in the future, I will neither experience a loss or gain in value, as measured in my chosen unit.

{{< figure src="/2021-01-14-stablecoin-by-any-other-name/bcg.jpeg" title="The Boston Consulting Group’s famous matrix, invented by the group's founder, Bruce Henderson, in the 1970s." width="100%" >}}

This reminded me of the classic, well-known Boston Consulting Group growth-share matrix for assessing products lines, which I have reproduced here. With some rearrangement, we can repurpose it to classify all digital assets by their risk of loss and risk of gain. The four categories are still stars, dogs, unknowns, and cash cows. 

{{< figure src="/2021-01-14-stablecoin-by-any-other-name/risk-loss-empty.jpeg" title="A gain-loss matrix for assessing digital assets." width="100%" >}}


A star investment, with no risk of loss but a risk of gain, are rare in the present but abundant in hindsight, such as when one regrets selling Bitcoin back in 2010. Stars also exist in the imagination. Such was the case with the investors in Bernie Madoff’s fund. But those investments quickly reveal themselves to be dogs. Dogs are sure losers—there is no risk of gain, but if you hold them long enough the risk of loss becomes an actual loss. Owning a house in hurricane-prone areas is an example. Gambling in Vegas is another.

{{< figure src="/2021-01-14-stablecoin-by-any-other-name/star.png" title="Star investments are most abundant in hindsight, when we can no longer buy them." width="100%" >}}


Unknowns are your regular investments, you could be up or down in terms of value, depending on the day. Most digital assets, even Bitcoin, fall into this category. Lastly, cash cows are investments that have minimal risk of loss or gain. They are dependable. We can now take those projects that journalists have named “stablecoins” and see which ones fit the bill.

{{< figure src="/2021-01-14-stablecoin-by-any-other-name/risk-loss-full.jpeg" title="Putting major digital assets and “stablecoins” into the gain-loss matrix." width="100%" >}}

One lesson here is that when we talk about “a rose by any other name,” we really have to clarify whether we mean this specific plant right here, or any flower that smells just as sweet. As should be obvious, not one of the projects called “algorithmic stablecoins” smells sweet at all! They are stablecoins in name only. Because of their multiple token design, they have no risk of gain—as all new supply is given to investors—but holders retain a risk of loss. Yikes.

Another lesson is that a price peg is not enough. Journalists erroneously label Ampleforth a stablecoin, even though it is obvious that owning AMPL carries a risk of gain and a risk of loss. The expected value of owning the asset could be positive or negative, but it is definitely not zero. Another lesson is that it is important to specify a unit when discussing value. If our measurement unit is the US dollar, then wBTC is not a stablecoin. But if we are defining value in terms of BTC, then wBTC is a the perfect stablecoin!

Lastly, risk assessment is hard! I’ve received pushback about classifying Tether as a “stablecoin” given its counter-party risk. More than a few friends fear the company might have its funds frozen by governments again, or might suffer a massive hack. These are all valid points. Except under extraordinary circumstances, no stablecoin is truly free of the risk of loss. Perhaps Tether is a cross between a dog and a cow.

Nonetheless, it should be clear that certain projects egregiously appropriate the term “stablecoin” in a bid to grant investors a risk of gain while saddling holders with a risk of loss. Since no sane person would hold these assets on their books, however, it is almost certain that these dogs will go extinct.

## An expected-value stablecoin?

Astute readers will have noticed that expected value is not just a function of the probability of loss and gain—the magnitude of losses and magnitude of gains is just as important. For example, assume I have a fair die. If I roll a 6 I win $60. If I roll any other number I lose $6. The expected value of rolling the die is, \\(\\ EV(dice)=$60\*p(gain)-$6\*p(loss) \\)
\\(\\ =$60\*(1/6)-$6\*(5/6)=$5 \\)

The natural question is, can we expand the concept of a risk-defined stablecoin into that of an expected-value stablecoin? In other words, would it suffice for the expected value of holding an asset to be zero? Using the die example above, this condition would be met if I won only $30 instead of $60. So any time I try to convert this DieCoin into USD, there is a 5/6 chance I will realize a loss in value, and a 1/6 chance I will realize a gain. But because the gain is so much larger than the loss, these cancel out.

I think this could be a clever approach that can be realized through a set of derivative contracts. However, it would lose the property of allowing holders to exit their position with minimal impact to their portfolios. This should remind us that, ultimately, definitions are artifacts of a community of speakers. And I find it doubtful that more than a few people will find an expected value definition persuasive.

## Conclusion

It is a sign of how young our industry is that commentators routinely fail to provide a coherent descriptive definition of stablecoin. Rather than use “stablecoin” as a historical name for a set of existing projects, instead I have endeavored to provide a precise, logical definition of the term. I began with an account of “value in terms of a measurement unit”, and used it to classify digital assets into a two-by-two gain-loss matrix. I then argued that we are best served by using descriptively defining “stablecoin” as any asset where the risk of gain or loss are exactly zero, that is, where \\(\\ p(gain)=p(loss)=0\\) 

According to this schema, and if we believe the custodial risk is minimal, we can conclude that USD Coin, Diem, and Tether are stablecoins. We can also conclude that any system with multiple tokens, such as Basis Cash, Elastic Set Dollar, and FRAX, give their holders a risk of loss but no risk of gain. Although calling themselves stablecoins, it turns out “algorithmic stablecoins” by any other name would not smell as sweet. They would smell like dog.

