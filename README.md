# game-pair-of-players-in-python
The function aims to check if all pairs of players have played against each other in the m rounds of games

You are given three arguments: n, m, games. Your task is to check that for all pairs of players 1≤𝑥,𝑦≤𝑛, player 𝑥 has played against 𝑦. games is a 2-dimensional list that represents the 𝑚 rounds of games among 𝑛 players.

Write a function check(n, m, games) that takes in 3 arguments.

Inputs It is guaranteed that 𝑛,𝑚 are integers and 1≤𝑛≤20,000, 1≤𝑚≤30. It is also guaranteed that 𝑛 is even.

games is a 2 dimensional list with m rows and n columns, where games[i] is a permutation of 1,2,3,...,n representing round number 𝑖. In particular for round i, games[i][0], games[i][1], games[i][n/2-1] is on one team, games[i][n/2], games[i][n/2+1], games[i][n-1] is on the other team.

Outputs check(n, m, games) should return a boolean, True if and only if all pairs of players have played against each other in the 𝑚 rounds of games.

Examples check(2, 1, [[1, 2]]) = True

check(4, 2, [[1, 2, 3, 4], [4, 3, 1, 2]]) = False

check(4, 2, [[1, 2, 3, 4], [1, 3, 2, 4]]) = True

check(6, 6, [[1, 6, 3, 4, 5, 2], [6, 4, 2, 3, 1, 5], [4, 2, 1, 5, 6, 3], [4, 5, 1, 6, 2, 3], [3, 2, 5, 1, 6, 4], [2, 3, 6, 4, 1, 5]]) = True

check(6, 6, [[3, 1, 4, 5, 6, 2], [5, 3, 2, 4, 1, 6], [5, 3, 6, 4, 2, 1], [6, 5, 3, 2, 1, 4], [5, 4, 1, 2, 6, 3], [4, 1, 6, 2, 5, 3]]) = false

APPROACH 1

The function takes three inputs: n, m, games. n is the number of players, m is the number of rounds of games, and games is a 2D list representing the rounds of games among the n players.

It starts by generating a list of all possible player pairs called 'group_of_pairs'. This list contains tuples of all possible combinations of players.

Then, it iterates through each player pair "i" in the 'group_of_pairs' list and sets a boolean flag called 'both_player' to False.

For each player pair "i", it iterates through each round of games "game" and checks if the two players in the pair were on different teams in that round. To do that, it split the "game" into two teams, left and right, and, if the i[0] matches with i[1] in both teams, the 'both_played' flag is set to True and the loop breaks. It the 'both_played" flag is still 'False', it continues to the next round of games "game" until finishing all iterations of games. Then, it goes to step 2 above for next player pair "i" in the "group_of_pairs" list until finishing all player_pair "i"'s.

If the 'both_played' flag remains False after looping through all rounds of games for a player pair, the function returns False as this means that the two players in the pair have not played against each other.

Finally, if the loop finishes for all player pairs and no False value is returned, the function returns True, indicating that all players have played against each other in the given m rounds of games.

Reasoning: The idea is to check if each pair of players have played against each other in the m rounds of games. Getting all pairs with 'n' players, it has to iterate first with each pair, and for each pair, it has to iterate each game. For each pair, it checks all games and see if the pair in mention, which are two players, have played together. If they have, the loop brakes and continues with the next pair of 'n players. If all pair of players have matched playing against each other, the fuction returs a True, otherwise a False.

TEST CASES

there are two players "n" and one game "m' and the game is [[1, 2]]. So check(2,1,[[1,2]]) will give an Answer = 'True'.
Reasoning: There are two players and one game, getting the only pair (1,2) with '2' players and only one game which is [1,2]. For that, player 1 matches with player two, so the function returns a True.

there are four players (n), 2 games (m) and the games are: [[1, 2, 3, 4], [4, 3, 1, 2]] So check(4, 2, [[1, 2, 3, 4], [4, 3, 1, 2]]) will give an answer = False.
Reasoning: There are four players with two games. It iterates the first pair which is (1,2),then iterates through two games. The first game is [1,2,3,4] and checks if player one has been the opponent of player 2 in teams [1,2] and [3,4] and it has not been, iterates game [4,3,2,1] and see if player one has been opponent of player 2 in teams [4,3] and [2,1]. Here, also, player 1 has not been an opponent of player 2, and 'both_played' keeps on "False", stops iterations and the function returns a "False".

