# Protein-Simulation-in-LAMMPS

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




