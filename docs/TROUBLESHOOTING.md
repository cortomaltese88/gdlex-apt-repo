# Troubleshooting

## `apt update` segnala cambio `Origin` / `Label` / `Suite` / `Codename`

Verificare il contenuto di `dists/stable/Release`. Se i metadata sono cambiati rispetto alla configurazione precedente del client, APT puo' richiedere conferma esplicita lato utente. Prima di intervenire, controllare che i valori attesi restino:

- `Origin: GDLEX`
- `Label: GDLEX`
- `Suite: stable`
- `Codename: stable`

## Il candidato non risulta aggiornato

Usare:

```bash
apt policy gdlex-pct-validator
```

Se la versione candidata non e' quella attesa, verificare che GitHub Pages abbia gia' pubblicato i file piu' recenti e che i metadata APT siano coerenti.

## `Packages` non contiene la nuova versione

Controllare che il `.deb` sia stato copiato correttamente in `pool/` e che `Packages` sia stato rigenerato. Se il file non elenca la nuova versione, il problema e' a monte del client APT.

## Metadata `Release` mancanti o incoerenti

Verificare `apt-ftparchive.conf` e il file `dists/stable/Release`. In particolare, controllare presenza e correttezza dei campi `Origin`, `Label`, `Suite`, `Codename`, `Architectures` e `Components`.

## GitHub Pages non ancora aggiornato

Dopo una pubblicazione, GitHub Pages puo' richiedere un breve tempo di propagazione. Prima di ripetere la pubblicazione, verificare se i file serviti dall'URL pubblico sono gia' aggiornati.

## `Bad credentials` o token scaduto

Se il workflow fallisce in pubblicazione, controllare i token e i permessi GitHub usati dal repository sorgente che aggiorna questo APT repo. Non inserire mai token nel repository.

## Pacchetto in stato `iF` lato client

Lo stato `iF` indica installazione incompleta o configurazione fallita lato utente. In questo caso il problema e' generalmente sul sistema client o nel pacchetto applicativo, non nei metadata APT statici.

## Quando NON fare force push

Non fare `force push` per correggere problemi ordinari di metadata, sincronizzazione o ritardi di Pages. Il `force push` va evitato salvo casi eccezionali e consapevoli, perche' rende piu' difficile auditare la storia delle pubblicazioni del repository APT.
