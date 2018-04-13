### Podatkovno rudarjenje, vmesno poročilo o opravljenem delu, 12. 4. 2018

# Priprava podatkov in osnovna vizualizacija

**Nejc Prijatelj**

**Žan Pristopec**

**Miha Štravs**

## Podatki

Kratek opis podatkov je bil podan že pri osnutku projekta, tu pa bi si najprej na hitro pogledali kaj točno dani podatki vsebujejo. Gre za podatke o trending videih na strani youtube, link do podatkov(https://www.kaggle.com/datasnaek/youtube-new/data).

Vse podatke ki smo jih dobili s spletne strani Kaggle hranimo v diretktoriju "data" in so sledeči:

* *CAvideos.csv:* podatki o trendih videih za Kanado,
* *DEvideos.csv:* podatki o trendih videih za Nemčijo,
* *FRvideos.csv:* podatki o trendih videih za Francijo,
* *GBvideos.csv:* podatki o trendih videih za Veliko Britanijo,
* *USvideos.csv:* podatki o trendih videih za Združene Države,

Vsak podatek v tej zbirki ima naslednje atribute:

* *video_id:* je kar link do videa, in je za vsak vnešen podatek unikaten.
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

### Kaj nas zanima?
Pri projektni nalogi želimo ugotoviti:
* glavne značilnosti trending videov,
** kako pomembni so "tagi",
* kakšne in kako velike so razlike po regijah,
* vpliv časa(npr. koliko časa mine od "uploada" pa do dne ko se video znajde na trending strani?),



### Pridobivanje podatkov
Samo branje podatkov ni bilo težko saj je podatkovna zbirka lepo urejena. Podatke smo prebrali v pandas data frame z preprosto funkcijo, za vsako državo posebej:

def read_table(file_name):
    data = pan.read_csv(file_name, sep=',')
    return data
    
Kar nas je takoj zmotilo je bil format v katerem je bil zapisan datum zato smo ga spremenili v nam bolj domačega:
YY.DD.MM &rarr; DD.MM.YY


### Nekaj vizualnih predstavitev
Naša podatkovna zbirka vsebuje na dan izdelave tega poročila kar 116739 podatkov, ki pa se skoraj dnevno posodabljajo.
Ker je tako velika količina podatkov prevelika da bi iz nje lahko kar tako ugotovili določene zanimive lastnosti, smo se odločili da bomo najprej naredili nekaj grafov da dobimo občutek s čem imamo opravka, in da predstavimo nekatere bolj zanimive podatke.

Najprej smo naredili stolpčne diagrame ki nam pokažejo koliko je trending videov glede na kategorijo. To smo naredili za vse države in izkazalo se je da je v večini prevladala kategorija entertainment, le v Veliki Britaniji so očitno bolj priljubljeni videi iz kategorije music.

![Alt text](images/CA_cat.png?raw=true "CA_cat")

![Alt text](images/GR_cat.png?raw=true "GR_cat")

Naslednje nas je zanimalo koliko youtube kanalov ima določeno število videov. Zato smo naredili naslednje grafe iz katerih je razvidno da ima največ kanalov od 11 pa tja do 15 trending videov.

![Alt text](images/per_channel.png?raw=true "per_channel")

Z naslednjim pie chart-om prikazujemo pričakovan podatek, in sicer je vidno da je razmerje pozitivnih ocen in negativnih močno v prid pozitivnih. Variacije po državah so minimalne.

![Alt text](images/pie.png?raw=true "pie") ![Alt text](images/CA_pie.png?raw=true "CA") ![Alt text](images/DE_pie.png?raw=true "DE") ![Alt text](images/GB_pie.png?raw=true "GB_pie")


*Koda za zgoraj pridobljene rezultate se nahaja v datoteki project_code.ipynb(https://github.com/n3jc123/PR18NPZPMS/blob/master/project_code.ipynb)*

