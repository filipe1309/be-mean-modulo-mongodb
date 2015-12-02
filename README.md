# be-mean-modulo-mongodb

Repositório criado para armazenar os exercicios do módulo de Mongodb do [Workshop de BE MEAN - Instagram](https://github.com/Webschool-io/be-mean-instagram), da [Webschool.io](https://github.com/Webschool-io)

### Aula 01
####[Export e Import](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/module-mongodb/export_import.md)

 - [Slides](https://docs.google.com/presentation/d/1KXxmcwd47x4v2SymyiBPK7ucn80PruSvcw4mZ5S3nWc/edit?pli=1#slide=id.p)
 - [Vídeo](https://www.youtube.com/watch?v=leYxsEAL_yY)
 - [Descrição do exercício](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/mongodb/export_import.md)
 - [Resolução do exercício](https://github.com/filipe1309/be-mean-modulo-mongodb/blob/master/exercises/class-01-resolved-filipe1309-filipe-leuch-bonfim.md)

#### Resumo:
Nesta aula foi apresentado uma visão geral do Workshop de BE MEAN - Instagram.
Um pouco de teria sobre bancos de dados NoSQL (analogia das cervejas =)).

    Bancos Relacionais -> Respostas
	Bancos NoSQL -> Perguntas
	Princípais grupos NoSQL
	- chave/valor
	- documento
	- grafos
	- colunas
	- mistos

Também foi passado um pouco de teoria especificamente sobre o mongoDB.
- C++
- Schemaless(não Shemale =P)
- JSON/BSON
- Réplica
- Sharding (problema de falta de mmemória)
- Terminologia
- ...

Por fim, foram passada alguns comandos básicos(mongoimport/export) e configuraçõẽs especificas do mongoDB, além de uma API chamada Mongo Hacker.


### Aula 02
####[use db, show dbs/collections, insert/save](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/classes/mongodb/class-02-resolved.md)

 - [Slides](https://docs.google.com/presentation/d/1KXxmcwd47x4v2SymyiBPK7ucn80PruSvcw4mZ5S3nWc/edit?pli=1#slide=id.p)
 - [Vídeo](https://www.youtube.com/watch?v=PaNVk0V2UNI)
 - [Descrição do exercício](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/classes/mongodb/class-02-resolved.md)
 - [Resolução do exercício](https://github.com/filipe1309/be-mean-modulo-mongodb/blob/master/exercises/class-02-resolved-filipe1309-filipe-leuch-bonfim.md)

#### Resumo:
Nesta aula foram vistos diversos comandos do mongoDb.

```
use db ('cria' ou muda para um db existente)
show dbs (banco não é criado até a 1ª inserção)
insert (1ª inserção + demorada, pois pré aloca espaço no HD)
show collections
createCollection (para criar coleção vazia)
find() (retorna cursor)
save() (insere e salva)
findOne() (retorna objeto)
iterar um cursor: while( cur.hasNext()) {cur.next()}
```


### Aula 03
####[find,findOne, Operadores de Aritmética/Lógicos/Existênciais/Negação](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/module-mongodb/find-findOne.md)

 - [Slides](https://docs.google.com/presentation/d/1KXxmcwd47x4v2SymyiBPK7ucn80PruSvcw4mZ5S3nWc/edit?pli=1#slide=id.p)
 - [Vídeo](https://www.youtube.com/watch?v=cIHjA1hyPPY&feature=youtu.be)
 - [Descrição do exercício](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/classes/mongodb/class-03-resolved.md)
 - [Resolução do exercício](https://github.com/filipe1309/be-mean-modulo-mongodb/blob/master/exercises/class-03-resolved-filipe1309-filipe-leuch-bonfim.md)

#### Resumo:
Nesta aula foram vistos diversos comandos do mongoDb.
```
_id (UUID, 4b - timestamp do Unix, 3b - ex: mac, 2b - PID, 3b - contador(hex) random)
```
Sintaxe das buscas
```
find({clausulas}, {campos}) => clasulas = WHERE, campos = SELECT
Query
	var query = {campo: valor} = JSON (WHERE do relacional)
	...find(query)
Fields
	Basta apenas informar os campos a serem retornados na busca
	0 = FALSE,
	1 = TRUE
	var fields = {campo: boolean(0/1), ...} = JSON (SELECT do relacional)
	Campo _id sempre retorna, para eliminar o _id na busca:
		{..., _id: 0}
Busca + complexas:
Operadores aritméticos -> {campo: {OA: valor}}
	<  -> $lt
	<= -> $lte
	>  -> $gt
	>= -> $gte

Operadores lógicos -> {OL: [{COND1}, {COND2}]}
	OR -> $or
	NOR (Not OR) -> $nor
	E -> $and

Operadores existenciais -> {campo: {OE: boolean(true/false)}}
	$exists (ex nuvem de tags)

```

### Aula 04 - Parte 1
####[Save, Update, Operadores de array](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/module-mongodb/update.md)

 - [Slides](https://docs.google.com/presentation/d/1KXxmcwd47x4v2SymyiBPK7ucn80PruSvcw4mZ5S3nWc/edit?pli=1#slide=id.gd8825a620_4_118)
 - [Vídeo](https://www.youtube.com/watch?v=ONzJsNbv15U)

#### Resumo:
```
db.collection.update(query, modifications, options)
    Ao contrário do save(), não é necessário buscar o documento antes de poder modificá-lo

    Operadores de modificação
        {$set: { campo: valor }} -> modifica um valor ou cria se não existir
        {$unset: { campo: 1 }} -> remove campos
        {$inc: { campo: valor }} -> incrementa um valor no campo, se o campo não existir, irá criar e setar o valor

Operadores de array
    {$push: { campo: valor }} -> adiciona um valor ao campo do tipo array. Se o campo não existir irá criá-lo, e se o campo não for do tipo array, retornará erro
    {$pushAll: { campo: [array de valores] }} -> adiciona cada valor do [array de valores] ao campo do tipo array. Se o campo não existir irá criá-lo, e se o campo não for do tipo array, retornará erro
    {$pull: { campo: valor }} -> retira o valor do campo do tipo array. Se o campo não existir não faz nada, e se o campo não for do tipo array, retornará erro
    {$pullAll: { campo: [array de valores] }} -> retira cada valor do [array de valores] do campo do tipo array. Se o campo não existir não faz nada, e se o campo não for do tipo array, retornará erro
```

### Aula 04 - Parte 2
####[Options, Operadores de array/negação](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/module-mongodb/find-findOne.md)

 - [Slides](https://docs.google.com/presentation/d/1KXxmcwd47x4v2SymyiBPK7ucn80PruSvcw4mZ5S3nWc/edit?pli=1#slide=id.gd8825a620_4_118)
 - [Vídeo](https://www.youtube.com/watch?v=ozbmQb6SVQk)
 - [Descrição do exercício](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/classes/mongodb/class-04.md)
 - [Resolução do exercício](https://github.com/filipe1309/be-mean-modulo-mongodb/blob/master/exercises/class-04-resolved-filipe1309-filipe-leuch-bonfim.md)

#### Resumo:
```
db.collection.update(query, modifications, options)
    options -> configura alguns valore diferentes do padrão para o update
        {
            upsert: boolean, // default: FALSE
                Caso o documento não seja encontrado, insere o objeto passado como modificação
            multi: boolean, // default: FALSE
                atualizada todos os objetos da 'collection' com o que foi passado no campo 'modifications' 'modifications'
            writeConcern: document
                descreve a garantia, ou nível de garantia, de escrita do MongoDb. Fraco -> retorna rápido
        }

    Operadores de modificação
        setOnInsert -> define valores que serão adicionados caso ocorra um upsert



    Operadores de array
    in = or
        {campo: {$in: [array de valores]}}, retorna os docuemtnos que possuem algum dos valores do [array de valores]
    $nin -> {campo: {$nin: [array de valores]}}
        retorna documentos que não possuem os valores passados.
    all = and
        {campo: {$all: [array de valores]}}
        retorna os documentos que possuem todos os valores definidos.

    Operadores de negação
        $ne = Not Equal
            {campo: {$ne: valor}}
            não aceita regex =/
        $not = !
        $remove = remove o documento e não a coleção(neste caso seria drop()), é multi: true -> ele deixa vc fazer MERDA!!!!

```

### Aula 05
####[Distinct, group, limit, skip, aggregate](x)

 - [Slides](https://docs.google.com/presentation/d/1KXxmcwd47x4v2SymyiBPK7ucn80PruSvcw4mZ5S3nWc/edit?pli=1#slide=id.ge839fbc67_123_11)
 - [Vídeo](https://www.youtube.com/watch?v=1eHc8reT_Vk)
 - [Descrição do exercício](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/classes/mongodb/class-05.md)
 - [Resolução do exercício](https://github.com/filipe1309/be-mean-modulo-mongodb/blob/master/exercises/class-05-resolved-filipe1309-filipe-leuch-bonfim.md)

#### Resumo:
```
count() + rápido que o length()
O count() aceita as mesma queries que o find(), update() ...

distinct() == no SQL,
    retorna array direto, e não um documento
    podendo usar o lengh direto
    aceita valor, nome de array

sort().reverse()

limit( valor_limit ).skip( valor_limit * num_págino ) == paginação

/* Agrupa */
db.collection.group({
    initial: {total: 0} // variavel acumuladora
    cond: {...}
    reduce: function(curr, result) { // execuatdo para cada documento da collection, curr == documento atual
    },
    finalize: function(result) { // roda 1 vez no fim

    }
})

/* Agrupa e efetua alguma operação,
geralmente o que é possível fazer no group tbm é possivel no aggregate e vice-versa
 */
db.collection.aggregate({
    $group: {
        var: {$avg : '$campo'} // retorna a média da coluna/campo
        // outras opções: $sum
    }
})

/* aggregate com match(cond)
== group + cond
*/
aggregate([
    {$match: {campo: valor/expressão}},
    {
        $group: ...
    }
])
```

### Aula 06 - Parte 1
####[Relacionamentos](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/module-mongodb/relations.md)

 - [Slides](https://docs.google.com/presentation/d/1KXxmcwd47x4v2SymyiBPK7ucn80PruSvcw4mZ5S3nWc/edit?pli=1#slide=id.ge8eaeb64b_110_8)
 - [Vídeo](https://www.youtube.com/watch?v=5bbWeEEzRQM)

#### Resumo:
```
Relacionamentos entre collections
**JOINS NO eCxistem!!!!!!!!!!!!!**
 -> mas existem 2 formas:
    Manual
        - salvando o _id de uma coleção em outra
        var pokemons = [
            {"_id": ObjectId("12321...")},
            {"_id": ObjectId("22321...")},
            {"_id": ObjectId("32321...")},
        ];
        var json = {
            "name": "Meus pokemons",
            pokemons: pokemons
        }
        db.inventario.insert(json)

        var pokemons = []
        var getPokemon = function(id){ pokemons.push(db.pokemons.findOne(id)) }
        var inventario = db.inventario.findOne()
        // inventario.pokemons = array de ids de pokemon
        inventario.pokemons.forEach(getPokemon) // da um forEach no array de id de pokemons, executando o getPokemon para cada id

    Dbref
        - Convenção para representar um documento relacionado
        - é interessante utilizar quando os documentos referenciados estão en outra db
        $ref -> nome da coleção referenciada
        $id -> ObjectId do documento referenciado
        $db -> db da coleção referenciada

    -> no mongoose utiliza-se o populate =)

```

### Aula 06 - Parte 2
####[]()

 - [Slides](https://docs.google.com/presentation/d/1KXxmcwd47x4v2SymyiBPK7ucn80PruSvcw4mZ5S3nWc/edit?pli=1#slide=id.ge8eaeb64b_110_8)
 - [Vídeo]()
 - [Descrição do exercício](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/classes/mongodb/class-06.md)
    Name:
    db.pokemons.find({name: ?? }).explain('executionStats').executionStats
    db.pokemons.createIndex( { name: 1 } )
    db.pokemons.find({name: ?? }).explain('executionStats').executionStats

    2 campos:
    db.pokemons.find({name: ?? , attack: ??}).explain('executionStats').executionStats
    db.pokemons.createIndex( { name: 1, attack: 1 } )
    db.pokemons.find({name: ??, attack: ?? }).explain('executionStats').executionStats


 - [Resolução do exercício](https://github.com/filipe1309/be-mean-modulo-mongodb/blob/master/exercises/class-05-resolved-filipe1309-filipe-leuch-bonfim.md)

#### Resumo:
```
Explain
    Porque?
        Mostra o que banco está fazendo, como ele executa as queries internarmente
            _rand() -> número aleatório entre 0 e 1
                ex: db.cl.find().limit(1).skip( _rand() *  db.cl.count() )
            db.cl.find(query).explain() -> mostra como o mongo fez para executar a query
            .explain('executionStats') -> mostra + infos
            .explain('executionStats').executionStats.executionTimeMillis
    Quando?
        Quando quiser analisar a forma em que a query foi executada, para otimizações

Index (Indices)
    Porque?
        melhora consideravelmente o desempenho da consultas para os campos indexados
        cuidado para não criar indices desnecessariamente, pois aumentará consideravelmente  o tamanho do db
        db.cl.getIndexes()
        db.system.indexes.find()
        Para criar um indice:
            Simples:
                db.cl.createIndex( { campo: ordem } ) // ordem natural:1, inversa:-1
            Composto:
                db.cl.createIndex( { campo: ordem, campo2: ordem } )
        Para remover um indice?
            db.cl.dropIndex( { campo: ordem } )

GridFs
    Sistema de arquivos do mongoDb
        BSON -> max 16 MB
        documentos maiores que 16 MB -> GridFs
        Não joga o arquivo inteiro para a memória RAM
        Quando usar?
            quando seu FS limita a quantidade de arquivos em memória
            para manter seus arquivos e metadados automaticamente sincronizados (réplicas)
            acessar informações de grandes arquivos sem ter que carregar todos na memória
        Quando NÃO usar?
            atualizar conteúdo, para isto se utiliza versões de arquivos
            arquivos < que 16 MB podem ser armazenados como 'BinData'
        Como usar?
            mongofiles (fora do mongo)
            mongofiles -d nome_db put arquivo
            Ao inserir com o grdFs sao criadas 2 coleções (fs.chunks e fs.files)
                fs.chunks
                    arquivos binários divididos em pequnas partes de 255KB cada
                    chunk:
                        { _id, files_id, n, data}
                fs.files
                    metadados dos arquivos armazenados
                    file:
                        {_id, length, chunkSize, uploadDate, md5, filename}
                        -> o campo md5 pode ser utilizado para encontrar arquivos duplicados
            Utilizar em um servido próprio, separado do mongod, para configurá-lo da melhor forma possível

Réplica
    Espelhamento dos dados de um servidor para outro
    ReplicaSet -> conjunto de replicas, com até 50 membros/réplicas contando com os árbitros
    Operações ocorrem na réplica primária e replicadas para as secundárias (opLog)
    2 etapas:
        1 - initial Sync
            inicia o "passo-a-passo" da réplica
                - Clona db
                - Aplica alterações (opLog)
                - Constrói indices (menos _id)
                - transição para um estado normal/secundário
        2 - Replication
            - etapa que deixa os dados atualizados/sincronizados


    opLog - Log de operações
        é um capped collection (coleção de tamanho finito) especial que mantém os registros de todas as operações de modificação de dados

    -> operações feitas no primário, e registradas no opLog do mesmo.
    -> (consistência eventual) os secundários copiam e aplicam o opLog do primário de forma assíncrona

    Porque usar?
        Garantia de dados!!
        indicado pelo mongoDb no minimo 1

    Quando usar?
        SEMPRE!

    Como usar?
        1 - criar diretório para cada réplica /data/rs1, /data/rs2, /data/rs1
        2 - criar 3 servidores de réplica, com suas respectivas portas e seus logs
        comando:
            mongod --replSet nome_do_replica_set --port porta_do_replica_set --dbpath caminho_do_replica_set --logpath nome_do_arquivo_de_log_do_replica_set --fork
        #!/bin/bash
        mongod --replSet replica_set --port 27017 --dbpath /data/rs1 --logpath /data/rs1/log.txt --fork
        mongod --replSet replica_set --port 27018 --dbpath /data/rs2 --logpath /data/rs2/log.txt --fork
        mongod --replSet replica_set --port 27019 --dbpath /data/rs3 --logpath /data/rs3/log.txt --fork
        https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/module-mongodb/data/create-replicaset.sh
        3 - configurando e iniciando (no mongo com o parametro --port porta_do_replica_set)
        mongo --port 27017
        rsconf = {
            _id: "replica_set",
            members: [
                {
                    _id: 0,
                    host: "127.0.0.1:27017"
                }
            ]
        }
        rs.initiate(rsconf)
        Depois disto a replica primária estará criada
        o proximo passo é adicionas as répliacas secundárias na primária
        rs.add("127.0.0.1:27018")
        rs.add("127.0.0.1:27019")

        verificar replicas secundarias
        mongo --port 27018
        mongo --port 27019

    (primária) Ver status da configuração da Replica set
    rs.status()

    Ver status do opLog
    rs.printReplicationInfo()

    Para rebaixa a primária para secundário
    rs.stepdown()
    depois deste comando o mongoDb irá eleger uma secundária para primária, e cada réplica tem um voto para indicar qual deverá se tornar a primária (Impate -> árbitros)


```

## Projeto final
[Relacional -> NoSQL](https://github.com/Webschool-io/be-mean-instagram-mongodb-projects)

### Links importantes:
- MongoDb
 - [Apostila MongoDB](https://github.com/Webschool-io/be-mean-instagram/tree/master/apostila/mongodb)
 - [Chat MongoDB - Rocket](http://be-mean.rocket.chat/channel/mongodb)
 - [E-book MongoDb - Guia rápido](http://mundointerativo.com/b/e-book-mongodb-guia-rapido-para-iniciantes/)
 - [FAQ MongoDb](https://github.com/Webschool-io/be-mean-instagram-mongodb-FAQ)
 - [Mongo Hacker](https://github.com/TylerBrock/mongo-hacker)

- Geral
 - [Chat Geral - Rocket](http://be-mean.rocket.chat/channel/general)
 - [Class Guidelines](https://github.com/Webschool-io/be-mean-instagram/blob/master/class-guidelines.md)
 - [Como entregar o exercício](https://github.com/Webschool-io/be-mean-instagram/wiki/Exerc%C3%ADcios)
 - [Dagora - BE MEAN](http://dagora.net/be-mean/)
 - [EAD - Dagora](http://aprenda.dagora.net/login/)
 - [Facebook - Webschool.io - Workshop Be MEAN](https://www.facebook.com/groups/workshop.be.mean/)
 - [Material de estudos - Pré-requisito](http://aprenda.dagora.net/discussao/1/1/material-de-estudos-como-pre-requisitos/)
 - [Repositório de exercícios](https://github.com/Webschool-io/be-mean-instagram-mongodb-excercises)
 - [Wiki](https://github.com/Webschool-io/be-mean-instagram/wiki)
