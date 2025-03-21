## Git: Virheellisen Branchin Poistaminen ja `git push` -ongelmien ratkaisu

### 🔹 Paikallisen branchin poistaminen
1. Varmista, ettet ole poistettavalla branchilla:
   ```bash
   git checkout main  # Vaihda toiselle branchille
   ```
2. Poista branch:
   ```bash
   git branch -d branchin-nimi
   ```
   - Jos branch ei ole täysin yhdistetty (`merged`), pakotettu poisto:
     ```bash
     git branch -D branchin-nimi
     ```

### 🔹 Etäbranchin (remote) poistaminen
Poista branch GitHubista tai muusta etärepostasi:
```bash
 git push origin --delete branchin-nimi
```

### 🔹 Vanhat viittaukset ja päivittäminen
1. Tarkista, näkyykö poistettu branch edelleen listauksessa:
   ```bash
   git branch -a
   ```
2. Päivitä viittaukset:
   ```bash
   git fetch --prune
   ```
   Jos tämä ei auta, poista kaikki vanhat viittaukset:
   ```bash
   git remote prune origin
   ```

### 🔹 `git push` ei toimi? Kokeile näitä
1. **Tarkista virheilmoitus** ja varmista, että olet oikealla branchilla:
   ```bash
   git branch
   ```
2. **Varmista etärepository:**
   ```bash
   git remote -v
   ```
   Jos se puuttuu, lisää se:
   ```bash
   git remote add origin https://github.com/kayttajanimi/repon-nimi.git
   ```
3. **Päivitä ja yritä uudelleen:**
   ```bash
   git pull --rebase
   git push origin main
   ```
4. **Kirjaudu uudelleen sisään, jos tarvitaan:**
   ```bash
   git credential reject https://github.com
   git push
   ```
5. **Pakota push (jos historia on muuttunut):**
   ```bash
   git push --force
   ```
6. **Tarkista SSH-yhteys (jos käytössä):**
   ```bash
   ssh -T git@github.com
   ```
   Jos SSH ei toimi, varmista, että SSH-avain on lisätty GitHubiin.
c