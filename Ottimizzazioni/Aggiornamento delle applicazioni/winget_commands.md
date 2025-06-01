# Winget: Comandi Principali

## 1. Cercare un pacchetto
```powershell
winget search <keyword>
# Esempio:
winget search vscode
```

## 2. Installare un’app
```powershell
winget install <PackageIdentifier>
# Esempio:
winget install Microsoft.VisualStudioCode
```

## 3. Elencare le app installate
```powershell
winget list
```

## 4. Aggiornare un singolo pacchetto
```powershell
winget upgrade --id <PackageIdentifier>
# Esempio:
winget upgrade --id Mozilla.Firefox
```

## 5. Aggiornare tutti i pacchetti
```powershell
winget upgrade --all
```

## 6. Disinstallare un’app
```powershell
winget uninstall <PackageIdentifier>
# Alias: winget remove, winget rm
```

## 7. Esportare la lista dei pacchetti
```powershell
winget export -o packages.json
```

## 8. Importare i pacchetti da un file
```powershell
winget import -i packages.json
```

## 9. Mostrare i dettagli di un pacchetto
```powershell
winget show <PackageIdentifier>
```

## 10. Informazioni sul client Winget
```powershell
winget --info
```