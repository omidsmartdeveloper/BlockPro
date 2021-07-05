# BlockPro

In diesem Projekt soll ein revisionssicherer Herkunfts- und Verbrauchsnachweis für Energie (pro 
kWh) entwickelt werden. Auf Basis einer bereits existierenden elektronischen Hardware (Edge 
Device) soll eine neue Hard- und Software-Kombination entwickelt werden, die
sowohl beim Energieerzeuger als auch beim Energieverbraucher installiert ist und 
blockchainbasiert die Erzeugungsart (z. B. erneuerbar/CO2-neutral), die lokale Herkunft der 
Energie und die Energiemenge fixiert und der betreffenden kWh zuordnet.  

Die Blockchain Technologie der Doichain wird als Grundlage für die fälschungssichere Erfassung der Quelle erneuerbarer Energien verwendet. Alle 15 Minuten soll ein Herkunftsnachweis aufgezeichnet werden und in die Blockchain geschrieben, um die Existenz des Zählerstands zu beweisen und zusätzlich wird ein Verzeichnis in das Inter Planetary FileSystem gespeichert, damit die Daten jederzeit gefunden werden können.

Beschreibung
Liest Daten von Consolino über die serielle Schnittstelle
Erzeugt einen sha256-Hash dieser Daten
Schreibt die Daten direkt auf einen laufenden js-ipfs-Knoten
Speichert einen Proof-Of-Existence (PoE) auf Doichain über RPC calls


## Architekturfluss

![Architektur](https://user-images.githubusercontent.com/68154263/124475865-80c88f00-dda2-11eb-96ba-b6e54b4c6a83.PNG)


## Installation

## doichain/node-only docker image

1. Dieses Repository klonen mit: 

       git clone https://github.com/Doichain/docker.git doichain-docker


2.Docker-Image erstellen 

    
    docker build --no-cache -t dc0.16.3.1 --build-arg DOICHAIN_VER=doichain/node-only .
    cd doichain-docker/node-only
    docker build --no-cache -t dc0.16.3.1 --build-arg DOICHAIN_VER=doichain/node-only .


Docker-Image ausführen

Parameter:

    -e RPC_PASSWORD= (optional) - wenn nicht angegeben, wird es vom Startskript generiert - siehe
    ~/.doichain/doichain.conf
    -e TESTNET=true für den Fall, dass Sie Testnet betreiben, wenn Sie Mainnet betreiben, bitte entfernen
    -e DAPP_URL=http://localhost:4010 (optional) die URL Ihrer lokalen dApp (mainnet Standard: http://localhost:3000       testnet kein Standard, aber verwenden Sie: http://localhost:4010)



4.Verbinden Sie sich mit dem Docker-Container und prüfen Sie, ob der Knoten mit dem Testnetz verbunden ist


    docker exec -it doichain-testnet doichain-cli -getinfo
    

5.Bitte sichern Sie IMMER Ihre PrivatKeys! über

    docker exec -it doichain-testnet doichain-cli getnewaddress
    docker exec -it doichain-testnet doichain-cli dumpprivkey <address>


Klonen und Erstellen von ConsolinnoDoc mit git:

    git clone https://github.com/webanizer/Consolino2IPFS.git
    cd Consolino2IPFS
    
Klonen und Erstellen von ConsolinnoDoc mit git:

    npm i

# Wallet

# Electrum-Doichain Portierung
   
## Vorraussetzungen
Ausführen von Doichaind und ElectrumX
Der Electrum Client sendet niemals private Schlüssel an die Server. Darüber hinaus verifiziert er die von den Servern gemeldeten Informationen mit einer Technik die Simple Payment Verification genannt wird.


    git clone git://github.com/namecoin/electrum-nmc.git
    cd electrum-nmc
    git submodule update --init
      
Führen Sie install aus (dadurch sollten die Abhängigkeiten installiert werden):
    
    python3 -m pip install --user -e .

    

Schließlich, um Electrum zu starten:  
    
    ./run_electrum_nmc


        

    
# AuxPoW Branch  // Merge Mining

Electrum-NMC unterhält auch einen auxpow-Zweig. Dieser Zweig ist identisch mit der Upstream-Bitcoin-Version von Electrum (z. B. hat er keine Namensunterstützung oder Namecoin-Rebranding), außer dass er AuxPoW (merged mining) unterstützt. Sie kann als Ausgangspunkt für die Portierung von Electrum auf andere AuxPoW-basierte Kryptowährungen nützlich sein.

    
# Offene Fragen
Welche Daten müssen wir tatsächlich speichern? Verbraucht und produziert: 1.8.0 und 2.8.0 einspeisen und verbrauchen
Warum gibt es einen public key? Bereit für netzwerk? digital ambus
Wie rechnen wir Differenz aus und wo? Menge von 15 min evtl Blockexplorer der die Stromverbräuche ausrechnet zusätzlich zu Transaktionen Differenz zwischen Verbrauch und Produktion mit geographischen Daten/ Public key Wallet oder Zähler
Kann der Zähler selber seinen Stand in der Doichain speichern? Mit seinem Public Key
Nur CID statt hash, erst cid als name und hash als value?


![image](https://user-images.githubusercontent.com/68154263/124521436-c2335b80-ddef-11eb-9b9c-c8f9a9d1f11c.png)



In writePoeToDoichain.js wird der hash über die SML Daten der letzten 15 Minuten abgeholt und zusammen mit dem confirm Client in den RPC Call name_doi übergeben, der den Hash in die Doichain schreibt.






# Resources

Serial Port npm package https://www.npmjs.com/package/serialport
Example on how to call the RPC on Doichain
getblockcount https://github.com/Doichain/meteor-api/blob/e6bfd0a3ac74b0c1ffdbcd019488deab4d3c4c28/server/api/doichain.js#L223
listtransactions https://github.com/Doichain/meteor-api/blob/e6bfd0a3ac74b0c1ffdbcd019488deab4d3c4c28/server/api/doichain.js#L260
the rpc-client implementation https://github.com/Doichain/meteor-api/blob/e6bfd0a3ac74b0c1ffdbcd019488deab4d3c4c28/imports/startup/server/doichain-configuration.js
namecoin rpc lib - https://www.npmjs.com/package/namecoin
   












