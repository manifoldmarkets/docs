# Guide to YES/NO markets

# Basic facts

- Markets are structured around a question with a binary outcome.
- Traders can place a bet on either YES or NO and receive shares in the outcome in return.
- 1 YES share = $1 if the event happens. 1 NO share = $1 if the event does not happen.
    - Notice that 1 YES share + 1 NO share = $1. If you ever get multiple YES and NO shares, they will cancel out and you will be left with cash.
- When the market is resolved, you will be paid out according to your shares. If you own 100 YES shares, if the event resolves YES, you will earn $100. (If the event resolves NO, you will earn $0).
- The creator of each market is responsible for resolving each market YES or NO.
    - Creators can also resolve N/A to cancel all transactions and return the money, or resolve to a particular probability (say 50%).

# Betting

- Betting on YES will increase the market’s implied probability; betting on NO will decrease the probability.
- Manifold uses an automated market maker to automatically adjust the market probability after each trade and to determine how many shares a user will get for their bet.
- You can sell back your shares for cash. If you sell YES shares, the market probability will go down. If you sell NO shares, the probability will go up.
- Manifold charges fees on each trade. They are baked into the number of shares you receive.
    - If you place a $100 bet on YES when the probability is 50%, you may end up with 150 YES shares. These shares already include our fees. Notice also that when you buy, the probability goes up, so you are not getting in exactly at 200 shares or 50%.
    - Our fee schedule is currently: 13% * (1 - post-bet probability) * bet amount
        - The post-trade probability is what the market probability would be after your bet if there were no fees.
        - Example:
            - If you bet $100 on NO and the resulting probability without fees would be 10%, then you pay `$100 * 13% * 10% = $1.3`.
            - If you bet $100 on YES and the resulting probability without fees would be 90%, then you pay `$100 * 13% * 10% = $1.3`.
        - The fees are used to provide a commission to the market creator and to subsidize trading within the market.
        - The market creator’s commission is paid out only after the market is resolved.
    - No fees are levied on sales.

# Market creation

- Users can create a market on any question they want.
- When you create a market, you must choose an initial probability and a close date (after which trading will halt).
- You must also pay a M$ 50 market creation fee, which is used to subsidize trading on your market.
- You will earn a commission on all bets placed in your market.
- You are responsible for resolving your market in a timely manner. All the fees you earned as a commission will be paid out after resolution.

# Liquidity

- The liquidity in a market is the amount of capital available for traders to trade against.
- The more liquidity, the greater incentive there is for traders to bet, the more accurate the market will be.
- You can add liquidity to a market you are interested in to increase the incentives for traders to participate. You can think of added liquidity as a subsidy for getting your question answered.
- You can add liquidity to any market by opening up the market info popup window located in the (...) section of the header on the market page.
