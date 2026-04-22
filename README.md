# GameLink
Repositorio con las instrucciones para el despliegue de la base de datos en Neo4J "GameLink" cuyo propósito es didáctico para la clase de BAE en 1ºDAM.

## Instrucciones para el despligue con Docker
1. Clonar el repositorio
```
git clone https://github.com/slayaglez/GameLink-Neo4J.git
cd GameLink-Neo4J
```
2. Crear el .env desde la plantilla
```
cp .env.example .env
```
3. Crear las carpetas que Neo4j necesita
```
mkdir -p data logs plugins
```
4. Levantar Neo4j
```
docker compose up -d
```
5. Esperar a que esté healthy y cargar los datos
```
docker exec -it neo4j-gamelink cypher-shell \
  -u neo4j -p gamelink1234 \
  --file /var/lib/neo4j/import/datos.cypher
  ```
Si funciona deberían salir muchos INSERTS, tras ello entra en:
__http://localhost:7474/__