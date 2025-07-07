Ejemplo 4.2 Cálculo de densidad y RDF usando COM del sistema etanol-hexano

En la carpeta deben estar los siguientes archivos:
 a) input.dat
 b) pairparameters.dat
 c) structure.dat

1. Abrir el archivo input.dat y modificar los parametros para calcular los RDF’s de etanol-etanol, etanol-hexano, hexano-hexano usando COM
 .
 .
 .
compute         rdfc_nvt all rdf 500  ?  ?
	- se modifico el interrogantes por los números identificativos -
 
2. Ejecutar el programa explícitamente usando:
 a) lmp_serial < input.dat
 b) ó lammps < input.dat (Homebrew)

#######(Densidad)########
3. Para observar el comportamiento de la densidad usando el archivo eta_hex.dens depurando y guardando un archivo eta_hex_1.dens:
tail -1000 eta_hex.dens > eta_hex_1.dens

4. Elaborar la gráfica en xmgrace usando:
xmgrace eta_hex_1.dens

5. Ver la densidad promedio abriendo el archivo prom_eta_hex.dens y comparar con el valor experimental de la mezcla (T=298.15 K P=1 atm) 0.7363 gr*cm^-3
	- [(ultima densidad simulada promedio - densidad experimental.7363 ) / densidad experimental .7363]*100 = porcentaje de error -

#######(RDF’s)########

6. Rdf de etanol-etanol, depurar la salida y guardarla en un archivo denominado RDFCOMe.rdf usando: 
 tail -1000 rdf_com1.rdf > RDFCOMe.rdf

7. Seleccionar las columnas 2 y 3 y guardar el archivo en RDFCOMee.rdf usando:
 awk 'NF==4 && $1+0==$1 {print $2, $3}' RDFCOMe.rdf > RDFCOMee.rdf

8. Elaborar la gráfica en xmgrace usando:
 xmgrace RDFCOMee.rdf

9. Repetir los pasos del 3 al 5 para generar las gráficas RDF de:   
 etanol-hexano

 a) tail -1000 rdf_com2.rdf > RDFCOMe_.rdf
 b) awk 'NF==4 && $1+0==$1 {print $2, $3}' RDFCOMe_.rdf > RDFCOMeh.rdf
 d) xmgrace RDFCOMeh.rdf

 hexano-hexano

 a) tail -1000 rdf_com3.rdf > RDFCOMh.rdf
 b) awk 'NF==4 && $1+0==$1 {print $2, $3}' RDFCOMh.rdf > RDFCOMhh.rdf
 c) xmgrace RDFCOMhh.rdf

10. Abrir movieEMD.lammps en OVITO para visualizar el comportamiento de (O-H) del etanol, para mejorar la visualización selecciona las partículas 5 y 6 en data source usando particle type PARA color coding y radius
   ovito movieEMD.lammps

11. Obtener las gráficas RDF para los archivos rdf_c4oh.rdf y rdf_c5ho.rdf, asimilando los pasos del 6 al 8.
 Usar un nombre diferente al original. 
 a) tail -1000 rdf_c4oh.rdf > rdf_c4oh-1.rdf
 b) cut -f 2-3 -d' ' rdf_c4oh-1.rdf > RDF_c4oh_clean.rdf
 c) xmgrace RDF_c4oh_clean.rdf