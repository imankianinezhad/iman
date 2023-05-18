# iman kiani
Bonus task
Design a GA (chromosome, crossover, mutation, fitness function) to solve 8-queen problem

Introduction
To express this problem in the form of this algorithm, we have considered each chromosome as an array of eight, and the indices of this array represent the columns of the chess house and each value in this array is the row number. The values of this array are non-repeating and alternating numbers from one to eight. Here I have considered the initial population as 100, but any number can be chosen as desired.
The condition for stopping the algorithm is to complete 10,000 rounds or to find the solution to the problem. The way of choosing parents to produce children is that we choose 5 chromosomes randomly and after these five chromosomes, two chromosomes that have the maximum utility function are selected. The way to calculate the usefulness of a chromosome is that for each gene or queen in a chromosome, the number of threats is calculated and from their sum and then reversing it, the value of the utility function for a chromosome is calculated. The goal is to maximize the utility function. A random point in the chromosome is also selected to produce children. The first child inherits the genes to the left of this point in the first parent and the second child inherits the genes to the left of this point in the second parent. Then, to fill the rest of the genes on the right side of this point in the first child, scroll the second parent from left to right and insert any value that was not present in the first child in the same order of scrolling. To fill the right side of the second child, we repeat the same thing with the first parent.
Two random indices are selected to mutate the children and the values in these indices are moved together. Then, the entire population is sorted according to the fitness function, and we replace the last two chromosomes, which are among the worst, with the children.
Implementation
In the following, according to the explanations given, the required functions are implemented and we give a brief explanation of each of them.
Functions
Ints :
 
The first function that is called in the implementation of this algorithm is the “ints” function to generate the initial population, which receives an input of the population size. According to the number of inputs of this function, a list of permutations of numbers one to eight is randomly generated.
Print_Chr:
 
This function is used to print a chromosome on the chess board.
Q_penalty:
 
This function calculates and returns the number of threats available for a minister. Its input is the column number of the desired minister and its corresponding chromosome. The way to calculate the meeting of two ministers is based on Manhattan distance. If we add or subtract from the column number of the two ministers based on whether the other minister is ahead or behind, the two ministers should face each other. If this happens, these two ministers will threaten each other.
Config_penalty:
 
This function returns the total amount of threats in a chromosome by calculating this value of each of the queens (genes) with the help of the Q_penalty function and their sum.
Ch_fit:
 
This function is responsible for calculating the fitness for a chromosome. By calculating the total amount of threats in a chromosome and inverting it, the utility of a chromosome is obtained. If in the chromosome, the queens do not threaten each other, or if the desired chromosome is the answer to the problem, the usefulness of that value is 2, which is the maximum.
Select:
 
This function randomly selects 5 chromosomes for reproduction. Its input is the list of total population and number of parents to select.
Tow_par:
 
This function returns the two parents of the chromosomes selected in the selection function with maximum utility.
C_O:
 
This function produces 2 children with two parents selected by the two_par function with the mentioned method.
Mut and Mutate:
 
These two functions are responsible for performing the mutation operation with the mentioned method in the produced children. The mut function takes two children and generates a probability for each. If it is below 80%, it creates a mutation in the child with the mutate function, otherwise no mutation is created.
S_Select:
 
This function also replaces the generated children with the method mentioned in the total population list.

Parameters
pop_size : initial population size.
select_random: the number of chromosomes that are randomly selected to select parents.
mut_prob: probability of mutation.
rounds: the number of iterations of the algorithm.

Final result
According to the selected population, the algorithm can reach the answer after more than 200 repetitions. In one of the executions of this algorithm, I got the answer after 273 repetitions.

Top ten chromosomes:
(4, 1, 5, 8, 2, 7, 3, 6),
(1, 5, 2, 6, 3, 7, 4, 8),
(5, 4, 2, 7, 3, 6, 8, 1), 
(4, 2, 5, 8, 1, 7, 3, 6), 
(1, 6, 4, 2, 8, 5, 3, 7), 
(1, 5, 2, 8, 4, 7, 3, 6), 
(4, 5, 1, 8, 6, 3, 7, 2), 
(1, 5, 2, 6, 3, 7, 8, 4), 
(5, 1, 2, 6, 3, 7, 4, 8), 
(1, 5, 2, 8, 4, 7, 3, 6)
The superior chromosome and the answer to the problem:
(4, 1, 5, 8, 2, 7, 3, 6)

 
