Ejemplo 1. Cálculo de RDF en un sistema LJ a diferentes Temperaturas

En la carpeta deben estar el siguiente archivo que será editado 3 veces:
 1) in.LJ

En este punto la Temperatura es 0.5, comprobar que a estas condiciones se trata de un sólido.

1. Ejecutar el programa en singlecore (se puede usar paralelo pero sin el mpirun) usando: 
./lmp_serial < in.LJ o ./lmp_mpi < in.LJ

Se debera generar
 1)trayectoria: dump_T[{}.lammpstrj
 2)salida: LJ_T{T}.rdf
 3)estado final final_T{T}.data

2. Depurar la salida y guardarla en un archivo usando: 
tail -100 LJ_T0.5.rdf > LJSolid_c.dat

3. Seleccionar las columnas 2 y 3 y guardar en otro archivo usando:
awk '{print $2, $3}' LJSolid_c.dat > RDFSolid.dat

4. Elaborar la gráfica en xmgrace usando:
xmgrace -display :0 RDF_solid.dat

5. Modificar el archivo de entrada in.LJ en la linea 1 y 11, cambiando la Temperatura a 4.0 y el archivo donde se guardarán los datos de RDF a LJLiquid.dat

6. Repetir los pasos del 1 al 4 para generar la gráfica de RDF en xmgrce:
 a) ./lmp_mpi < in_l.LJ
 b) tail -100 LJ_T4.rdf > LJLiquid_c.dat
 c) awk '{print $2, $3}' LJLiquid_c.dat > RDFLiquid.dat
 d) xmgrace -display :0 RDFLiquid.dat

7. Modificar el archivo de entrada in.LJ en la linea 1 y 11, cambiando la Temperatura a 10.0 y el archivo donde se guardarán los datos de RDF a LJGas.dat

8. Repetir los pasos del 1 al 4 para generar la gráfica de RDF en xmgrce:
 a) ./lmp_mpi < in_g.LJ
 b) tail -100 LJ_T10.rdf > LJGas_c.dat
 c) awk '{print $2, $3}' LJGas_c.dat > RDFGas.dat
 d) xmgrace -display :0 RDFGas.dat