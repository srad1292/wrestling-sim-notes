- Max 3 stages
- Last stage must be either single group round robin or elimination
- Elimination 
	- Brackets must be power of two
	- If not last stage, can have multiple brackets (2,3,4) to have multiple winners move on to next stage
	- Single or double elimination
	- If last stage, must be single bracket to have a single winner
- Round Robin
	- 1-4 groups
	- Single or double 
	- If last stage, must be single group
	- If not last stage, number of people who move on should be some multiple of the number of groups
	- Tie breaker
		- Order tied teams by record against each team that's tied
		- Order remaining ties by shortest win
		- "Coin toss" any remaining ties (basically just order randomly)
- Stage N must be X-(# stage N-1 winners) where x is a power of 2
- If stage N is a round robin, user can choose where any winner from previous goes
- If stage N is an elimination, user can choose where any winner from previous goes

Round Robin Input
- Number of groups
- Single or double
- Number of participants
- Participants 
- Number that moves on

Round Robin Validation
- Single or double
- Groups 1-4 (just make this a dropdown)
- Number of participants per group for one group:
	- 3-24
- Number of participants per group for 2-4 groups:
	- N x GroupSize min 4, max 24, 
	- 3-12 per group for two groups
	- 3-8 per group for for three groups
	- 3-6 per group for for four groups
- Number that advance -> must be a multiple of the number of groups up to the total number of participants.  So 3 groups of 4 could have 3, 6, 9, or 12 that advance
- If not first stage, total number of participants must be >= to the number that advanced from previous round


Elimination Input
- Number of brackets
- Single or double
	- Double is only for single bracket
- Number of participants (must be a power of 2) -> 
	- Single bracket 4-64 people
	- Multiple brackets 2-8 people
- Participants
- Number that moves on is one per bracket so not really an input
- Match type for each round in winners bracket
	- Number of rounds is what power of two makes up number of participants
	- This can be done with log(participants)/log(2)  -> for example log(64)/log(2) is 6 so 6 rounds
	- If double elimination, this number is increased by 1 because winner of upper bracket plays winner of lower bracket in one final match.  So a 64 person double elimination has 7 rounds instead of 6
	- Match type for each round in losers bracket
		- 64 person has 10 rounds in lower bracket
		- 32 -> 32 -> 16 -> 16 -> 8 -> 8 -> 4 -> 4 -> 2 -> 2
			- So is this log(participants/2)/log(2)*2?

Elimination Validation
- If not last stage number of brackets must be 1
- For single bracket, number of participants must be power of 2 between 4 and 64
- For 2-4 brackets, number of participants per bracket must be power of 2 between 4 and 8
- If not last stage, number of participants must be >= number that advanced from previous stage
- Number that moves on is 1 per bracket

