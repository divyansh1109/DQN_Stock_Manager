# DQN-Stock-Manager

This Deep Reinforcement Learning model is an attempt to manage the buying and selling of a stock. The main goal of this model is to predict one of the three actions, buy, sell and hold from an input of Historical Closing Prices and technical indicators like RSI and EMA.

The environment consists of the following main points:
1. history_t defines the time period of the history of stock prices that we want to feed into our model during each training step.
2. self.df is the list of all stocks' data. The self.data chooses one stock out of the available stocks in df and trains on that one. This happens every epoch. Thus giving the model different data to train on everytime, and in turn, enhancing its versatality.
3. self.capital is the initial capital the model has. The model is heavily penalised to buy stocks that are worth more than its buying capacity.
4. The ovservation vector consists of current position value, capital, RSI Closing Price to EMA ratio and history of closing prices.


Below are the important points for the reward:
1. A reward of -1 for holding the stock at each step. This ensures that our model does not hold a stock for too long for a small profit.
2. A small reward of +2 for every eligible buy to encourage activity in the portfolio.
3. Heavy penalty of -100 for either buying stocks beyond available capital, or selling stocks when none of them are present in the portfolio.
4. Other reward consists of profit/loss occured during selling.

For the training purpose, the model uses two neural networks that are similar in architecture to predict Q-value and Target Q-value respectively. The target Q-value predicting Neural Network is trained less frequently and only after certain number of steps. 
Epsilon is reduced linearly. It specifies the probability of exploration against exploitation.

Lastly, results are analysed and we observe that the model gives and average annual return of 2.86% over a period of approximately 5 years.
The images of these results are placed in the images folder.
