# Community FAQ

Originally compiled by [Isaac King](https://outsidetheasylum.blog/manifold-markets-faq/).

## General

### Do I have to pay real money in order to participate?

Nope! Each account starts with a free M$ 1000. If you invest it wisely, you can increase your total without ever needing to put any real money into the site.

### What is the name for the currency Manifold uses, represented by M$?

It doesn't have an official name yet. Cast your vote [here](https://manifold.markets/Sinclair/what-should-we-call-the-digital-cur).

### Can M$ be transferred between users?

Not directly. You can indirectly accomplish this by creating a market and bidding against the other user, then resolving it in their favor. This will however cost you the 1% currency-destruction fee, and other users may interfere if the market isn't resolved quickly enough.

### Can M$ be sold for real money?

No. Gambling laws put many restrictions on real-money prediction markets, so Manifold uses play money instead.

### How do the free response markets work?

Any user can enter a response and bet on it, or they can bet on on other people's responses. The response probabilities are weighted proportionally to how many people have bet on them. The market creator's ante goes into a "none of the above" pseudo-option that can't be bet on and can't be chosen as a correct answer when the market is resolved. (This means that free response markets tend to lose their creator almost their entire ante, whereas normal markets only lose them a small fraction that's proportional to how well they chose their starting odds. It also means that if there are only a finite number of options that could win, bettors can make guaranteed money by investing in them all equally.) See [here](https://manifoldmarkets.substack.com/p/above-the-fold-milestones-and-new) for more information.

### How accurate are the market probabilities?

In general, prediction markets are very accurate. They do have some known issues, most which can be found on the [Wikipedia page.](https://en.wikipedia.org/wiki/Prediction_market#Accuracy). There are also a few factors that are specific to Manifold Markets:

- Manifold uses play money for their markets, so there's less of an incentive for people to invest safely. People often goof around with silly markets and investments that they don't expect to win M$ from.
- Anyone can create a market on Manifold, and there's nothing preventing the creator of a market from trying to manipulate it to make a profit.
- Manifold Markets is a new project and has a large number of individual markets, which means that many of their markets don't have many participants, sometimes less than 5 people.
- Manifold's betting system isn't perfect and has some sources of error, discussed in detail [here](https://kevin.zielnicki.com/2022/02/17/manifold/).

As a general heuristic, check the total pool for the market in question. The more M$ there is in the market, the more likely it is to be accurate.

### How do I leave a comment on a market?

Putting any M$ into a market gives you the ability to leave a comment. You can buy M$ 1 and then sell it in order to leave a comment for free.

### Can I participate without having a Google account?

No. See [here](https://manifold.markets/hamnox/will-manifold-markets-add-nongoogle) for the probability that this changes.

## Placing and winning bets

### What is the "amount loaned" field when I place a bet?

You get an interest-free loan of M$ 20 on each market. This incentivizes people to participate in longer-term markets, since it removes the opportunity cost associated with the ability to spend that M$ 20 elsewhere. This is all handled automatically by the site, all you have to do is bid normally. See [here](https://manifoldmarkets.substack.com/p/above-the-fold-borrow-away?s=r) for more information.

### The payout probabilities I'm shown sometimes aren't right. For example if a market is at 15% and I bet M$ 1 on "no", it tells me that I'll make a 42% profit if I win, but the listed payout is just M$ 1. What's going on?

Payout amounts are visually rounded to the nearest M$ 1, and only integer amounts can be put into markets. Behind the scenes however, your balance does track fractional amounts, so you're making a M$ 0.42 profit on that bet. Once you win another M$ 0.08, that fractional M$ 0.5 will display as an extra M$ 1 in your account. (There's no way to view your exact balance, you can only see the rounded value.)

### Are there any fees for betting in a market?

Yes, all successful bets have a 5% fee taken. 4% of it goes to the market creator, and 1% is destroyed in order to avoid inflation of the currency as more users join. Note that this fee is on each individual share, not your net profits for an entire market. For example, if you own shares on two different responses in a free response market such that when the market resolves you win M$ 100 from the correct answer and lose M$ 50 from the incorrect answer, the total fee you pay is M$ 5, not M$ 2.5.

### What's a "share"? Is that equal to the amount of money I put into the market?

No. M$ 10 might buy you 10 shares, 5 shares, 15 shares, or some other number. It depends on what probability the market is at when you invest the M$. Details are [here](https://www.notion.so/Technical-Guide-to-Manifold-Markets-b9b48a09ea1f45b88d991231171730c5).

### What are the rules about insider trading? (Using private information about a market to make a profit.)

It's not only allowed, but encouraged. The whole point of a prediction market is to uncover and amplify this sort of hidden information. For example, if there's a market like "will [company] make [decision]?" and you work for that company and know what decision they're going to make, you can use that information to win M$ and make the market more accurate at the same time. (Subject to your company's policies on disclosing internal information of course.) However, if the reason you have private information is because you're colluding with the market creator, this will likely earn both of you a bad reputation and people will be less interested in participating in your markets in the future.

### Can I see who is buying/selling in a market?

Trading is anonymous by default. You'll only see their username if they leave a comment. As an exception, trading from the market's creator has their name attached.

## Creating and resolving markets

### Is there any benefit to creating markets?

You get your question answered! Plus, you earn 4% of all bettor profits in your markets.

### What can I create a market about?

Anything you want to! People ask about politics, science, gaming, and even [their personal lives](https://www.smbc-comics.com/?id=2418). Take a look at the [current list of markets](https://manifold.markets/markets) to see what sorts of things people ask about.

### What is the "market ante" when I'm creating a market, and why would I make it higher than the minimum of M$ 10?

The ante is an amount of M$ that you put into your own market as an incentive for other people to participate. It's equivalent to you putting that much M$ into the market at the same mix of probabilities as the market starts. The higher the ante, the more M$ people stand to gain by betting against you. For example, if you ante M$ 10 into a market that starts at 50%, you've effectively bought M$ 5 of "yes" and M$ 5 of "no" in that market. Someone who thinks the answer will be "yes" can only win at most M$ 5 by betting against you, so there's no incentive for them to put more than M$ 5 into the market. Someone who comes along later thinks the answer will be "no" can now win up to M$ 10, M$ 5 of it from you and M$ 5 of it from the other trader. Opening a market with a larger pool allows it to grow more quickly. In a normal market, you'll usually end up losing a little bit of your ante and getting some of it back. The more accurate your starting probability is, the less you'll lose. In a free response market, you'll usually end up losing almost your entire ante, since the ante goes onto the "none of the above" option, which can't win.

### What's the difference between a market being "closed" and being "resolved"?

A market being "closed" means that people can no longer place or sell bets, "locking in" the current probability. Markets close when the close date of the market is met. A market being "resolved" means that the market creator has indicated a given resolution to the market's question, such as "yes", "no", "N/A", or a certain probability. This is the point at which people are cashed out of the market. Resolving a market automatically closes it, but a market can close days, weeks, or even years before it gets resolved.

### What does "PROB" mean?

Resolving a market as "PROB" means that it's resolved at a certain probability, chosen by the market creator. PROB 100% is the same as "yes", and PROB 0% is the same as "no". For example, if a market is resolved at PROB 75%, anyone who bought "yes" at less than 75% will (usually) make a profit, and anyone who bought "yes" at greater than 75% will (usually) take a loss. Vice versa for "no". (The "usually" is due to some quirks of the betting system; in rare cases it's possible to lose money on a bet even if the market moved closer to it. See [here](https://kevin.zielnicki.com/2022/02/17/manifold/).)

### What happens if a market creator resolves a market incorrectly, or doesn't resolve it at all?

Nothing. The idea is for Manifold Markets to function with similar freedom and versatility to a Twitter poll, but with more accurate results due to the dynamics of prediction markets. Individual market resolution is not enforced by the site, so if you don't trust a certain user to judge their markets fairly, you probably shouldn't participate in their markets.

### How do I tell if a certain market creator is trustworthy?

Look at their market resolution history on their profile page. If their past markets have all been resolved correctly, their future ones probably will be too. You can also look at the comments on those markets to see if any traders noticed anything suspicious. You can also ask about that person in the [Manifold Markets Discord](https://discord.gg/eHQBNBqXuh). And if their profile links to their website or social media pages, you can take that into account too.

### Are there any content filters? What happens if someone creates an inappropriate, offensive, or [dangerous](https://en.wikipedia.org/wiki/Assassination_market) market?

Right now, there are no restrictions on what markets can be created. If this becomes a problem, they may change their policies.

### Can a market creator change the close date of their market?

Yes. As long as the market hasn't been resolved yet, the creator can freely change its close date. They can even reopen a market that has already closed.

### Is there a way to see my closed markets that I need to resolve?

You'll get an automated email when they close. You can also go to your profile page and select "closed" in the dropdown menu. (This will display only markets that you haven't resolved yet.)

### When do market creators get their 4% cut?

When the creator resolves their market, they get 4% of the profits from all shares that were in the market when it closed. If a bettor sells some of their shares at a profit before the market closes, the market creator gets 4% of those profits at that time. If a market resolves as N/A, the creator doesn't get any profit from shares in the market when it closed, but they do keep the 4% gained from any shares that were sold beforehand.

### Where can I see how much M$ I made on a market I created?

Currently, you can't see that anywhere. The payout numbers on your own markets only count your ante plus any other shares you put into the market.

### How do I see all markets that are currently open?

You can't. You can see the top 99 markets in various categories [here](https://manifold.markets/markets), but there's no way to see the whole list.

### Can I bet in a market I created?

Yes. However if you're doing things that the community would perceive as "shady", such as put all your money on the correct resolution immediately before closing the market, people may be more reluctant to participate in your markets in the future. Betting "normally" in your own market is fine though.

## Miscellaneous

### How do I report bugs or ask for new features?

Contact them via [email](mailto:info@manifold.markets), post in their [Discord](https://discord.gg/eHQBNBqXuh), or create a market about that bug/feature in order to draw more attention to it and get community input.

### How can I get notified of new developments?

Being a very recent project, Manifold is adding new features and tweaking existing ones quite frequently. You can keep up with changes by subscribing to their [Substack](https://manifoldmarkets.substack.com/), or joining their [Discord server](https://discord.gg/eHQBNBqXuh).

### Is there anything preventing people from creating fake accounts to get free M$ to transfer to their real account?

Integrity.

### Can a market's pool decrease?

Yes. The pool is the total amount of M$ invested into that market, so it will go down if someone sells their shares.

### Is there an app?

No, but the website is designed responsively and looks great on mobile.

### I keep seeing descriptions that use the term "iff". What does that mean?

"Iff" is [logician slang](https://en.wikipedia.org/wiki/If_and_only_if) for "if and only if". For example, "I will go to the store iff I run out of milk" means both "if I run out of milk, I will go to the store" and "I will not go to the store unless I run out of milk".

### What does "DPM" mean?

It stands for "Dynamic Pari-Mutuel Market", which is technical term for certain types of betting markets, including the one that Manifold uses. Learn more on [Wikipedia](https://en.wikipedia.org/wiki/Parimutuel_betting) or by reading [some papers](https://scholar.google.com/scholar?&q=dynamic+pari-mutuel+market) about it. An explanation of Manifold's exact system is [here](https://www.notion.so/Technical-Guide-to-Manifold-Markets-b9b48a09ea1f45b88d991231171730c5), a sandbox version is [here](https://manifold.markets/simulator), and more discussion about it is [here](https://kevin.zielnicki.com/2022/02/17/manifold/) and [here](https://manifold.markets/kjz/will-manifolds-developers-agree-wit).

### Does Manifold have an API for programmers?

Yep. Documentation is [here](https://www.notion.so/Manifold-Markets-API-5e7d0aef4dcf452bb04b319e178fabc5).

### If I have a question that isn't answered here, where can I ask it?

You can contact Manifold Markets via [email](mailto:info@manifold.markets) or post in their [Discord](https://discord.gg/eHQBNBqXuh). Once you have an answer, you can also [email me](mailto:is.aack@yahoo.com) about adding that question to this FAQ.
