![Hello there!](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExZTd3aWY0cjJ5cWIzY3EybXBsaWE2cGQ2bXB5ZnA2cWMzYjJheGhkbiZlcD12MV9naWZzX3NlYXJjaCZjdD1n/Nx0rz3jtxtEre/giphy.gif)

># TO GIT OR NOT TO GIT
Om je code veilig te gaan bewaren of om het samenwerken aan projecten eenvoudiger te laten verlopen, kan je gebruik gaan maken van Git. Git maakt gebruik van remote repositories (kortweg: repo's) om nieuwe projecten op te starten of om bestaande/lokale bestanden of code te koppelen aan deze remote repo's. Er zijn een enkele opties om je repo's te beheren, dit kan via volgende tools:
- [De Github Desktop applicatie](#code-editor-visualstudio-code)
- [Code editor (VisualStudio Code)](#code-editor-visualstudio-code)
- [Git commands (CLI)](#git-commands-cli)

## GIT READY
Eerst en vooral heb je [Git for Windows](https://gitforwindows.org/) (en [Posh-Git](https://www.powershellgallery.com/packages/posh-git/0.5.0.2015) voor PS) nodig om lokaal aan de slag te kunnen met Git.

Verder moet je ook je lokale machine linken met de remote Git services. Dit kan via SSH keys om een veilige connectie te behouden, lees meer over het [toevoegen van SSH keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

>[!NOTE]
>Na authenticatie van je key kan je ook de nodige configuratie instellen zodat je jouw commits kan linken aan je GitHub account. Je kan hiervoor ook een username instellen (deze hoeft niet dezelfde te zijn als je GitHub username).
```PowerShell
git config --global user.name 'Master of Git'
git config --global user.email 'gitmaster@nzvl.be'
```

Wanneer je gaat werken met de CLI, is het aan te raden om de push configuratie in te stellen op 'simple'. Dit zorgt ervoor dat je op 1 branch pusht ipv alle branches (wat gebeurd bij de 'matching' optie).
```PowerShell
git config --global push.default simple
```

## GITHUB DESKTOP
Je kan gebruik maken van een desktop applicatie om je repo's te beheren, je kan deze downloaden via volgende link: [Download GitHub Desktop](https://desktop.github.com/).
De applicatie zorgt voor een gebruiksvriendelijke interface om een duidelijk overzicht te hebben van je repo's.

![Github desktop screenshot](https://github.com/Neutraal-Ziekenfonds-Vlaanderen/.github/assets/113903077/9b5150ba-4b10-4471-9609-93243e4c43cd)


## VISUALSTUDIO CODE
Het beheren van je repositories en branches kan tegenwoordig ook rechtstreeks in je code editor! Dit met behulp van de ingebouwde Source Control tool of met enkele extensies zoals Gitlens.

De Gitlens extensie heeft de meerwaarde dat deze ook de 'blame' functie heeft, dit maakt het mogelijk per regel te tonen wat de laatste commit was en door wie.

![Gitlens blame function](https://github.com/Neutraal-Ziekenfonds-Vlaanderen/first-repo/assets/113903077/3af35dd6-27fe-40d3-8fa0-5ea704b17e71)

![Shame!](https://media0.giphy.com/media/vX9WcCiWwUF7G/giphy.gif?cid=6c09b9525ix3e7xyr3o8nfsi4olz1b32nn84iaomnu220yjz&ep=v1_gifs_search&rid=giphy.gif&ct=g)

## CIT COMMANDS
Indien je makkelijker je weg vindt in de terminal, kan je jouw git goodies ook beheren via deze weg. Je kan ook een Git Shell openen via de desktop applicatie maar omdat deze gebruik maakt van een 32 bit versie in plaats van 64 bit, geeft dit problemen bij enkele PowerShell modules. Hieronder staat beschreven hoe je een PowerShell ISE sessie kan starten zonder problemen!

[Github setup for PowerShell](https://mikefrobbins.com/2016/02/09/configuring-the-powershell-ise-for-use-with-git-and-github/#documentTop)

Via deze weg kan je adhv enkele commands snel door je repo's gaan, commits pullen, nieuwe branches maken, etc. Hieronder even de basis Git commands kort uitgelegd om aan de slag te kunnen gaan.

`git init` maakt lokaal een nieuwe repo aan. **Deze staat enkel lokaal!** Om deze ook remote te zetten, kan je deze adden, committen en pushen.
```PowerShell
git add .
git commit -m 'Init new repo'
git push --set-upstream origin main
```

`git pull` Haal de laatste wijzigingen van de remote repo binnen om je lokale repo te updaten.

`git add .` Voeg alle wijzigingen in je lokale repo toe aan de commit tree. Je kan de gewijzigde bestanden ook één voor één of per folder toevoegen via `git add <bestand>`.

`git commit -m 'Samenvatting wijzigingen'` Hiermee kan je een opmerking (commit message) toevoegen om te verduidelijken welke wijzigingen er gebeurd zijn. Je kan ook meerdere commits toevoegen vooraleer je deze pusht naar de remote repo. Dit zorgt voor een beter overzicht van alle wijzigingen.

`git push` Als laatste kan je de lokale commit tree pushen naar de remote repo. Hierdoor wordt er dus remote ook een nieuwe versie gemaakt.

![Meme merge conflicts](https://github.com/Neutraal-Ziekenfonds-Vlaanderen/first-repo/assets/113903077/948d75a1-90e0-437d-84f0-5c0bfcf67a2f)

Wanneer je start in een lokale repo die niet up-to-date is met de (reeds bestaande) remote repo en je hierin commits wil pushen, ga je te maken krijgen met merge conflicts. Dit gebeurd wanneer je een bestand gewijzigd hebt in jouw commit, welke ook in een pull commit zit. Vooraleer je een werkt aan een bepaalde repo is het dus belangrijk steeds het pull command eerst te gebruiken om ervoor te zorgen dat je lokale repo up-to-date is!

`git stash` Heb je toch merge conflicts en wil je jouw wijzigigen even apart bijhouden zonder deze te verliezen, dan kan je gebruik maken van stash. Dit maakt het mogelijk je commit(s) toe te voegen aan een lijst om deze op later moment terug op te halen. Je stash kan je op een later moment, bijvoorbeeld na een `git pull`, terug ophalen via het `git pop command`.

Met behulp van `git stash save 'Beschrijving stash'` kan je een beschrijving toevoegen aan je stash items. Dit zorgt voor extra leesbaarheid in de `git stash list`.

**.gitignore**

Er zijn projecten waar je niet alles wil meepushen naar je remote repo (bijvoorbeeld build bestanden), deze bestanden of directories kan je toevoegen aan de .gitignore om deze enkel lokaal te houden.

>[!NOTE]
>Let op! Git files die reeds getracked worden, kunnen niet zomaar in de gitignore file worden toegevoegd. Je kan deze bestanden untracken via `git rm --cached <bestand>`
