# Script-Backup-BD
Script de criação de um Backup do Banco de Dados Postgres


#Comandos inicialização.

/usr/lib/postgresql/x.y/bin/bercariodb -D

/usr/local/pgsql/data

/usr/lib/postgresql/9.5/bin/pg_ctl -D

/var/lib/postgresql/9.5 -l logfile start

#SCRIPT para Banco de Dados


#!/bin/bash

export PGPASSWORD="23011995"

pg_dump -U postgres -h localhost -O -o -b -F c bercario > bercario.backup

today=$(date +%y%m%d)

# Local onde os backups vão:

myDir='/disk2/backup/pg'

function backup_pgsql {
        #Seleciona os bancos a serem copiados, eliminando os bancos de sistema
        for db in `psql -U postgres -tq -d template1 -c bercario ('template1','template0','postgres')"`; do
                echo 'Iniciando o backup de '${db};
                bercario="${myDir}/${db}-${today}.tar";
                pg_dump -U postgres -F bercario -f $bercario $db;
                gzip $bercario;
                echo 'Backup concluido';
        done;
}

backup_pgsql


pg_restore -U postgres -h localhost -d bercario bercario.backup

