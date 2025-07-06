# lammps_e1
Instructivo, archivos de entrada y log's de la simulación del ejemplo 1

Comandos para su ejecucion en la terminal:

    export OMP_NUM_THREADS=2

para el solido:

    mpirun -np 2 lmp_mpi < in_s.LJ
.

    tail -100 LJ_T0.5.rdf > LJSolid_c.dat


    awk '{print $2, $3}' LJSolid_c.dat > RDFSolid.dat


    xmgrace -display :0 RDF_solid.dat
