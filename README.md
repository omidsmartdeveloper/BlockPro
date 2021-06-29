# BlockPro

In diesem Projekt soll ein revisionssicherer Herkunfts- und Verbrauchsnachweis für Energie (pro 
kWh) entwickelt werden. Auf Basis einer bereits existierenden elektronischen Hardware (Edge 
Device) des Antragstellers soll eine neue Hard- und Software-Kombination entwickelt werden, die
sowohl beim Energieerzeuger als auch beim Energieverbraucher installiert ist und 
blockchainbasiert die Erzeugungsart (z. B. erneuerbar/CO2-neutral), die lokale Herkunft der 
Energie und die Energiemenge fixiert und der betreffenden kWh zuordnet.  

Die Blockchain Technologie der Doichain wird als Grundlage für die fälschungssichere Erfassung der Quelle erneuerbarer Energien verwendet. Alle 15 Minuten soll ein Herkunftsnachweis aufgezeichnet werden und in die Blockchain geschrieben, um die Existenz des Zählerstands zu beweisen und zusätzlich wird ein Verzeichnis in das Inter Planetary FileSystem gespeichert, damit die Daten jederzeit gefunden werden können.

Beschreibung
+Liest Daten von Consolino über die serielle Schnittstelle
+Erzeugt einen sha256-Hash dieser Daten
+Schreibt die Daten direkt auf einen laufenden js-ipfs-Knoten
+Speichert einen Proof-Of-Existence (PoE) auf Doichain über RPC calls


# Schnellstart

## Installation

Klonen und Erstellen von ConsolinnoDoc mit git:

    
    git clone https://github.com/webanizer/Consolino2IPFS.git
    cd Consolino2IPFS
    
Klonen und Erstellen von ConsolinnoDoc mit git:

   
    npm i

    
    
# Offene Fragen
Welche Daten müssen wir tatsächlich speichern? Verbraucht und produziert: 1.8.0 und 2.8.0 einspeisen und verbrauchen
Warum gibt es einen public key? Bereit für netzwerk? digital ambus
Wie rechnen wir Differenz aus und wo? Menge von 15 min evtl Blockexplorer der die Stromverbräuche ausrechnet zusätzlich zu Transaktionen Differenz zwischen Verbrauch und Produktion mit geographischen Daten/ Public key Wallet oder Zähler
Kann der Zähler selber seinen Stand in der Doichain speichern? Mit seinem Public Key
Nur CID statt hash, erst cid als name und hash als value?

# Resources

Serial Port npm package https://www.npmjs.com/package/serialport
Example on how to call the RPC on Doichain
getblockcount https://github.com/Doichain/meteor-api/blob/e6bfd0a3ac74b0c1ffdbcd019488deab4d3c4c28/server/api/doichain.js#L223
listtransactions https://github.com/Doichain/meteor-api/blob/e6bfd0a3ac74b0c1ffdbcd019488deab4d3c4c28/server/api/doichain.js#L260
the rpc-client implementation https://github.com/Doichain/meteor-api/blob/e6bfd0a3ac74b0c1ffdbcd019488deab4d3c4c28/imports/startup/server/doichain-configuration.js
namecoin rpc lib - https://www.npmjs.com/package/namecoin
   












