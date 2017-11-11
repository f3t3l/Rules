# Skill Execution Order

The idea is to start with Player 1:
1. Check if any Player has targeted the current player
	- 0 Player have targeted the player: Go to step 2
	- 1 or more Player have targeted the player: for every Player that has targeted the current Player start at 1.
2. Execute the players ability if not blocked by something (e.g. death) or if the player either
	1. is immune to the specific block (Passive)
	2. targets himself with a skill which would make him immune (Active)
3. Remove the skill from skills to be executed.
4. Check if some skills didn't get executed because they didn't target anyone in the tree and start from 1.
5. Check the state of each player: e.g. if they got healed/protected and attacked they survive the attack, ...

This would create something like the following tree:

![alt text](./night/ability_player_example_tree.svg "Example Exection Order")

**TODO**: Check how abilities should work, when they affect anyone visiting.
e.g. laying a trap

## Problem: Cyclic Dependencies

If a player targets another one already in the tree there will be a cycle.
![alt text](./night/ability_player_example_tree_cyclic.svg "Example Exection Order")
Here Player 1 also targets Player 3.
This would result in an endless circle.

**TODO**: Check how this should be solved.
Especially if 2 player block each other.
e.g. If Player 1 kills Player 2 and Player 2 kills Player 1.
How should this be handled?
