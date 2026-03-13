---
title: "Why “bond coins” cannot work—two easy, three-step proofs"
date: 2020-12-27T18:28:29-08:00
draft: true
---



Abstract: XXXX


I’ve been asked a lot about “bond coins,” which are a family of protocol designs for solving the “stable coin” problem—any solution produces a non-rebasing coin that reliably sustains a pegged exchange rate. Inspired by central bank open market operations (OMO), these protocols issue more coins when the price is above the peg, and create yield-bearing staking contracts (the “bonds”) to soak up supply when the price falls below the peg. I’ve discovered that the complexity of this design, and the misuse of central banking language, makes it difficult for newcomers to understand why, in the context of decentralized finance (DeFi), such systems are precarious and unstable. Standard critiques state that the market for the staking contracts can fail and break the peg. Bond coin promoters retort that the problem is either one of scale or of collective faith—if the coin captures a sufficiently big market cap, or if enough speculators believe that demand for the project will increase, then the market for “bonds” cannot fail. 

Naturally, I disagree—bond coin projects will fail at any size as soon as demand contracts. The argument advanced here is simple. Bond coin protocols have no way to force a reduction in coin supply—the “bond” sales are voluntary—which anchors the coin supply to the all-time highest market cap. To make matters worse, the temporary supply reduction is bought with “yield,” which is either a promise of future inflation or a bet on demand surpassing its previous all-time high. For these reasons, any reduction in demand will expose a permanent supply overhang that either produces endless price oscillations, or a break from the peg. Bond coin protocols can survive price fluctuations which the market perceives to be small and temporary. But the peg becomes more fragile the further and longer the coin’s price falls below the peg. It is implausible that a bond coin will not experience massive volatility—even Bitcoin, which is the largest in the asset class, has experienced drops in value over 50% that last for months or years. Thus, when, not if, demand for a bond coin falls, the design will most certainly fail as a stable coin solution. 

Why is it that central bank OMOs work, then? The short answer is that real world OMOs are backstopped by sovereign authority. Central banking laws privilege the use of government bonds as reserves—these are designated as “safe assets”—thus coercing commercial banks into becoming buyers of last resort. Banks prefer to hold yield-bearing bonds instead of non-yielding cash. OMOs usually work only in domestic markets, though sometimes foreigners buy these bonds. In the case of the US, this is due to the dollar’s role as a reserve currency internationally, and a demand for dollar safe assets. The long answer, in the case of the dollar, requires a deep dive into trade-settlement network effects, banking sector dollarization, commodities settlement, and historical path dependence.

Bond coin protocols, in contrast, are institutionally naked—they have no backstop, and are supposed to function in high-volatility, trustless environments. They rely solely on high yields, denominated in their native coin, to attract buyers. They function more like speculative, low-grade corporate debt than government-issued safe assets. To look at state-backed open market operations and think that such a mechanism is the right way to build private money is akin to looking at a bird and thinking that humans can fly by flapping our arms with wings attached. To argue that the problem is a lack of scale—that bond coins would work if their market cap were big enough—is to argue that the problem is that our wings are not big enough or that we are not flapping hard enough.  To argue that the problem is a lack of collective faith—that bond coins would work if they attract enough speculative demand—is to argue that the problem is that we are not flapping hard enough. The real problems lie elsewhere.

The rest of this essay consists of four parts. The first two parts are comprised of two inductive proofs outlining what happens when demand falls. In the first part, we assume that staking contracts, like real world bonds, have maturity dates after which they are redeemed. The second part explores the different challenges that arise if, following the Basis Labs design, staking contracts can only be redeemed when prices are so high that the protocol mints enough new coins to cover the “bond” amount and its yield. The third part examines the plausibility of our inductive base step—a reduction in demand for Coin—and concludes that it is almost certain to occur. Centuries of financial history show this happens even to real world currencies despite all the state-given advantages they enjoy. In the fourth and final part, I explore the conditions that allow central banking OMO to work, and why these conditions do not exist in DeFi. I also explore ways to increase the resilience of bond coins. One such way is to create a reserve fund to defend the peg. Because defending a peg is a sure way to lose, not make, money, a protocol would need a way to replenish its reserves—either a buyer of last resort, a source of income, or a deep-pocketed charitable patron.

Some assumptions and concepts

