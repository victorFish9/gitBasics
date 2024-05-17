# git-oppimispaivakirja
Johdanto versionhallintaan

Harjoitus 1

1. git ja VSCode olivat asenettu aikoja sitten.
2. git ja editorin käyttäjätiedot oli konfigorouitu Back end kursilla
3. Github tili on luotu Back end kursilla

Vaikka kaikki tarvittavat olin asentanut aikoja sitten, silti pääsin tutustumaan git sanastoon, joka oli minulle hyödyllistä

Paikallinen Git

Peruskäyttö

demo kansio sekä tyhjän repon luotu seuraavilla komennoilla:
mkdir demo
cd demo
git init

libgit2 sain clounattua kansion ja poistettua samalla: 
git clone https://github.com/libgit2/libgit2
rm -r libgit2

git tilan tarkistaminen:
git status

muutosten tallettaminen ja tarkistaminen

git add tiedostonNimi / . (piste viittaa koko hakemistoon ts. talennetaan koko hakemisto eikä pelkkä tiedosto)
git commit / git commit -m "oma viesti"
tarkistaminen:
git status
git log

tiedostojen poistaminen ja siirtäminen

poistaminen -> rm
git rm text.txt
git commit -m "oma viesti"

siirtäminen/uudelleen nimeäminen -> mv

uudelleen nimeäminen:
git mv vanha_tiedoston_nimi uuden_tiedoston_nimi

siirtäminen:
git mv tiedoston_nimi hakemiston_nimi

Harjoitus 2
touch test.txt
mkdir hello
cd hello
touch hello.html
mv hello.html index.html
rm test.txt
touch anotherFile.txt
git add .
git commit -m "poistettu ja lisätty 
uusi tiedosto"

Paluu menneisyyteen

Paluu menneisyyteen onnistuu git log ja git checkout commit_numeron avulla.

git log
git checkout a7b69b6f7

nykytilaan palauttaminen tapahtuu:
git switch - 

Harjoitus 3
1. useita muutoksia
mkdir new_dr 
mkdir new_dr2
2. add-toiminnon peruuttamista
git add .
git reset
git status
git add .
git reset HEAD new_dr
git reset HEAD new_dr2
3. Kokeile työtilaan tehtyjen muutosten peruuttamista
touch new_dr/newFile.txt
git add .
git commit -m "tiedosto luotu hakemistoon"
git log 
git checkout e8e3af27d468
git reset .
4. Talletuksen peruuttamista
git add .
git commit -m "Talletettu kaikki muutokset"
git revert HEAD
git log : 
commit 76b60fb29b1bd714ea2d260e2bb06fbff9211c4c (HEAD)
Author: Victor <aue228lublupacanov@gmail.com>
Date:   Thu May 16 13:17:19 2024 +0300

    tallenetaan kaikki muutokset

commit e8e3af27d4681e75993b3e06e599ee98e17e59a1
Author: Victor <aue228lublupacanov@gmail.com>
Date:   Thu May 16 13:09:31 2024 +0300

    tiedosto luotu hakemistoon


Etärepositoriot

Kloonaus
git clone https://github.com/libgit2/libgit2

Etärepositorion määrittely
git remote add origin https://github.com/user/repository.git

Etärepositorion listaus
git remote
git remote -v

Etärepositorion uudelleennimeäminen ja poistaminen
git remote rename origin temp
git remote rm temp

Tietojen haku etärepositoriosta

Fetch lataa etärepositorion tiedot paikalliseen repositorioon
git fetch origin
git branch -r
git checkout master
git merge origin/master

Pull
hakee nykyisen haaran uudet tiedot etärepositoriosta ja yhdistää ne nykyiseen haaraasi automaattisesti

git pull origin
sama kuin
git fetch
git merge

Tietojen vienti etärepositorioon
git push origin master

kaikki paikalliset haarat viedään tämän avulla
git push --all

Tämä komento asettaa kyseinen etärepositoriohaaran vietävän paikallisen haaran oletusarvoiseksi etärepositoriohaaraksi.
git push -u origin master

Tällöin etärepositoriota ei tarvitse jatkossa erikseen komennossa ilmoittaa vaan riittää
git push

Etärepositoriot ja haarat

etärepositorion synkrointi
git push -u origin commit_code

Harjoitus 5
1.
Loin tyhjän repostirotion Githubiin.
Mitä GitHub-repositoriosivulla näkyy?:
quick setup with command line.
2-4.
mkdir harjoitus5
touch text.txt
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:victorFish9/
test.git
git push -u origin main
github-repositorisivulla on nyt pushattu text.txt tiedosto
sain tiedoston päivitettyä

6.
git fetch
git checkout origin/master
8.
git checkout master
git merge origin/master

Git projektissa
Talletusten käytännöt

git diff --check

Yhteistyö keskitetyssä mallissa 

git clone <repository-url>
git commit 
git push origin master

Rinnakkaiset muutokset

git fetch origin          # 1, haetaan muiden tekemät muutokset
git merge origin/master   # 2. yhdistetään ne omiin muutoksiin
# ...ratkotaan mahdolliset konfliktit
git push origin master    # 3. viedään valmis lopputulos yhteiseen repositorioon

fetch ja merge voi myös oikaista pull avulla
git pull origin master
on suositeltavaa käyttää git status ennen pull


Harjoitus 6
git remote add actions https://github.com/mruonavaara/git-actions.git
git fetch actions main
git merge actions/main --allow-unrelated-histories

1.
git switch -c develop
git push -u origin develop

2.Lisäys html tiedostoon ja talletus
<div id="datetime"></div>
<button>Mitä kello on?</button>
git add .
git commit -m "html tiedosto päivitetty"
git config pull.rebase false
git pull

3.
<script src="scripts.js"></script>
git mv scripts.js .github/test
onclick="setTime()
git add .
git commit -m "talletus"
git checkout main
git merge develop

4.
css rivit on lisätty onnistuneesti

5.
en löytänyt

6.
viety ilman 5. vaihetta
