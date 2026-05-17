# Uso del repository APT GD LEX

## Aggiunta della sorgente APT

Il repository e' attualmente pubblicato senza firma GPG / `InRelease`. Per questo motivo l'aggiunta come sorgente APT richiede temporaneamente `trusted=yes`.

Esempio:

```bash
echo "deb [trusted=yes] https://cortomaltese88.github.io/gdlex-apt-repo stable main" | sudo tee /etc/apt/sources.list.d/gdlex.list
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

## Nota sul repository non firmato

- `trusted=yes` e' una soluzione provvisoria, non la configurazione finale desiderata
- finche' il repository resta non firmato, l'utente deve essere consapevole di questa eccezione
- la roadmap prevede l'introduzione futura della firma GPG
