# AI-INFRASTRUCTURE-SPECIALIST

GITBOOK DI ROBERTO https://zafirogroup.gitbook.io/machine-learning/



Cap 1 COMANDI LINUX <br>
Cap 2 INTRODUZIONE ALLE RETI <br>
Cap 3 DOCKER 

# Capitolo 1 COMANDI LINUX
Per i comandi principali vedere la repository https://github.com/ludomontanaro17-bit/linux-for-hacker-and-pentester
Inoltre
```bash                 
chmod -r folder/                             # tolgo il permesso di lettura a tutti i files della directory folder
chmod -R 777 folder/                         # cambio tutti i permessi di tutti i files nella directory folder
history > file.txt                           # salvo la history (lista comandi precedenti) nel file fil.txt
find /home/user -name "*.txt"                # cerco tutti i file di tipo *.txt nella directory specificata dal                                                   # percorso assoluto
tree / L 1                                   # albero a profondità limitata
read -p numero_                              # operazione io bloccante
cp *.txt backup/                             # copio tutti i file con estensione .txt nella directory backup
more uno.txt                                 # alternativa a cut
less uno.txt
[comando] | at [time scheduling]             # per installarlo apt get install at
atq                                          # visualizzo elenco lavori in programma -> mi rida ID dei lavori
atrm [ID]                                 # annullo lavoro programmato
grep "pattern" file.txt                   # cerco l'espressione pattern nel file file.txt
grep -r "funzione"                        # cerco la stringa funzione in tutti i file della directory corrente e varie sottodirectory
grep -n "warning" file.txt                # mostra le righe in cui appare warning e i numeri di riga
grep -i "esempio" file.txt                # cerco ignorando maiuscole e minuscole
```


# Capitolo 2 INTRODUZIONE ALLE RETI 
```bash
service [nome_servizio] [azione]
sudo systemctl start [nome_servizio]
sudo systemctl stop [nome_servizio]
sudo systemctl restart [nome_servizio]
sudo systemctl reload [nome_servizio]
sudo systemctl status [nome_servizio]
sudo systemctl enable [nome_servizio]
sudo systemctl disable [nome_servizio]
sudo systemctl is-enabled [nome_servizio]
systemctl status xrdp                 # servizio di desktop da remoto
ssh nome_utente@indirizzo_ip -p numero_di_porta
chown username file.txt
sudo apt get install java
sudo nano /etc/hosts
adduser Mario
cat /etc/passwd                       # fa vedere gli utenti nei gruppi
```
```bash
traceroute [IP_che_voglio_raggiungere]
ping [IP_che_voglio_raggiungere]
ping -c 4 [IP_che_voglio_raggiungere]
sudo nmap -sS [IP_che_voglio_raggiungere]         # per vedere se una macchina è effettivamente accesa
ifconfig | grep 192                               # per vedere indirizzo IP (inet), broadcast e netmask
nmap -v google.it                                 # quali porte sono aperte sulla macchina di google?
nmap -vv [IP]                                     # più informazioni
nmap -v -sV [IP]                                  # software e numero di versione
nmap -v -p- [IP]                                  # scansiono tutte le porte
nmap -r [IP]                                      # scansiono tutte le porte in maniera consecutiva
last                                              # quali e quando gli utenti si sono collegati
telnet [IP] [numero_di_porta]                     # se una porta è aperta o meno e serve per interagire con i servizi a livello testuale con i rispettivi comandi relativi
nc [IP] [numero_di_porta]                         # più potente di telnet
```




# Capitolo 3 DOCKER 
Installato dal sito docker, su docker.hub sono presenti i container.

```bash
docker ps                        # mostra tutti i container attivi
docker ps -a                     # mostra tutti i container attivi e non attivi
docker images                    # immagini scaricate e quanto pesano
docker run -p [porta_esterna]:[porta_interna] [nome_immagine] --name [nome_container]
docker rmi [image_name]          # rimuovo un'immagine
docker rm [id_container]         # rimuovo un container
docker start [id_container]      # avvio un container fermato
docker stop [id_container]       # stoppo un container attivo
docker stop [id_container]; docker rm [id_container] # stoppo e rimuovo un container 
```

NOTA: invece dell'[id_container] posso usare solo le prime tre cifre.

## Per installare PORTAINER https://docs.portainer.io/start/install-ce/server/docker/linux

```bash
docker volume create portainer_data           # creo un volume (o zona di lavoro) dedicata al container
```
```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:lts
```
```bash
docker ps -a                                 # per vedere se è attivo
```
poi per aprire la pagina sul web https://127.0.0.1:9443

