# GRU-Recurrent-Neural-Networks-A-Smart-Way-to-Predict-Sequences-in-Python
Gated Recurrent Units (GRU) and Long Short-Term Memory (LSTM) have been introduced to tackle the issue of vanishing / exploding gradients in the standard Recurrent Neural Networks (RNNs).

We know that RNNs utilize recurrent units to learn from the sequence data, which is true for all three types — standard RNN, LSTM, and GRU.
However, what happens inside the recurrent unit is very different between them.

For example, standard RNN uses a hidden state to remember information. Meanwhile, LSTM and GRU introduce gates to control what to remember and what to forget before updating the hidden state. In addition to that, LSTM also has a cell state, which acts as long-term memory.

How does GRU work?

GRU is similar to LSTM, but it has fewer gates. Also, it relies solely on a hidden state for memory transfer between recurrent units, so there is no separate cell state. 

1–2 Reset gate — previous hidden state (h_t-1) and current input (x_t) are combined (multiplied by their respective weights and bias added) and passed through a reset gate. Since the sigmoid function ranges between 0 and 1, step one sets which values should be discarded (0), remembered (1), or partially retained (between 0 and 1). Step two resets the previous hidden state multiplying it with outputs from step one.

3–4–5 Update gate — step three may seem analogous to step one, but keep in mind that weights and biases used to scale these vectors are different, providing a different sigmoid output. So, after passing a combined vector through a sigmoid function, we subtract it from a vector containing all 1s (step four) and multiply it by the previous hidden state (step five). That’s one part of updating the hidden state with new information.

6–7–8 Hidden state candidate — after resetting a previous hidden state in step two, the outputs are combined with new inputs (x_t), multiplying them by their respective weights and adding biases before passing through a tanh activation function (step six). Then the hidden state candidate is multiplied by the results of an update gate (step seven) and added to previously modified h_t-1 to form the new hidden state h_t.
Next, the process repeats for timestep t+1, etc., until the recurrent unit processes the entire sequence.

Now, we will use GRU to create a many-to-many prediction model, which means using a sequence of values to predict the following sequence. Note that GRU could also be used in one-to-one (not recommended because it’s not sequence data), many-to-one, and one-to-many setups.

GRU and LSTM are similar not only in their architecture but also in their predictive ability. Hence, it’s up to you to try them both before picking your favourite. 
