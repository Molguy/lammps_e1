# lammps_e1
Instructivo, archivos de entrada y log's de la simulación del ejemplo 1,

Comandos para la ejecucion en terminal:

    export OMP_NUM_THREADS=2

para el solido:

    mpirun -np 2 lmp_mpi < in_s.LJ
.

    tail -100 LJ_T0.5.rdf > LJSolid_c.dat
.

    awk '{print $2, $3}' LJSolid_c.dat > RDFSolid.dat
.

    xmgrace -display :0 RDF_solid.dat

para el liquido:

    lmp_mpi < in_l.LJ
.

    tail -100 LJ_T4.rdf > LJLiquid_c.dat
.

    awk '{print $2, $3}' LJLiquid_c.dat > RDFLiquid.dat
.

    xmgrace -display :0 RDFLiquid.dat

para el gas:

    mpirun -np 2 lmp_mpi < in_g.LJ
.

    tail -100 LJ_T10.rdf > LJGas_c.dat
.

    awk '{print $2, $3}' LJGas_c.dat > RDFGas.dat
.

    xmgrace -display :0 RDFGas.dat 
