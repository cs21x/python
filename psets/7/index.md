# Simulating the Spread of Disease and Virus Population

In this problem set, using Python and pylab you will design and implement a stochastic simulation of patient and virus population dynamics, and reach conclusions about treatment regimens based on the simulation results.

In this problem set, using Python and pylab you will design and implement a stochastic simulation of patient and virus population dynamics, and reach conclusions about treatment regimens based on the simulation results.

## Getting Started

For this lab, you will be using the classes from Problem Set 7. Feel free to use your own implementations from Problem Set 7, or you may use the compiled version provided in the download above.

## Implementing a Simulation With Drugs

For this part, use the skeleton code provided in ps8.py.
In this problem, we consider the effects of both administering drugs to the patient and the ability of virus particle offspring to inherit or mutate genetic traits that confer drug resistance. As the virus population reproduces, mutations will occur in the virus offspring, adding genetic diversity to the virus population. Some virus particles gain favorable mutations that confer resistance to drugs.
In order to model this effect, we introduce a subclass of SimpleVirus called ResistantVirus. ResistantVirus maintains the state of a virus particle’s drug resistances, and account for the inheritance of drug resistance traits to offspring. Implement the ResistantVirus class.
You will test your implementation in problem 2.

We also need a representation for a patient that accounts for the use of drug treatments and manages a collection of ResistantVirus instances. For this we introduce the Patient class, which is a subclass of SimplePatient. Patient must make use of the new methods in ResistantVirus and maintain the list of drugs that are administered to the patient.
Drugs are given to the patient using the Patient class’s addPrescription() method. What happens when a drug is introduced? The drugs we consider do not directly kill virus particles lacking resistance to the drug, but prevent those virus particles from reproducing (much like actual drugs used to treat HIV). Virus particles with resistance to the drug continue to reproduce normally. Implement the Patient class.

## Running and Analyzing a Simulation with a Drug

In this problem, we will use the implementation you filled-in for problem 1 to run a simulation. You will create a Patient instance with the following parameters, then run the simulation and answer several questions:

* viruses, a list of 100 ResistantVirus instances
* maxPop, Maximum Sustainable Virus Population = 1000