***Assumptions***. Assume for simplicity the following conditions—once we have proved our result, we can relax them and see that they do not change our conclusion:
-	There is an infinite number of willing speculators, though each has finite capital
-	The yield is fixed at rate R
-	All liquidity for Coin exists in a single liquidity provider (LP) pool on a single automated market maker (AMM)
-	Coin’s LP pool pair is an asset with an absolutely stable price and infinitely deep reference markets—say, a digital US dollar (e.g. USDC)
-	Speculators—like the famous Yearn Finance protocol—buy C at the AMM to “farm” yield, and then “harvest” this yield by C back for USDC, since they ultimately need to return to investors assets like ETH or DAI, which are the assets in their vaults.
-	No new LPs add liquidity to the pools, no LPs leave the pools
-	Except for the base case, there is no increase or decrease in aggregate demand for C
-	Redemption occurs at a fixed time after issuance, regardless of exchange rate


**Exercise 1: Redemption at maturity**

***Base case***: There is a secular reduction in the demand for Coin (C), a bond coin, such that it’s price (\\(P_1\\)) falls below parity (\\(P0=Pt\\))
Inductive step: Each successive round of “bond” staking and redemption is larger than the previous round, and each resulting price is lower than the price from the last round—i.e. Pn > Pn+1 > Pn+2 > …
Conclusion: Pc will experience increasing larger oscillations between Pt and {Pn, Pn+1,…}, thus Coin cannot be a solution to the stable coin problem.

Assumptions. Assume for simplicity the following conditions—once we have proved our result, we can relax them and see that they do not change our conclusion:
-	There is an infinite number of willing speculators, though each has finite capital
-	The yield is fixed at rate R
-	All liquidity for Coin exists in a single liquidity provider (LP) pool on a single automated market maker (AMM)
-	Coin’s LP pool pair is an asset with an absolutely stable price and infinitely deep reference markets—say, a digital US dollar (e.g. USDC)
-	Speculators—like the famous Yearn Finance protocol—buy C at the AMM to “farm” yield, and then “harvest” this yield by C back for USDC, since they ultimately need to return to investors assets like ETH or DAI, which are the assets in their vaults.
-	No new LPs add liquidity to the pools, no LPs leave the pools
-	Except for the base case, there is no increase or decrease in aggregate demand for C
-	Redemption occurs at a fixed time after issuance, regardless of exchange rate

Since this is the inductive step, we assume that the reduction in demand has already happened, and thus that the price P1 < Pt. We can visualize this state of affairs with a simplified supply and demand curve—the real curves are well, curved, but don’t change the result.

 

Previously, when Pc=Pt=$1, the number of tokens in each pool was the same. Lc0=Lu0. A reduction in demand means that holders swapped some of their C for USD, such that the amount of tokens in Lc is now larger than that in Lu. Thus, Lc1> Lc0, Lu1<Lu0. And the marginal price is simply the ratio of these token amounts P1 = Lu1/ Lc1.

{{< figure src="/bond-coin-post/corgi-husky-mix.jpg" width="100%" >}}
 

The protocol now needs to raise the price back to Pt, and can do this by reducing the supply of C in the liquidity pool. It thus issues “bonds”—it creates staking contracts for the amount S1=| Lc1- Lc0|, with a yield R. Speculators will swap USD for C in the pools, restoring their 1:1 ratio. Once S1 of C has been bought, the price will return to Pt. This is what it looks like.

 

Maturity will trigger a redemption by the protocol at some point. Speculators will receive S2=S1*(1+R) of C. They will then swap this amount for USDC. By definition, S2=S1*(1+R) > S1, meaning a full redemption creates more C than was originally locked into the staking contracts. Thus the liquidity pool quantity Lc2= Lc1+R*| Lc1- Lc0| > Lc1. Thus, by definition, Lu2 < Lu1. Thus, P2 = Lu2/ Lc2< P1=Lu1/ Lc1. We can visualize the resulting, lower price below.
 

Of course, now the price is once again below parity, and another round of bond issuance and redemption begins, which will produce ever lower prices after each round.


Exercise 2: Redemption through exchange rate conditions

Base case: There is a secular reduction in the demand for Coin (C), a bond coin, such that it’s price (P1) falls below parity (P0=Pt)
Inductive step: No speculator would rationally ever buy C to stake because redemption conditions will never be met.
Conclusion: Pc will permanently diverse from Pt, thus Coin cannot be a solution to the stable coin problem.

Assumptions: Redemption occurs and continues only under certain exchange rate conditions—when the price Pn > Pt, and enough new supply has been created by the protocol to cover the original amount staked and the yield.

 

