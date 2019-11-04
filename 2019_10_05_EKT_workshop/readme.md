# EstNLTK õpituba

**Autorid:** Dage Särg ja Sven Laur <br> 
**Toimumisaeg:** 5. november 2019 <br>
**Asukoht:** EKT konverents. Prototüübist teostuseni. Tallinn <br>
**Materjalid allalaadimiseks:** TODO

## Ettevalmistused õpitoas osalemiseks

Need, kes soovivad EstNLTK õpitoas näidatut kohe oma arvutis järgi proovida, peaksid selleks eelnevalt installima vajaliku tarkvara. 

### EstNLTK lingvistilise analüüsi töövahendite kasutamiseks oleks vaja teha järgmist:

1) Installida Anaconda, mille saab alla laadida siit https://www.anaconda.com/distribution/ (Python 3.7 versioon).

2) Avada terminaliaken ning luua ja aktiveerida conda keskkond, mis kasutab Python 3.6:

<code>
conda create -n estnltk python=3.6 -y
   
conda activate estnltk
</code>   

3) Installida loodud keskkonda EstNLTK 1.6 ning jupyter:

<code>
conda install -c estnltk -c conda-forge estnltk
   
conda install jupyter
</code>   

4) Liikuda käsureal cd käsu abil kausta, kuhu on alla laaditud fail [notebook-example.ipynb](https://drive.google.com/file/d/12pdLl8J0KxoUJ6Mj-75-kpOzzUTSg-Ms/view?usp=sharing) ning käivitada näidis-notebook:

<code>
jupyter notebook notebook-example
</code> 

5) Jooksutada Shift+Enter abil läbi notebookis olev koodilahter ning veenduda, et asi töötab


### EstNLTK andmebaasitöövahendite kasutamiseks on vaja lisaks veel järgmist:

1) Installida loodud conda keskkonda psycopg2 ja conllu paketid:

<code>
conda install -n estnltk psycopg2 <br>

conda install -n estnltk -c conda-forge conllu <br>
</code>

2) Lokaalset Postgre serverit  

#### Postgre serveri installimine

Operatsioonisüsteemi MacOS korral on kõige lihtsam viis installida [Postgres.app](https://postgresapp.com), kui teil pole juba varem installitud lokaalset postgre serverit. 

Operatsioonisüsteemi Ubuntu Linux korral saab jälgida installimisjuhendit [How to Install PostgreSQL 11 on Ubuntu 18.04 & 16.04 LTS](https://tecadmin.net/install-postgresql-server-on-ubuntu/) 

Järgnevalt oleks vaja luua ka andmebaas `ekt` ja andmebaasi kasutaja ning soovi korral ka skeema `media_analysis`. Selleks tuleb postgre serveriga õigetes õigustes ühenduda kasutades programmi `psql`.

MacOS korral saab vastava keskonna käima, klikkides andmebaasi ikoonile. Linuxis on vaja kahte rida:

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


**Kui ei soovi või ei oska tarkvara installida, aga tahaks ikka töövahendeid ise katsetada:**

Sellisel juhul tuleb installida virtuaalmasin koos eelinstallitud  Ubuntu Linux operatsioonisüsteemiga:

* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [VitualBox-i image](https://drive.google.com/open?id=1R8Cb2aIyMiD6KhvPyenR-yDYyyavxAnq)
   

