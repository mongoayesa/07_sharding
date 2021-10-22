# Sharding en MongoDB

Arquitectura distribuida de los cluster de servidores en la que los datos de algunas de las colecciones se
reparten entre los diferentes shards (particiones) para escalar horizontalmente nuestros sistemas.

## Componentes del sharding

- Shards. Cada una de las particiones en las que se distribuyen los datos (cluster)
- Config server. Cluster con los metadatos de los shards.
- Mongos (router). Servidor que enruta las operaciones a cada shard.

- Chunk. Mecanismo automatizado de migración de datos de un shard a otro para balancear la colección.