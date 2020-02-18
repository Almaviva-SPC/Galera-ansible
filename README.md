Installazione Cluster Mariadb Galera
===================================================

### Prerequisiti ###
--------------------------------
Assicurarsi che sulle macchine sia presente:
- la scheda di interconnessione
- un disco dedicato hai dati del Db
- che siano stati dati gli ip a tutte le schede di rete


Installazione e configurazione iniziale dei nodi 
--------------------------------

- fare il download con git clone
- modificare il file **galera.hosts** con gli ip degli host da raggiungere
- modificare le variabili sotto **group_vars/all/vars.yml**
- fare un accesso in ssh sugli host da raggiungere per rispondere "yes" alla domanda degli "host conosciuti"
- lanciare lo script ansible e alla richiesta delle credenziali mettere quelle di root dei nodi:
    
    `ansible-playbook -i galera.hosts galera.yml -k`

!! N.B.!!
Prima di effettuare il bootstrap lanciare la SECURE INSTALLATION su entrambi i nodi del cluster

Bootstrapping MariaDB Galera cluster
------------------------------------
- lanciare lo script ansible e alla richiesta delle credenziali mettere quelle di root dei nodi:

    `ansible-playbook -i galera.hosts galera_bootstrap.yml -k`
