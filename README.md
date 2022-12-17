# Miniproject-D7041E Chess Evaluation

## Intro
Our goal was to create a neural network that could evaluate chess positions and predict which side is in the lead or if the game is even. Our training data and test data use predictions made by [Stockfish](https://stockfishchess.org/) as the correct labels as it is and has been one of the highest-rated chess engines during the latest decade.

Typically chess engines use a set of algorithms to analyse a chess position. These algorithms consider a wide range of factors, for example, how each piece can move, which side has control of key squares and the safety of the king are some normal factors to consider. We wanted to try if it is possible to train a neural network to learn patterns these algorithms created by just watching different board states with the evaluation made by Stockfish used as the label.

There are two main ways a chess engine can learn how to play chess
Playing itself over and over again
Learning from watching played games

The two classic examples of these two methods are AlphaZero and Stockfish. AlphaZero is thoroughly trained by playing itself over and over and learning from the matches through reinforcement learning. Stockfish on the other hand is mainly trained by human influences.


## Setup
To setup and run our current version you simply have to open our colab link and run all the cells.

Sidenote: Install gui with chess engines :)

## Dataset
The dataset used is a collection of all games played on [Lichess](https://lichess.org/) during July 2021. The dataset comes with the current position given in [FEN format](https://www.chess.com/terms/fen-chess#piece-placement) and evaluations made by Stockfish, these evaluations will be used as our labels/correct answers.


## Model
Our model consists of the game state and trying to determine who is in the lead requires some factors. The evaluation score (eval) is a way to show who is in the lead. If the eval is positive then it means that white is in the lead and negative means black is in the lead. The first factor is simple, if you take a piece from the other player you increase your evaluation score. Depending on what piece you take it increases the score differently. A pawn is worth 1 point, a knight is 3 points etc.

But just because one side has taken more pieces than the other it does not necessarily mean that they are winning. The second factor is how the pieces are positioned, if a side has a more favourable position it means that their score will increase. The final factor is the number of future moves available which also impacts the score. 

We create our model by representing the current FEN board as a bitboard which is a 64-bit string. The evaluation can be represented by a single neuron that spikes when a board is represented. Our neural network consists of 4 hidden layers with 808 neurons with a final output layer with 1 neural. 

### Stockfish

--- Funny text

### Leela Chess Zero

--- Funny text

## Results
* Game 1 *
First try:

  Stockfish evaluation: 1.92
  
	Our prediction: -1.19
  
  Loss: 3.11
  
  
Second try:

  Stockfish evaluation: 1.92
  
	Our prediction: 0.6
  
  Loss: 1.32
  


![Game 1](https://user-images.githubusercontent.com/60612941/208242997-7008acd3-31b0-4938-bb96-9cd19958b7a2.png)

* Game 2 *
First try:
  Stockfish evaluation: -4.12
	Our prediction: -4.63
  Loss: 0.51
Second try:
  Stockfish evaluation: -4.12
	Our prediction: -4.58
  Loss: 0.46


![Game 2](https://user-images.githubusercontent.com/60612941/208243019-5c833534-fe85-4864-84b0-18c641bcf193.png)

* Game 3 *
First try:
  Stockfish evaluation: 2.68
	Our prediction: 0.04
  Loss: 2.64
Second try:
  Stockfish evaluation: 2.68
	Our prediction: 0.77
  Loss: 1.91
  
![Game 3](https://user-images.githubusercontent.com/60612941/208243173-eb5a593b-a629-4dc2-9ab5-561a23b236bd.png)

* Game 4 *
First try:
  Stockfish evaluation: 6.72
	Our prediction: 6.15
  Loss: 0.57
Second try:
  Stockfish evaluation: 6.72
	Our prediction: 6.02
  Loss: 0.7
   
![Game 4](https://user-images.githubusercontent.com/60612941/208243183-4b615707-a620-4670-939b-2bd3b8317b14.png)


* Game 5 *
First try:
  Stockfish evaluation: 10.03
	Our prediction: 9.55
  Loss: 0.48
Second try:
  Stockfish evaluation: 10.03
	Our prediction: 1.39
  Loss: 8.64
![Game 5](https://user-images.githubusercontent.com/60612941/208243211-bdb9b977-bbef-4857-9fee-aa11e6ebdf7a.png)





## Evaluation

Our neural network model yielded different results. Some scenarios gave predictions that were close to the eval value that Stockfish provides and some failed to give an accurate score. We had one issue with using the google colab feature which was that it timed out after a few hours. A model like this needs to run for multiple hours and even days to give an accurate prediction of multiple boards. Therefore, we had to lower the sample size to actually run the model and provide an example of the method.

Despite the low accuracy on some boards, our model performed well considering that 27164639 amount of boards are few in comparison to the amount of training a self-learning model needs to reach the same amount of accuracy. Another factor to consider is that our dataset is based on actual moves from lichess which means that the same moves (especially starting moves) will be repeated which means that the model trains on the same scenario multiple times. This is not a negative thing, it does mean that it will be better to predict more common boards rather than more unique boards.






