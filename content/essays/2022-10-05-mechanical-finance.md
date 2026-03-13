---
hidden: true
title: "Mechanical Finance: Vaults, Runs, Aggregation and Automation"
date: 2022-10-05
---
hidden: true
***TL;DR\:***

***1. Finance can be mechanized through vaults, smart contracts that replace hundreds or thousands of transactions with a single transaction, obviating the need for blockchains capable of processing millions of transactions per second.***

***2. Although infinitely customizable, a Vault is a simple contract with three sets of rules for three sets of actions: 1) depositing and redeeming collateral, 2) minting and burning notes, and 3) deploying and recovering investments.***

***3. Traditional regulation aims to mitigate runs by managing the balance sheet composition of society’s largest vaults—its commercial banks. Yet, a vault’s financial properties ALSO arise from how its deposit-redeem and mint-burn rules are configured.***

***4. The vault framework reveals that disallowing either on-demand burning or collateral choice at redemption can avert runs in the first place.***

***Written January 11, 2022; updated slightly and with graphics October 5, 2022.***


## Introduction

Many of the 2021 predictions for the future of decentralized finance take for granted that transaction throughput is the key bottleneck for blockchain adoption today. FTX CEO Sam Bankman-Fried, who has billions invested in Solana, a faster competitor to Ethereum, claims that "millions of transactions per second is really a requirement of any mass-scale system," Bankman-Fried said in November 2021, "Solana is one of the few currently existing public blockchains that has a really plausible road map to scale millions of transactions per second at, you know, fractions of a penny per transaction.”[^1]

[^1]: Camomile Shumba, “The crypto billionaire Sam Bankman-Fried says solana is better than ethereum, as it's one of the few networks able to handle mass adoption,” Markets Insider, November 11, 2021. [URL](https://markets.businessinsider.com/news/currencies/sam-bankman-fried-solana-ethereum-mass-adoption-crypto-ftx-2021-11)

I think Sam is dead wrong. 

## Mechanizing the  world

Consider the history of traditional finance. Borrowing and lending are simple ways to mobilize capital and make it productive.[^2]  The accumulation and deployment of scarce and hard-earned capital was a prerequisite for the technological revolution that took us from an organic to an industrial society. But making loans is not easy—you need to know who you are lending to, assess their risk, negotiate terms, draft a contract, notarize it, and, lastly, ensure that you can enforce it. 

[^2]: As a survey, see Hernando de Soto. The Mystery of Capital: Why Capitalism Triumphs in the West and Fails Everywhere Else. Basic Books, 2000. However, capital accumulation and mobilization certainly happened outside the West, see Madeleine Zelin. The Merchants of Zigong: Industrial Entrepreneurship in Early Modern China. Columbia University Press, 2006.

Borrowing and lending were key institutions that allowed various economies to commercialize, and some to industrialize. But how did this happen? Did millions of 18th and 19th century European and Chinese peasants make millions of small loans to leading commercial and industrial enterprises? Clearly not. Just like agriculture and manufacturing benefited from mechanization (the essence of industrialization), so too did finance. 

Mechanization is not automation. Automation is a technology that allows output production without human input. Mechanization is a technology that augments the output of an individual. A backhoe or crane are good examples. So are wheels, motors, and combustion engines. A tractor allows a single farmer to equal the productive output of a hundred men swinging a scythe. Mechanization was so fundamental to rising living standards that the Chinese Communist Party put Liang Jun, China’s first woman tractor driver, on the currency.


{{< figure src="/2022-10-05-mechanical-finance/LiangJun.jpg" title="Monetary commemoration of agricultural mechanization" width="100%" >}}


Mechanical finance is the art of creating “vaults.” In traditional finance, a vault is simply an institution that accepts collateral in deposit. Under the direction of key managers, that institution then deploys this collateral into investments, and recovers proceeds. At some point in the future depositors redeem their claims for a share of the vault’s collateral. Banks are one such type of vault. A single bank director could large sums of a nation’s savings—think of the Rothschild’s extending sovereign loans. Such is the power of financial mechanization.

In this light, Sam’s argument is analogous to thinking that our traditional financial system needed to accommodate the throughput of millions of people directly investing in thousands of businesses. 