NOTA: se dice che per sicurezza è finito il tempo fai 
```bash
docker ps
```
```bash
docker stop [id_container]
```
```bash
docker start [id_container]
```
e poi riapri https://127.0.0.1:9443.

### Per risettare la password dello user 
```bash
docker stop "id-portainer-container"
```
```bash
docker pull portainer/helper-reset-password
```
```bash
docker run --rm -v portainer_data:/data portainer/helper-reset-password

```
If successful, the output should look like this:
```bash
2020/06/04 00:13:58 Password successfully updated for user: admin
2020/06/04 00:13:58 Use the following password to login: &_4#\3^5V8vLTd)E"NWiJBs26G*9HPl1

```
If the helper is unable to find an admin user to update, it will create a new one for you. If the username admin is already used, it will create a user named admin-[randomstring]:

```bash
2022/08/10 07:36:33 [WARN] Unable to retrieve user with ID 1, will try to create, err: object not found inside the database
2022/08/10 07:36:33 Admin user admin-u0512b3f0v4dqk7o successfully created
2022/08/10 07:36:33 Use the following password to login: Sr#]YL_6D0k8Pd{pA9^|}F32j5J4I=av
```

e poi per riattivare il container
```bash
docker start "id-portainer-container"
```
e poi per riloggarmi
https://127.0.0.1:9443.

Clicca su local

<img width="871" height="480" alt="Screenshot 2025-10-13 alle 12 22 04" src="https://github.com/user-attachments/assets/d873c75a-ff08-4d9d-bf3d-3cf1a2da3b24" />
<img width="869" height="686" alt="Screenshot 2025-10-13 alle 12 23 49" src="https://github.com/user-attachments/assets/22984ce4-04cc-4278-8c24-33672a4ba111" />
<img width="870" height="721" alt="Screenshot 2025-10-13 alle 12 27 59" src="https://github.com/user-attachments/assets/4027232d-f0ce-4542-ba3d-b970ea8d85b9" />
metti come porte dell'host 80 e 443
<img width="860" height="710" alt="Screenshot 2025-10-13 alle 12 28 05" src="https://github.com/user-attachments/assets/e426587e-6d3c-44e3-9a41-7d4b20aa5f28" />
Per vedere se funziona -> DEPLOY THE CONTAINERS
Per aprirlo sul web http//127.0.0.1 (posso non inserire il numero di porta perchè coincide con quella privata)

## Modifica la pagina di benvenuto di nginx con "Ciao sono Ludovica"
```bash
docker exec -it [container_id] /bin/bash # per aprire la shell del container
```
```bash
apt update   # aggiorno elenco repository
```
```bash
apt install nano # serve per installare il comando
```
```bash
(apt search java  # mi da l'elenco dei pacchetti che posso installare)
```
```bash
apt upgrade   # per aggiornare i pacchetti con le ultime versioni
```
```bash
 cd /etc/apt  # mi serve per i pacchetti 
  ls -la       #entro in debian.source con cat per capire le corrispondenze per pescare il software
nano debian.source # aggiorno le repositories ```
```bash
which nginx # dove è la cartella nginx
```
```bash
cd /usr/sbin/nginx # per scendere nella cartella
```
```bash
cd /usr/share/nginx
```
```bash
cd html/
```
```bash
nano index.html  -----> da qua modifica la scritta di benvenuto
```
```bash
touch about_me.html
```
```bash
nano about_me.html -----> in html posso scrivere cose
```
```bash
which nginx     # dove si trovano ESEGUIBILI con relativo percorso
```
```bash
whereis nginx   # per eseguibili e stringhe 
```
```bash
apt update   # aggiorno elenco repository
```
```bash
apt install nano # serve per installare il comando
```
```bash
apt search java  # mi da l'elenco dei pacchetti che posso installare
```
```bash
apt upgrade   # per aggiornare i pacchetti con le ultime versioni
```
---------------------------------------------
Dopo aver creato un nuovo container di nginx (stando attenta a non fare errore di binding di porte), devo aprire il terminale e pingare l'altro container:
```bash
apt update
```
```bash
apt install iputils-ping
```
```bash
ping [ID_altra_macchina]
```
----------------------------------------------
Invece di verificare una ad una se le macchine siano connesse con ping posso faee
```bash
nmap -v -sn 192.168.1.1-255     # scansionami gli indirizzi nel segmento di rete da 1 a 255
```
oppure 
```bash
nmap -v -sn 192.168.1.1/24    # scansionami gli indirizzi nel segmento di rete da 1 a 255
```
## Istruzioni per creare una sottorete:
```bash
docker network create rete-nginx 
```
```bash
docker run -d --name nginx 1 --network rete-nginx -p 8080:80 nginx:latest
```
-----------------------------------------------

