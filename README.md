Installazione Cluster Mariadb Galera
===================================================


Installazione e configurazione iniziale dei nodi 
--------------------------------

- fare il download con git clone
- modificare il file galera.hosts con gli ip degli host da raggiungere
- modificare le variabili sotto group_vars/all/vars.yml
- fare un accesso in ssh sugli host da raggiungere per rispondere "yes" alla domanda degli "host conosciuti"
- lanciare lo script ansible:
    
    ansible-playbook -i galera.hosts galera.yml -k

!! N.B.!!
Prima di effettuare il bootstrap lanciare la SECURE INSTALLATION su entrambi i nodi del cluster

Bootstrapping MariaDB Galera cluster
------------------------------------
-lanciare lo script ansible:

    ansible-playbook -i galera.hosts galera_bootstrap.yml
