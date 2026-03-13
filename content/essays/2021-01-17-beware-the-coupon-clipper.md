---
title: "Beware the Coupon Clipper: The Insurmountable Flaws of so-called Algorithmic Stablecoins"
date: 2021-01-17
hidden: false
---
***TL;DR\: “Coupon coins” peg their exchange rates by minting coins when their price is above the peg, and issuing interest-bearing coupons when below. Because these protocols cannot force a permanent reduction in coin supply, once demand growth flatlines the protocol itself creates and magnifies instability, causing the price to oscillate wildly and the peg to break.***
***Coupon coins borrow the language of central bank open market operations, which is grossly misleading. Not only do regulations treat government debt as a "safe asset," central banks nonetheless opt for exchange rate intervention or capital controls to enforce a peg.***

***Note\: I originally wrote this essay in November of 2020. I thank Evan Kuo and Jason C. for wading through a much longer and much worse draft. The more technical aspects have been placed in an appendix [here](thinking.farm/essays/2021-01-17-beware-the-coupon-clipper-technical).*** 

## Introduction
Resemblance is not identity. Just because something claims to look like a central bank does not mean it works like a central bank. In the world of crypto—and really, in life—there is no such thing as proof by analogy, only hints and suggestions.[^1] “Coupon coins,” often called “algorithmic stablecoins” or “bond tokens,” are a family of protocols for creating fiat tokens whose price remains pegged to another currency. Inspired by central bank open market operations (OMO), these protocols issue more coins when the price is above their peg, and create yield-bearing coupons (or “bonds”) to soak up supply when the price falls below the peg. Examples include [Basis](basis.io), [Empty Set Dollar](www.emptyset.finance) (ESD), and their clones, which as of today have a combined [market capitalization](https://www.coingecko.com/en/stablecoins) of about $500 MN. 

[^1]: Analogical reason has a long history—Plato’s *Republic* is an example of the technique, where he makes an argument through the analogy of the human soul and a city state. For a summary of the topic, see: Paul Bartha. "Analogy and Analogical Reasoning", *The Stanford Encyclopedia of Philosophy* (Winter 2016 Edition), Edward N. Zalta (ed.).

In the context of decentralized finance (DeFi), such protocols have proven precarious and unstable. Coupon coin promoters argue that the problem is either one of scale or collective faith; i.e. if the coin captures a sufficiently big market capitalization, or if enough speculators believe that coin demand will increase, then the market for coupons, and thus the coin’s peg, will not fail.

Naturally, I disagree. The argument advanced here is simple. Coupon coin protocols have no way to force a permanent reduction in coin supply—coupon purchases are voluntary, and coins are removed from supply only until the coupons are redeemed. This anchors the coin supply to the all-time highest market capitalization. To make matters worse, these temporary supply reductions are bought with “yield,” which requires inflating the coin supply in the future. I conclude the essay by examining why despite some resemblance, OMO is used by central banks but cannot work to peg exchange rates in DeFi. 

## Coupon design space: four “pure” cases

Now, one could argue that things are more complex—coupons could expire, and they can be redeemed in different ways. I have labeled four design permutations the table below, created through two choices. The first choice is whether coupons redeem after a fixed period of time, or whether they are paid out of supply expansions. The second choice is whether coupons expire or not. There are various in-between options for each choice—e.g. a coupon whose yield declines the longer it is in a queue—but they do not change our analysis.

|   |**Coupons do not expire**  | **Coupons expire**
|----|----|----|
| **Coupons redeemed at maturity**| ***Case I*** | ***Case III (does not exist)***
| **Coupons redeemed by supply expansions**|    ***Case II*** | ***Case IV***

So let us consider these four cases in turn. For those more curious I have outlined three short inductive demonstrations as a [technical appendix](thinking.farm/essays/2021-01-17-beware-the-coupon-clipper-technical) to this essay. 

### Case I
The simplest case is one where coupons do not expire, and they redeem after a fixed period of time. Assume, for the moment, that speculation triggered an overproduction of a coupon coin called, simply, “coin,” and that its price \\(\\ p_1\\)has fallen below the peg of \\(\\ p_0\\). The protocol will issue a coupon to remove a certain number of coin, call it \\(\\ s_1\\). Speculators will buy \\(\\ s_1\\) of coin to purchase the coupons, and the price is restored to \\(\\ p_0\\). But after a certain amount of time, the coupons are redeemed, along with yield. So the speculators receive a certain amount of coin covering the original amount bought plus an interest rate, \\(\\ s_2 = s_1 * (1 + r)\\). Assuming a healthy, steady state level of activity, this means that demand for coin has not increased. So when speculators try to realize profits, the new price is lower than the last. So after selling \\(\\ s_2\\), we now have \\(\\ p_2 < p_1 < p_0 \\). In general, \\(\\ p_0 > p_1 > … > p_n \\). In short, the price will oscillate, falling further and further below the peg, as can be seen below.

{{< figure src="/2021-01-17-beware-the-coupon-clipper/case1.jpeg" title="Ever-widening oscillation when coupons redeem after a fixed period of time." width="100%" >}}

### Case II
Let us consider now Case II, where coupons do not expire but are only paid out of supply expansions, which occur when the price is above the peg. There are two scenarios to consider—one where we have an unlimited number of speculators, each with finite capital, and one where we have some speculators with nearly unlimited capital (colloquially known as whales.) 

Under the first scenario, no speculator will buy a coupon if they believe demand for the coin will remain stable. They will only buy a coupon if they think there is a good chance that demand will increase enough not only to cover the original amount of the coupon \\(\\ s_1\\) but also its yield. Raising the interest rate \\(\\ r\\) helps but not by much—a high interest rate is a type of call option on tail scenarios where demand spikes far above expectations. The value of these options is bolstered if yield is paid out as it is minted. Still, their ex ante value is low given the low probability of such an event. 

Under the second scenario, a single speculator has enough capital to raise the price far enough above the peg to fully redeem his coupons. As before, because \\(\\ s_2 > s_1 \\), this means that when the speculator sells \\(\\ s_2\\), then \\(\\ p_2 < p_1 \\). As long as the speculator has enough capital to engage in this cycle, they will be able to ***profit at the expense of liquidity providers.***  Again we have a situation where \\(\\ p_0 > p_1 >… > p_n\\). More interestingly, the speculator will deploy increasingly larger amounts of capital as with each new cycle he needs to drive demand higher. Why? Because to restore the peg, the protocol will now issue ever larger coupons worth \\(\\ s_{n+1} = s_n * (1+r)\\). So the coin price will also reach increasingly higher intermediate levels, \\(\\ p^*_0 < p^*_1 < … < p^*_n \\). This will produce a price pattern that looks like the below.

{{< figure src="/2021-01-17-beware-the-coupon-clipper/case2.jpeg" title="Ever-widening oscillation when coupons are paid out from supply expansions." width="100%" >}}

### Cases III & IV

Case III is where coupons have fixed maturity dates, but they also expire. I do not think that this is a useful case—who would ever buy a coupon that expires before its maturity date? So let us move on to Case IV, where coupons expire and are paid out of supply expansions. This changes the dynamics of Case II, but not by much. If speculators have limited capital, they will be *less* not *more* likely to buy coupons. Without expiration a speculator might have thought they were purchasing a perpetual option on a tail scenario where demand for the coin spikes. With expiration, speculators will need to be certain that future demand is forthcoming, or they will risk realizing a loss. It does not change the dynamics in regards to large whales, as they are still redeeming their coupons before expiration.

## The protocol itself creates instability
As we can see, no matter the coupon design, the coupon coin protocol cannot stabilize the coin price even when demand for the coin is stable. ***In fact, the protocol itself is the source of instability!*** The coin price will oscillate more wildly as coupons are issued in ever larger amounts due to the need to pay interest. And the longer and further the price is from the peg, the less likely speculators are to buy the next coupon round, thereby increasing the chance that the peg breaks for good. We can conclude that the peg is only sustainable if demand is monotonically increasing, which is unrealistic. One way to mitigate this issue would be to only create coupons or coins if the price is something like 10% below or above the peg. But this only highlights the fact that the protocol itself is the problem. 

{{< figure src="/2021-01-14-stablecoin-by-any-other-name/risk-loss-full.jpeg" title="Unlike true stablecoins or regular speculative assets, coupon coins promise losses but no gains." width="100%" >}}

This inherent instability is augmented by feedback loops. Coin holders have no probability of gain, since minted coins go to coupon owners. But holders retain a probability of loss, since the peg will eventually break once demand flatlines. Thus, holders—who are the *core* users of a supposed “stablecoin”—will dump their coins, depressing prices and increasing the chance that the peg breaks. At the same time, liquidity providers on automated market makers will realize that they are the ones paying for speculator profits, and will withdraw liquidity from the protocol.

## Not everything with wings can fly
Why is it that central banks use open market operations (OMO), then? One reason is because OMOs are backstopped by sovereign authority. Regulation labels government debt as a “safe asset,” which lets some institutions treat them as “risk-free” and take risks elsewhere with their portfolios—even if these assets are not in fact always low-risk. Regulated financial institutions thus act as “buyers of last resort.”[^2] Anna Gelpern and Erick Gerding succintly summarize the matter:

>Precisely because there are no risk-free contracts, state intervention
supplies the essential infrastructure to let people act as if some contracts were
risk-free. The law constructs and maintains safe asset fictions, and it places
them at the foundation of institutions and markets. This project is unavoidably
distributive and fraught with distortions.

In the case of the US, the dollar’s role as a reserve currency encouraged demand for dollar safe assets.[^4] Despite a declining US share of world GDP, self-reinforcing trade-settlement network effects, banking sector dollarization, and other forms of historical path dependence sustain this demand of dollar safe assets in what is sometimes called "dominant currency paradigm".[^5]

This relationship is also not entirely straightforward, however. Before the 2008 financial crisis, many financial institutions preferred to hold yield-bearing "safe-assets" instead of non-yielding cash. However, the Federal Reserve has since decided to pay 25 bps of interest on bank reserves, which lowered the opportunity cost of holding reserves. This created an ocean of cash. Total reserves in US depository institutions had been about $44 BN on January 1, 2000. By December 1, 2020, this number was 71 times larger at $3,145 BN. 

{{< figure src="/2021-01-17-beware-the-coupon-clipper/reserves.png" title="Excess banking reserves have reached astronomical levels since 2008. Data source: Federal Reserve Board." width="100%" >}}


This massive increase in excess reserves has been matched by growth in the Fed’s balance sheet, as it purchased a large number of assets—particularly Treasury bills—from banks.[^3] 

{{< figure src="/2021-01-17-beware-the-coupon-clipper/balance_sheet2.png" title="The growth in reserves has been matched by growth in the Fed’s Balance sheet. Source: Federal Reserve Board." width="100%" >}}


This highlights the second peculiarity of OMO—they are used primarily to anchor interest rates and modulate credit levels in the domestic economy. To peg exchange rates, governments prefer to intervene directly in exchange markets or to enact capital controls.

[^2]: Anna Gelpern and Erik F. Gerding. "Inside Safe Assets," *Yale Journal on Regulation*, Vol. 33, 2016: 363-421. They outline three ways in which the law helps create safe assets: 1) Making: that is, regulating institutions to take less risk and create safer instruments. 2) Labeling: allowing institutions to treat some assets “as if” they were risk-free 3) Guaranteeing: committing social resources to mitigate losses on otherwise risky assets
[^3]: Ben R. Craig and Matthew Koepke. “Excess Reserves: Oceans of Cash,” *Economic Commentary,* February 12, 2015.
[^4]: A good place to start understanding the uniqueness of the US dollar--and its deficiencies as a model for private money creation--is: Barry Eichengreen. *Exorbitant Privilege: The Rise and Fall of the Dollar and the Future of the International Monetary System.* Oxford: Oxford University Press, 2011.
[^5]: Gita Gopinath, Emine Boz, Camila Casas, Federico Diez, Pierre-Olivier Gourinchas, and Mikkel Plagborg-Moller. 2020. "Dominant Currency Paradigm." *American Economic Review*, 110 (3): 677-719.

