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
(Part 3 remains unfinished at this time)

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


**Part 1: Brownian Motion -> Assembly of Large Particles**

The original file for part 1 was "brownian.lam" taken from: http://www.zqex.dk/index.php/method/lammps-demo
which showed the brownian motion of a large particle in a solvent.

A video from this original file is in: Protein-Simulation-in-LAMMPS/Part1_Brownian_Motion/Brownian_movies/img_Brownian_test.avi
The video file img_Brownian_5Particles.avi shows the same settings, but with 5 large particles undergoing brownian motion.

The two code files found in the Part1_Brownian_Motion/BrownianMotionCodes folder contain all the code needed to create the videos
found in the folder: 

Part1_Brownian_Motion/Brownian_movies/

In order to run the files:

transfer all files onto your computer or remote terminal found in the folder Part1_Brownian_Motion/BrownianMotionCodes

please make sure you have LAMMPS installed. For more information on this, use the following link:

https://lammps.sandia.gov

In the computer terminal make sure to navigate to the correct folder using the cd (change directory) command.
Use the ls (list) command to make sure all the relevant files are in the folder.

Run the file using the command:

lmp -in AW_brownian.lam

you will get a set of images saved in the folder “img”

These images can then be viewed as jpeg files or opened as a stack and viewed and saved as a movie. (e.g. avi file)

CHANGING THE INTERACTION TYPES BETWEEN PARTICLES

The file AW_brownian is set up to allow for easy recreation of any of the type of interactions used to create the 
videos in the Brownian_movies folder. 

Each type of interactions used is listed as a pair_style command with corresponding pair_coeff commands
commented out in the file. To use the desired pair_style interactions uncomment the pair_style command and corresponding pair_coeff commands
Make sure all other pair_style and pair_coeff commands are commented out.
run the file again using the steps above to recreate the movies in the Brownian_movies file.

The types of interactions between particles and how to represent them in the lammps file were found 
using the LAMMPS manual https://lammps.sandia.gov/doc/pair_style.html

The movie img_Brownian_3Interactiontypes_Yukawa_cutoff5_energy10_vel1.5.avi was created with the following pair_style commands:

pair_style hybrid lj/cut 2.0 soft 7.0 yukawa 3.5 5.0

pair_coeff 1 1 lj/cut 1.0 1.0

pair_coeff 1 2 soft 10.0 5.0

pair_coeff 2 2 yukawa 10.0 5.0

This command defines the following interactions between particles:

define lennar-jones interactions between small particles (1) with 1

define yukawa interactions between large particles (2) with 2

define soft repulsive interactions between 1 and 2

The numbers following the pair_coeff command refer to the particles undergoing the interaction type. 

1 is the small particles

2 is the larger particles.

The other numbers in the pair_style and pair_coeff command lines can be changed to simulate different conditions of a system.
More information can be found at: https://lammps.sandia.gov/doc/pair_style.html
And some examples and information (including basic graphs) of the interaction potentials can be found in the file:
Protein-Simulation-in-LAMMPS/Protein_Simulations_in_Lammps_Part1_Brownian_Motion_AlaunaWheelerPhys230.pdf

changes to the original brownian.lam file, 
such as increased mass of the large particle and decreased velocity of the system have been noted in the file using comments

Note:The file: AW_brownian_10x.lam
can be run using the same steps as AW_brownian.lam

It has the same interaction types as img_Brownian_3Interactiontypes_Yukawa_cutoff5_energy10_vel1.5.avi
And the interaction types can be altered the same as for AW_brownian.lam

However, it has been altered to have 10 times the number of particles, 10 times the area of the 2D box, and 10 times the number of steps
These changes are noted with comments.

A video of these changes is too large to upload to github, but can be viewed at:

https://youtu.be/eXjN_RpkbgA

A question that came up was whether the yukawa interaction is actually repulsive or attractive?
If the yukawa interaction between two larger green particles is repulsive, 
and yet they are still assembling due to the soft repulsive interactions they have with the smaller red particles, 
then it is an interesting result.

