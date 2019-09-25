# MSA - INSTALLAZIONE

## Prerequisiti

* Java 8
* MongoDB (vers. 3.6.3)

## Configurazione

Per poter installare l'MSA occorre configurare alcuni file:

1. **application.properties**: descrive la porta da utilizzare per l'applicazione MSA e i parametri di connessione a
MongoDB per i vari audit per la registrazione dello stato dell'elaborazione delle caselle di posta.
2. **it.highwaytech.broker.properties**: per i parametri di connessione al broker ExtraWay e le varie configurazioni
dell'audit applicativo.
3. **it.tredi.msa.properties**: configurazioni generali delle modalità operative di esecuzione dell'agent (per maggiori
informazioni controllare i commenti presenti sul file).
4. **log4j2.xml**: parametri di configurazione dei log applicativi.


## Configurazione servizi

### msa (LINUX)

- File di avvio di MSA su Linux.  Di seguito è riportata la sezione del file che deve **obbligatoriamente** essere 
configurata:

```
# N.B.: E' richiesto Java8 per l'esecuzione del processo
JAVA_COMMAND=/usr/bin/java

# Massima dimensione della memoria heap per il MSA
MAXHEAP=-Xmx128m

MSAPID=/tmp/msa.pid

NICE_LEVEL=10
```

### msa.bat (WINDOWS)

- File per un avvio da riga di comando in ambiente Windows. Di seguito è riportata la sezione del file che deve 
**obbligatoriamente** essere configurata:

```
rem la variabile JVM serve per impostare la java virtual machine che verra' utilizzata per avviare il servizio
rem per avviare da un persorso specifico si puo' settare la variabile come nell'esempio seguente
rem set "JVM=C:\JDKS\64bit\1.8.0_40\bin\java.exe"
rem NOTA BENE e' richiesta una versione di JVM non inferiore alla 1.8.0
set "JVM=java"

rem per settare le opzioni della JVM settare la variabile JVM_OPTS
set JVM_OPTS=-Xmx1024m -Xms1024m
```

### install-32.bat (WINDOWS)

- File per installare come servizio in ambiente Windows a 32 bit. Di seguito è riportata la sezione del file che deve 
**obbligatoriamente** essere configurata:

```
set JVM=auto
rem settata con auto ricava la jvm dal registro di windows
rem per impostarla a una jvm specifica occorre settarla al path della jvm.dll
rem set JVM="C:\JDKS\32bit\1.8.0_40\jre\bin\server\jvm.dll"

set xms=1024m
set xmx=1024m
```

### install-amd64.bat (WINDOWS)

- File per installare come servizio in ambiente Windows amd a 64 bit. Di seguito è riportata la sezione del file che deve 
**obbligatoriamente** essere configurata:

```
set JVM=auto
rem impostare a una jvm specifica occorre settarla al path della jvm.dll
rem set JVM="C:\JDKS\32bit\1.8.0_40\jre\bin\server\jvm.dll"

set xms=1024m
set xmx=1024m
```

### install-ia64.bat (WINDOWS)

- File per installare come servizio in ambiente Windows ia a 64 bit. Di seguito è riportata la sezione del file che deve 
**obbligatoriamente** essere configurata:

```
set JVM=auto
rem impostare a una jvm specifica occorre settarla al path della jvm.dll
rem set JVM="C:\JDKS\32bit\1.8.0_40\jre\bin\server\jvm.dll"

set xms=1024m
set xmx=1024m
```

### uninstall.bat (WINDOWS)

- File per rimuovere il servizio in ambiente Windows.


## Esecuzione

**Linux**

```
bin/msa {start|stop|status|restart|debug}
```

**Windows - Avvio Manuale**

Spostarsi da prompt nella directory bin e lanciare

```
msa.bat
```

**Windows - Installazione Servizio**

Spostarsi da prompt nella directory bin e lanciare a seconda del sistema

```
install_32.bat
```
oppure

```
install_amd64.bat
```
oppure

```
install_ia64.bat
```

**Windows - Disinstallazione Servizio**

Spostarsi da prompt nella directory bin e lanciare a seconda del sistema

```
uninstall.bat
```
