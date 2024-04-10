- a method for analyzing a given algorithm's time and memory complexities. 
- For a given operation of an algorithm, certain situations may imply a significant cost in resources, whereas other situations may not be as costly.
- The amortized analysis **considers both the costly and less costly operations together over the whole sequence of operations**.

The basic idea is that a worst-case operation can alter the state in such a way that the worst case cannot occur again for a long time, thus "amortizing" its cost. 

Generally, three methods for performing amortized analysis:
1. aggregate method
2. accounting method
3. potential method

- the choice of which to use depends on which is most convenient for a particular situation.

**Aggregate Analysis**: Determines the upper bound $T(n)$ on the total cost of a sequence of $n$ operations, then calculates the amortized cost to be $T(n)/n$. 

**Accounting method**: a form of aggregate analysis which assigns to each operation an *amortized cost* which may differ from its actual cost. Early operations have an amortized cost higher than their actual cost, which accumulates a saved "credit" that pays for later operations having an amortized cost lower than their actual cost.

**Potential method**: a form of accounting method where the saved credit is computed as a function (the "potential") of the state of the data structure. The amortized cost is the immediate cost plus the change in potential. 