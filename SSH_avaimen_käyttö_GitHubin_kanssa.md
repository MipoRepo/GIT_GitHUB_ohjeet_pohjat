<img src="repo_transparent_100.png" alt="logo" style="float: right;">

# SSH-avaimen käyttö GitHubin kanssa
SSH-avaimen käyttö GitHubin kanssa on hyvä tapa autentikoida ja turvallisesti puskea koodia ilman, että tarvitsee syöttää GitHubin käyttäjätunnusta ja salasanaa joka kerta. Tässä on ohjeet SSH-avaimen luomiseen ja sen käyttöönottoon GitHubissa:

    1. Luo SSH-avain komennolla ssh-keygen
    2. Lisää avain SSH-agenttiin komennolla ssh-add
    3. Lisää julkinen SSH-avain GitHubiin "SSH and GPG keys" -asetuksista
    4. Testaa yhteys komennolla ssh -T git@github.com
    5. Käytä SSH-URL:ää repositoryjen kanssa


#### Vaihe 1: Tarkista, onko sinulla jo SSH-avain

Ennen kuin luot uutta SSH-avainta, tarkista, onko sinulla jo olemassa avain.
>Avaa terminaali ja tarkista, onko SSH-avaimia kansiossa ~/.ssh:
>
>bash
>__ls -al ~/.ssh__
>Jos kansiossa on tiedostoja kuten id_rsa ja id_rsa.pub, sinulla on jo olemassa SSH-avaimet.
>
>>*Jos ei ole, jatka SSH-avaimen luomiseen!*

#### Vaihe 2: Luo uusi SSH-avain

Avaa terminaali ja luo uusi SSH-avain komennolla (korvaa your_email@example.com omalla GitHub-sähköpostiosoitteellasi):
>ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

Tämä komento luo uuden SSH-avaimen käyttäen RSA-algoritmia 4096-bittisellä avaimella.
>Sinua pyydetään valitsemaan, mihin tallennat avaimen. Voit painaa Enter, jolloin avain tallennetaan oletuskansioon ~/.ssh/id_rsa.
>Jos haluat, voit määrittää salasanan (passphrase) avaimelle. Tämä on lisäkerros turvallisuutta varten, mutta voit myös jättää kentän tyhjäksi ja painaa Enter.

#### Vaihe 3: Lisää SSH-avain SSH-agenttiin

SSH-agentti huolehtii SSH-avaimen hallinnasta ja varmistaa, että sinun ei tarvitse syöttää avaimen salasanaa joka kerta.

1. Käynnistä SSH-agentti:
>eval "$(ssh-agent -s)"

2. Lisää luomasi SSH-avain agenttiin:
>ssh-add ~/.ssh/id_rsa

#### Vaihe 4: Lisää SSH-avaimen julkinen osa GitHubiin

1. Kopioi SSH-avaimen julkinen osa (id_rsa.pub) GitHubiin lisättäväksi. Voit käyttää cat-komentoa:
> cat ~/.ssh/id_rsa.pub

2. Mene GitHubiin ja kirjaudu sisään
3. Mene Settings-osioon ja valitse vasemmalta SSH and GPG keys
4. Klikkaa New SSH key
5. Liitä kopioitu SSH-avain Key-kenttään ja anna sille nimi (esim. "My Laptop SSH Key").
6. Klikkaa Add SSH key.


#### Vaihe 5: Testaa yhteys GitHubiin

Varmista, että SSH-yhteys GitHubiin toimii oikein:
>ssh -T git@github.com

Jos kaikki on kunnossa, näet viestin, joka ilmoittaa, että olet onnistuneesti kirjautunut GitHubiin:
>Hi username! You've successfully authenticated, but GitHub does not provide shell access.

#### Vaihe 6: Käytä SSH:ta GitHubin kanssa

Kun SSH-avain on lisätty, voit alkaa käyttää sitä GitHubin kanssa ilman käyttäjätunnuksen ja salasanan syöttämistä. Kun lisäät etärepositoryn, varmista, että käytät SSH-URL:ää eikä HTTPS-URL:ää.

>git remote add origin git@github.com:username/repository-name.git


