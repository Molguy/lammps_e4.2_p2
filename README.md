# lammps_e4.2_p2
El log de la simulación no fue arrojado, pero en cambio se tiene un registro en la terminal del ejemplo 4.2 parte 2 que tambien sirve para revisar su ejecucion.

    lmp_serial < input.dat
.
    
    tail -1000 eta_hex.dens | xmgrace -
.

    tail -1000 rdf_com1.rdf | awk 'NF==4 && $1+0==$1 {print $2, $3}' > RDFCOMee.rdf
.    
    
    tail -1000 rdf_com2.rdf | awk 'NF==4 && $1+0==$1 {print $2, $3}' > RDFCOMeh.rdf
.    

    tail -1000 rdf_com3.rdf | awk 'NF==4 && $1+0==$1 {print $2, $3}' > RDFCOMhh.rdf
.    
    
    xmgrace RDFCOMee.rdf RDFCOMeh.rdf RDFCOMhh.rdf
.

    ovito movieEMD.lammps
.

    tail -1000 rdf_c4oh.rdf > rdf_c4oh-1.rdf
    cut -f 2-3 -d' ' rdf_c4oh-1.rdf > RDF_c4oh_clean.rdf
    tail -1000 rdf_c5ho.rdf > rdf_c5ho-1.rdf
    cut -f 2-3 -d' ' rdf_c5ho-1.rdf > RDF_c5ho_clean.rdf
    xmgrace RDF_c4oh_clean.rdf RDF_c5ho_clean.rdf 
