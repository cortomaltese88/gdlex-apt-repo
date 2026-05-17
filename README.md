# GD LEX APT Repository

Repository APT pubblico per la distribuzione di strumenti desktop della suite GD LEX tramite GitHub Pages.

URL pubblicato:

`https://cortomaltese88.github.io/gdlex-apt-repo`

## Pacchetti disponibili

- `gdlex-pct-validator`

Il repository potra' ospitare in futuro anche altri strumenti della suite, come `yt-transcriber`, dopo audit e pubblicazione controllata.

## Installazione lato utente

Il repository e' attualmente pubblicato senza firma GPG / `InRelease`. In questa fase l'aggiunta come sorgente APT richiede quindi una configurazione provvisoria con `trusted=yes`.

Esempio:

```bash
echo "deb [trusted=yes] https://cortomaltese88.github.io/gdlex-apt-repo stable main" | sudo tee /etc/apt/sources.list.d/gdlex.list
sudo apt update
sudo apt install gdlex-pct-validator
```

Nota: `trusted=yes` e' una soluzione temporanea adatta solo finche' il repository resta non firmato.

## Stato firma

- Stato attuale: repository non firmato GPG e senza file `InRelease`
- Roadmap: introduzione futura di firma GPG per eliminare la necessita' di `trusted=yes`

## Struttura del repository

- `pool/`: contiene i pacchetti `.deb` pubblicati
- `dists/stable/main/binary-amd64/`: contiene `Packages` e `Packages.gz`
- `apt-ftparchive.conf`: configurazione usata per generare i metadata APT

## Manutenzione

- Il repository viene normalmente aggiornato dai workflow dei singoli progetti applicativi
- Le pubblicazioni copiano i nuovi `.deb` nel `pool/` e rigenerano i metadata APT
- Evitare modifiche manuali a `dists/`, `pool/` e ai metadata, salvo manutenzione controllata

## Licenza e responsabilita'

I file di configurazione e documentazione di questo repository sono distribuiti con licenza `GPL-3.0-or-later`. Il testo completo e' disponibile in [LICENSE](LICENSE).

Il repository APT e' fornito "as is", senza garanzie espresse o implicite. L'utente e il manutentore restano responsabili della verifica dei pacchetti pubblicati, dei metadata generati e della corretta configurazione lato client.

Il nome, il logo e il marchio **STUDIO GD LEX** / **GD LEX** restano distinti dalla licenza del codice e non sono concessi in uso salvo autorizzazione separata.
