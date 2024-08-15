# Python-Gurobi-Staff-Assingment-Optimization
This project is my practice on operations research where I use Gurobi solver on Python environment to optimize the staff assignment for a factory

Given a factory with the below information:
- The factory produces 7 days a week with 3 shifts a day: morning, afternoon and evening
- The factory already planned for the demand next week and estimated the required workforce as below: Monday (6,4,3), Tuesday (5,5,5), Wednesday (6,4,4), Thurday (5,5,5), Friday (5,5,3), Saturday (6,5,4) and Sunday (5,5,4)
- The total workforce that the factory has is 20 people. According to the labor rights, a labor can only work 1 shift a day and each week, a labor must take leave at least 2 days
- If a labor works on evening shift today, he/she cannot work on the morning shift tomorrow
- So, us, as a production planner, how can we assign each labor to each day and each shift to minimize the cost, satisfy the demand but still follow the rights?

Formulation of the problem:
Sets:
I is the set of labor, I = {1,2,3,…,21}
J is the set of day, J = {1,2,3,…,7}
K is the set of shift, K = {1,2,3}

Indices:
xijk is the decision variable whether labor i is assigned to day j shift k, xijk ⤶23∊ {0,1}. ∀ i ⤶23∊ I, ∀ j ⤶23∊ J, ∀ k ⤶23∊ K
djk is the labor demand at day j shift k

Formulation 
Objective function: Min ∑24_(𝑖∊𝐼)^ ▒" "  ∑24_(𝑗∊𝐽)^ ▒" "  ∑24_(𝑘∊𝐾)^ ▒〖"x" 𝑖𝑗𝑘〗
Constraint 1: ∑_(𝑖∊𝐼)^ ▒〖"x" 𝑖𝑗𝑘〗 ≥ djk, ∀ j ⤶23∊ J, ∀ k ⤶23∊ K
Constraint 2: ∑_(𝑘∊𝐾)^ ▒〖"x" 𝑖𝑗𝑘〗≤1, ∀ i ⤶23∊ I, ∀ j ⤶23∊ J
Constraint 3: ∑_(𝑗∊𝐽)^ ▒" "  ∑_(𝑘∊𝐾)^ ▒〖"x" 𝑖𝑗𝑘〗≤5, ∀ i ⤶23∊ I
Constraint 4: "x" 𝑖𝑗3 + "x" 𝑖𝑗+11 ≤1, ∀ i ⤶23∊ I, ∀ j ⤶23∊ J
