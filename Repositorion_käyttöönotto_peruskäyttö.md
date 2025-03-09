<img src="repo_transparent_100.png" alt="logo" style="float: right;">

# GitHub: repositorion käyttöönotto VScode
---
#### Tässä ohjeessa
__Uusi repo: työjärjestys__
1. Luo GitHub-repository
2. Aseta tunnukset Gitissä
3. Alusta Git-repository paikallisessa kansiossa
4. Lisää tiedostot, tee commit ja yhdistä GitHub-repositoryyn
5. Pushaa koodi GitHubiin

__Peruskäyttö__
- Muutosten push ja pull

---
### Luo uusi repository GitHubissa

- Kirjaudu sisään GitHub-tilille
   > 1.Napsauta oikeassa yläkulmassa olevaa "New" -painiketta (uuden repositoryn luominen).
   > 2.Anna repositorylle nimi (esim. my-project).
   > 3.Valitse repositoryn julkisuus (Public/Private).
   > 4.Älä lisää README.md -tiedostoa tai muuta sisältöä, sillä lisäät sen myöhemmin.
   > 5.Klikkaa "Create repository".

- Aseta GitHub-tunnukset tietokoneellasi
    >GitHubin käyttöön tarvitset Gitin asennettuna. Jos et ole asentanut sitä, voit ladata sen täältä. [Git for All Platforms: Documentation ](http://git-scm.com)
    >Aseta Git-tunnukset (vain kerran)
    >Avaa VSCode tai terminaali ja määritä Gitin käyttäjätunnukset:
    >
    >git config --global user.name "GitHub-käyttäjätunnus"
    >git config --global user.email "sähköpostiosoitteesi@example.com"

### Siirrä koodisi GitHubiin
- Siirry VScodessa koodikansioon
- Avaa terminaali (Bash)

- Alusta uusi Git-repositorio komennolla git init

    ```
    git init      | Tämä luo Git-repositorion hakemistoosi
    ```
    


- Voit tarkistaa, että repositorio on luotu, suorittamalla komennon:

    ```
    git status
    ```

    Jos repositorio on luotu, näet viestin:
    ```
    On branch master
    No commits yet
    nothing to commit (create/copy files and use "git add" to track)
-  Lisää tiedostoja kansioon

    >Tee README.md esimerkiksi VScode:ssa ja commitoi muutokset

    >GitBashillä voi myös luoda README.md tiedoston, tekstiä voi lisätä käyttäen md notafikaatioita
    >echo "Teksti tähän..# MipoRepo" > README.md
    
- Lisää tiedosto väliaikaiselle alueelle
    
    >**Optiot**
    >- git add README.md | Lisää tietty tiedosto
    >- git add .         | Lisää kaikki muutetut ja uudet tiedostot
    >- git add *.py      | Lisää kaikki tietyn tyyppiset tiedostot
    
    >**Commitoi muutokset**  
    git commit -m "Initial commit: README.md added"

    __Miksi "Initial commit" on tärkeä?__
    > - Versionhallinnan alku: Se merkitsee projektin alkamista ja luo pohjan kaikille tuleville muutoksille.
    > - Historian alku: Kaikki myöhemmät commitit perustuvat tähän ensimmäiseen committiin.
    > - Projektin dokumentointi: README.md tai muut alkuperäiset tiedostot antavat yleiskuvan projektista.
  
### Yhdistä GitHub-repositoryyn

   >Yhdistä paikallinen repository GitHubissa olevaan repositoryyn. 
   >Käytä GitHub-repositoryn URL:ää, jonka kopioit aiemmin.
   >
   >git remote add origin https://github.com/kayttaja/repository-name.git

### Pushaa koodisi GitHubiin

   >__git push -u origin master__
   >>
   >>Tämä asettaa master-haaran seuraamaan origin-etärepositorya, ja jatkossa voit käyttää pelkkää git push tai git pull ilman tarvetta määrittää etäosoitetta ja haaraa.

__Git push tarkemmin:__

   >__1. git push__
   >>git push on komento, jolla lähetät (push) paikallisen repositoryn muutokset etärepositoryyn (kuten GitHubiin).

   >__2. -u optio__
    >>Origin on oletusnimi etärepositorylle. Kun kloonaat repositoryn GitHubista tai muusta etäpalvelusta, se nimetään usein origin-nimiseksi. Voit vaihtaa sen toiseen nimeen, mutta origin on yleisin.

   >__4. master | main__
    >>master on perinteinen nimitys ensisijaiselle haaralle. Nykyään monet projektit käyttävät main-haaraa ensisijaisena, mutta tämä voi vaihdella.
    >*git push -u origin main*
    >>

---
### Perus käyttö 

> - git add – Lisää muutokset Gitin versionhallintaan.
> - git commit – Luo commit muutoksille.
> - git push – Puskaa muutokset etärepositoryyn ilman, että tarvitsee erikseen määrittää etärepositorya ja haaraa, koska upstream-haara on jo määritetty.

__1. Tee muutoksia koodiin__

Kun olet tehnyt muutoksia paikalliseen repositoryyn (esimerkiksi tiedostojen muokkausta tai lisäämistä), voit käyttää seuraavia komentoja:

    >**Optiot**
    >- git add README.md | Lisää tietty tiedosto
    >- git add .         | Lisää kaikki muutetut ja uudet tiedostot
    >- git add *.py      | Lisää kaikki tietyn tyyppiset tiedostot

__2. Tee commit muutoksille__
> git commit -m "Lisätty uusi ominaisuus"

__3. Pushaa muutokset etärepositoryyn__
> git push

__4. Vedä (pull) päivitykset etärepositorysta__
Jos etärepositoryyn on tullut muutoksia toisten tekijöiden toimesta, sinun on ehkä vedettävä (pull) päivitykset ennen omien muutosten työntämistä, jotta vältät mahdolliset yhteensopivuusongelmat.
>git pull
>
>Tämä lataa ja yhdistää uusimmat muutokset etärepositorysta nykyiseen paikalliseen haaraasi.

#### Lisäoptioita git push-komennolle
- __-force (tai -f)__
Pakottaa pushin etärepositoryyn, vaikka paikallinen historia ei vastaisikaan etärepositoryn historiaa 
__(tämä voi olla vaarallista, koska se voi ylikirjoittaa etärepositoryn historian)__:
>git push -f origin master

- __-dry-run__
Simuloi pushia, mutta ei tee mitään muutoksia etärepositoryyn. Tämä on hyödyllistä, jos haluat tarkistaa, mitä push-komento tekee ennen sen suorittamista:
>git push --dry-run origin master

- __-all__
Pushaa kaikki haarat, ei vain nykyistä:
>git push --all origin

- __-tags__
Pushaa kaikki paikalliset tagit etärepositoryyn:
>git push --tags origin

- __-set-upstream-to=<remote>/<branch>__
Jos haluat asettaa paikallisen haaran seuraamaan tiettyä etäharaa, voit käyttää tätä komentoa. Tämä on hyödyllistä, jos haluat määrittää uuden upstream-haaran:
>git push --set-upstream-to=origin/main

---
__Esimerkki commit-historiasta__
> __Bash:__
> git log

>__Näet commit-historiaa:__
>commit 1a2b3c4d5e6f7g8h9i0j (HEAD -> master)
>Author: OmaNimi <osahkoposti@example.com>
>Date:   Mon March 9 00:00:00 2025 +0300
>Initial commit
>
>---
