# GHC und GHCI mit Windows10/GitBash/Stack

## Installation
Stack installiert auf Windows
- C:\sr und
- C:\Users\user\AppData\


## GHCI
Windows GitBash> stack exec ghci oder stack ghci

## Script
> stack exec runghc file.hs oder stack runghc file.hs

## Projekt
stack new name new-template; cd name  
stack build  
make changes to hs-files in app/ und src/  
stack build  
stack exec name-exe  



# Haskell-IDE-Engine mit Windows/VSCode

## Installation
https://github.com/alanz/vscode-hie-server, using stack
dauerte mehrere Stunden

installiert HIE auf Windows
- C:\hie
- C:\Users\user\AppData\

In VSCode die Extension Haskell Language Server aktivieren

VSCode Settings: Language Server Haskell > Trace:Server      auf verbose stellen,
denn bei mir gab es einige Hürden


##Verwendung
Neues Projekt erstellen mit GitBash und stack, siehe oben

>code		Es öffnet sich VSCode.

Ordner des eben erstellten Projektes öffnen und in src/ oder lib/ eine
	hs-Datei anklicken, dann sollte alles functionieren aber:

### Fehlermeldung:
Mismatching GHC versions: Stack project is 8.8.3, HIE is 8.6.5
You may want to use hie-wrapper. Check the README for more information

stack.yaml:  
#&#8203;resolver: lts-15.4 <!-- !#8203; zero with space -->  
resolver: lts-14.20  
>stack build ladet diese Version (ghc-8.6.5) auf AppData\Local\Programs\stack\x86_64-windows

### Neue Fehlermeldung:
Cannot satisfy ...  
VSCode schließen und in GitBash "code" eingeben

Hoover funktioniert, dauert aber



# Haskell-IDE-Engine mit Debian/WSL VSCode

## Installation
WSL
Debian
cabal und gch über downloads.haskell.org/debian

Versuche mit

NIX mit cachix (schneller, da binaries)
HIE mit cachix
RemoteWSLExtension für VSCode
Nix Environment Selector für VSCode

schlugen alle fehl, verwende daher obige Windows HIE

Das Problem bei NIX/Debain/WSL scheint zu sein:
in /etc/nix/nix.config muss man schreiben:
sandbox = false
use-sqlite-wal = false

Besser dürfte Dual Boot sein.

Bleibe daher zum Compilieren bei Windwos.
Für die Paketerstellung mit NIX wechsle ich auf Debian/WSL

### fdlock Fehlermeldungen
Diese sind unter anderem auch aufgetaucht und scheinen entscheidend zu sein.
Sie sollen nur bei WSL 1 auftreten, WSL 2 ist erst ab windows build 18917 erhältlich.
Dieses ist vorab mit der Gefahr des Garantieverlustes downloadbar (Windwos Insider Programm).

