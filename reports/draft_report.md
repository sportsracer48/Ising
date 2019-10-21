# The Q2R Ising Model and the Arrow of Time
Henry Rachootin

Physicists believe that the universe is time-reversal symmetric, meaning that if one were to reverse the momentum, spin, and charge of each particle then it would soundly rewind itself back to the big bang of time. Actually doing this would be impossible, but if it is true then it raises the question: why is it that time always seems to move forward? If the universe that starts now and runs all the way back to the big bang is just as consistent as the one that starts then and goes until now, then why do we always seem to be moving away from it? The answer comes from thermodynamics: entropy increases over time, and we move forward in the direction of increasing entropy. In much the same way that we have a direction called ‘down’ since we are near a very special patch of space called the Earth, we have a direction called ‘future’ because we are near a very special patch of space-time called the Big Bang. However, how can it be that such a reversible process can have such irreversible effects at large scales over long times?

In [1], Lindgren and Olbrich present a highly simplified model of physics called the Q2R Ising Model automaton which is totally reversible. It is a one dimensional cellular automaton in which each cell’s state is a spin of either up (1) or down (-1). On each time step every other cell updates its state by flipping its spin if and only if it has one up neighbor and one down neighbor, so that the even numbered cells and odd numbered cells update on alternate steps. If we say that two adjacent matching spins contribute +1 to the total energy of the system, and two adjacent mismatched spins contribute -1, then these spins flip whenever doing so would not change the total energy. By alternating evens and odds, we ensure that the automaton is reversible; If we take a state and translate it left or right by one cell, it will evolve backwards to its initial condition. A sample of the automaton from a random initial condition is shown below:

![](https://raw.githubusercontent.com/sportsracer48/Ising/master/code/p50n500m500.png)

Lindgren and Olbrich analyzed the system mathematically, and found that if the automaton started with a random distribution of ups and downs with some bias towards one or the other, it would converge over time to an even distribution of ups and downs. They defined the entropy of the system by how far it was from an even distribution, so I used overall probability of a cell being spin up as a stand-in for entropy. I wrote a program to simulate the Q2R automaton, and found that their analysis was correct, as shown below, where the probability stays near 0.5 for any initial probability:

![](https://github.com/sportsracer48/Ising/blob/master/code/outMu.png)

However, a different story emerges when we look at the actual graphs of the probability over time:

![](https://raw.githubusercontent.com/sportsracer48/Ising/master/code/p_0%3D.01.png)
![](https://raw.githubusercontent.com/sportsracer48/Ising/master/code/p_0%3D.1.png)
![](https://raw.githubusercontent.com/sportsracer48/Ising/master/code/p_0%3D.2.png)
![](https://raw.githubusercontent.com/sportsracer48/Ising/master/code/p_0%3D.4.png)
![](https://raw.githubusercontent.com/sportsracer48/Ising/master/code/p_0%3D.5.png)

It looks like the probability varies more over time for initial conditions with low initial entropy (starting strongly biased towards down) while always hovering around 0.5. Indeed, when we graph the variance of the probability over time, we get a beautiful power law relationship:

![](https://github.com/sportsracer48/Ising/blob/master/code/outSigma.png)

This is _not_ what we would expect from the real world. In reality two systems which start with different entropy will approach the same equilibrium _and_ hover around it with the same variance, if they have the same temperature. In this model it is as if initial entropy and temperature are coupled, and there is no way to uncouple them. This casts some doubt on the explanatory value of the model, since it fails to capture the fact that entropy and temperature are not totally coupled.

[1] Lindgren, K. & Olbrich, E. J. The Approach Towards Equilibrium in a Reversible Ising Dynamics Model: An Information-Theoretic Analysis Based on an Exact Solution. Stat Phys (2017) 168: 919. https://doi.org/10.1007/s10955-017-1833-8 