Obviously, the historical answer was different. The modern world was built on a financial system predicated on pieces of paper that had to be physically certified, mailed, shipped, and shuffled all over the world. *How many transactions per second did the early 20th century financial system handle?* I’d venture to guess between a hundred and a thousand. The real economy likely needs no more than this—atoms only move so fast after all. Stratospheric transaction throughput benefits only high-frequency jockeys and speculators.

{{< figure src="/2022-10-05-mechanical-finance/paperwork.webp" title="Sure doesn't look like a million transactions per second to me." width="100%" >}}
 

## Vaults—a new abstraction

I have no doubt that vaults are not only the past but also the future of finance. I think we can abstract the infinite legal and institutional complexity of historical vaults into a simple definition for the world of smart contracts. 

Vaults are structures that aggregate assets and automate deployment. Although infinitely customizable, a Vault (capitalized) is a simple contract with three sets of rules governing three sets of actions: 
1) depositing and redeeming collateral, 
2) minting and burning notes, and 
3) deploying and recovering investments. 

We can visualize this below.


{{< figure src="/2022-10-05-mechanical-finance/vault.png" title="Anatomy of a Vault, showing its three sets of rules." width="100%" >}}

The configuration of deposit, minting, and investment rules produces different financial behaviors. For traditional institutional vaults, attention is most often paid to the investment rules—how to deploy and recover capital. Asset allocation today is for all intents and purposes choosing the vault with the best “investment module,” that is, a combination of process and talent. A lot of these investment modules bear names like “venture capital,” “private equity,” or “special operations.”

In a permissionless environment like DeFi, however, the deposit and minting rules can alter the financial properties of the Vault’s notes. A Vault could have null investment rules and its notes would still exhibit interesting financial behavior.

Consider a simple example, a Vault will mint 1 NOTE token whenever 1 DAI or 1 USDT is deposited, and will burn 1 NOTE and redeem it for 1 DAI or 1 USDT, as the user chooses. What is the value of 1 NOTE? As should be obvious, these deposit and minting rules create a constant-sum condition. Thus, if the price of DAI is less than USDT, users will use DAI to mint NOTE and redeem them for the more valuable USDT, and vice versa. This Vault’s collateral will consist almost entirely of the least valuable token.

Investment rules are almost all that matters for traditional vaults—with a very big exception, as we’ll see below. But for DeFi Vaults deposit and minting rules can be just as important, if not more interesting for creating important and useful **autonomous** financial behavior.

## Runs—balance sheet management

Our biggest vaults are our commercial banks, and commercial banks are the source of the financial instability around which central banks and other regulators have been organized. Why? As John Cochrane says of the Great Financial Crisis of 2008, “At its core, the financial crisis was a systemic run.” Runs are in part created by institutional vaults holding long-term assets and short-term liabilities. “Among other features, run-prone contracts promise fixed values and first-come first-served payment.”[^3] Thus, from the perspective of the economist-regulator, as Douglas Diamond noted in 2008, “Financial crises are everywhere and always due to problems of short-term debt.”[^4]

[^3]: John Cochrane. “Toward a Run-free Financial System,” in Martin Neil Baily, John B. Taylor, eds., Across the Great Divide: New Perspectives on the Financial Crisis. Hoover Institution Press, 2014.
[^4]: Douglas Diamond. "The Current Financial Crisis, Other Recent Drises, and the ROle of Short-term Debt." Chicago Booth Presentation, 2008.

{{< figure src="/2022-10-05-mechanical-finance/bridgingtime.png" title="Bridging time with a Vault; four ways of categorizing maturity mismatch." width="100%" >}}
 

The theory of bank runs—and runs more generally—was transformed by the publication of Douglas Diamond’s and Philip Dybvig’s seminal “Bank Runs, Deposit Insurance, and Liquidity,” which articulated a game theoretic model for these events.[^5]

[^5]: Douglas Diamond and Philip Dybvig. "Bank runs, deposit insurance, and liquidity". Journal of Political Economy. 1983: 401–419.

