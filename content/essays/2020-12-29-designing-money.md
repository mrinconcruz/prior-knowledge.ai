---
title: "Designing Money: A Functional Trilemma for the Digital Age"
date: 2020-12-29T15:50:17-07:00
---
***TL;DR\: We need a new way to understand money—instead of discussing what money is we are best served by clarifying what money does. I propose a trilemma of functions that money can support\:***
-	***adaptive supply***
-	***durable value***
-	***stable peg***

***Fiat moneys support adaptive supply and value durability—these are good media of exchange. Collateral moneys support value durability and peg stability—these are good stores of value. Rebasing moneys support adaptive supply and peg stability—these are good units of account.*** 

***Moneys that try to support all three functions are fragile and inevitably break, reverting to their most stable configurations. Fiat moneys with managed exchange rates eventually revert to pure fiat and give up peg stability, often through painful devaluations. Collateral moneys with fractional reserves eventually revert to full collateralization and give up adaptive supply, shrinking the money supply in circulation, often trigerring financial panics and crises.***

***More importantly, this fragility remains regardless of the size of the money supply—it cannot be eliminated by “bootstrapping” or “growing” out of it.***

## Introduction
It is time to do away with the conventional economists’ definition of money as a unit of account, store of value, and medium of exchange. For one, it is a definition derived from myths about the origins of money, positing a progression from barter and the problem of coincidence of wants, to free trade and precious metals. More importantly, the definition is useless when it comes to designing money, leading to endless debates about what counts as money, not how it could be made. 

## A new typology—the functional trilemma
I believe it is time to focus less on what money **is** and more on what money **does**. Thus, I propose a new typology based on a trilemma of three functions that money can support—adaptive supply, durable value, and a stable peg. In the long-run, each money can only support two of these functions. Those that try to support all three will inevitably revert back to their most robust two-function configuration, like how a rubber band stretched over three pegs might slip to just two. 

We can derive the traditional economics definition and classify historical monetary systems just by combining these three functions. More importantly, the functional trilemma is a map to the design limitations of digital money, and highlights the fragility that will break the newest generation of “stablecoin” protocols, which try to do too much.

 {{< figure src="/2020-12-29-designing-money/trilemma.jpeg" width="100%" >}}


Let us define these three functions in more detail. By adaptive supply, I mean that supply is a function of demand: \\(\\ S=f(D) \\). By durable value I mean that the purchasing power of a money stock stays constant across time:\\(\\ v_t (S) = v_{t+n} (S) \\). By stable peg I mean that the measured purchasing power of a single money unit stays constant across time: \\(\\ v_t (unit) = v_{t+n} (unit) \\).

## Fiat, collateral, and rebasing moneys
 
  {{< figure src="/2020-12-29-designing-money/fiat.jpeg" width="100%" >}}


Let’s flesh out the trilemma with three robust classes of money designs—fiat, collateral, and rebasing moneys. We can represent them with some examples from traditional and digital finance:the US dollar (USD), USD Coin (USDC) , and Ampleforth (Ample/AMPL). 

Fiat moneys are the easiest to understand: 1) their supply is modulated by the authorities to meet demand, and 2) the purchasing power of the total stock of money, in the long run, is stable over time. Monetary policy, for the most part, produces changes in consumer or asset price levels, as well as a redistribution of resources, but cannot change the long-run level of economic activity. For these reasons, pure fiat currencies have free floating exchange rates--that is, they cannot support a stable peg.
 
 {{< figure src="/2020-12-29-designing-money/collateral.jpeg" width="100%" >}}

Collateral moneys like USDC or currency boards with convertibility (also called redeemability) have 1) a stable peg, since convertibility into the reserve assets anchors the price, and 2) durable value, since each unit is backed by an exact quantity of the reserve asset, and is constant across time. In the case of USDC, each coin is backed by exactly one USD. Collateral moneys are the quintessential “stores of value”—many emerging market residents prefer that their national currency have a hard peg, as it guarantees that their savings and investments can retain their value over time, instead of suffering from inflation and devaluation. 

Collateral moneys do not have adaptive supply, however. They can only mint or redeem money according to the amount of assets in their reserves. In a true specie standard, this was determined by the supply of gold or silver. In the age of the dollar, the reserves are held in dollars or other qualifying foreign exchange, like yen or Euro. In the case of USDC, the supply is a strict function of the amount of USD locked into custodian institutions, the same is true of wrapped Bitcoin (wBTC). Neither USDC or wBTC supply are functions of market demand for USDC or wBTC.
 
  {{< figure src="/2020-12-29-designing-money/rebasing.jpeg" width="100%" >}}

Lastly, consider what it would mean for a money to have both adaptive supply and a stable peg—this combination is the trickiest one of them all, because it is so unintuitive, and historically rare. These are rebasing moneys.

  {{< figure src="/2020-12-29-designing-money/ampl-illustration.jpg" title="Illustration of automatically changing AMPL balances over time (Ampleforth.org)" width="100%" >}}

