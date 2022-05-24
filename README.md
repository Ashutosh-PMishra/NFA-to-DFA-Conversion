# NFA-to-DFA-Conversion
This repository consist of FAFL and CDSS project.

[View Demo](http://127.0.0.1:5500/index.html)

# ABSTRACT
This is the Project for the Automata Theory/Formal Languages term project. The goal was to develop an algorithm that converts a Non-deterministic Finite Automata (NFA) to a Deterministic Finite Automata (DFA). This project describes the design process, implementation, and visualization of the algorithm developed.
The objective of this project was to develop a visualized procedure that converts an NFA into its equivalent DFA. The conversion process will never fail because if a language can be recognized by an NFA, there will always be an equivalent DFA. Because our procedure should be able to handle a NFA containing λ-productions (i.e. null-productions or - productions), the final DFA should have the ability to contain multiple states within a single state. In addition, a trap state will also be included in the resulting DFA if any state in the given NFA has an undefined transition.

# INTRODUCTION
The first step when developing this algorithm, or in other words, the NFA-to-DFA visualization procedure, the differences between an NFA and a DFA had to be known. Unlike a DFA, an NFA is capable of being in multiple states at once, having undefined or λ transitions, and multiple transitions when given only a single input. 
##► Differences between NFA and DFA 
 	An NFA is similar to a DFA, except that there are three main differences that are allowed in a NFA but not allowed in a DFA: 
1) NFA permits λ-transitions 
2) NFA is able to have undeclared or undefined transitions 
3) NFA may contain transitions to different states after receiving a single input (can be in multiple states at once) 
Two automates are equivalent if and only if they both accept the same language. As a result, it can be concluded that if both automates accept the same language, then they are equal. It is also important to know that the NFA-to-DFA procedure will always terminate because the number of states in a NFA and its equivalent is always finite. The final DFA may have 2 n states, where n is the number of states of the original NFA.

##► Important factors during the conversion process 
During the process, there are important factors that the algorithm should track during the conversion process: 
1) Is a trap state required? 
2) What is the initial state?
3) What are the final states? 
4) Does the original NFA contain λ-transitions? 
5) How will the algorithm know when it is done?
6) Is there a λ-transition from initial state to final state?

# Steps for converting NFA to DFA:
Step 1: Initially Q' = ϕ
Step 2: Add q0 of NFA to Q'. Then find the transitions from this start state.
Step 3: In Q', find the possible set of states for each input symbol. If this set of states is not in Q', then add it to Q'.
Step 4: In DFA, the final state will be all the states which contain F(final states of NFA)

# CONCLUSION
Although the process of converting an NFA to a DFA seems simple when doing it manually, it is much more complicated to convert this process into code. One of the most challenging parts during development was to determine the transitions for the new state. For this part, it was necessary to look at every state from the original NFA that compose the new state, then search for all the states in the transition table and finally join the closure for those states. The use of data structures such as classes and stacks facilitated the development. There are a lot of details involved in creating the DFA. For example, the algorithm must keep track of the initial and final states, check to see if a trap state is necessary, and perform the closure of any lambda transitions present in the NFA, and so on. The algorithm needed to handle all these details in order to create the correct DFA, for example, there was one bug that we had where the initial state of the DFA was not final, but in the correct answer, and the initial state should also be final. That’s because when there’s a λ-transition from the initial state to a final state in the original NFA, the initial state has to be a final state in the DFA, we noticed and fixed this bug during the testing phase. Additionally, after the DFA is created, there was also the reduction procedure which removed useless or repetitive states and transitions.