Coupon coin protocols, in contrast to central banks, are institutionally naked. They function more like speculative, low-grade corporate debt than government-issued “safe assets.” To look at state-backed open market operations and think that such a mechanism is the right way to build private money is akin to looking at a bird and thinking that humans can fly by flapping their arms with wings attached.

  {{< figure src="/2020-12-29-designing-money/managed.jpeg" title="Seen through the functional trilemma, coupon coins are a type of fiat token with a managed peg, which is an unstable combination of properties. The peg eventually breaks." width="100%" >}}

As I argued in ["A Functional Trilemma,”](http://thinking.farm/essays/2020-12-29-designing-money/_) pegging a fiat currency is a costly endeavor.  Some societies have chosen to pay the price, yet even with national resources at their disposal these efforts sometimes fail. These costs are sometimes justified, for example if in service of an export-led industrialization drive to raise long-term living standards. But no such rationale exists in the case of DeFi. For whom and for what are we working so hard to create a peg? 

## Conclusion
Any reduction in demand will expose a permanent supply overhang that either produces endless price oscillations, or a break from the peg. Coupon coin protocols can survive price fluctuations which the market perceives to be small and temporary. But the peg becomes more fragile the further and longer the coin’s price falls below the peg. In fact, the protocol itself is the source of price instability even under conditions of stable demand. 

It is implausible that a coupon coin will not experience a reduction in demand—even Bitcoin, which is the largest in the asset class, has experienced drops in value over 80% that last for months or years. Thus, when, not if, demand for a coupon coin falls, the design will fail as a stable coin solution. In the end, not everything with wings can fly. Not everything claiming to be an “algorithmic central bank” is a viable means of making money.