The basic insight from Diamond and Dybvig is that depositors prefer liquid accounts offering some sort of yield, while borrowers prefer long-term loans. Runs are “self-fulfilling prophecies.” A customer might think the bank has made too many loans and might therefore not be able to redeem his deposits for cash. If this happens, the bank would declare bankruptcy and the customer will be stuck waiting a long time to be paid back. So this customer redeems his deposits. This only makes it more likely that another customer reaches the same conclusion. Thus, a wave of customers will seek to redeem their deposits, triggering the bankruptcy they all feared.

Diamond and Dybvig’s work provided the intellectual foundation for deposit insurance. The core idea is that rather than letting banks suspend redemptions—to buy themselves more time to collect on loans—the government should commit to making customers whole. In theory this would be cheap—large insurance commitments would reduce the number of runs, so the insurance would never have to be paid out.

In practice, this has been expensive. Massively so. 

As Cochrane argues, the true cost of deposit insurance is moral hazard on part of the banks. Customers no longer pick prudent bankers because their deposits are insured. Bankers are thus less prudent and make riskier loans. Even worse, the government has felt compelled to support banks even when their riskier loans sour as a means of preventing disruptions to the real economy when bankrupt banks unwind their loan portfolios. The regulatory answer has been to manage bank balance sheets—to impose restrictions on the type of assets that banks can hold and impose capital requirements. 

But this is a Sisyphean task. 

Over more than a century, regulation has expanded to stop crises which nevertheless kept coming. “Each new step follows naturally to clean up the unintended consequences of the last one. The expansion is nonetheless breathtaking. Beyond massively ramping up the intensity, scope, and detail of financial institutions and markets regulation, central banks are now trying to control the underlying market prices of assets, to keep banks from losing money in the first place. The little old lady swallowed a fly, then a spider to catch the fly, a bird to catch the spier, and so on. Horse is on the menu. Will we eat?”[^6]

[^6]: Cochrane, 201.

{{< figure src="/2022-10-05-mechanical-finance/lady.jpg" title="A representation of the current state of our run-prevention regulatory apparatus." width="100%" >}}


## The Vault-based alternative—deposit and minting management

Vaults provide a different view on the contract configurations that prefigure runs. The analysis itself is also simpler.
Rather than make assumptions about the order of notes burned and assets redeemed, we can instead create much more general conditions: 
1. Rules that allow on-demand note burning
2. Rules that allow collateral choice on redemption.

The first condition states that a note-holder can choose the time to burn a note. The second condition states that the note-holder can choose which collateral he receives on redemption. Runs can happen when both these conditions are met.

{{< figure src="/2022-10-05-mechanical-finance/runnable.png" title="Creating run-proof Vaults; disallow either burns on-demand or redemptions with collateral choice." width="100%" >}}
 


Consider the case where a Vault allows collateral choice on redemption and the collateral inside is of uneven value. Naturally, note-holders will rush to burn their notes and choose the collateral they perceive to be the most valuable. If notes can be burned on-demand, the entire Vault will be drained of collateral, beginning from the most valuable and ending with the least valuable, distributed on a first-come first-served basis. Restricting note-burning in some way can limit these runs. For example, a Vault might only allow 10 percent of its notes to be redeemed each month because each month 10 percent of its investments have matured.

Consider the opposite case, where the Vault allows on-demand note burning, but does not allow collateral choice on redemption. Note-holders can burn their notes at any time, but they each receive a proportional share of all the collateral in the Vault. A note-holder thus has no reason to burn their notes ahead of other note-holders—they will just receive a percentage share of the Vault’s total value, regardless of the burn order.

Certainly other permutations are possible, but in general as long as a Vault falsifies one of the above two conditions it will be safe from runs.

## Conclusion

We have outlined here the general design of a type of contract known as a Vault. Vaults provide two great benefits. First, Vaults will help mechanize decentralized finance, much as institutional vaults like banks mechanized traditional finance, reducing the total number of financial transactions by multiple orders of magnitude. Financial activity thus becomes more efficient, allowing us to avoid centralized blockchains promising a higher transaction throughput.

Second, Vaults provide a new framework through which to understand the ancient pathology of contract runs. Rather than focusing on managing balance sheet composition, as regulators have done in the traditional financial system, Vaults direct our attention towards the deposit-redemption, mint-burn rules which determine its financial properties.
