# AntColonySystem-TSP
Ant Colony System (ACS) algorithm to solve the Traveling Salesman Problem (TSP)

In this code, I have implemented the Ant Colony System (ACS) algorithm to solve the Traveling Salesman
Problem (TSP). The ACS algorithm is a type of Ant Colony Optimization (ACO) algorithm, which is inspired
by the foraging behavior of ants. The goal is to find an efficient tour that visits all cities and returns to the
starting city.
Here is the breakdown of the key components of the code:

* Initialization:

    I start by defining several parameters such as the number of ants (m), pheromone influence (alpha),
    distance influence (beta), evaporation rate (rho), and the number of cities (n). I also initialize matrices
    and lists to store pheromone levels, distances, and candidate lists.

* Candidate Lists:

    To implement the POPMUSIC algorithm, I provide a method take_candidates to select a list of candidate
    cities for a given city based on their distances. Additionally, I read candidate lists generated from external
    files using the LKH implementation.

* ACS Class:

    I define the ACS class, which encapsulates the ACS algorithm. The class has methods for state transition,
    local updating of pheromones, and global updating based on the best tour found. The class also includes
    an iteration function that performs the main steps of the ACS algorithm.

* Iteration:

    The iteration method initializes ants' positions and constructs tours based on the state transition rules.
    Local pheromone updating is performed during the tour construction. After constructing tours, the
    lengths of the tours are computed, and the best tour is updated if a shorter tour is found. Finally, global
    pheromone updating is performed based on the best tour.

* Solve:

    The solve method is responsible for executing a specified number of iterations and returning the
    resulting tours and their lengths. Optionally, it includes a 2-opt local search optimization step to improve the solution further.

* Visualization:

    The code includes visualization using matplotlib to show the progress of the algorithm. It plots the best
    tour found at each iteration, providing a visual representation of the optimization process. In particular, I
    have modified the code in the file IO_manager/io_tsp so that it could plot both the optimal tour (if it
    exists) and the solution founded. Then, I added the possibility to plot it at each step, resulting in an
    animation.

## Notes:
For the global update, we have two options:
1) Update the pheromone of the edges in the best tour every time an ant pass by an
edge in the best tour

2) Update the pheromone of the edges in the best tour just once, even if no ants pass by
the edges in the best tour
I implemented both of them, but the first one seems to work really better
Regarding the seed, I set it at 0 to have deterministic results. I did not do an average on multiple seeds
since it was not required, and would have triplicated the already too high computational time.

## Results:
I include here just a few plots to keep the report cleaner. In particular I reported three plots for the first
problem, with q=0.98, for each solver (basic, 2.opt and 2.opt + POPMUSIC), and just two examples of the
other two problems, with the same q and the basic solver. In the repository only the first problem has its
optimal solution stored, so I couldn’t plot it for the other two instances. Anyway, you can see the optimal
solution with the blue dashed line under my own solution, represented by the green continuous line.
The first two plots report the iterations, while the other ones report the number of generated tours (that
are just the iterations multiplied by m=10 in my case, since I check for the time constraint only after
every ant has completed its tour, so I generate exactly 10 tours for each iteration). It’s just a different
notation, in my case.