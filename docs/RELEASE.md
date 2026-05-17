# Release e manutenzione

## Ruolo dei workflow

L'aggiornamento di questo repository APT avviene normalmente dai workflow dei singoli progetti applicativi della suite GD LEX. In condizioni ordinarie non si pubblicano pacchetti a mano direttamente da questo repository.

## Flusso atteso di pubblicazione

1. Un progetto applicativo produce un nuovo pacchetto `.deb`
2. Il workflow copia il file nel percorso corretto sotto `pool/`
3. I metadata APT vengono rigenerati
4. I file aggiornati vengono pubblicati su GitHub Pages tramite questo repository

## Rigenerazione metadata

I file coinvolti sono:

- `dists/stable/main/binary-amd64/Packages`
- `dists/stable/main/binary-amd64/Packages.gz`
- `dists/stable/Release`

La configurazione di riferimento e' `apt-ftparchive.conf`. Questo file definisce i parametri essenziali per la generazione coerente dei metadata.

## Metadata Release attesi

I campi da mantenere coerenti sono:

- `Origin: GDLEX`
- `Label: GDLEX`
- `Suite: stable`
- `Codename: stable`
- `Architectures: amd64`
- `Components: main`

## Verifiche dopo una pubblicazione

Controlli consigliati:

```bash
apt policy gdlex-pct-validator
grep -n "Version:" dists/stable/main/binary-amd64/Packages
grep -E "^(Origin|Label|Suite|Codename|Architectures|Components):" dists/stable/Release
```

Se in futuro verranno aggiunti altri pacchetti della suite, il controllo va ripetuto anche per i nuovi nomi pubblicati.
