# Uso del repository APT GD LEX

## Aggiunta della sorgente APT

Il repository e' pubblicato con firma GPG e file `InRelease`. La configurazione consigliata usa `signed-by=` con keyring locale.

Esempio:

```bash
curl -fsSL https://cortomaltese88.github.io/gdlex-apt-repo/keys/gdlex-archive-keyring.asc \
  | gpg --dearmor \
  | sudo tee /usr/share/keyrings/gdlex-archive-keyring.gpg >/dev/null

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/gdlex-archive-keyring.gpg] https://cortomaltese88.github.io/gdlex-apt-repo stable main" \
  | sudo tee /etc/apt/sources.list.d/gdlex.list
```

## Aggiornamento indici

```bash
sudo apt update
```

## Installazione del pacchetto disponibile

```bash
sudo apt install gdlex-pct-validator
```

## Verifica lato client

Per controllare che APT veda correttamente il repository e il pacchetto candidato:

```bash
apt policy gdlex-pct-validator
```

## Rimozione del pacchetto

```bash
sudo apt remove gdlex-pct-validator
```

## Configurazione consigliata con repository firmato

Quando il client usa il repository firmato, la configurazione consigliata e' la seguente:

```bash
curl -fsSL https://cortomaltese88.github.io/gdlex-apt-repo/keys/gdlex-archive-keyring.asc \
  | gpg --dearmor \
  | sudo tee /usr/share/keyrings/gdlex-archive-keyring.gpg >/dev/null

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/gdlex-archive-keyring.gpg] https://cortomaltese88.github.io/gdlex-apt-repo stable main" \
  | sudo tee /etc/apt/sources.list.d/gdlex.list

sudo apt update
```

I file attesi sul repository firmato sono:

- `dists/stable/Release`
- `dists/stable/InRelease`
- `dists/stable/Release.gpg`

## Nota su `trusted=yes`

- `trusted=yes` e' una configurazione legacy/deprecata e non piu' consigliata
- un client gia' configurato in questo modo puo' continuare a funzionare, ma va migrato a `signed-by=`
- la configurazione raccomandata resta quella con keyring locale e verifica GPG
