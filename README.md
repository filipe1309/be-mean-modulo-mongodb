# be-mean-modulo-mongodb

Repositório criado para armazenar os exercicios do módulo de Mongodb do [Workshop de BE MEAN - Instagram](https://github.com/Webschool-io/be-mean-instagram), da [Webschool.io](https://github.com/Webschool-io)

### Aula 01
- [Export e Import](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/mongodb/export_import.md)

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
- [use db, show dbs/collections, insert/save](https://github.com/Webschool-io/be-mean-instagram/blob/master/apostila/classes/mongodb/class-02-resolved.md)
 
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


### Links importantes:
- MongoDb
 - [Mongo Hacker](https://github.com/TylerBrock/mongo-hacker)
 - [Chat MongoDB - Rocket](http://be-mean.rocket.chat/channel/mongodb)
 - [Dagora - BE MEAN](http://dagora.net/be-mean/)
 - [Apostila MongoDB](https://github.com/Webschool-io/be-mean-instagram/tree/master/apostila/mongodb)

- Geral
 - [Chat Geral - Rocket](http://be-mean.rocket.chat/channel/general)
 - [Class Guidelines](https://github.com/Webschool-io/be-mean-instagram/blob/master/class-guidelines.md)
 - [Como entregar o exercício](https://github.com/Webschool-io/be-mean-instagram/wiki/Exerc%C3%ADcios)
 - [EAD - Dagora](http://aprenda.dagora.net/login/)
 - [Facebook - Webschool.io - Workshop Be MEAN](https://www.facebook.com/groups/workshop.be.mean/)
 - [Material de estudos - Pré-requisito](http://aprenda.dagora.net/discussao/1/1/material-de-estudos-como-pre-requisitos/)


