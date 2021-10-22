# Chunks en Sharding

Agrupación lógica de documentos de una coleccion sharding con un rango (basado en la key sharding) para
distribuir uniformemente los documentos en los diferentes shard.
El motivo del mecanismo es reducir el impacto de las migraciones o balanceo de documentos.

Agrupa documentos hasta un determinado tamaño (chunkSize: 64 MB) y cuando el tamaño del chunk se supera
realiza un proceso automático (split) porque l que se divide en dos generando un nuevo chunck.

Cuando se produce una diferencia entre el numero de chunks de un shard y otro, se produce una migración
automática (siempre que esté activado el balanceador) de los chunk hacia el shard más proximo en rango.

Esa descompensación que lanza la migracion depende del número de chunks totales:

nº Chunk totales        Diferencia que lanza migración
menos de 20 chunks                  2
20-79 chunks                        4
mas 80                              8

## Modicación del tamaño

Ventaja distribuye mas uniformemente la colección
Incoveniente se produciran mas migraciones (se puede mitigar programando el balance)