The movie img_Brownian_large_zeroType_interaction.avi sets the following interactions:

define lennard-jones interactions between small particles (1) with 1

define soft repulsive interactions between 1 and 2

define zero interactions between large particles (2) with 2

and uses the following pair_style commands:

pair_style hybrid lj/cut 2.0 soft 7.0 zero 5.0

pair_coeff 1 1 lj/cut 1.0 1.0

pair_coeff 1 2 soft 10.0 5.0

pair_coeff 2 2 zero

This showed that the large particles assemble without any attractive force between them.

The movie img_Brownian_large_lj_20energy_sigma2.avi sets the following interactions:

define lennard-jones interactions between small particles (1) with 1

define soft repulsive interactions between 1 and 2

define lennard-jones interactions between large particles (2) with 2

you can change the parameters for energy level, cutoff, and screening length (please look at lammps manual for
more info on these interaction types)

and uses the following pair_style commands:

pair_style hybrid lj/cut 7.0 soft 7.0 

pair_coeff 1 1 lj/cut 1.0 1.0 2.0

pair_coeff 1 2 soft 10.0 5.0

pair_coeff 2 2 lj/cut 20.0 2.0

This showed that the large particles assemble and then arrange into the distance from each other associated with that potential well,
but then move together as one entity.


The movie img_Brownian_large_softRepulsion_cutoff2.avi sets the following interactions:

define lennar-jones interactions between small particles (1) with 1

define soft repulsive interactions between large particles (2) with 2

define soft repulsive interactions between 1 and 2

and uses the following pair_style commands:

pair_style hybrid lj/cut 7.0 soft 7.0

pair_coeff 1 1 lj/cut 1.0 1.0 2.0

pair_coeff 1 2 soft 10.0 5.0

pair_coeff 2 2 soft 20.0 2.0

This showed that the large particles assemble even though they repel each other. They continue to repel each other, 
but are pushed back together by the interactions with the small particles.

The movie img_Brownian_large_yukawa_cutoff_15_energy100_vel_1.5.avi sets the following interactions:

define lennar-jones interactions between small particles (1) with 1

define yukawa interactions between large particles (2) with 2

define soft repulsive interactions between 1 and 2

You can change the parameters for energy level, cutoff, and screening length (please look at lammps manual for
more info on these interaction types)

and uses the following pair_style commands:

pair_style hybrid lj/cut 2.0 soft 7.0 yukawa 0.3 15.0

pair_coeff 1 1 lj/cut 1.0 1.0

pair_coeff 1 2 soft 10.0 5.0

pair_coeff 2 2 yukawa 100.0 15.0

These settings allowed the large particles to interact with each other while still farther away than before, 
and so they were able to repel each other to a certain distance away, 
although they are forced to that distance by the interactions with the smaller particles. 
And they continue to interact with each other from there, 
instead of as a roiling mass that we had in the earlier yukawa interaction experiments. 
So it is a repulsive yukawa interaction! 
But the large particles are still forced to assemble due to the interactions with the smaller particles. 
An interesting result that occurs in real systems. (e.g. Depletion forces)


A future goal of Part 1 is to determine the Time Progression of the Radial Distribution Function in order to 
measuring the self-assembly of the large particles.
We would do this by determining the pair correlation function of the large particles and how it progresses with time.

**Part 2: Polymer Simulations - Using a polymer to simulate the protein**

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

**Part 3: Using a Martini model for the protein**

%Challenges to simulate the coarse-grained protein using the Martini model
Initially we planned to do the followings

Choose small protein of interest
Compile protein structure from PDB into a coarse-grained model
Import protein into our system in Part I as large particle

But there are some challenges to implement the simulation of the coarse-grained protein using the Martini model. Such challenges involve making both the Martini force field and input files (topology, bond information, etc) compatible within LAMMPS. Unfortunately, we were unable to overcome these challenges at this time and look forward to any and all suggestions from the reader. 



