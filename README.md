# Protein-Simulation-in-LAMMPS

The objective of this project is to simulate a coarse-grained protein in multiple types of
solvents. We will do this by using LAMMPS to establish the interactions between
different types of particles and incrementally increasing the complexity of the particle
simulating the protein. Our first goal is to add multiple large particles where they begin in a
mixed state and subsequently phase separate out of solution. The interactions between large
particles will be zero or yukawa interactions while small particle interactions will follow the
Lennard-Jones potential. We will have soft repulsive interactions between the large and small
particles. Our second goal is to incorporate a polymer immersed with at least two different types
of solvent particles. Time permitted, we will replace the large particle with a coarse-grain
simulation of a protein using the Martini model.

We can divide our work into three parts mentioned below:

Part 1 is to model the proteins as a set of simple large particles (A) surrounded by the
solvent (B).

Part 2 is to model the proteins as a cluster or polymer (A) surrounded by the solvent (B).

Part 3 is to use a Martini model (a coarse-grained force field) to model the protein (A) in the solvent (B).

Some steps/procedures of coding are as follows:
•	Define the large particles (A):   mass/density/size
•	Define the small particles (B): mass/density/size
•	Define the interactions of the large particles with each other (AA): zero/yukawa
•	Define the interactions of the small particles with each other (BB): Lj fluid interactions
•	Define the interactions between large particles with small particles (AB): Repulsive hare/soft
•	Set size of simulation grid
•	Set percentage of area filled with particles/density of particles
•	Number of particles
•	Set temperature/energy level of system
•	Set time step information: How long time step and Number of time steps       
•	Set image information
•	Save an image every 10000 frames
•	Run the simulation

We will have soft repulsive interactions between the large and small
particles. Our second goal is to incorporate a polymer immersed with at least two different types
of solvent particles. 

Time permitted, we will replace the large particle with a coarse-grain
simulation of a protein using the Martini model


Polymer Simulations

all code was derived from the following website: 
http://www.zqex.dk/index.php/method/lammps-demo

please make sure you have LAMMPS installed. For more information on this, use the following link: 

https://lammps.sandia.gov

transfer all files onto your computer or remote terminal found in the folder “Polymersimulations”

in the folder you will simulations for three different polymers, a single polymer, 5 monomeric polymers, a circular polymer, and 4 starred polymer

all .lam files will be used to run the simulation while .input files will contain information regarding bond types and bond angles

RUNNING A SINGLE POLYMER

cd polymer

then change input file

nano poly.lam 

look for the read_data command and make sure it reads as below

read_data poly1.input

save and exit

RUNNING THE SIMULATION

use the command: 

lmp -in poly.lam

you will get several images saved in the folder “img” 

RUNNING 5 POLYMERS

to run multiple polymers, change the read_data command as: 

read_data poly5.input

you can change from poly5.input to poly1.input to alternate between 5 polymers to a single polymer respectively

use the same input as before to run the simulation.

RUNNING POLYMERS IN A SOLVENT

open the brownian.lam file and modify the read_data command depending on whether you want to run a single polymer or 5 polymers

modify parameters as deemed fit. Ex: number of particles, or interactions between particles.

to run the simulation, use the command: 

lmp -in brownian.lam

you will get several images saved in the folder “img” 

to run either star or circle polymer simulation, make sure you are in the corresponding directory

to run a single polymer simulation without solvent, use 

lmp -in poly.lam

again, make sure the read_data command is poly1-circle.input or poly1-star.input depending on which simulation and hence, directory you’re in 

to run a single polymer simulation with solvent, use 

lmp -in brownian.lam

again, make sure the read_data command is poly1-circle.input or poly1-star.input depending on which simulation and hence, directory you’re in

these parameters should already be set in the downloaded files 

%Challenges to simulate the coarse-grained protein using the Martini model
Initially we planned to do the followings

Choose small protein of interest
Compile protein structure from PDB into a coarse-grained model
Import protein into our system in Part I as large particle

But there are some challenges to implement the simulation of the coarse-grained protein using the Martini model