## Istruzioni per spostare un container nella nuova sottorete di nome myNetwork creata\
1) premi sul nome in blu del container che voglio spostare
2) premo su duplicate/edit
<img width="861" height="722" alt="Screenshot 2025-10-13 alle 16 48 28" src="https://github.com/user-attachments/assets/bf07cd3d-3b93-49cf-b776-c4bea0f75975" />
3) sul menù a tendina dei network seleziono myNetwork
   <img width="884" height="721" alt="Screenshot 2025-10-13 alle 16 49 01" src="https://github.com/user-attachments/assets/c7341fb3-39b4-4911-8d78-15c46c3f0ef4" />
4) deploy the container (con rimpiazzo)

Oppure da terminale 
```bash
docker network ls    # per lista dei network
```
```bash
docker network connect [nome_rete] [nome_container]
```
Uno stesso container può appartenere a diversi segmenti di rete; infatti se vado sulla shell del container 

```bash
apt update
```
```bash
apt install net-tools     # per usare ifconfig
```
```bash
ifconfig
```
mi esce che ho PIU' INTERFACCE DI RETE 
<img width="862" height="693" alt="Screenshot 2025-10-13 alle 17 02 52" src="https://github.com/user-attachments/assets/798f19d8-bbb0-44ad-a7e5-313fa2678cf7" />

---------------------------------------------------
* Esercitazione 
## Installa ubuntu su portainer
Cerco su templates -> applicazioni -> search: ubuntu -> configuro e deployt -> apro la shell con >_ \
Per aprire la shell da terminale posso anche usare il comando 
```bash
docker exec -it [id_container] /bin/bash
```
e mi ritroverò sulla shell del container in questione.\
MAPPA LE PORTE DALL'INIZIO ALTRIMENTI DEVO FARE UN REPLACEMENT DEI CONTAINER E PERDO TUTTE LE COSE CHE HO INSTALLATO. (ALTRIMENTI VAI SU *duplicate/edit* -> MAPPO 22:22)
## Configura e installa ssh:
```bash
apt get update
```
```bash
apt install -y openssh-server
```
```bash
service ssh start 
```
```bash
service ssh status 
```
```bash
which ssh     # per vedere dove si trova l'eseguibile ssh 
```
```bash
passwd        # per modificare la passwd dell'utente root
```
```bash
service ssh status 
```
```bash
apt update
apt install iputils-ping
ping [id_macchina]
```
```bash
ssh root@ [id_macchina] # di default va alla 22, altrimenti -p 22:22)
```
## Per collegarmi con root devo abilitarla con il comando
```bash
sed -i 's/^#\?PasswordAuthentication.*/PasswordAuthentication yes/' /etc/ssh/sshd_config
sed -i 's/^#\?PermitRootLogin.*/PermitRootLogin yes/' /etc/ssh/sshd_config
```
## Per collegarmi da remoto con un utente che ho creato
```bash
adduser ludo
```
```bash
ssh ludo@[id_ubuntu]
```
Il collegamento è rifiutato se sono su segmenti di rete diversi. 

<img width="573" height="134" alt="Screenshot 2025-10-14 alle 10 58 29" src="https://github.com/user-attachments/assets/6bad68e6-f099-4dc0-b482-150e40301dab" />
Mi fa capire che sono su due segmenti di rete diversi e quindi è ovvio che non potrò connettere le due macchine dato che la mia ha ip 192... e la macchina in questione 172...

## Mi collego dal container web_001 sul container ubuntu
In teoria lo posso fare perchè condividono lo stesso segmento di rete come si evince dagli IP che sono 172.17.0.4 e 172.17.0.3
Vado sulla shell di web_001
```bash
apt update
```
Se mi serve il client per collegarmi in ssh
```bash
apt install openssh-client -y      
```
```bash
ssh ludo@[id_di_ubuntu]
```

