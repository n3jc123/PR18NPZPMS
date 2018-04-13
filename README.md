### Podatkovno rudarjenje, koda za vmesno poročilo o opravljenem delu, 12. 4. 2018

# Priprava podatkov in osnovna vizualizacija

**Nejc Prijatelj**

**Žan Pristopec**

**Miha Štravs**

## Podatki

Kratek opis podatkov je bil podan že pri osnutku projekta, tu pa bi si najprej na hitro pogledali kaj točno dani podatki vsebujejo. Link do podatkov(https://www.kaggle.com/datasnaek/youtube-new/data).

Vse podatke ki smo jih dobili s spletne strani Kaggle hranimo v diretktoriju "data" in so sledeči:

* *CAvideos.csv:* podatki o trendih videih za Kanado,
* *DEvideos.csv:* podatki o trendih videih za Nemčijo,
* *FRvideos.csv:* podatki o trendih videih za Francijo,
* *GBvideos.csv:* podatki o trendih videih za Veliko Britanijo,
* *USvideos.csv:* podatki o trendih videih za Združene Države,

Vsak podatek v tej zbirki ima naslednje atribute:
* *video_id:* je kar link do videa, in je za vsak vnesen podatek unikaten.
* *trending_date:* datum, katerega je bil video trending.
* *title:* naslov videa.
* *channel_title:* ime youtube kanala ki je video naložil na youtube.
* *category_id:* id kategorije v katero spada video.
* *publish_time:* kdaj je bil video naložen.
* *tags:* ključne besede ki opisujejo video.
* *views:* število ogledov.
* *likes:* število pozitivnih odzivov.
* *dislikes:* število negativnih odzivov.
* *comment_count:* število komentarjev.
* *thumbnail_link:* link do thumbnaila.
* *comments_disabled:* onemogočeni komentarji(true/false).
* *ratings_disabled:* onemogočen odziv na video(true/false).
* *video_error_or_removed:* če je bil video odstranjen(true/false).
* *description:* opis.

Poleg petih že naštetih csv datotek pa podatkovna zbirka vsebuje še pet json datotek, v katerih je podrobneje opisan atribut *category_id* za vsako regijo. Na kratko povedano nam pove kaj pomeni naprimer category_id = 10 &rarr; "music".

### Pridobivanje podatkov

Najprej smo vse podatke prebrali v panda data frame s spodaj napisano funkcijo, in v vsaki tabeli spremenili datume tako, da so bolj po našem okusu.

### Nekaj vizualnih predstavitev

Ker je tako velika količina podatkov prevelika da bi iz nje lahko kar tako ugotovili določene zanimive lastnosti, smo se odločili da bomo najprej naredili nekaj grafov da dobimo občutek s čem imamo opravka, in da predstavimo nekatere bolj zanimive podatke.

Najprej smo naredili stolpčne diagrame ki nam pokažejo koliko je trending videov glede na kategorijo. To smo naredili za vse države in izkazalo se je da je v večini prevladala kategorija entertainment, le v Nemčiji so očitno bolj priljubljeni videi iz kategorije music.

![Alt text](images/CA_cat.png?raw=true "CA_cat")

![Alt text](images/GR_cat.png?raw=true "GR_cat")

Naslednje nas je zanimalo koliko youtube kanalov ima določeno število videov. Zato smo naredili naslednje grafe iz katerih je razvidno da ima največ kanalov od 11 pa tja do 15 trending videov.

![Alt text](images/per_channel.png?raw=true "per_channel")