Steps:
•	P1 < Pt
•	Protocol issues staking contract for S1=| Lc1- Lc0| to raise the price back to Pt.
•	Speculators purchase supply S1 of C to stake, and raise the price back to Pt.
•	Protocol stops issuing staking contracts.
•	At this point, if the market is large enough, no individual speculator can or will push the price high enough to redeem the outstanding “bonds” and their yield—this would also not be profitable as the price appreciation and additional supply is shared by all speculators, not just our heroic price manipulator.
•	So speculators will only be rewarded if there is an aggregate demand increase equal to their staking contract and its yield.
•	But by our assumptions and base case, the new long-run aggregate demand does not change.
•	Thus, unless P1 is close to Pt, speculators would never redeem their “bonds” and yield.
•	Knowing this, a speculator will never buy and stake C in the first place.
•	Thus the price remains below parity indefinitely.


Exercise 2.5: Redemption through exchange rate conditions which can be triggered by a single speculator

Base case: There is a secular reduction in the demand for Coin (C), a bond coin, such that it’s price (P1) falls below parity (P0=Pt)
Inductive step: The speculator will buy enough C to raise the exchange rate past parity, to the point of full redemption, after which they will liquidate their “harvest” and drive the price lower than the starting point. These cycles produce ever higher and ever lower prices, and is a special case of Exercise One.
Conclusion: These cycles produce ever higher and ever lower prices, like in Exercise One, thus Coin cannot be a solution to the stable coin problem.

Assumptions: Redemption occurs at a price Pn > Pt which can be induced by a single speculator. 

 
Steps:
•	P1 < Pt
•	Protocol issues staking contract for S1=| Lc1- Lc0| to raise the price back to Pt.
•	Sing speculator purchases supply S1 of C to stake, and raises the price back to Pt.
•	Protocol stops issuing staking contracts.
•	Single speculator purchases an additional S1(1+R) to raise the price P1* > Pt to a point where he is redeemed for the staking contract and the yield S1*R.
•	He now owns S1(2+2R) of supply of C. He purchased S1(2+R) and received S*R as “seignorage” yield.
•	He now sells his tokens to collect his harvest. He regains his original capital invested by selling S1(2+R), and makes a profit from selling S1*R once the price is back at P1.
•	Selling S1*R tokens means Lc2> Lc1> Lc0, thus P2 < P1 < Pt.
•	The protocol now goes onto the next round, and needs to issue staking contracts for S2=S1(1+R) to raise the price back to Pt…

 

As we can see, post-redemption price Pn > Pn+1 > … and speculative price P*n < P*n+1 < …, meaning the Pc will oscillate between ever higher highs and lower lows.

Is the base case plausible?
Is it possible that there is a secular reduction in aggregate demand for Coin? Absolutely—all digital assets have experience this. It can be something as simple as better investment opportunities, so that holders want to cash out and invest elsewhere. Or it can be caused by investor liquidity needs, if they suffered losses elsewhere, or if the market is generally deleveraging. The situation can also arise in circumstances that are usually positive for other protocols, for example, if there is too much excitement about the project, the protocol might expand supply above what is appropriate for stable, long-run demand.


Possible work-around? 
Is there a way to make a bond coin less fragile in the face of demand fluctuations? One way would be to issue “bonds” repayable in “foreign currency”—that is, they are not paid in Coin but in a larger asset, such as wBTC or ETH or DAI. Functionally, however, this is equivalent to running a reserve system.

Another solution is to just run a reserve system, where “foreign reserves” are used to defend the peg. This was very likely the reason for the $133 M in dollars raised by the Basis team. The problem is that defending a peg will cause reserves to leak—one is buying Coin at a higher than market price. When reserves run out, the peg breaks. Central banks have multiple ways of replenishing their reserves—customs duties, taxes, capital controls, government grants, etc. Naked protocols do not. Trying to accumulate reserves by selling Coin recreates the issue explored in Exercise 2 above—except now the protocol takes the place of the speculative investor! 
 

One way to make a reserve sustainable in the longer term would be to form partnerships with deep-pocketed outside entities, such as very large funds or even local governments, who are willing to lock up endless amounts of capital for as long as is needed to reach parity, and write off any resulting losses. But then again, such a system would not be very decentralized at all! 

Conclusion
Bond coin protocols have no way to actually remove supply. Thus any reduction in demand will create a permanent supply overhang that either produces endless price oscillations, or a break from the peg. Bond coin protocols can handle demand fluctuations which the market perceives to be small and temporary. The peg becomes more fragile the further and longer the price diverges from the peg. Given the massive volatility in digital assets—which is the source of investor interest—this design will most fail as a stable coin solution.

