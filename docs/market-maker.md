# Manifold's Market Maker

A brief technical overview of [Manifold Markets](https://manifold.markets/)’ Dynamic Parimutuel (DPM) betting system

By [Stephen Grugett](https://manifold.markets/SG)

Basic facts:

- Markets are structured around a question with a binary outcome.
- Traders can place a bet on either YES or NO. The trader receives some shares of the betting pool. The less likely the outcome, the more shares the trader receives per dollar.
- When the market is resolved, the traders who bet on the correct outcome are paid out of the final pool in proportion to the number of shares they own.

## Probability

If _y_ is the total number of outstanding shares of YES, and _n_ is the total number of outstanding shares of NO, the instantaneous implied probability of the market is given as

$$
P(y, n) = \frac{y^2} {y^2 + n^2}
$$

## Betting

We introduce a cost function _C_ which captures the total amount wagered by all traders given the current shares of YES and NO:

$$
C(y,n) = \sqrt{y^2 + n^2}
$$

If a trader places a bet of $_b_ on YES, they add $_b_ into the YES pool and receives _s_ shares of the final pool if YES is the outcome.

$$
pool_{Y_{new}} = pool_{Y_{current}}  + b
$$

$$
b = C(y+s, n) - C(y, n)
$$

## Antes

The market creator chooses an initial probability _p_ and an ante amount to initialize the betting pool.

$$
p = \frac{y_{start}^2}{y_{start}^2+n_{start}^2} \; \newline s.t. \; \; \sqrt{y_{start}^2+n_{start}^2}=  ante \newline y_{start},n_{start} \gt 0
$$

## Market Resolution

### I. Typical case: Resolving YES or NO

Suppose the market resolves YES. The winnings for the *i-*th YES bet of $b and s shares (with y total YES shares) are

$$
winnings = \frac{s}{y}*pool
$$

Fees are deducted from the profits to get the final payout:

$$
payout = b + (1- fees)(winnings - b)
$$

### II. Resolving PROB

Sometimes the market creator does not want to wait until the outcome of the event is fully resolved but would like to close out the market at a specific probability (often the current implied probability). The resolution option PROB can be used for this purpose.

Let the probability the creator resolves the market to be *p. T*he payout for the *i-*th YES bet of s shares is

$$
winnings = \frac{ps}{py+(1-p)n}pool
$$

Fees are deducted on the profits as above to determine the final payout.

And the payout calculation for NO bets is the same, but using the probability _1-p_.

### III. Resolving N/A

In addition to resolving a market YES or NO, there is a third resolution option, N/A, which can be used to cancel the market and return people’s money.

Cancellations can be used to create conditional markets that only are resolved YES or NO if some precondition holds, e.g. a market based on the question “If Trump wins the 2024 presidential election, will the average inflation rate in 2025 be over 10%?” can be cancelled if Trump does not win the election.

Since we allow selling, we cannot simply return every bet because the total amount of money in the pool may not equal the total money bet.

The payout associated with the _i_-th bet of a market resolved N/A is

$$
payout_i = \frac{b_i}{\sum_{j \in Y \cup N}{b_j}}pool
$$

Note that no fees are levied for cancelled markets.

## Fees

Manifold Markets currently charges two separate fees on profits:

- Commission of 4% (paid to the market creator)
- Platform fee of 1% (burned)

## Selling

Traders sometimes wish to cash out of their bet before the market is resolved. Unfortunately, the shares a trader owns are shares in the final pool—which is unknowable prior to market resolution. We can still let traders cash out by having them receive money from the pool they bet in, if there’s still money available.

Suppose a trader who bet $_b_ on YES for _s_ shares wishes to cash out. First, we calculate $_m_, the amount of money you would need to sell from the current pool in order to get _s_ shares.

$$
m = C(y, n) - C(y - s, n)
$$

To disincentivize traders from selling we cap the sale amount to

$$
sale=  min(m, pool_Y)
$$

This ensures that traders cannot cash out their bet at a profit if no one else has bet on their side.

The trader then receives the sale amount after deducting our fees on any profits they may have earned.

The YES pool is updated

$$
pool_{Y_{new}} = pool_{Y_{current}}-sale
$$

# References

Pennock: [A Dynamic Pari-Mutuel Market for Hedging, Wagering, and Information Aggregation](http://dpennock.com/papers/pennock-ec-2004-dynamic-parimutuel.pdf)

Chen et al.: [An Empirical Study of Dynamic Pari-mutuel Markets: Evidence from the Tech Buzz Game](http://yiling.seas.harvard.edu/wp-content/uploads/BuzzGameAnalysis.pdf)

# Appendix: Derivation of implied probability

Given our cost function and payout structure, we’d like to show that our implied probability calculation is correct.

First question: What does it mean for the market to imply a particular probability?

We define the implied probability of a market as the probability _p_ where the expected value of buying an infinitesimal number of shares in YES (or NO) is zero.

Given the payout for YES and the instantaneous share price, $\pi_Y$, the calculation is:

$$
0 = p*E[payout_Y | Y] - \pi_Y
$$

Solving for p, we get:

$$
p = \frac {\pi_Y} {E[payout_Y|Y]}
$$

We know that the share price is the derivative of the cost function so:

$$
\pi_Y = \frac{\partial}{\partial y}C(y, n) = \frac {y} {\sqrt{y^2 + n^2}}
$$

We can also simplify the payout term by assuming that the expected payout given that the market is resolved YES is equal to the current payout for YES. This will be true in all cases where payout follows a random walk (which is a reasonable assumption if [markets are efficient](https://en.wikipedia.org/wiki/Efficient-market_hypothesis)).

$$
E[payout_Y|Y] = payout_Y
$$

We also know the payout per share is equal to the pool divided by the the number of outstanding YES shares.

$$
payout_Y = \frac{pool} {y}
$$

From the definition of our cost function we know

$$
pool = C(y, n) = \sqrt{y^2+n^2}
$$

Therefore,

$$
E[payout_Y|Y] = \frac {\sqrt{y^2+n^2}} {y}
$$

Now, substituting everything into our calculation for _p:_

$$
p = \frac {\frac {y} {\sqrt{y^2 + n^2}}} {\frac {\sqrt{y^2+n^2}} {y}} = \frac {y} {\frac{y^2+n^2}{y}} = \frac{y^2}{y^2 + n^2} = P(y, n)
$$