----------------------------------------------------------------
Oppure in maniera più elegante creo un file in ssh e lo eseguo
```bash
apt update
```
```bash
apt install nano
```
```bash
nano file.ssh
```
```bash
#!/bin/bash 

echo "Installing ssh server on Machine"

apt update
apt install openssh-server -y 
service ssh start
echo "Enable root access"
sed -i 's/^#\?PasswordAuthentication.*/PasswordAuthentication yes/' /etc/ssh/s>
sed -i 's/^#\?PermitRootLogin.*/PermitRootLogin yes/' /etc/ssh/sshd_config
```
```bash
ls -la file.ssh    # mancano i permessi
```
```bash
chmode +x file.ssh   # setto i permessi
```
```bash
./file.ssh    # per far girare il programma 


```
 Poi cambia sempre la password dell'user con cui sto accedendo
```bash
passwd
```
```bash
passwd [nome_utente]    # l'utente root può modificare le password degli altri utenti così
```

Se mi sono collegata bene dalla macchina web_001 sulla macchina ubuntu (con id 172.17.0.4) esce questo
<img width="748" height="551" alt="Screenshot 2025-10-14 alle 11 11 01" src="https://github.com/user-attachments/assets/e3b45f31-78e1-47f0-baec-0ed7e1f76c84" />



# DOCKER CREATE IMAGES
## file sorgente -> build image -> runno il container
Voglio deployare l'app come se fosse un container di docker.\
Mettere un'applicazione sotto container serve per metterla sul mercato e renderla fruibile.
<img width="632" height="602" alt="Screenshot 2025-10-14 alle 14 12 40" src="https://github.com/user-attachments/assets/83b22262-971c-4ff8-adbe-9116b9053cb8" />

## Scrivo il mio codice sorgente su Virtual Studio Code
1) Installazione di visual studio code: https://code.visualstudio.com/download\ oppure da terminale 
```bash
choco install vscode    # per Windows
brew install vsce       # per Mac
```
Con *Material Icon Theme* puoi impostare le icone colorate.\
Con *control+s* salvo il codice!!!!!!!!!!!



2) Il comando node è utilizzato per eseguire applicazioni JavaScript sul server, senza la necessità di un browser.\
Installo da terminale **node**: 
```bash
choco install nodejs-lts # per Windows
apt get install node     # per Linux
brew install node        # per Mac
```
Per verificare l'installazione questo codice dovrebbe ridare una cosa del tipo v24.10.0

```bash
node -v 
```

Dentro ESEMPIO-APP-SERVER creo la cartella src dentro cui scrivo il file server.js
<img width="980" height="420" alt="Screenshot 2025-10-14 alle 14 17 42" src="https://github.com/user-attachments/assets/2d8e1d17-3f2a-4551-9885-3dfa3576bdfb" />
Dentro src -> package.json che è un oggetto
<img width="961" height="202" alt="Screenshot 2025-10-14 alle 14 23 23" src="https://github.com/user-attachments/assets/2065b57d-7e85-472e-bce7-f0094ef8627c" />


Gli attributi dell'oggetto sono:\
-name \
-version\
-dependencies ----> l'applicazione per andare ha bisogno che ci sia installato il framework express.js

Apro la power shell
<img width="1340" height="137" alt="Screenshot 2025-10-14 alle 14 28 27" src="https://github.com/user-attachments/assets/5504d386-fefe-45e5-8b4c-1f812717b7e7" />

Con questo comando installo tutte le dipendenze che occorrono per poter lavorare correttamente (in questo caso express)

```bash
cd src       # per entrare nella cartella
```

```bash
sudo npm install     
```

Quindi per vedere 'ok' devo scrivere su internet https://127.0.0.1:3000 \
E per vedere 'Pagina dei contatti' devo scrivere su internet https://127.0.0.1:3000/contatti 

Prima di dockerizzare devo vedere se l'applicazione funziona 
```bash
node server.js     # verifico se è andato con control+c si ferma
```

Creo file docker con i comandi
<img width="910" height="278" alt="Screenshot 2025-10-14 alle 15 24 10" src="https://github.com/user-attachments/assets/354ba058-e0f9-459c-9be5-7ec179ede5eb" />

Spiegazione particolareggiata di 
```bash
FROM node:19-alpine

COPY package.json /app/
COPY . /app/

WORKDIR /app

RUN npm install

EXPOSE 3000

CMD ["node","server.js"]
```

<img width="872" height="759" alt="Screenshot 2025-10-14 alle 15 47 18" src="https://github.com/user-attachments/assets/1b441ced-0653-4e06-82d6-f79512108314" />

<img width="838" height="663" alt="Screenshot 2025-10-14 alle 15 47 26" src="https://github.com/user-attachments/assets/c8768bd6-a1d9-4c84-b307-93148eb29c58" />




Creo una nuova immagine con 
```bash
sudo docker build . 
```

Mi da questo errore 

