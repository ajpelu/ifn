# Prepara datos IFN

- Descargo los datos de IFN en 
este [link](https://www.miteco.gob.es/es/biodiversidad/servicios/banco-datos-naturaleza/informacion-disponible/ifn3_bbdd_descargas.htm.aspx)

- Descomprimo con: 

```
#!/bin/bash
for z in *.zip; do unzip $z && rm $z; done
```

- Con este script de bash consigo convertir la base de datos de cada provincia. Utilizo el .jar de [RebaseData](https://www.rebasedata.com/convert-access-to-xlsx-online) 

- He pagado 19 $USD para tener la licencia premium 

- Ojo necesito descargar el client-0.0.5.jar de la página de rebasedata. 

```sh
for num in {1..50}
do
provincia=$(printf "%02d" $num)
mkdir "$provincia"
java -jar /Users/ajpelu/Downloads/client-0.0.5.jar convert --api-key=f37962c0f804d81e4008a0c968945b5f --output-format=xlsx /Users/ajpelu/Downloads/raw_ifn_p/p/Ifn3p$provincia.mdb /Users/ajpelu/Downloads/raw_ifn_p/$provincia/
done
```

```sh
for num in {1..50}
do
provincia=$(printf "%02d" $num)
mkdir "$provincia"
java -jar /Users/ajpelu/Downloads/client-0.0.5.jar convert --api-key=f37962c0f804d81e4008a0c968945b5f --output-format=xlsx /Users/ajpelu/Downloads/raw_ifn_sig/sig/Sig_$provincia.mdb /Users/ajpelu/Downloads/raw_ifn_sig/$provincia/
done
```

