
<img src="repo_transparent_100.png" alt="logo" style="float: right;">

# GITbash | CHEAT SHEET
### Git: Mitä se on?

Git on ilmainen ja avoimen lähdekoodin hajautettu versionhallintajärjestelmä, joka vastaa kaikesta GitHubiin liittyvästä, joka tapahtuu paikallisesti tietokoneellasi. Tämä pikaoppas sisältää tärkeimmät ja yleisimmin käytetyt Git-komennot helpon viitteen vuoksi.

### Asennus & graafiset käyttöliittymät

Alustakohtaisilla asennusohjelmilla Gitille, GitHub tarjoaa myös helpon tavan pysyä ajan tasalla viimeisimmistä komentorivityökalun julkaisuista tarjoten graafisen käyttöliittymän päivittäiseen vuorovaikutukseen, tarkasteluun ja arkiston synkronointiin.

- [Git for All Platforms: Documentation ](http://git-scm.com)


### Työskentely tilannekuvien ja Gitin väliaikaisen alueen kanssa

- `git status`  
  Näytä muokatut tiedostot työhakemistossa, jotka on valmiina seuraavaan committiin.

- `git add [tiedosto]`  
  Lisää tiedosto nykyisessä tilassaan seuraavaan committiisi (vaiheista).

- `git reset [tiedosto]`  
  Poista tiedosto väliaikaiselta alueelta säilyttäen muutokset työhakemistossa.

- `git diff`  
  Näytä muutokset, jotka eivät ole vielä vaiheistettu.

- `git diff --staged`  
  Näytä muutokset, jotka on vaiheistettu mutta ei vielä commitoitu.

- `git commit -m "[kuvaava viesti]"`  
  Commitoi vaiheistettu sisältö uudeksi tilannekuvaksi.

### Käyttäjätietojen määrittäminen, jota käytetään kaikissa paikallisissa arkistoissa

- `git config --global user.name "[etunimi sukunimi]"`  
  Aseta nimi, joka on tunnistettavissa version historian tarkastelussa.

- `git config --global user.email "[kelvollinen sähköposti]"`  
  Aseta sähköpostiosoite, joka liitetään jokaisen historian merkintään.

- `git config --global color.ui auto`  
  Aseta automaattinen komentorivin värittäminen Gitille helpottamaan tarkastelua.

### Käyttäjätietojen määrittäminen, arkistojen alustaminen ja kloonaaminen

- `git init`  
  Alusta olemassa oleva hakemisto Git-arkistoksi.

- `git clone [url]`  
  Hae koko arkisto isännöidyltä paikalta URL-osoitteen kautta.

### Työn eristäminen haaroihin, kontekstin vaihtaminen ja muutosten yhdistäminen

- `git branch`  
  Listaa haarasi. * näkyy nykyisen aktiivisen haaran vieressä.

- `git branch [haaran-nimi]`  
  Luo uusi haara nykyisessä commitissa.

- `git checkout`  
  Vaihda toiseen haaraan ja tarkista se työhakemistoosi.

- `git merge [haara]`  
  Yhdistä määritetyn haaran historian nykyiseen haaraan.

- `git log`  
  Näytä kaikki commitit nykyisen haaran historiassa.

### Päivitysten hakeminen toisesta arkistosta ja paikallisten arkistojen päivittäminen

- `git remote add [alias] [url]`  
  Lisää Git-URL aliasina.

- `git fetch [alias]`  
  Hae kaikki haarat kyseisestä Git-etäarkistosta.

- `git merge [alias]/[haara]`  
  Yhdistä etähaara nykyiseen haaraan saattaaksesi sen ajan tasalle.

- `git push [alias] [haara]`  
  Lähetä paikalliset haaran commitit etäarkiston haaraan.

- `git pull`  
  Hae ja yhdistä kaikki commitit seurattavasta etähaarasta.

### Tiedostojen poistamien ja polkumuutosten versiointi

- `git rm [tiedosto]`  
  Poista tiedosto projektista ja vaiheista poisto commitia varten.

- `git mv [nykyinen-polku] [uusi-polku]`  
  Muuta olemassa olevaa tiedostopolkua ja vaiheista siirto.

- `git log --stat -M`  
  Näytä kaikki commit-lokit ilmaisten kaikki siirretyt polut.

### Tallenna väliaikaisesti muokatut ja seuratut tiedostot vaihtaaksesi haaraa

- `git stash`  
  Tallenna muokatut ja vaiheistetut muutokset.

- `git stash list`  
  Listaa stashausten pinojärjestys.

- `git stash pop`  
  Kirjoita työhakemistoon pinon päällimmäisenä olevat muutokset.

- `git stash drop`  
  Hylkää pinon päällimmäisenä olevat muutokset.

### Haarojen uudelleenkirjoittaminen, committien päivittäminen ja historian tyhjentäminen

- `git rebase [haara]`  
  Sovella nykyisen haaran committeja määritetyn haaran edelle.

- `git reset --hard [commit]`  
  Tyhjennä väliaikainen alue, kirjoita työhakemisto uudelleen määritetystä commitista.

### Lokien, erojen ja objektitietojen tarkastelu

- `git log`  
  Näytä commit-historia nykyiselle aktiiviselle haaralle.

- `git log haaraB..haaraA`  
  Näytä commitit, jotka ovat haarassa A mutta eivät haarassa B.

- `git log --follow [tiedosto]`  
  Näytä commitit, jotka muuttivat tiedostoa, jopa nimeämisten yli.

- `git diff haaraB...haaraA`  
  Näytä ero siitä, mikä on haarassa A mutta ei haarassa B.

- `git show [SHA]`  
  Näytä mikä tahansa Git-objekti ihmisen luettavassa muodossa.

### Estä tiedostojen vahingollinen vaiheistaminen tai commitointi

- `git config --global core.excludesfile [tiedosto]`  
  Järjestelmänlaajuinen ohitusmalli kaikille paikallisille arkistoille.
