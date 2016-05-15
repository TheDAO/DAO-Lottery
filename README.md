# DAO-Lottery
Lottery backed by funds from the DAO, with profits going to the DAO.  Proposal to be submitted.

----------

DAO Lottery brainstorming

Ticket for .1 ETH?  About $1USD at current prices, it's low enough that pretty much anybody can do it and also low enough that it'll take a lot to get any significant amount tied up in the Jackpot.

Weekly payouts?  Monthly?  Allows for an accumulation of tickets over time, with each ticket getting a random number to determine the payout, if any.  Can't get higher payouts and lower payouts on the same ticket.

Cumulative ratio of odds must be lower than payout at that level.  This will leave a small amount of profit for the DAO, while still giving good odds (significantly better than Powerball, apparently).

Example (actual payouts up for debate, I'm taking suggestions (should we have each higher payout have lower odds than the previous payout?)):
- 2x - 15% - cumulative 48% plus jackpot odds (less than 1/2)
- 3x - 9% - cumulative 33% plus jackpot odds (less than 1/3)
- 4x - 12% - cumulative 24% plus jackpot odds (less than 1/4)
- 8x - 3% - cumulative 12% plus jackpot odds (less than 1/8)
- 10x - 9% - cumulative 9% plus jackpot odds (less than 1/10)

Jackpot - 50% of the ticket sales goes to the jackpot pool.  On a jackpot win, that pool gets distributed to the winners evenly.  There can be multiple winners, just like in Powerball.
   - The odds of the Jackpot need to be set very carefully.  There needs to be a very, very low probability of a large amount of ETH getting stuck in the jackpot at any time.  I'll be working on the math for this myself, and I'll get a simulation running to double check.  If the Jackpot ever ends up with too large of a chunk, we will have the ability to change the price of a ticket.  We will lower the price of a ticket, and hopefully that will sort things out quickly.
   
On that note, we need to be careful building this thing.  It's going to be difficult to change the code after it's submitted, so everything that can possibly be a variable must be a variable.  Everything.  Payouts and odds will probably be in a variable-size list, so we can add or delete things at will.

Most of the lottery will be automated, but it will be editable by a multisig of trusted people, likely the devs and maybe a few other well-known and trustworthy DAO members.  Not the DAO directly, even though that's where the profits will go, since that would mean reaction times would be way too large.

-----

Alright, so, Jackpot odds:

- 1/x = the odds of winning the jackpot
- n = the number of tickets sold
- m = the odds the jackpot doesn't get hit

So...

- 1-1/x = the odds of not winning the jackpot
- (1-1/x)^n = the odds that none of the tickets sold win the jackpot
- m = (1-1/x)^n

We're looking for appropriate odds for the jackpot, so we're going to solve for x and assign values to m and n

- nth root of m is rendered by m^(1/n)
- m^(1/n) = 1-1/x
- m^(1/n)-1 = -1/x
- 1-m^(1/n) = 1/x
- 1/(1-m^(1/n)) = x

Current ETH in existance is a little over 80 million, so I'm going to take a wild baseless guess and say the total ETH in the future will be 100 million.  Things can be changed as this changes, but I'm going to base these numbers on this.

Let's say I want to have a very good chance that the jackpot never holds more than 10% of the ETH in existance, so as to not influence the price of ETH as much as possible.  We're going to use [nines notation](https://en.wikipedia.org/wiki/High_availability#Percentage_calculation) for this.
- If I have 6 9's of certainty, then m = .000001
- Assuming a market cap of 100 million and a ticket price of .1, 10% of ETH would be n = 100,000,000 tickets
- x = 1/(1-m^(1/n))
- x = 7,238,241.8654

So jackpot odds of a little worse than 1 in 7 million.

If I want 9 9's of certainty,
- m = .000000001
- n = 100,000,000
- x = 1/(1-m^(1/n))
- x = 4,825,494.7424

So jackpot odds of a little better than 1 in 5 million.

A quick look at those odds suggests obvious averages for when the jackpot will be hit, and it's in high hundreds of thousands of ETH.  However, knowing statistics over large numbers tends to be finicky and weird, I'll come back later with some math of actual averages.  Also, coded simulations, possibly in python because I don't really want to launch eclipse every time I want to run or update this thing.