<img width="617" height="390" alt="Screenshot 2025-10-14 alle 15 17 42" src="https://github.com/user-attachments/assets/9ec2c51a-3674-4a86-b08e-a0854dffe0cd" />

che ho risolto così

<img width="637" height="120" alt="Screenshot 2025-10-14 alle 15 22 06" src="https://github.com/user-attachments/assets/c10aea8d-b940-47c1-9997-5f1c5439bc63" />

Creo una README per delle istruzioni aggintive
<img width="810" height="121" alt="Screenshot 2025-10-14 alle 15 26 21" src="https://github.com/user-attachments/assets/f1e3786f-0886-4f74-a82d-9a269bd1e4a2" />

Creo un'immagine dal nome app-express-image
```bash
docker build -t app-express-image .
```

<img width="668" height="599" alt="Screenshot 2025-10-14 alle 16 17 24" src="https://github.com/user-attachments/assets/bc904116-f92d-4164-8381-495589f6c228" />


Mi crea effettivamente un'immagine



Per verificare di avere effettivamente un'immagine
```bash
docker images | grep app
```



<img width="639" height="81" alt="Screenshot 2025-10-14 alle 15 27 46" src="https://github.com/user-attachments/assets/14884f28-87a4-4c80-a0a7-e87a6fbdaa73" />

Runno l'immagine che ho

```bash
docker run -d -p 3000:3000 app-express-image --name [nome_container]
```

<img width="566" height="69" alt="Screenshot 2025-10-14 alle 15 41 09" src="https://github.com/user-attachments/assets/a0bcc765-bdb3-4ae6-b34c-7879960b4acd" />


<img width="668" height="537" alt="Screenshot 2025-10-14 alle 16 18 53" src="https://github.com/user-attachments/assets/d8d927bd-a82c-4338-8856-3fb70da6741e" />



Ho dockerizzato completamente l'app se dall'indirizzo http://127.0.0.1:3000 esce


<img width="995" height="163" alt="Screenshot 2025-10-14 alle 15 35 06" src="https://github.com/user-attachments/assets/3ce25cb8-5405-49c5-bbec-9c588ab33b61" />

oppure se da http://127.0.0.1:5001 esce

<img width="993" height="137" alt="Screenshot 2025-10-14 alle 15 49 32" src="https://github.com/user-attachments/assets/931f8817-0125-4743-a210-003f15ae21f9" />


Prova del nove: apro portainer con http://127.0.0.1:9443

<img width="1290" height="156" alt="Screenshot 2025-10-14 alle 15 53 48" src="https://github.com/user-attachments/assets/99fdee50-eaa5-49e9-8523-c74891367e8e" />

e i due container che ho creato prima stanno runnando!

-------------------------------------------------------

**Esercitazione**
TASK: dockerizza l'applicazione in python

```bash
Example Code
python

Copia codice




from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run(debug=True)





Nota : potrebbe essere necessario costruire un file di requiremens in python ( google it!)

Explanation
Import Flask: The Flask class is imported from the flask package.
Create an Instance: An instance of the Flask class is created.
Define a Route: A route is defined using the @app.route('/') decorator, which maps the URL to the hello_world function.
Return Statement: The hello_world function returns the string "Hello, World!" when accessed.
Run the Application: The app runs in debug mode, which is useful during development to catch errors.
Running the Flask App
Make sure you have Flask installed. You can install it using pip:
bash

Copia codice
pip install Flask
Save the code in a file named app.py.
Run the file:
bash

Copia codice
python app.py
Open a web browser and go to http://127.0.0.1:5000 to see the message "Hello, World!".
```

<img width="669" height="244" alt="Screenshot 2025-10-14 alle 18 03 12" src="https://github.com/user-attachments/assets/853eaefd-aadc-44ee-9d1e-d29bd98072d8" />

<img width="439" height="98" alt="Screenshot 2025-10-14 alle 18 03 16" src="https://github.com/user-attachments/assets/27cbeee1-8034-43ba-80e7-4c56c3e3d462" />

<img width="434" height="411" alt="Screenshot 2025-10-14 alle 18 20 53" src="https://github.com/user-attachments/assets/db5d8e23-0d6a-40e0-9da9-469aa1c2c94f" />



Per vedere se il programma app.py gira in locale
```bash
chmod u+x app.py
./app.py

```

Per creare l'immagine flask-app
```bash
docker build -t flask-app .
```

Per creare il container usando questa immagine con mapping di porte 5555:5555
```bash
docker run -p 5555:5555 flask-app
```



