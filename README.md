Installazione Cluster Mariadb Galera
===================================================

## Prerequisiti ##
Assicurarsi che sulle macchine sia presente:
- la scheda di interconnessione
- un disco dedicato hai dati del Db
- che siano stati dati gli ip a tutte le schede di rete


Installazione e configurazione iniziale dei nodi 
--------------------------------

- fare il download con git clone
- modificare il file **galera.hosts** con gli ip degli host da raggiungere
- modificare le variabili sotto **group_vars/all/vars.yml**

    datadev_name: sdb <br>
    mysql_dir: "/mysql/data" <br>
    mariarelease: 10.4 <br>
    galeraclusterid: 1 <br>
    galeraclustername: "nome del cluster" <br> 
    galerainterconnectinterface: "nome device di interconnesione di solito ens192" <br>
    sst_user: galera1 <br>
    sst_pass: galera1 <br>
    node_ips: "tutti gli ip di interconnessione separati dalla virgola" <br>


- fare un accesso in ssh sugli host da raggiungere per rispondere "yes" alla domanda degli "host conosciuti"
- lanciare lo script ansible e alla richiesta delle credenziali mettere quelle di root dei nodi:
    
    `ansible-playbook -i galera.hosts galera.yml -k`

!! N.B.!!
Prima di effettuare il bootstrap lanciare la SECURE INSTALLATION su entrambi i nodi del cluster

Bootstrapping MariaDB Galera cluster
------------------------------------
- lanciare lo script ansible e alla richiesta delle credenziali mettere quelle di root dei nodi:

    `ansible-playbook -i galera.hosts galera_bootstrap.yml -k`
