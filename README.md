# be-mean-modulo-mongodb

Repositório criado para armazenar os exercicios do módulo de Mongodb do [Workshop de BE MEAN - Instagram](https://github.com/Webschool-io/be-mean-instagram), da [Webschool.io](https://github.com/Webschool-io)

### Aula 01
#### [Export e Import](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/module-mongodb/export_import.md)

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
#### [use db, show dbs/collections, insert/save](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/classes/mongodb/class-02-resolved.md)

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
#### [find,findOne, Operadores de Aritmética/Lógicos/Existênciais/Negação](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/module-mongodb/find-findOne.md)

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
#### [Save, Update, Operadores de array](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/module-mongodb/update.md)

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
#### [Options, Operadores de array/negação](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/module-mongodb/find-findOne.md)

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
#### [Distinct, group, limit, skip, aggregate](x)

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
#### [Relacionamentos](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/module-mongodb/relations.md)

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
#### Explain, Índices, [Réplicas](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/module-mongodb/replica.md), [GridFs](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/module-mongodb/gridfs.md)

 - [Slides](https://docs.google.com/presentation/d/1KXxmcwd47x4v2SymyiBPK7ucn80PruSvcw4mZ5S3nWc/edit?pli=1#slide=id.ge8eaeb64b_110_8)
 - [Vídeo](https://www.youtube.com/watch?v=IXz4IL0da1k)
 - [Descrição do exercício](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/classes/mongodb/class-06.md)

 - [Resolução do exercício](https://github.com/filipe1309/be-mean-modulo-mongodb/blob/master/exercises/class-06-resolved-filipe1309-filipe-leuch-bonfim.md)

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


### Aula 07
#### Réplicas (continuação ...), [Sharding](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/module-mongodb/sharding.md), [Gerenciamento de usuários](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/module-mongodb/users-and-passwords.md)

 - [Slides](https://docs.google.com/presentation/d/1KXxmcwd47x4v2SymyiBPK7ucn80PruSvcw4mZ5S3nWc/edit?pli=1#slide=id.gea0103700_69_22)
 - [Vídeo](https://www.youtube.com/watch?v=1ElYrkSIvII)

#### Resumo:
```
Réplicas (continuação ...)
    Árbitro -> desempate, voto de minerva
        serviço que não possui réplica, e não pode virar réplica primária
        dica: colocar em uma máquina com pouco hd e memória, pois o árbitro não consome muitos recursos
        - vota quando existe um empate na votação de uma nova réplica primária

        Porque usar?
            Para, quando a réplica primária for rebaixada, seja escolhida uma réplica secundária, evitando o empate.

        Quando usar?
            quando tem um um número par de réplicas

        Como usar?
            - Adicionar qunado existe um número par de membros (réplica primária e secundárias)
            mkdir /data/arb/ && cd /data/arb/
            mongod --port 30000 -dbpath /data/arb --replSet replica_set
            - conectar na réplica primária e adicionar o árbitro com rs.addArb()
            rs.addArb("127.0.0.1:30000")


        Comunicação do árbitro com os outros membros
            - votar durante eleições
            - heartbeats (pings para avisar que está em execução)
            - dados de configuração

Sharding
    é o processo de armazenamento de dados em várias máquinas, para o crescimento de dados
    São adicionadas mais máquinas para suportar o crescimento de dados e o I/O.

    Escalabilidade vertical
        - mais recursos no mesmo servidor

    Escalabilidade horizontal
        - mais servidores
        - sharding mondoDb

    Porque usar?
        Por causa da queda drástica de performance, devido a páginação de dados que ocorre quando a memória ram é excedida pelo MongoDB. (coleção > Memória RAM)

    Quando usar?
        A partir da verificação de que uma coleção do banco de dados está se apreximando do quantidade de memória RAM do servidor.

    Como usar?
        1º entendo a arquitetura do shard:
            3 serviços:
                - shards: onde ficam os dados
                - config servers:
                        servidores de configuração do cluster, instância do MongoDB com os metadados. Os metadados mapeiam os chunks (pedaços) de dados para os shards.
                - routers:
                    Instância de mongos, que roteia o I/O para os shards.
                    Recebem as requisições, busca no shard correto e entrega a resposta

            Criando um cluster:
                Config Server:
                    mkdir \data\configdb
                    mongod --configsvr --port 27010

                Router:
                    mongos --configdb localhost:27010 --port 27011

                Verifica conexões do mongos
                    mongos
                        db._adminCommand("connPoolStats");

                Shards
                    - criando as pastas
                    mkdir /data/shard1 && mkdir /data/shard2 && mkdir /data/shard3
                    - criar shards
                    mongod --port 27012 --dbpath /data/shard1
                    mongod --port 27013 --dbpath /data/shard2
                    mongod --port 27014 --dbpath /data/shard3
                    Registrando os shards no routes
                    - conecata no router
                    mongo --port 27011 --host localhost
                    - registra os shards
                    > sh.addShard("localhost:27012")
                    {"shardAdded": "shard0000", "ok": 1}
                    > sh.addShard("localhost:27013")
                    {"shardAdded": "shard0001", "ok": 1}
                    > sh.addShard("localhost:27014")
                    {"shardAdded": "shard0002", "ok": 1}

                    Especificar qual database irá shardear
                    (no mongos) -> sh.enableSharding("db")
                    sh.enableSharding("be-mean")

                    Especificar qual coleção dessa database irá ser shardeada
                    -> sh.shardCollection("db.coleção", shardKey), // shardKey = campo que será "quebrado"
                    sh.shardCollection("be-mean.notas", {"_id": 1})

                    inserindo dados (no mongos)
                    for (i = 1; i < 100000; i++ ) {
                        db.notas.insert({
                            tipo: "prova",
                            nota: Math.random() * 100,
                            estudante_id: i,
                            active: true,
                            date_created: Date.now(),
                            escola: "Webschool",
                            pais: "Brasil",
                            rg: i*3
                        });
                    }

Comandos de gerenciamento de usuários
    autenticação e autorização: coleção system.users do banco de dados admin
    comandos:
        createUser -> cria um novo usuário no db em que está, retorna erro se duplicado.
            sintaxe:
            db.runCommand (
                {
                    createUse: "nome",
                    pwd "senha",
                    customData: {},
                    roles [
                        {role: "role", db: "db"} | "role",
                    ]
                    digestPassword: boolean, // Opcional, TRUE o próprio mongodb cria um hash random com sha1
                    writeConcern: {"wc"}
                }
            )

            Acesso requerido
                grantRole

            Ex:
                Craindo um adm:
                use admin
                db.createUser(
                    {
                        user: "FilipeAdmin",
                        pwd: "admin123"
                        roles: [
                            { role: "userAdminAnyDatabase", db: "admin" }
                        ]
                    }
                )

        updateUser -> altera um usuário
            sintaxe:
                db.updateUser (
                    {
                        user: "nome",
                        pwd "senha",
                        customData: {},
                        roles [
                            {role: "role", db: "db"} | "role",
                        ]
                        digestPassword: boolean, // Opcional, TRUE o próprio mongodb cria um hash random com sha1
                        writeConcern: {"wc"}
                    }
                )

                Acesso requerido (Ação/Papel)
                    revokeRole -> para atualizar papéis de um usuário
                    grantRole -> para adicionar uma função a um usuário
                    changeAnyPassword e changeAnyCustomData-> para alterar o pwd ou o customData de um usuário
                    changeOwnPassword e changeOwnCustomData -> para alterar o próprio pwd ou o customData

                Ex:
                db.runCommand (
                    {
                        updateUser: "FilipeAdmin",
                        customData: { teacher: false },
                    }
                )

                CUIDADO!!!!
                Atualizar os papéis, substituirá completamente os anteriores.
                Para adicionar ou remover funções sem substituir todas:
                    grantRolesToUser
                    revokeRolesFromUser

            dropUser -> remove um usuário
                sintaxe:
                    db.runCommand (
                        {
                            dropUser: "usuario",
                            writeConcern: {"wc"}
                        }
                    )

                    Acesso requerido (Ação)
                        dropUser

                    Ex:
                    db.runCommand (
                        {
                            dropUser: "FilipeAdmin",
                            writeConcern: { w: "majority", wtimeout: 5000 }
                        }
                    )

            db.system.users.find() -> mostra todos usuários

            dropAllUserFromDatabase -> remove todos usuários do banco de dados
                sintaxe:
                db.runCommand (
                    {
                        dropAllUserFromDatabase: 1,
                        writeConcern: { "wc" }
                    }
                )

                Acesso requerido
                    dropUser


            grantRolesToUser -> Adiciona papéis ao usuário
                sintaxe:
                {
                    grantRolesToUser: "nome",
                    roles: [<roles>],
                    writeConcern: { <wc> }
                }

                Acesso requerido
                    grantRole

            revokeRolesFromUser -> Remove papéis do usuário
                sintaxe:
                {
                    revokeRolesFromUser: "nome",
                    roles: [<roles>],
                    writeConcern: { <wc> }
                }

                Acesso requerido
                    revokeRole

            usersInfo
                sintaxe:
                {
                    usersInfo: { user: <name>, db: <db>},
                    showCredentials: <Boolean>,
                    showPrivilegies: <Boolean>
                }

                Ex:
                - listar todos usuários
                db.runCommand ( {usersInfo: 1} )
                - listar um usuário
                db.runCommand ( {usersInfo: "FilipeAdmin"} )

        Conectar autenticando
            mongod --auth --port 27017
            mongo --port 27017 -u "FilipeAdmin" -p "admin123" --authenticationDatabase "admin"

Modelagem
    - documento max 16MB
    - mongo não se preocupa com duplicidade, e sim com desempenho

Robomongo
    - programa visual para gerenciar o mongoDb
```


## Projeto final
[Relacional -> NoSQL MongoDb](https://github.com/Webschool-io/be-mean-instagram-mongodb-projects)
Repositório: https://github.com/Webschool-io/be-mean-instagram-mongodb-projects

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
