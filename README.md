# ideal-strength-vasp
Automatically exported from code.google.com/p/ideal-strength-vasp

Introduction
Calculating Ideal strength of crystal structure using vasp. PRL 82,2713(1999)

Details
First you need to modify vasp code. If you want to calculate ideal tensile strength, you should add 'FCELL(1,1)=0.0' to constr_cell_relax.F of vasp code. That means the Stress at x axis is fixed and vasp not relax the lattice at x axis. And if you choose ideal shear strength, you should add 'FCELL(1,3)= 0.0' and 'FCELL(3,1) = 0.0' to constr_cell_relax.F of vasp code. Here, you need to recompile vasp.

second, you should prepare input.dat and this file as below:

POSCAR

0.02 #strain

20 #step

-45.0 35.264390 0.0 # rotate Z, Y and X.

1 # 1 tensile, 2 shear

mpiexec -np 8 vasp.4.6

The first line is the name of POSCAR. The second line is strain of distortion. The third line is total step of distortion. The fourth line is degree of rotation. This is for calculating special orientation. For example, if you want to calculating ideal strength of Diamond along 100, you just set 0.0 0.0 0.0. If you want to calculate 110 orientation, you need set -45.0 0.0 0.0. If you want to calculate 111 orientation, you need set -45.0 35.264390 0.0.

It is for rotating the x, y and z axis as a Right-handed helical rule. The five line is to choose tensile of shear. The sixth line is execute command.

If you have any question or find bug, I am pleased that you send email to me.

This code was programed under guidance of Prof. Ma Yanming and Li Quan.

At that time, I was a Ph.D candidate at State Key laboratory of Superhard Materials, Jilin university

Hopefully you can cite the following papers, if you used this code. Many thanks!

Quan Li, Hanyu Liu, Dan Zhou, Weitao Zheng, Zhijian Wu and Yanming Ma, "novel low compressible and superhard carbon nitride: Body-centered tetragonal CN2" Phys. Chem. Chem. Phys., 2012, 14, 13081–13087

Miao Zhang, Mingchun Lu, Yonghui Du, Lili Gao, Cheng Lu and Hanyu Liu, "Hardness of FeB4?: Density functional theory investigation" J. Chem. Phys. 140, 174505 (2014)

Dr. Hanyu Liu

Email: lhy@calypso.cn or hanyuliu801@gmail.com
