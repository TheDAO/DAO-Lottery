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
