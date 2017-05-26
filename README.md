Este Script tem por sua finalidade realizar um backup de uma BDPOSTGRESQL, temos a declaração de variáveis e
as regras para inicialização e realização do BACKUP.

#SHELLSCRIPTPARABACKUPBDPOSTGRE

#!/bin/sh

#bkp_bercario.sh

#DATA iria imprimir a data no estilo dia-mes-ano.

DATA='/bin/date+%d-%m-%Y'

#NOME armazena o nome do arquivo de BACKUP

#O Diretório onde o arquivo será salvo neste caso é.

#/www/virtual/backup é uma pasta publica do apache.

#Coloque o diretorio onde quiser guardar o BACKUP.

NOME="/www/virtual/backup/bercario-$DATA.sql"

#Variaveis do POSTGRESQL

HOST="localhost"

USER="postgre"

PASSWORD="23011995"

DATABASE="bercario.sh"

pg_dump -h $localhost -u $postgre -p $23011995 $bercario.sh > $backup
