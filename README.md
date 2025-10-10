# AI-INFRASTRUCTURE-SPECIALIST

Cap 1 COMANDI LINUX <br>
Cap 2 INTRODUZIONE ALLE RETI <br>
Cap 3

# COMANDI LINUX 
Linux è **case sensitive**.\
**root**  :Linux has an administrator or superuser account, designed for use by a trusted person who can do nearly anything on the system. This would include such things as reconfiguring the system, adding users, and changing passwords. In Linux, that account is called root. As a hacker or pentester, you will often use the root account to give yourself control over the system. In fact, many hacker tools require that you use the root account.


**Script** : This is a series of commands run in an interpretive environment that converts each line to source code. Many hacking tools are simply scripts. Scripts can be run with the bash interpreter or any of the other scripting language interpreters, such as Python, Perl, or Ruby. Python is currently the most popular interpreter among hackers.

**Shell** : This is an environment and interpreter for running commands in Linux. 

<img width="666" alt="Screenshot 2024-02-15 alle 10 55 41" src="https://github.com/MrMagicalSoftware/linux-for-hacker-and-pentester/assets/98833112/5070c9ec-06e4-4b27-a4be-77b150bcfc27">

1. **/ (root):** La directory radice del sistema di file. Tutti i file e le directory si trovano sotto questa directory principale.

2. **/bin (binary):** Contiene i file binari essenziali necessari per il funzionamento del sistema e il ripristino in caso di problemi.

3. **/boot:** Contiene i file necessari per il caricamento del kernel Linux durante l'avvio del sistema.

4. **/dev (devices):** Contiene file speciali che rappresentano dispositivi hardware. Ad esempio, i file nella directory /dev possono rappresentare dischi, dispositivi di input, ecc.

5. **/etc (et cetera):** Contiene i file di configurazione del sistema. Qui si trovano molte configurazioni globali del sistema e delle applicazioni.

6. **/home:** Questa è la directory principale per gli utenti del sistema. Ogni utente ha la propria sottodirectory qui, ad esempio, /home/nomeutente.

7. **/lib (library):** Contiene le librerie condivise essenziali necessarie per il funzionamento del sistema e dei programmi di sistema.

8. **/media:** Utilizzato per montare temporaneamente dispositivi rimovibili come chiavette USB o unità CD/DVD.

9. **/mnt (mount):** Utilizzato per montare temporaneamente file system aggiuntivi o dispositivi di archiviazione.

10. **/opt (optional):** Spazio destinato per l'installazione di software aggiuntivo che non fa parte del sistema principale.

11. **/proc:** Un file system virtuale che fornisce informazioni sul kernel, i processi e il sistema in tempo reale.

12. **/root:** La directory home dell'utente root, l'amministratore del sistema.

13. **/sbin (system binaries):** Contiene i file binari di sistema essenziali utilizzati solo dall'amministratore del sistema.

14. **/srv (service):** Contiene dati specifici del servizio fornito da questo sistema.

15. **/tmp (temporary):** Utilizzato per archiviare file temporanei. Il contenuto di questa directory viene cancellato durante il riavvio del sistema.

16. **/usr (user):** Contiene la maggior parte dei programmi e dei file a cui gli utenti accedono regolarmente. Spesso separato in /usr/bin, /usr/lib, ecc.

17. **/var (variable):** Contiene dati variabili, come log di sistema, file di stampa e altri dati che possono variare nel tempo.

## COMANDI ESSENZIALI 


Il comando `whoami` in un sistema Unix/Linux restituisce il nome dell'utente che attualmente ha effettuato l'accesso al sistema. In altre parole, mostra il nome dell'utente associato all'identità corrente dell'esecuzione del comando.

Per utilizzare il comando `whoami`, apri il terminale e digita semplicemente:

```bash
whoami
```

Dopo aver premuto Invio, il terminale mostrerà il nome dell'utente associato alla sessione corrente.

Ad esempio, se sei loggato come utente "john", il comando `whoami` restituirà:

```
john
```

Questo comando è utile quando si lavora con script o comandi che richiedono informazioni sull'utente corrente. Può essere usato anche per verificare rapidamente sotto quale identità si sta eseguendo il terminale in un dato momento.



**COMANDO pwd**

Il comando `pwd` (Print Working Directory) in un sistema Unix/Linux restituisce il percorso completo (path) della directory corrente in cui ti trovi nel terminale. Quando lo esegui, il terminale mostra il percorso completo dalla radice del file system fino alla directory corrente.

Per utilizzare il comando `pwd`, basta digitare il comando nel terminale e premere Invio:

```bash
pwd
```

Il risultato sarà il percorso completo della directory corrente. Ad esempio:

```
/home/tuo_utente
```

Questo è particolarmente utile quando si naviga tra le directory o si lavora con file e cartelle in modo da sapere sempre in quale posizione del sistema di file ci si trova.


___________________________________

