The Ampleforth protocol adjusts the balances in owners' wallets--this is a process called rebasing. When demand for Amples is high, the number of AMPL in wallets increases, and when demand is low, the number of AMPL decreases--so I might have 1 AMPL today, 3 tomorrow, and 2 the day after. Physically, this system is impossible to recreate, though Nobel Prize-winning economist James Buchanan dreamed of such an automatically adjusting digital money in the late 1950s. He imagined it would be run out of a massive mainframe, to which the keys to change its code had been destroyed, making it tamper-proof.

So far 1) the purchasing power of a single AMPL has remained more or less equal to the 2019 USD (when it was launched), and 2) the AMPL supply is responsive to demand. However, the purchasing power of the AMPL money stock has not remained constant—it has risen and fallen, sometimes by more than an order of magnitude!

From a historical perspective, Amples have some similarity to the “virtual tael/silver” or *xuliang/xuyin* 虛兩/虛銀 of the Qing Empire. During the Qing, the empire’s vast majority of circulating media of commercial exchange were copper cash 錢. Cash was the preferred money in the countryside where over 90% of the population worked. In cities and interregional trade lived a zoo of silver ingots called taels, as well as silver and gold coins, all minted locally or abroad. It took historians a long time to understand this financial system and how it worked without a unified territorial currency. Though assaying was sometimes used, for the most part taels and coins circulated at different prices in different regions. Thus, two taels or coins by different mints, even if they have the same silver content, could carry different prices.

The empire’s Board of Revenue, however, kept its books in a unit called the *kuping tael* 庫平兩—taxes had to be settled and remitted in this unit. Long-dated commercial contracts were also in *kupingliang*. The price of silver and copper coins might fluctuate depending on how many were being minted or melted down, but the government and the private sector certainly thought contracts in *kupingliang* were more stable in value. Organizations rarely kept assets physically in this unit, which is why they were called “virtual” (though 虛 also means "false"). To settle contracts or taxes one could either buy the *kupingliang* on the market, or the receiving authority could “convert” a payment into *kupingliang* at a rate of their choosing or estimate. Digital money is different because this second option is not available—smart contracts require the actual token in question to be settled. So a contract denominated in AMPL needs AMPL tokens to settle!


## Two is company, three is a (fragile) crowd
 
  {{< figure src="/2020-12-29-designing-money/econ.jpeg" width="100%" >}}

We can see from this excursion that the Economics 101 three-part definition of money is mistaken--money does NOT have to simultaneously satisfy all three properties! In fact, good money designs are robust because they are great at just one thing--whether that is as a store of value, medium of exchange, or unit of account. How is that the case? The economists definition's three parts are actually equivalent to the two-function combinations embedded in the trilemma: fiat moneys are great media of exchange, collateral moneys are the best stores of value, and rebasing moneys are the ideal units of account. Since moneys can only robustly support two of three functions in the trilemma, this means that historical moneys robustly fulfilled only one part of the Economics 101 definition. **In fact, history shows that moneys which try to fulfill all three functions inevitably have to snap back into a robust two-function configuration.** In other words, to be robust, money has to focus on a fiat, collateral, or rebasing design.
 
  {{< figure src="/2020-12-29-designing-money/managed.jpeg" width="100%" >}}

Well, what about a fiat system with a managed peg, one might say? Most fiat currencies today have a “managed float,” where the central bank intervenes in foreign exchange markets to anchor the price of its money. But the arrangement is unstable—it cannot last forever, and historically pegs have always broken down, usually when the central bank runs out of reserves. In those moments, the true nature of the system is revealed. In the case of the Mexican 1994 crisis or the Asian financial crisis of 1997, these currencies were exposed as true fiat moneys when they gave up their fixed exchange rates.
 
 {{< figure src="/2020-12-29-designing-money/fractional.jpeg" width="100%" >}}

Something similar happens with collateral moneys that try to make their supply more responsive to money demand. A classic situation is that of redeemable, specie-backed moneys in places where fractional reserve banking and note issuance is allowed. When times were good, credit and note issuance expanded the supply of money in circulation. This produced financial fragility, as von Mises reminds us. But when credit or financial activity contracted, as they inevitably always do, fractional reserve systems would rapidly shrink the money supply to the level of the reserves. Such systems revert to collateral money. The costs were bank runs, panics, and crises every 10 years.

## Conclusion

  {{< figure src="/2020-12-29-designing-money/full-trilemma.jpeg" title="The full functional trilemma, with the three most robust money designs possible-fiat, collateral, or rebasing." width="100%" >}}

The functional trilemma is a better way to understand how to design money—by focusing on what it does rather than what it is. Moneys are robust when they only span two of three functions: 1) adaptive supply, 2) durable value, and 3) stable peg. History shows that designs straddling the full triad inevitably break at the weakest feature and revert to the most stable, two-function design, at the cost of devaluations or financial crises. 
Digital assets are far more volatile than any traditional asset class or currency. In this environment, it is more important than ever to choose the most robust functional design for a money protocol--the existing tried-and-true templates are fiat, collateral, or rebasing designs. History suggests that the fragility of three-function moneys remains despite the size of their money supply and sometimes even despite government support. To believe that three-function moneys, such as the latest generation of "algorithmic stablecoins", can “bootstrap” or “grow” their way out of these lasting design questions is wishful, if not outright foolish, thinking.
