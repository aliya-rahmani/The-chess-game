# The-chess-game
This program is a chess game. The user may play against a friend or the
computer.

The game state is mainly stored as a 2D list of strings, and most of the
processing is thus done on a list of strings.

The GUI takes the current state and displays it on the screen. The GUI allows
drag and drop movement of pieces as well as click-click movement.

The AI that plays against the human evaluates all possible moves made by either
player up to a certain level of depth. The AI evaluates each position by giving
it a score. The higher the value of the score, the more favorable a position
is for white, and the lower the value of the score, the more favorable the
position is for black. Knowing that white will try to get the score to be higher
and black will try and get the score to be lower, the AI assumes the best play from
either side as it traverses up the search tree and chooses the best move to be
played. A problem that may arise is the number of positions that need to be
evaluated. Even at 3 levels of depth, thousands of positions have to be
evaluated.
Several methods are used in this program to reduce positions that are searched:
1. Alpha-beta pruning: As a result of evaluating a position it can be found
that a portion of the search tree can be ignored as no further evaluations can
guarantee better results. This can happen because white and black are against
one another. White plays what is best for it and black plays what is best for it,
so it would make sense for white to ignore any portion of the tree where black
has a clear upper-hand that it can choose to play.
2. Transposition table: Often, two different pathways in a search tree can result
in the same board being evaluated. Instead of evaluating the same board several
times, the program stores a table of values in a dictionary where the keys are
the positions. This way, repeated positions can have their evaluations looked up
fairly quickly, as the board state is hashed.
3. Opening Book - An opening book is again a dictionary that stores board
positions often seen in the beginning few moves in chess. Appropriate moves that
can be played at such positions are stored in the dictionary. A random move is
selected and played from the list of suggested moves without searching if the AI
finds itself confronting such a board position. Note that this opening book was
recorded by myself and so it does not have many positions stored in it.
