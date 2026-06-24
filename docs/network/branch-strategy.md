# Branch Strategy

## Struktura gałęzi
 - main - stabilna gałąź "produkcja" homelab
 - dev - gałąź robocza, tu trafiają gotowe funkcje
 - feature/* - tu pracuję nad konkretnym zadaniem

## Workflow
1. Tworzę feature/nazwa-zadania
2. Pracuję i commituje na feature
3. Merguje feature do dev
4. Gdy dev jest stabilny - mearguje do main
5. na main tworże tag wersji (v0.1.0)
