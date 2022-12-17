# Miniproject-D7041E Chess Evaluation

## Intro
Our goal was to create a neural network that could evaluate chess positions and predict which side is in the lead or if the game is even. Our training data and test data use predictions made by Stockfish(https://stockfishchess.org/) as the correct labels as it is and has been one of the highest-rated chess engines during the latest decade.

Typically chess engines use a set of algorithms to analyse a chess position. These algorithms consider a wide range of factors, for example, how each piece can move, which side has control of key squares and the safety of the king are some normal factors to consider. We wanted to try if it is possible to train a neural network to learn patterns these algorithms created by just watching different board states with the evaluation made by Stockfish used as the label.

There are two main ways a chess engine can learn how to play chess
Playing itself over and over again
Learning from watching played games

The two classic examples of these two methods are AlphaZero and Stockfish. AlphaZero is thoroughly trained by playing itself over and over and learning from the matches through reinforcement learning. Stockfish on the other hand is mainly trained by human influences.


## Setup
To setup and run our current version you simply have to open our colab link and run all the cells.

Sidenote: Install gui with chess engines :)

## Dataset
The dataset used is a collection of all games played on Lichess(Lichess.com) during July 2021. The dataset comes with the current position given in FEN format(https://www.chess.com/terms/fen-chess#how-does-fen-work) and evaluations made by Stockfish, these evaluations will be used as our labels/correct answers.

## Model
Our model consists of the game state and trying to determine who is in the lead requires some factors. The evaluation score (eval) is a way to show who is in the lead. If the eval is positive then it means that white is in the lead and negative means black is in the lead. The first factor is simple, if you take a piece from the other player you increase your evaluation score. Depending on what piece you take it increases the score differently. A pawn is worth 1 point, a knight is 3 points etc.

But just because one side has taken more pieces than the other it does not necessarily mean that they are winning. The second factor is how the pieces are positioned, if a side has a more favourable position it means that their score will increase. The final factor is the number of future moves available which also impacts the score. 

We create our model by representing the current FEN board as a bitboard which is a 64-bit string. The evaluation can be represented by a single neuron that spikes when a board is represented. Our neural network consists of 4 hidden layers with 808 neurons with a final output layer with 1 neural. 


## Results


## Evaluation








