# EstNLTK õpipada  

**Autorid:** Dage Särg ja Sven Laut <br> 
**Toimumisaeg:** 5. november 2019 <br>
**Asukoht:** EKT konverents. Prototüübist teostuseni. Tallinn

## Ettevalmistused õpipajas osalemiseks

Õpipajas tulemuslikult osalemiseks on vaja:

* Jupyter keskonda
* EstNLTK 1.6 viimast binaarversiooni
* lokaalset Postgre serverit  

**Ma ei oska tarkvara installida:**

Sellisel juhul tuleb instaleerida virtuaalmasin koos eelinstaleeritud  Ubuntu Linux operatsioonisüsteemiga:

* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [VitualBox-i image](https://drive.google.com/open?id=1R8Cb2aIyMiD6KhvPyenR-yDYyyavxAnq)


### Conda instaleerimine

Operatsioonisüsteemide Linux, MacOS ja Windows korral on mõistlik kasutada Anaconda keskonna graafilisi instaleerimisvahendeid. Õpetused selleks leiab aadressilt [https://docs.anaconda.com/anaconda/install/](https://docs.anaconda.com/anaconda/install/)

### EstNLTK instaleerimine käsurealt

<code>
conda create --name estnltk python=3.6 <br>
conda install -n estnltk jupyter <br>
conda install -n estnltk psycopg2 <br>
conda install -n estnltk -c estnltk -c conda-forge estnltk <br>
conda install -n estnltk -c conda-forge conllu <br>
</code>

### Postgre serveri instaleerimine

Operatsioonisüsteemi MacOS korral on kõige lihtsam viis instaleerida [Postgres.app](https://postgresapp.com) kui teil pole juba varem instaleeritud lokaalset postgre serverit. 

Operatsioonisüsteemi Ubuntu Linux korral saab jälgida instaleerimisjuhendit [How to Install PostgreSQL 11 on Ubuntu 18.04 & 16.04 LTS](https://tecadmin.net/install-postgresql-server-on-ubuntu/) 

Järgnevat oleks vaja luua ka andmebaas `ekt` ja andmebaasi kasutaja ning soovi korral ka skeema `media_analysis`. Selleks tuleb postgreg serveriga õigetes õigustes ühenduda kasutades programmi `psql`.

MacOS korral saab vastava keskonna käima klikkides andmebaasi ikoonile. Linuxi all on vaja kahte rida

<code>
sudo su - postgres <br>
psql
</code> 

Neist esimene viib meid õige kasutaja õigustesse ja teine paneb `psql` programmi tööle. 

Nüüd tuleb teha `psql` aknas järgmised sammud

<code>
CREATE DATABASE ekt;<br>
CREATE USER swen WITH PASSWORD 'kala'; <br>
ALTER USER swen WITH PASSWORD 'kala'; <br>
CREATE SCHEMA media_analysis;
</code>

Esimene rida loob andmebaasi. Teine ja kolmas loovad ja muudavad Postgre serveri kasutaja tunnust. Neljas rida loob andmebaasi skeema.

   

