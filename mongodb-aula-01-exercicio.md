# MongoDB - Aula 01 - Exercício
autor: Filipe Leuch Bonfim

## Importando os restaurantes

    ```
     mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    connected to: 127.0.0.1
    Mon Nov  9 22:04:50.483 dropping: be-mean.restaurantes
    Mon Nov  9 22:04:50.771 check 9 25359
    Mon Nov  9 22:04:50.983 imported 25359 objects


    ```

## Contando os restaurantes

    ```
    nz-fedora(mongod-2.4.6) be-mean> db.restaurantes.find({}).count()
    25359

    ```