There are four players with two games and the games are: [[1, 2, 3, 4], [1, 3, 2, 4]] So, check(4, 2, [[1, 2, 3, 4], [1, 3, 2, 4]]) will give an answer = True.
Reasoning: The function check(4, 2, [[1, 2, 3, 4], [1, 3, 2, 4]]) first generates all possible pairs of players from 1 to 4. These pairs are [(1, 2), (1, 3), (1, 4), (2, 3), (2, 4), (3, 4)]. Then for each pair, the function checks if the two players in the pair have played against each other by checking if they were on different teams in any of the 2 rounds of games. If they have not played against each other in any of the rounds, the function returns False. In this case, all pairs of players have played against each other in the two rounds of games. Player 1 played against player 2 in the second round and against player 3 in the first round. Player 2 played against player 3 in the first round and against player 4 in the second round. Player 3 played against player 4 in the second round. Therefore, the function returns True.

There are six players with six games and the games are: [[1, 6, 3, 4, 5, 2], [6, 4, 2, 3, 1, 5], [4, 2, 1, 5, 6, 3], [4, 5, 1, 6, 2, 3], [3, 2, 5, 1, 6, 4], [2, 3, 6, 4, 1, 5]])) So, check(6, 6, [[1, 6, 3, 4, 5, 2], [6, 4, 2, 3, 1, 5], [4, 2, 1, 5, 6, 3], [4, 5, 1, 6, 2, 3], [3, 2, 5, 1, 6, 4], [2, 3, 6, 4, 1, 5]]) the answer is "True".
Reasoning: The function check(6,6, [1, 6, 3, 4, 5, 2], [6, 4, 2, 3, 1, 5], [4, 2, 1, 5, 6, 3], [4, 5, 1, 6, 2, 3], [3, 2, 5, 1, 6, 4], [2, 3, 6, 4, 1, 5]]) first generates all possible pairs of players from 1 to 6 ((1,2),(1,3),(1,4),(1,5),(1,6),(2,3)....). . Then for each pair, the function checks if the two players in the pair have played against each other by checking if they were on different teams in any of the 6 rounds of games. If they have not played against each other in any of the rounds, the function returns False. In this case, all pairs of players have played against each other in the six rounds of games. For example, player 1 played against player 2 in the first round and against player 3 in the third round, player 2 played against player 3 in the forth round and against player 4 in the first round. Player 3 played against player 4 in the firstd round. And so on. Therefore, the function returns True.

There are six players with six games and the games are: [[3, 1, 4, 5, 6, 2], [5, 3, 2, 4, 1, 6], [5, 3, 6, 4, 2, 1], [6, 5, 3, 2, 1, 4], [5, 4, 1, 2, 6, 3], [4, 1, 6, 2, 5, 3]])) So, check(6,6,,nt(check(6, 6, [[3, 1, 4, 5, 6, 2], [5, 3, 2, 4, 1, 6], [5, 3, 6, 4, 2, 1], [6, 5, 3, 2, 1, 4], [5, 4, 1, 2, 6, 3], [4, 1, 6, 2, 5, 3]])) is False.
Reasoning: The function check(6,6, [[3, 1, 4, 5, 6, 2], [5, 3, 2, 4, 1, 6], [5, 3, 6, 4, 2, 1], [6, 5, 3, 2, 1, 4], [5, 4, 1, 2, 6, 3], [4, 1, 6, 2, 5, 3]]) first generates all possible pairs of players from 1 to 6 ((1,2),(1,3),(1,4),(1,5),(1,6),(2,3)....). . Then for each pair, the function checks if the two players in the pair have played against each other by checking if they were on different teams in any of the 6 rounds of games. If they have not played against each other in any of the rounds, the function returns False. In this case, not all pairs of players have played against each other in the six rounds of games, so the answer is "False". For example, player 1 played against player 2 in the first round and against player 3 in the second round, but palyer 1 has not plaplayer 2 played against player 3 in the forth round and against player 4 in the first round. Player 3 played against played against player 4, so the function returns "False".
To check the code click[here](code)
