# CS 238 Final Project: Bidding Simulation and Optimization

This project focuses on simulating the bidding process for a house and optimizing the decision-making strategy using Value Iteration on an MDP (Markov Decision Process).

## Simulation

In the simulation phase, we simulate the bidding process with other buyers for a house, considering a maximum of 5 bidding rounds. The key steps involved are as follows:

1. Generate 4 bids given the listed price, which is sampled from a Gaussian distribution with a mean equal to the listed price.
2. If the mean bid exceeds the listed price, the seller asks for more offers.
3. Our agent chooses a random action.
4. The bidding game ends after a maximum of 5 rounds.

To gather data, we simulate 200,000 bidding scenarios for listing prices ranging from $1 million to $5 million, assuming a fixed budget.

Based on this data, we create Transition and Rewards matrices using the Maximum Likelihood Model. The transition probabilities are estimated as follows:

T(s′ | s, a) ≈ N(s, a, s′) / N(s, a)

The reward function is estimated using the formula:

R(s, a) ≈ ρ(s, a) / N(s, a)

## Optimization

The optimization phase involves setting up an MDP with the approximate Transition and Rewards matrices, defining states and actions. We then employ the Value Iteration algorithm to find the optimal value function and policy for our MDP.

Value Iteration updates the value function directly using the Bellman Backup:

Uk+1 (s) = maxa(R(s, a) + γ∑s' T(s' | s, a)Uk (s'))

Since we have a finite horizon problem, we set the discount factor (γ) to 1. This guarantees convergence to the optimal value function.

Finally, we extract the best policy from the optimal value function obtained through Value Iteration.

## Usage

To replicate and explore the results of this project, you can follow these steps:

1. Clone this repository to your local machine.
2. Ensure that you have the required dependencies and packages installed.
3. Run the simulation script to generate the Transition and Rewards matrices based on the provided data.
4. Set up the MDP with the obtained matrices and define the states and actions.
5. Run the optimization script using the Value Iteration algorithm to find the optimal value function and policy.
6. Extract the best policy and analyze the results.

Feel free to modify the simulation parameters, such as the number of bidding scenarios or the price range, to further investigate the bidding process and its optimization.

For more detailed information and implementation details, please refer to the code and comments provided in the repository.

## Credits

This project was developed by Hannah Ashai, Raghav Sharma, and Candice Penelton. If you have any questions or suggestions, please feel free to reach out.
