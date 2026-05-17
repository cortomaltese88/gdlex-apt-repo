# GD LEX APT Repository

Repository APT pubblico per la distribuzione di strumenti desktop della suite GD LEX tramite GitHub Pages.

URL pubblicato:

`https://cortomaltese88.github.io/gdlex-apt-repo`

## Pacchetti disponibili

- `gdlex-pct-validator`

Il repository potra' ospitare in futuro anche altri strumenti della suite, come `yt-transcriber`, dopo audit e pubblicazione controllata.

## Installazione lato utente

Il repository e' pubblicato con firma GPG e file `InRelease`. La configurazione consigliata lato client usa un keyring locale e `signed-by=`.

Esempio:

```bash
curl -fsSL https://cortomaltese88.github.io/gdlex-apt-repo/keys/gdlex-archive-keyring.asc \
  | gpg --dearmor \
  | sudo tee /usr/share/keyrings/gdlex-archive-keyring.gpg >/dev/null

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/gdlex-archive-keyring.gpg] https://cortomaltese88.github.io/gdlex-apt-repo stable main" \
  | sudo tee /etc/apt/sources.list.d/gdlex.list

sudo apt update
sudo apt install gdlex-pct-validator
```

Nota: `trusted=yes` e' ora una configurazione legacy/deprecata. Puo' continuare a funzionare per client gia' configurati, ma non e' piu' la soluzione consigliata e va migrata a `signed-by=`.

## Configurazione consigliata con repository firmato

La configurazione client consigliata e' basata su keyring locale e `signed-by=`.

Esempio:

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

Per utenti gia' configurati con `trusted=yes`: la configurazione puo' continuare a funzionare, ma va considerata legacy e migrata appena possibile alla forma con `signed-by=`.

## Stato firma

- Stato attuale: repository firmato GPG con `InRelease` e `Release.gpg`
- Configurazione consigliata: uso di keyring locale e `signed-by=`

## Struttura del repository

- `pool/`: contiene i pacchetti `.deb` pubblicati
- `dists/stable/main/binary-amd64/`: contiene `Packages` e `Packages.gz`
- `dists/stable/`: contiene `Release`, `InRelease` e `Release.gpg`
- `apt-ftparchive.conf`: configurazione usata per generare i metadata APT

## Manutenzione

- Il repository viene normalmente aggiornato dai workflow dei singoli progetti applicativi
- Le pubblicazioni copiano i nuovi `.deb` nel `pool/` e rigenerano i metadata APT
- Evitare modifiche manuali a `dists/`, `pool/` e ai metadata, salvo manutenzione controllata

## Licenza e responsabilita'

I file di configurazione e documentazione di questo repository sono distribuiti con licenza `GPL-3.0-or-later`. Il testo completo e' disponibile in [LICENSE](LICENSE).

Il repository APT e' fornito "as is", senza garanzie espresse o implicite. L'utente e il manutentore restano responsabili della verifica dei pacchetti pubblicati, dei metadata generati e della corretta configurazione lato client.

Il nome, il logo e il marchio **STUDIO GD LEX** / **GD LEX** restano distinti dalla licenza del codice e non sono concessi in uso salvo autorizzazione separata.
