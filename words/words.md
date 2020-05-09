<div class="section">
    <div>
    	<iframe id="splash" width="960" height="480" src="banners/splash.html"></iframe>
        <div style="top: 70px;font-size: 75px;font-weight: bold;">
        	Šta se sledeće dešava? 
       	</div>
		<div style="font-weight: 500;top: 140px;left: 10px;font-size: 29px;">
			COVID-19 budućnosti, objašnjene sa interaktivnim simulacijama
		</div>
		<div style="font-weight: 100;top: 189px;left: 10px;font-size: 19px;line-height: 21px;">
			<b>
				🕐 30 min igre/čitanja
				&nbsp;&middot;&nbsp;
			</b>
			pripremili
			<a href="https://scholar.google.com/citations?user=_wHMGkUAAAAJ&amp;hl=en">Marcel Salathé</a>
			(epidemiološka slika)
			&
			<a href="https://ncase.me/">Nicky Case</a>
			(umetnost/kod)
		</div>
	</div>
</div>

"Jedina stvar za strah je sam strah" bio je glup savet.

Naravno, ne morate nagomilavati rolne toalet papira – ali ako se oni zaduženi za donošenje odluka plaše straha, oni će podceniti realnost situacije sa ciljem da izbegnu "masovnu paniku". Strah nije problem, već kako *kanališemo* naš strah. Strah nam daje energiju da se nosimo sa opasnostima sada i priprema nas za opasnosti kasnije.

Iskreno, mi (Marcel, epidemiološka slika + Nicky, umetnost/kod) smo zabrinuti. Kladimo se, i vi ste! Zato smo mi kanalisali naš strah u pripremanje ovih **simulacija za igranje**, tako da *vi* možete kanalisati strah u razumevanje:

* **Poslednjih nekoliko meseci** (uvodni kurs epidemiologije, SEIR model, R & R<sub>0</sub>)
* **Narednih nekoliko meseci** (ograničenja kretanja, praćenje kontakata, maske)
* **Narednih nekoliko godina** (gubitak imuniteta? nedostatak vakcine?)

Ovaj vodič (objavljen prvog maja 2020. vidi ovu fusnotu!→[^timestamp]) za cilj ima da u vama pobudi nadu *i* strah. Da bismo pobedili COVID-19 **na način koji čuva naše mentalno i finansijsko stanje**, potreban nam je optimizam za smišljanje planova, i pesimizam za smišljanje rezervnih planova. Po rečima Gladis Brovnin Stern (Gladys Bronwyn Stern): *“Optimista izmisli avion a pesimista padobran.”*

[^timestamp]: Fusnote će sadržati izvore informacija, linkove i bonus komentare, kao ovaj komentar!
    
    **Ovaj vodič je objavljen prvog maja 2020.** Mnogi detalji će se menjati ali smo mi uvereni da će ovaj vodič pokriti 95% mogućih budućnosti i da će početni kurs Epidemiologije biti zauvek od koristi.

Vežite se: na putu smo da osetimo turbulencije.

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Poslednjih nekoliko meseci</div>
    </div>
</div>

Piloti koriste simulatore letenja da nauče kako da ne ruše avione.

**Epidemiolozi koriste simulatore epidemija da nauče kako da ne uruše čovečanstvo.**

Počećemo od veoma, *veoma* jednostavnog "epidemiološkog simulatora letenja"! U ovoj simulaciji, <icon i></icon> zarazni ljudi (eng. Infected) mogu preneti zarazu na podložne/zdrave ljude <icon s></icon> (eng. Susceptible) uvećavajući tako broj zaraznih <icon i></icon>:

![](pics/spreadsrb.png)

Procenjeno je da *se na početku* COVID-19 pandemije, virus prenosio sa <icon i></icon> na <icon s></icon> svaka 4 dana, *u proseku*.[^serial_interval] (zapamtite, ovo puno varira)

[^serial_interval]: “Prosečno vreme prenošenja zaraze (eng. serial interval) je 3.96 dana (interval poverenja od 95% je 3.53–4.39 dana)”. [Du Z, Xu X, Wu Y, Wang L, Cowling BJ, Ancel Meyers L](https://wwwnc.cdc.gov/eid/article/26/6/20-0357_article) (Upozorenje: Preliminarne verzije članaka ne treba uzimati u obzir na isti način kao finalne verzije.)

Ako simuliramo "dupliranje broja slučajeva na svaka 4 dana" *i ništa više*, na nivou populacije sa samo 0.001% <span class="nowrap"><icon i></icon>,</span> šta se događa? 

**Pritiskom na "Pokreni" pokreće se simulacija! Možete je puštati ponovo kasnije sa drugačijim parametrima:** (tehnički detalji: [^caveats])

[^caveats]: **Zapamtite: sve ove simulacije su vrlo pojednostavljene u svrhu obrazovanja.**
    
    Jedno pojednostavljenje: Kada kažete simulaciji "Inficiraj 1 novu osobu svakih X dana", ona zapravo povećava broj zaraznih za 1/X svakog dana. Slično za buduća podešavanja u ovim simulacijama – "Oporavak svakih X dana" zapravo umanjuje broj zaraznih za 1/X svakog dana.
    
    Ove dve interpretacije *nisu* u potpunosti iste, ali su dovoljno blizu, i za potrebe obrazovanja učinkovitije su od direktnog uspostavljanja stopa transmisije i oporavka.

<div class="sim">
		<iframe src="sim?stage=epi-1" width="800" height="540"></iframe>
</div>

Ovo je **kriva eksponencijalnog rasta.** Počinje malim brojevima, ali brzo eksplodira. Od "oh pa to je samo grip" do "zapravo, grip ne uzrokuje *masovne grobnice u bogatim gradovima*". 

![](pics/exponentialsrb.png)

Ali, ova simulacija je pogrešna. Eksponencijalni rast, na svu sreću, ne dešava se u nedogled. Jedna stvar koja zaustavlja širenje virusa su ljudi koji *već* imaju virus:

![](pics/susceptiblessrb.png)

Što je više zaraznih <span class="nowrap"><icon i></icon></span>, brže zdravi <span class="nowrap"><icon s></icon></span> postaju zarazni <span class="nowrap"><icon i></icon>,</span> **ali ima manje zdravih <span class="nowrap"><icon s></icon>,</span> pa *sporije* zdravi <span class="nowrap"><icon s></icon></span> postaju zarazni <span class="nowrap"><icon i></icon>.</span>**

Kako ovo menja rast zaraženih tokom epidemije? Otkrijmo:

<div class="sim">
		<iframe src="sim?stage=epi-2" width="800" height="540"></iframe>
</div>

Ovo je "S-kriva" ili **kriva logističkog rasta.** Počinje malim brojevima, zatim eksplodira, a onda usporava.

Ali, ova simulacija je *i dalje* pogrešna. Nismo iskoristili činjenicu da zarazni <icon i></icon> u nekom trenutku prestaju da budu zarazni, ili 1) oporavkom, 2) "oporavkom" sa oštećenim plućima, ili 3) umiranjem.

Zarad pojednostavljenja, hajde da pretpostavimo da svi <icon i></icon> zarazni ljudi postaju <icon r></icon> oporavljeni (eng. Recovered). (Samo zapamtite da u realnosti, neki umiru. Prim. prev. zato se na engleskom u okviru SIR modela - Recovered često nazivaju i Removed, tj. uklonjeni iz daljeg epidemiološkog razmatranja ili smrću ili trajnim imunitetom) <span class="nowrap"><icon r></icon>s</span> oporavljeni ne mogu ponovo biti zaraženi, i pretpostavimo – *za sada!* –da oni ostaju doživotno imuni.

U slučaju COVID-19, procenjeno je da su <icon i></icon> zarazni 10 dana, *u proseku*.[^infectiousness] To znači da će se nekiporaviti za manje od 10 dana, a nekima će biti potrebno više. **To izgleda ovako sa simulacijom koja *počinje* sa 100% <span class="nowrap"><icon i></icon>:</span>**

[^infectiousness]: “Medijalna vrednost perioda tokom koga je COVID-19 pozitivna osoba zarazna \[...\] je 9.5 dana.” [Hu, Z., Song, C., Xu, C. et al](https://link.springer.com/article/10.1007/s11427-020-1661-4) Da, znamo da "medijalna" vrednost nije isto što i "prosečna vrednost". U cilju ovog pojednostavljenog edukativnog modela mislimo da su ove dve vrednosti dovoljno blizu.

<div class="sim">
		<iframe src="sim?stage=epi-3" width="800" height="540"></iframe>
</div>

Ovo je suprotno od eksponencijalnog rasta, ovo je **kriva eksponencijalnog opadanja.**

Šta se dešava ako simulirate S krivu logističkog rasta *sa* oporavljanjem?

![](pics/graphs_q.png)

Hajde da otkrijemo.

<b style='color:#ff4040'>Crvena kriva</b> predstavlja broj *aktuelnih* slučajeva <span class="nowrap"><icon i></icon>,</span>    
<b style='color:#999999'>Siva kriva</b> je *ukupan* broj slučajeva (aktuelni + oporavljeni <span class="nowrap"><icon r></icon>),</span>
počinjemo sa samo 0.001% <span class="nowrap"><icon i></icon>:</span>

<div class="sim">
		<iframe src="sim?stage=epi-4" width="800" height="540"></iframe>
</div>

I *otuda* poznata kriva! Ovo nije zvono kriva (prim. prev. normalna raspodela, Gausova raspodela), nije čak ni "log-normalna" kriva. Ona nema ime. Ali videli ste je zilion puta, i preklinjani ste da je spljoštite.

Ovo je takozvani **SIR model**,[^sir]    
(<icon s></icon>**S**usceptible - zdravi/podložni <icon i></icon>**I**nfectious - zarazni <icon r></icon>**R**ecovered - oporavljeni)      
*druga* najvažnija ideja u početnom kursu Epidemiologije:

[^sir]: Za više tehničkih objašnjenja o SIR modelu, vidite [Institut za modelovanje bolesti](https://www.idmod.org/docs/hiv/model-sir.html#) i [Vikipediju](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SIR_model)

![](pics/sirsrb.png)

**Komentar: Simulacije na osnovu kojih se donose odluke su *mnogo* sofisticiranije od ovih!** Ali SIR model i dalje može da objasni neke generalne trendove, iako mu nedostaju neke finese.

U stvari, hajde da dodamo još jednu finesu: pre nego što <icon s></icon> postane <span class="nowrap"><icon i></icon>, </span> oni prvo postanu <icon e></icon> inficirani (eng. Exposed). U ovom stanju, ljudi imaju virus ali ga ne mogu još prenositi, oni su zara*ženi* ali ne još zara*zni*.

![](pics/seirsrb.png)

(Ova varijanta modela zove se **SEIR model**[^seir], gde "E" potiče od <icon e></icon> "Exposed" - inficiranih. Na engleskom "Exposed" u svakodnevnom značenju približno našem "izložen", može značiti i da imate i da nemate virus, međutim u ovom tehničkom značenju, "Exposed" znači da imate virus. Naučna terminologija je loša. Prim. prevod. iz istog razloga je u ovom prevodu odabrano korišćenje "inficirani" umesto "izloženi".)

[^seir]: Za više tehničkih objašnjenja o SEIR modelu, pogledajte [Institute za modelovanje bolesti](https://www.idmod.org/docs/hiv/model-seir.html) i [Vikipediju](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SEIR_model)

U slučaju COVID-19, procenjeno je da se u stanju <icon e></icon> inficiran-ali-ne-još-zarazan provede 3 dana, *u proseku*.[^latent] Šta se dešava ako i to dodamo u simulaciju?

[^latent]: “Pretpostavljajući distribuciju perioda inkubacije sa prosečnom vrednošću od 5.2 dana iz druge studije na ranim COVID-19 slučajevima, mi smo zaključili da zaraznost počinje od 2.3 dana (interval sa 95% poverenja 0.8–3.0 dana) pre nego što počnu simptomi” (prevod: Pretpostavljajući da simptomi počinju petog dana, zaraznost počinje dva dana pre = zaraznost počinje tri dana nakon što je osoba inficirana) [He, X., Lau, E.H.Y., Wu, P. et al.](https://www.nature.com/articles/s41591-020-0869-5)

<b style='color:#ff4040'>Crvena <b style='color:#FF9393'>+ Roze</b> kriva</b> su *trenutni* slučajevi (zarazni <icon i></icon> + inficirani <span class="nowrap"><icon e></icon>),</span>    
<b style='color:#888'>Siva kriva</b> su *ukupni* slučajevi (trenutni + oporavljeni <span class="nowrap"><icon r></icon>):</span>

<div class="sim">
		<iframe src="sim?stage=epi-5" width="800" height="540"></iframe>
</div>

Nije se mnogo toga promenilo! Vreme tokom koga osoba ostaje <icon e></icon> inficirana (ali ne i zarazna) menja odnos <span class="nowrap"><icon e></icon>-naspram-<icon i></icon>,</span> kao i *kada* trenutni broj slučajeva dostiže maksimum... ali *visina* maksimuma, i ukupan broj slučajeva na kraju, ostaje isti.

Zašto je to tako? To je zbog *prve* najvažnije ideje u početnom kursu Epidemiologije:

![](pics/r.png)

Ovo je skraćeno od "Reproduktivni broj" (eng. Reproduction number). To je *prosečan* broj ljudi koje <icon i></icon> zarazi *pre* nego što oni ozdrave (ili umru).

![](pics/r2srb.png)

**R** se menja tokom trajanja epidemije, kako se povećava broj imunih kao i intervencija.

**R<sub>0</sub>** (u izgovoru R-nula ili na engleskom R-nought) je vrednost R *na početku epidemije, pre imuniteta ili intervencija*. R<sub>0</sub> bliže prikazuje snagu samog virusa, ali se ipak menja u zavisnosti od lokacije. Na primer, R<sub>0</sub> je veće u gušće naseljenim gradovima nego u retko naseljenim ruralnim sredinama.

(Većina članaka u novinama – čak i nekim istraživačkim radovima! – mešaju R i R<sub>0</sub>. Opet, naučna terminologija je loša)

R<sub>0</sub> "tipičnog" sezonskog gripa je oko 1.28[^r0_flu]. Ovo znači da na *početku* epidemije gripa, svaki <icon i></icon> zarazi 1.28 drugih *u proseku.* (Ako zvuči čudno što ovo nije ceo broj, setite se da "prosečno" majke imaju 2.4 deteta. To ne znači da polu-deca trče okolo.)

[^r0_flu]: “Medijalna vrednost R za sezonski grip je 1.28 (IQR: 1.19–1.37)” [Biggerstaff, M., Cauchemez, S., Reed, C. et al.](https://bmcinfectdis.biomedcentral.com/articles/10.1186/1471-2334-14-480)

Procenjena vrednost R<sub>0</sub> za COVID-19 je oko 2.2,[^r0_covid] mada jedna *još-uvek-nedovršena* studija procenjuje da je vrednost bila 5.7(!) u Vuhanu.[^r0_wuhan]

[^r0_covid]: “Procenili smo bazični reproduktivni broj R0 virusa 2019-nCoV na oko 2.2 (90% high density interval: 1.4–3.8)” [Riou J, Althaus CL.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7001239/)

[^r0_wuhan]: “izračunali smo da medijalna vrednost R0 iznosi 5.7 (interval sa 95% poverenja: 3.8–8.9)” [Sanche S, Lin YT, Xu C, Romero-Severson E, Hengartner N, Ke R.](https://wwwnc.cdc.gov/eid/article/26/7/20-0282_article)

U našim simulacijama – *na početku & u proseku* – <icon i></icon> zarazi nekoga svaka 4 dana, tokom 10 dana. "4 dana" je dva i po puta manje od "10 dana". Ovo znači da – *na početku & u proseku* – <icon i></icon> zarazi 2.5 drugih. Stoga je R<sub>0</sub> = 2.5. (upozorenja:[^r0_caveats_sim])

[^r0_caveats_sim]: Ovde smo pretpostavili da je osoba jednako zarazna tokom celog "zaraznog perioda". Opet, pojednostavljenje u službi obrazovanja.

**Igrajte se sa računanjem R<sub>0</sub> da vidite kako R<sub>0</sub> zavisi od vremena potrebnog za oporavak i vremena proteklog do novo-zaraženih:**

<div class="sim">
		<iframe src="sim?stage=epi-6a&format=calc" width="285" height="255"></iframe>
</div>

Ali zapamtite, što je manje <span class="nowrap"><icon s></icon>s</span>, *sporije* <span class="nowrap"><icon s></icon>s</span> postaju <span class="nowrap"><icon i></icon>s.</span> *Trenutni* reproduktivni broj (R) zavisi ne samo od *bazičnog* reproduktivnog broja (R<sub>0</sub>), *ali i od* toga koliko mnogo ljudi nisu više <icon s></icon> podložni/zdravi. (Na primer, ozdravljenjem i dobijanjem prirodnog imuniteta.)

<div class="sim">
		<iframe src="sim?stage=epi-6b&format=calc" width="285" height="390"></iframe>
</div>

Kada je dovoljan broj ljudi imun, R < 1, i virus je zauzdan! Ovo je **imunitet krda**. Za viruse gripa, imunitet krda se dostiže *vakcinisanjem*. Pokušaj da se dostigne "prirodan imunitet krda" izlažući ljude zarazi je *strašna* ideja. (Ali ne zbog razloga koji vam možda padaju na pamet! Objasnićemo kasnije.)

A sada, poigrajmo se sa SEIR modelom ponovo, ali prikazujući vrednosti R<sub>0</sub> i R kroz vreme, kao i granicu na kojoj je imunitet krda dostignut:

<div class="sim">
		<iframe src="sim?stage=epi-7" width="800" height="540"></iframe>
</div>

**Obratite pažnju: Ukupan broj slučajeva *ne staje sa rastom* dostizanjem broja zaraženih potrebnih za imuniteta krda, već ga prevazilazi!** I prevazilazi granicu *tačno u momentu* kada broj trenutnih slučajeva dostiže maksimum. (Ovo se dešava nezavisno od toga kako promenite parametre – probajte!)

Ovo se dešava zato što kada je više <span class="nowrap">ne-<icon s></icon>s</span> od potrebnog broja za imunitet krda, tada se dostiže R < 1. A kada je R < 1, tada i broj trenutnih sučajeva presta da raste: dostignut je maksimum.

**Ako ćete iz ovog čitanja usvojiti samo jednu pouku, nek bude ova** – u pitanju je izuzetno kompleksan dijagram, te mu posvetite koliko god je potrebno vremena da ga u potpunosti savladate:

![](pics/r3srb.png)

**Ovo znači: NE moramo da zauzdamo sva prenošenja virusa, čak ne ni skoro sva, da zaustavimo COVID-19!**

Ovo je paradoks. COVID-19 je ekstremno zarazan, ali da ga zauzdamo, "samo" je potrebno zaustaviti 60% prenosa virusa. 60%?! Da je to školska ocena, bila bi neka dvojčica. Ali ako je R<sub>0</sub> = 2.5, smanjenjem od 61% dostižemo R = 0.975, koje je manje od 1 i virus je zauzdan! (tačna formula:[^exact_formula])

[^exact_formula]: Setite se da je R = R<sub>0</sub> * udeo zaraza koje se i dalje mogu odvijati. I još se setite da je ovaj udeo zaraza koje i dalje mogu da se odvijaju = 1 - udeo zaraza koje su *zaustavljene*.
    
    Stoga, da bismo dostigli R < 1, potrebno je R<sub>0</sub> * MogućeZaraze < 1. 
    
    Stoga, MogućeZaraze < 1/R<sub>0</sub>
    
    Stoga, 1 - ZaustavljeneZaraze < 1/R<sub>0</sub>
    
    Stoga, ZaustavljeneZaraze > 1 - 1/R<sub>0</sub>
    
    Stoga, potreno je zastaviti više od **1 - 1/R<sub>0</sub>** prenosa zaraze da bi R < 1 i zauzdali virus!

![](pics/r4srb.png)

(Ako mislite da je R<sub>0</sub> ili bilo koji drugi broj u našim simulacijama premali/prevelik, super je da preispitujete naše pretpostavke! Na kraju ovog vodiča biće još fleksibilnija verzija simulacije u kojoj možete uneti *vaše* brojeve, i simulirati šta se dešava.)

*Sve* interevencije protiv COVID-19 o kojima ste čuli – pranje ruku, socijalno/fizičko distanciranje, policijski čas, samoizalacija, praćenje kontakata i karantin, maske, pa čak i "imunitet stada" –  one *sve* rade istu stvar:

Spuštaju vrednost do R < 1.

Sada, hajde da iskoristimo naš "epidemiološki simulator letenja" da istražimo: Kako postići R < 1 na način koji **štiti našu mentalnu *i* finansijsku stabilnost?**

Pripremite se za prinudno sletanje...

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Narednih nekoliko meseci</div>
    </div>
</div>

...moglo je biti gore. Evo paralelnog univerzuma koji smo zaobišli:

###Scenario 0: Ne učiniti apsolutno ništa

Otprilike jednoj od 20 osoba inficiranih koronavirusom potrebna je intenzivna nega.[^icu_covid] U bogatim zemljama kao što su SAD, postoji jedno mesto na intenzivnoj nezi na 3400 stanovnika.[^icu_us] Stoga, bolnički sistem u SAD može da podnese da 20 ljudi na svakih 3400 bude *istovremeno* zaraženo – ili 0.6% populacije.

[^icu_covid]: ["Procenat COVID-19 slučajeva u Sjedinjenim Američkim Državama od 12. februara do 16. marta 2020. godine kojima je bila potrebna intenzivna nega, grupisano po starosti"](https://www.statista.com/statistics/1105420/covid-icu-admission-rates-us-by-age-group/). Između 4.9% i 11.5% od *svih* COVID-19 slučajeva zahtevalo je intenzivnu negu. Velikodušno smo odabrali minimalnu vrednost, t. 5% odnosno 1 od 20. Obratite pažnju da je ova vrednost specifična u odnosu na starosnu strukturu Sjedinjenih Američkih Država, i može biti veća za države sa starijom populacijom, ili manja za države sa mlađom populacijom.

[^icu_us]: “Broj mesta na intenzivnoj nezi = 96,596”. Izvor [the Society of Critical Care Medicine](https://sccm.org/Blog/March-2020/United-States-Resource-Availability-for-COVID-19) Broj stanovnika u SAD bio je 328,200,000 u 2019. godini, stoga 96,596 naspram 328,200,000 = približno je 1 na 3400. 

Čak i kada bi SAD *utrostručili* kapacitet intenzivne nege na 2%, ovako bi izgledao slučaj kada se *ništa ne preduzme:* 

<div class="sim">
		<iframe src="sim?stage=int-1&format=lines" width="800" height="540"></iframe>
</div>

Ovo je daleko od dobrog.

Ovo je ono što je [Izveštaj Imperial Koledža od 16. marta](http://www.imperial.ac.uk/mrc-global-infectious-disease-analysis/covid-19/report-9-impact-of-npis-on-covid-19/) takođe zaključio: ako se ništa ne uradi, popuniće se svi kapaciteti intenzivne nege, dok je preko 80% stanovništva zaraženo. (Setite se: ukupan broj slučajeva je *preskočio* imunitet krda)

Čak i kad bi samo 0.5% zaraženih slučajeva preminulo - vrlo optimistična pretpostavka kad više nema dostupnih mesta na intenzivnoj nezi - u velikim državama kao što su SAD, sa populacijom od 300 miliona, 0.5% od tih 80% inficiranih - predstavlja u stvari 1.2 miliona mrtvih... *AKO ne bi ništa uradili.*

(Dosta vesti i medija na društvenim mrežama izveštava da će "80% biti inficirano" *i bez* "DA SE NE URADI NIŠTA". Strah je pretočen u klikove, a ne u razumevanje. :/ )

###Scenario 1: Peglanje krive / Imunitet krda

Plan "Peglanje krive" je bio reklamiran od strane svake zvanične javne zdravstvene organizacije, dok u Velikoj Britaniji pominjan "imunitet krda" je bio dosta kritikovan. To je u stvari *jedno te isto*. Samo su u VB plan dosta loše iskomunicirali.[^yong]

[^yong]: “On kaže da je cilj isti kao u drugim zemljama: peglanje krive time što se poljulja/uzdrma početak infekcije. Posledično, narod će postići imunitet krda; to je sporedni efekat, a ne cilj. [...] Zvaničan plan akcije vlasti u vezi sa koronavirusom, dostupan na njihovom sajtu, uopšte nije pominjao imunintet krda.”
    
    Iz [The Atlantic članak od Ed Yong](https://www.theatlantic.com/health/archive/2020/03/coronavirus-pandemic-herd-immunity-uk-boris-johnson/608065/)

Oba plana, iskreno, imaju jednu bukvalno fatalnu manu.

Prvo, pogledajmo dva osnovna puta kako se ”pegla kriva”: pranje ruku & fizičko distanciranje/udaljavanje.

Češće pranje ruku smanjuje prehlade & grip u bogatim zemljama za ~25%[^handwashing], dok je zatvaranje celog grada u Londonu smanjilo kontakte za ~70%[^london]. Stoga, hajde da pretpostavimo da pranje ruku smanjuje R za *do* 25%, a distanciranje/udaljavanje *do* 70%:

[^handwashing]: “U svih osam dostupnih istraživanja su zaključili da pranje ruku smanjuje rizik od infekcija respiratornog sistema, sa smanjenjem rizika u intervalu od 6% do 44% [pooled vrednost 24% (interval od 95% poverenja je 6–40%)].” Mi smo zaokružili srednju vrednost na 25% u ovim simulacijama radi jednostavnosti. [Rabie, T. and Curtis, V.](https://onlinelibrary.wiley.com/doi/full/10.1111/j.1365-3156.2006.01568.x) Napomena: kako ova meta-analiza pokazuje, kvalitet istraživanja na temu pranja ruku (bar u bogatijim zemljama) su uzašna.

[^london]: “Primećeno je da postoji 73% smanjenja u srednjem broju kontakata po učesniku. Ovo bi bilo dovoljno da smanji R0 sa 2.6, vrednosti koju je imalo pre zatvaranja grada/policijskog časa), na 0.62 (0.37 - 0.89) tokom zatvaranja grada”. Mi smo ovo zaokružili na 70% u ovim simulacijima radi jednostavnosti. [Jarvis and Zandvoort et al](https://cmmid.github.io/topics/covid19/comix-impact-of-physical-distance-measures-on-transmission-in-the-UK.html)

**Igraj se sa ovim kalkulatorom da vidiš kako  % <span class="nowrap">non-<icon s></icon>,</span> pranja ruku, i distanciranje smanjuju R:** (ovaj kalkulator vizualizuje njihov *relativni* uticaj, i zbog toga *izgleda* kao da povećanje jednog smanjuje efekat drugog.[^log_caveat])

[^log_caveat]: Ova iskrivljenost/distorzija ne bi postojala kad bismo predstavili R na logaritamskoj skali... ali onda bismo morali da objasnimo sta je *logaritamska skala.*

<div class="sim">
		<iframe src="sim?stage=int-2a&format=calc" width="285" height="260"></iframe>
</div>

Hajdemo sad da simuliramo šta bi se dogadilo sa COVID-19 epidemijom, da smo od marta 2020 češće prali ruke, ali samo sa *malim* fizičkim distanciranjem - tako da se R smanji, ali da je i dalje veće od 1:

<div class="sim">
		<iframe src="sim?stage=int-2&format=lines" width="800" height="540"></iframe>
</div>

Tri napomene:

1. Ovo *smanjuje* ukupan broj slučajeva! **Čak i da nemamo R < 1, smanjivanje R i dalje spašava živote, jer se time smanjuje i broj inficiranih ljudi preko broja potrebnog za imunitet krda.** Mnogo ljudi misli da "Peglanjem Krive" se samo vremenski raširi broj slučajeva bez uticaja na ukupan broj. To je nemoguće u *svakom* uvodnom epidemiološkom modelu. Ali, zbog toga što su na vestima rekli da će "80%+ biti inficirano" kao neizbežnu stvar, ljudi su milili da će ukupan broj slučajeva prosto biti isti, bez obzira na bilo šta. *:/*

2. Zbog dodatnih intervencija, trenutni slučajevi su dostigli maksimum *pre* nego što je došlo do imuniteta krda. Zapravo, u ovoj simulaciji, ukupan broj slučajeva tek *malo* premašuje imunitet krda - što je bio i plan Velike Britanije! Hm, u stvari, tako je ako se zanemari jedan problem:...

3. I dalje se zauzmu svi kapaciteti intenzivne nege. Na nekoliko meseci. (i setimo se, *već* smo uzeli utrostručen broj realne situacije za ove simulacije)

To je bio još jedan zaključak Izveštaja Imperial Koledza od 16. marta, koji je ubedio Engleze da odustanu od njihovog početnog plana. Svaki pokušaj u *ublažavanju* (što je smanjenje R, ali i dalje R > 1) će propasti. Jedini način da se izađe iz ove situacije je **suzbijanje** (smanjenje R tako da bude R < 1).


![](pics/mitigation_vs_suppressionsrb.png)

To znači da se prosto ne *pegla* kriva, nego da se *uništi* tj. suzbijemo. Na primer, sa...

###Scenario 2: Višemesečno Zatvaranje (gradova, policijski čas i slično)

Hajde da vidimo šta se dešava ako *suzbijemo* krivu sa petomesečnim zatvaranjem, smanjimo <icon i></icon> pratično potpuno, a onda se *napokon* vratimo normalnom životu:

<div class="sim">
		<iframe src="sim?stage=int-3&format=lines" width="800" height="540"></iframe>
</div>

Ups.

Ovo je taj "drugi talas" o kojem svi pričaju. Čim mi sklonimo zatvaranje, opet postane R > 1. Stoga, jedan preostali <icon i></icon> (ili neki koji je došao <span class="nowrap"><icon i></icon>)</span> može da prouzrokuje ponovni skok u broju slučajeva, što je skoro pa podjednako loše kao da smo samo uradili Scenario 0: Apsolutno ništa.


**Zatvaranje nije lek, već samo restart situacije.**

Dobro, šta, mi sad samo treba da se zatvaramo (ili da uvodimo policijski čas) iznova i iznova?

###Scenario 3: Naizmenično Zatvaranje-Otvaranje

Ovo rešenje je prvo bilo predloženo u Izveštaju Imperial Koledza 16. marta, i posle još jednom u jednom radu naučnika sa Harvarda.[^lockdown_harvard]

[^lockdown_harvard]: “Ako ne uzmemo u obzir ostale intervencije, glavni parametar uspešnosti sprovođenja mera fizičkog distanciranja je da li su popunjeni svi kapaciteti intenzivnih nega. Da bi se ovo izbeglo, produžena ili pak naizmenična fizička distanciranja su potencijalno neophodna i do 2022 godine.” [Kissler and Tedijanto et al](https://science.sciencemag.org/content/early/2020/04/14/science.abb5793)

**Evo i simulacije:** (Pošto se izigrate sa "već nameštenim scenariom", možete da probate i *vaše* rasporede zatvaranja gradova/policijskog časa, pomerajući slajdere/klizače/dugmiće *dok* traje simulacija! Setite se da možete da pauzirate & nastavite simulaciju, kao i da promenite njenu brzinu izvršavanja)

<div class="sim">
		<iframe src="sim?stage=int-4&format=lines" width="800" height="540"></iframe>
</div>

Ovo *bi* zadržalo ukupan broj slučajeva ispod kapaciteta invenzivne nege! I *mnogo* je bolje od zatvaranja gradova na 18 meseci, dok vakcina ne postane dostupna. Jedino što mi treba da radimo jeste.. da se zatvorimo na par meseci, otvorimo na par meseci, i ponavljamo ovo u krug dok ne dođemo do vakcine. (Ili u slučaju da nema vakcine, ponavljamo dok ne dostignemo imunitet krda... u 2022. godini.)

U redu, lepo je nacrtati tu liniju koja predstavlja "kapacitet intenzivne nege", ali postoji tu jođ vrlo bitnih stvari koje mi *ne možemo* da simuliramo. Na primer:

**Mentalno Zdravlje:** Usamljenost je jedno od najbitnijih faktora rizika za depresiju, anksioznost i samoubistvo. I povezuje se za preuranjenu smrtnost u sličnoj meri kao i da pušenje 15 cigareta dnevno.[^loneliness]

[^loneliness]: Pogledajte [Sliku 6 iz Holt-Lunstad & Smith 2010](https://journals.sagepub.com/doi/abs/10.1177/1745691614568352). Naravno, obratimo pažnju da su uočili *korelaciju*. Ali, sem ako ne želimo da nasumične ljude stavljamo u izolaciju da bismo istraživali usamljenost, jedino što imamo su prosto podaci sa posmatranja kao što je ovaj. 

**Finansijsko Zdravlje:** "Šta ćemo sa ekonomijom?!" zvuči kao da neko više brine o parama nego o životima, ali "ekonomija" nije samo berza i zarada poslodavaca: to je mogućnost ljudi da zarade za hranu i krov na glavom za njih i njihove bližnje, da ulažu u budućnost njihove dece, i uživaju u umetnosti, hrani, videoigrama - u svim onim stvarima koje čine život lepim i vrednim.I pored toga, siromaštvo *samo po sebi* ima katastrofalne posledice po mentalno i fizičko zdravlje.


Ne kažemo da *ne bi trebalo* da se zatvaramo opet! Vratićemo se kasnije na to "ciklično otvaranje" zatvaranja. I dalje je daleko od idealnog.

Ali, čekajte. Zar nisu Tajvan i Južna Koreja *već* zauzdala COVID-19? Na čitava četiri meseca, *bez* dugoročnog zatvaranja?!

Kako?

###Scenario 4: Testiranje, Praćenje, Izolovanje

*"Da, sigurno, mi \*smo mogli\* da uradimo to što su i Tajvan i Južna Koreja uradili na početku, ali sada je previše kasno za to. Omašili smo početak."*


Ali to je upravo to! “Zatvaranje nije lek, ali jeste samo restart”... **i novi početak je ono što nam treba.**

Da bismo razumeli kako su Tajvan & Južna Koreja zaustavile COVID-19, treba da razumemo tačnu vremenske okvire tipične COVID-19 infekcije [^timeline]:

[^timeline]: **3 dana u srednjem za infektivnost:** “Pretpostavljajući da je inkubacioni period normalna distribucija oko srednje vrednosti 5.2 dana (iz drugog istraživanja COVID-19 slučajeva), zaključujemo da infektivnost počinje vec od 2.3 dana (interval 95% poverenja je 0.8–3.0 dana) pre nego što se manifestuju simptomi” (u prevodu: Ako pretpostavimo da se simptomi vide od petog dana, zaraznost je počela dva dana pre = infektivnost počinje od treceg dana) [He, X., Lau, E.H.Y., Wu, P. et al.](https://www.nature.com/articles/s41591-020-0869-5)  
    
    **4 dana u proseku da se zarazi druga osoba:** “Usrednjen [serial] interval je bio 3.96 dana (interval 95% poverenja 3.53–4.39 dana)” [Du Z, Xu X, Wu Y, Wang L, Cowling BJ, Ancel Meyers L](https://wwwnc.cdc.gov/eid/article/26/6/20-0357_article)
    
    **5 dana u proseku da se ispolje simptomi:** “Medijana distribucije inkubacionog perioda je procenjena da je 5.1 dan (interval 95% poverenja 4.5 do 5.8 dana)” [Lauer SA, Grantz KH, Bi Q, et al](https://annals.org/AIM/FULLARTICLE/2762808/INCUBATION-PERIOD-CORONAVIRUS-DISEASE-2019-COVID-19-FROM-PUBLICLY-REPORTED)

![](pics/timeline1srb.png)

Ako se slučajevi samoizoluju kad shvate da su se razboleli (tj. osete simptome), virus i dalje može da se širi:

![](pics/timeline2srb.png)

I zapravo, 44% svih prenošenja su u stvari: *pred*-simptomatska! [^pre_symp]

[^pre_symp]: “Mi smo procenili da 44% (interval 95% poverenja 25–69%) sekundarnih slučajeva su bili zaraženi tokom predsimptomatskog perioda za dati slučaj.” [He, X., Lau, E.H.Y., Wu, P. et al](https://www.nature.com/articles/s41591-020-0869-5)

Ali, ako mi nađemo *i stavimo u karantin* skorašnje kontakte tog jednog analiziranog slučaja koji ispoljava simptome zaraze... mi zaustavljamo širenje, time što bivamo jedan korak ispred!

![](pics/timeline3srb.png)

Ovo se zove **praćenje kontakata**. Ideja je stara, i bila je korišćena u velikoj meri da se zauzda širenje Ebole[^ebola], i sada je suština kako su Tajvan & Južna Koreja zauzdali COVID-19!


[^ebola]: “Praćenje kontakata je bilo od suštinske važnosti u Liberiji i predstavlja jednu od najvećih napora i akcija za praćenje kontakata tokom svih epidemija u istoriji.” [Swanson KC, Altare C, Wesseh CS, et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6152989/)

(Ovim se takođe i omogućava da efikasnije koristimo ograničene testove, kako bismo locirali predsimtomatske <span class="nowrap"><icon i></icon>s</span> bez potrebe da testiramo celu populaciju.)

Tradicionalno, kontakti se saznaju prilikom intervjuisanja uživo zaražene osobe, ali to je samo po sebi vrlo sporo za vremenski prozor COVID-19 koji je ~48 sati. Zato ljudima koji sprovode intervjue treba pomoć, kao i podrška, aplikacija za praćenje kontakata, koji svakako ne bi mogle da ih zamene.


(Ova ideja nije potekla od "tehnikalaca/banderaša <3": korišćenje aplikacije da se suzbija COVID-19 je prvo bilo predloženo od strane [time epidemiologa sa Oksforda](https://science.sciencemag.org/content/early/2020/04/09/science.abb6936).)

Čekaj, aplikacije koje prate kontakte?... Da li to znači da se odričemo naše privatnosti, dajući pristup Velikom Bratu?

Ni pod razno! **[DP-3T](https://github.com/DP-3T/documents#decentralized-privacy-preserving-proximity-tracing)**, tim epidemiologa i kriptografičara (u koji je uključen i jedan od nas, Marcel Salathé) *već* rade na pravljenju takve aplikacije - sa kodom koji je dostupan svima - koja ne otkriva **nikakve podatke o identitetu, lokaciji, kontaktima, a čak ni *koliko kontakata* je osoba imala.**

Ovako ona radi:

![](pics/dp3tsrb.png)

([Ovde je ceo strip](https://ncase.me/contact-tracing/). Detalji oko "varanja"/lažno potizivnih/i ostalo u fusnoti:[^dp3t_details])

[^dp3t_details]: Da bi se onemogućilo  "varanje" (ljudi koji lažno tvrde da su zaraženi), DP-3T Protokol zahteva da ti bolnica prvo da jednokratnu šifru, što tebi dozvoljava da ustupiš bolnici sve tvoje poruke.

    Lažno pozitivni su problem u oba slučaja - i ručnom i automatskom praćenju kontakata. Mada, mi i dalje možemo da smanjimo broj lažno pozitivnih na dva načina: 1) time što bismo obavestili Bojane samo ako su čule, recimo, više od 30min poruka, ne samo jednu poruku u prolazu; 2) Ako aplikacija misli da Bojana *jeste* izložena virusu, može da kaže Bojani da ode na intervju u bolnici.
    
    Za ostale pitanja kao što je potrošnja podataka, integritet izvora (data bandwidth, source integrity), i ostala pitanja u vezi sa bezbednošću podataka, pogledajte [open-source DP-3T predloge/whitepapers!](https://github.com/DP-3T/documents#decentralized-privacy-preserving-proximity-tracing)

Usput sa sličnim timovima kao što su TCN Protocol[^tcn] i MIT PACT[^pact], inspirisali su i Apple i Google da se pozabave razvijanjem aplikacije za praćenje kontakata sa primarnom zaštitom privatnosti za Android/iOS.[^gapple] (Ne veruješ Google/Apple? Ako! Lepota ovog sistema jeste što mu *ne treba* tvoje poverenje!) Možda će uskoro tvoj zdravsveni sistem od tebe tražiti da intaliraš neku aplikaciju. Ako je ona pre svega sa zaštitom privatnosti i sa javno dostupnim kodom, molim te instaliraj je!

[^tcn]: [Temporary Contact Numbers, a decentralized, privacy-first contact tracing protocol](https://github.com/TCNCoalition/TCN#tcn-protocol)

[^pact]: [PACT: Private Automated Contact Tracing](https://pact.mit.edu/)

[^gapple]: [Apple i Google partneri za tehnologiju praćenja kontakata COVID-19](https://www.apple.com/ca/newsroom/2020/04/apple-and-google-partner-on-covid-19-contact-tracing-technology/). Primetite da ih oni ne prave *sami*, već da samo prave sistem koji će moći da *podrži* ovakve aplikacije.

Ali šta će da bude sa ljudima koji nemaju pametne telefone? Ili sa infekcijama preko kvaka na vratima? Ili sa "stvarnim" asimptomatskim slučajevima? Aplikacije za praćenje kontakata ne mogu da pohvataju baš sva prenošenja... *i to je okej!* Mi ni ne moramo da ih *sve* uhvatimo, već samo 60+% da dođemo do R < 1.

(Fusnota o rantu oko mešanja između predsimptomatskih i "stvarnih" asimtomatskih slučajeva - "stvarni" asimptomatski su vrlo retki:[^rant])

[^rant]: Veliki broj novih izveštaja - i iskreno, dosta istraživačkih radova - ne razlikuju između "slučajeva koji ne pokazuju simptome kad ih testiraju" (predsimptomastki slučajevi) i "slučajeva koji ne pokazuju simptome *nikada*" (stvarni asimptomatski). Jedini način na koji oni mogu da se razdvoje je da se radi ponovno kasnije testiranje.

    Šta je šta [ovo istraživanje](https://wwwnc.cdc.gov/eid/article/26/8/20-1274_article) je uradilo. (Obratite pažnju: "Rano objavljivanje radova se ne smatraju da su finalne verzije.") U kol-centru u Južnoj Koreji koja je imala izbijanje COVID-19 bolesti, "jedino 4 (1.9%) su ostali asimptomatski u toku 14 dana karantina, i niko od njihovih ukućana koji imao sekundarnu infekciju."
    
    
    To znači da su  "stvarni asimptomatski" slučajevi stvarno retki, ali i da takvi budu dalje zarazni je još ređe.
    

Izolacija *simptomatskih* slučajeva bi smanjila R skoro do 40%, a odlazak u karantin njihovih *pred/a-simptomatskih* kontakata bi smanjilo R do 50%[^oxford]:

[^oxford]: Iz istog istraživanja sa Oksforda koje je prvo predložilo aplikacije za suzbijanje COVID-19 bolesti: [Luca Ferretti & Chris Wymant et al](https://science.sciencemag.org/content/early/2020/04/09/science.abb6936/tab-figures-data) Pogledajte Sliku 2. Pretpostavljajući R<sub>0</sub> = 2.0, oni su zaključili da:    
    
    * Simptomatični doprinose R = 0.8 (40%)
    * Predsimptomatični doprinose  R = 0.9 (45%)
    * Asimptomatični doprinose R = 0.1 (5%, iako njihov model ima neke nesigurnosti i mogli bi da bude i dosta manji broj u pitanju)
    * Stvari u okolini kao što su kvake na vratima doprinose R = 0.2 (10%)

    I ako saberemo pred- i a-simptomatične kontakte (45% + 5%) dobijamo 50% od R!

<div class="sim">
		<iframe src="sim?stage=int-4a&format=calc" width="285" height="340"></iframe>
</div>

Stoga, čak i bez stavljanja u karantin 100% kontakata, možemo da dođemo do R < 1 *bez zatvaranja*! Ovo je mnogo bolje za naše mentalno zdravlje i finansijsku situaciju. (Što se tiče troškova ljudi koji moraju da se samoizoluju/odu u karantin, *vlada bi trebalo da ih pomogne/governments should support them*) - plati za testova, osigura njihove poslove, subvencioniše odsustvo, i ostalo. To je i dalje jeftinije nego zatvaranje čitavih gradova pa i naizmenično.)


Mi onda možemo da održavamo R < 1 dok se ne proizvede vakcina, što onda zdrave-podložne <span class="nowrap"><icon s></icon>s</span> pretvara u imune <span class="nowrap"><icon r></icon>s.</span> Imunitet *krda*, na pravi način:

ass="nowrap"><icon s></icon>s</span> into immune <span class="nowrap"><icon r></icon>s.</span> Herd immunity, the *right* way:

<div class="sim">
		<iframe src="sim?stage=int-4b&format=calc" width="285" height="230"></iframe>
</div>

(Komentar: ovaj kalkulator pretpostavlja da je hipotetička vakvinacina 100% efikasna. Zapamtimo da u realnosti to moramo da kompenzujemo time što se vakciniše *više* od onoga što je potrebno za "imunitet krda", da bismo *zapravo* imali taj imunitet krda)

Dobro, dosta priče. Ovo je simulacija:

1. Zatvaranja na nekoliko meseci, dok nismo u stanju da...
2. Pređemo na "Testiranje, Praćenje, Izolovanje", dok ne omogućimo da...
3. Vakcinišemo dovoljan broj ljudi, što bi značilo...
4. Da smo pobedili.


<div class="sim">
		<iframe src="sim?stage=int-5&format=lines" width="800" height="540"></iframe>
</div>

I to je to! Ovo je način na koji uspemo da izvedemo prinudno sletanje ovog aviona. 

I ovo je način na koji pobeđujemo COVID-19.

...

Ali šta ako stvari *i dalje* idu po zlu? Stvari su već otišle u vrlo pogrešnu stranu. To je strah, i to je dobro! Strah nam daje energiju da stvorimo sebi *rezervne planove*.

Pesimista pravi padobran.

###Scenario 4+: Maske Za Sve, Leto, Circuit Breakers

Šta ako je R<sub>0</sub> mnogo veće nego što smo mi mislili, i pored svih intervencija, i blagog distanciranja, mi *i dalje* ne uspevamo da dobijemo R < 1?

Setimo se, iako ne možemo da dobijemo da je R < 1, smanjenjem R smanjujemo ukupan broj slučajeva, što znači da spašavamo živote. Ali i dalje, R < 1 je idealno, tako da evo na koje još dodatne načine možemo da utičemo na smanjenje R:


**Maske Za Sve:**

*"Čekaj,"* možda ćeš pitati, *"Zar se nije pokazalo da maske ne mogu potpuno da zaštite od zaraze?"*

I bili biste u pravu. Maske ne mogu da nas zaštite od infekcije[^incoming]... one štite *druge* od nas.

[^incoming]: “Nijedna od ovih hirurških maski nema adekvatni učinak filtera, kao ni što ne prijanjaju licu u dovoljnoj meri, da bi mogle da se klasifikuju kao respiratorna zaštita.” [Tara Oberg & Lisa M. Brosseau](https://www.sciencedirect.com/science/article/pii/S0196655307007742)

[^outgoing]: “Ukupno smanjenje od 3.4 puta [70% smanjenja] u broju čestica aerosoli koje je primećeno, zajedno sa skoro potpunom eliminacijom velikih kapljica koje je demonstrirano od strane by Johnson et al., sugeriše da bi nošenje hirurške maske od strane zaraženog lica imalo klinički značajan uticaj na prenošenje zaraze.” [Milton DK, Fabian MP, Cowling BJ, Grantham ML, McDevitt JJ](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3591312/)

[^homemade]: [Davies, A., Thompson, K., Giri, K., Kafatos, G., Walker, J., & Bennett, A](https://www.cambridge.org/core/journals/disaster-medicine-and-public-health-preparedness/article/testing-the-efficacy-of-homemade-masks-would-they-protect-in-an-influenza-pandemic/0921A05A69A9419C862FA2F35F819D55) Pogledajte Tabelu 1: 100% pamučna majica ima oko 2/3 efikasnost filtriranja u poređenju sa hirurškom masku, za dve testirane bakterijske aerosoli.

![](pics/maskssrb.png)

Ako hoćemo da pričamo u brojevima: hirurške maske *na inficiranoj osobi* smanjuju prisutnost virusa prehlade i gripa u aerosoli za 70%.[^outgoing] Smanjivanje prenosa za 70% ima *sličan* efekat kad što ima i zatvaranje gradova!

No svejedno, mi i dalje ne znamo zasigurno koji je uticaj maski na *konkretno* COVID-19 zarazu. U nauci se uglavnom objavljuju jedino rezultati ako ste bar 95% sigurni u njih. (...ok, trebalo bi da je tako.[^replication]) Maske, barem 1. maja 2020, su manje od "95% sigurne".

[^replication]: Svi pravi naučnici koji su pročitali poslednju rečenisu su se upravo sarkastično/bolno nasmejali. Pogledajte: [p-hacking](https://en.wikipedia.org/wiki/Data_dredging), [kriza repreducibilnosti](https://en.wikipedia.org/wiki/Replication_crisis))


Svejedno, pandemija je kao poker. **Ako se kladite samo kad se 95% sigurni, izgubićete sve što imate.** Kao što je skorašnji članak na temu maski u Britanskom Medicinskom Časopisu primetio, [^precautionary] mi *moramo* da pravimo cost/benefit analize u nesigurnim vremenima/under uncertainty. 


[^precautionary]: “Vreme je da primenimo princip predostrožnosti” [Trisha Greenhalgh et al \[PDF\]](https://www.bmj.com/content/bmj/369/bmj.m1435.full.pdf)

Cost: Ako uzmemo ručno pravljene tekstilne maske (koje su ~2/3 efektivne kao hirurške maske[^homemade]), to je super jeftino. Ako uzmemo hirurške maske, skuplje ali i dalje prilično jeftino.

Benefit: Čak i ako je 50-50 šansa da hirurške maske smanje prenošenje sa 0% na 70%, prosečna "očekivana vrednost" je i dalje 35%, što je kao da smo uveli polu-policijski čas/zatvorili grad! Stg0oga, hajde da probamo da pogodimo-procenimo da hirurške maske smanjuju R za 35%, da smanjimo zbog nesigurnosti. (Kao i u prethodnom slučaju, možete da se igrate i vidimo kako se menjaju parametri ako pomerate slajdere levo-desno.)

<div class="sim">
		<iframe src="sim?stage=int-6a&format=calc" width="285" height="380"></iframe>
</div>

(ostali razlozi za/protiv maski:[^mask_args])

[^mask_args]: **"Mi moramo da čuvamo zalihe za bolnice."** *Apsolutno se slažem.* Ali to je u stvari argument da se poveća proizvodnja maski, a ne da se ostavlja u rezerve. U međuvremenu, možemo da pravimo tekstilne maske.
**"Teško je da se pravilno nose."** Takođe je teško da se peru ruke u skladu sa preporukama Svetske Zdravstvene Organizacije - ozbiljno, "Korak 3) desni dlan preko levog prednjeg dela šake/dorsum"?! - davno se učio latinski, plus nisu svi učili delove šake kao medicinski izraz – ali mi i dalje preporučujemo pranje ruku, jer nesavršeno je i dalje bolje nego ništa.
**"Ljudi će postati opušteniji sa pranjem ruku i fizičkim distanciranjem."**  Naravno, i pojasevi za vezivanje čine da ljudi prestanu da ignorišu stop znak, i konac za zube čini da ljudi jedu kamenje (sarkazam, prim prev :D). Da se uozbiljimo, mi bismo zapravo to koristilil kao kontra-argument - maske su ljudima *kontantni* podsetnik da treba da budu pažljivi - a i u Istočnoj Aziji, maske su takođe simbol solidarnosti!

*Samo* maskama nećemo dostići R < 1. Ali ako pranje ruku & "Testiranje, praćenje, izolovanje" spuste vrednost do R = 1.10, ako samo 1/3 ljudi nose maske dostićićemo R < 1, virus zauzdan!

**Leto:**

OK, ovo nije "intervencija" koju možemo kontrolisati, ali će pomoći! Neki mediji su izveštavali da leto neće učiniti ništa koronavirusu. Oni su samo delimično u pravu: samo leto neće pomoći da se dostigne R < 1, ali *hoće* umanjiti R.

U slučaju COVID-19, svaki dodatni 1° C (1.8 stepeni na Farenhajtovoj skali) snižava R za 1.2%.[^heat] Razlika u stepenima između leta i zime u Njujorku je 26°C (47°F),[^nyc_heat] tako da će kao posledica letnjih vrelina vrednost R opasti za ~31%. (Prim. prev. )

[^heat]: “Povećanje temperature za jedan stepen Celzijusove skale [...] smanjeuje R za 0.0225” i “Prosečna vrednsot R za ovih 100 gradova je 1.83”. 0.0225 ÷ 1.83 = ~1.2%. [Wang, Jingyuan and Tang, Ke and Feng, Kai and Lv, Weifeng](https://papers.ssrn.com/sol3/Papers.cfm?abstract_id=3551767)

[^nyc_heat]: Tokom 2019 u Centralnom parku, tokom najtoplijeg meseca (Jul) bilo je 79.6°F, a tokom najhladnijeg meseca (Januar) bilo je 32.5°F. Razlika je 47.1°F, odnosno ~26°C. [PDF from Weather.gov](https://www.weather.gov/media/okx/Climate/CentralPark/monthlyannualtemp.pdf)

<div class="sim">
		<iframe src="sim?stage=int-6b&format=calc" width="285" height="220"></iframe>
</div>

Leto samo po sebi neće učiniti da je R < 1, ali kako imamo ograničene resurse, možemo umanjiti neke od intervencija tokom leta – tako da ih možemo *povećati* tokom zime.

**"Ciklično" zatvaranje:**

I ako sve to *i dalje* nije dovoljno da dođemo do R < 1... možemo se ponovo zatvoriti.

Ali nećemo morati da prolazimo kroz ciklus 2 meseca u zatvorenom / 1 mesec na otvorenom iznova i iznova! Kako se R smanjuje, biće nam potreban jedan ili dva "ciklična" zatvaranja pre nego što se pojavi vakcina. (U Singapuru je moralo da dođe do ovoga nedavno, "iako" su uspevali da kontrolišu COVID-19 tokom prethodna 4 meseca. Ovo nije neuspeh: ovo *je* potrebno za uspeh.)

Evo simulacije "lenjog" scenarija:

1. Zatvaranje, praćeno
2. Umerenom količinom politika povećane higijene & "Testiranje, Praćenje, Izolovanje", sa blagom količinom "Maske za sve", a zatim...
3. Još jedan "ciklus" zatvaranja pre nego što vakcina postane dostupna.

<div class="sim">
		<iframe src="sim?stage=int-7&format=lines&height=620" width="800" height="620"></iframe>
</div>

Da ne pominjemo sve *ostale* intervencije koje možemmo primeniti da dodatno snizimo R:

* Restrikcije putovanja sa karantinom
* Kontrola temperature u tržnim centrima i školama
* Detaljno čišćenje javnih prostora
* [Prelazak na nogovanje umesto rukovanja](https://twitter.com/V_actually/status/1233785527788285953)
* I sve ostalo što će ljudi smisliti

. . .

Nadamo se da vam ovi planovi daju nadu. 

**Čak i u pesimističnom scenariju, *moguće* je pobediti COVID-19, štiteći našu mentalnu i finansijsku stabilnost.** Koristeći zatvaranja kao "dugme za reset", čuvajući R < 1 sa izolacijom slučajeva + prateći kontakte uz zaštitu privatnosti + *barem* platnenim maskama za sve... i život se može vratiti u nešto skoro-normalno!

Sigurno, suve su vam ruke. Ali, imaćete šansu da pozovete simpatiju u prodavnicu stripova! Imaćete šansu da odete sa prijateljima u bioskop i gledate poslednji holivudski blokbaster. Imaćete šansu da posmatrate ljude u biblioteci, uživajući u činjenici da ljudi nastavljaju sa sitnicama koje *život znače.*

Čak i u najgorem slučaju... život opstaje.

A sada, hajde da planiramo za neke od *gorih* najgorih scenarija. Sletanje na vodu, pripremite svoje prsluke za spasavanje, i molimo pratite svetla do izlaza u slučaju opasnosti:

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Narednih nekoliko godina</div>
    </div>
</div>

Dobili ste COVID-19 i oporavili ste se. Ili, primili ste vakcinu protiv COVID-19. U svakom slučaju, sada ste imuni...

...*koliko dugo?*

* COVID-19 je u najbližoj vezi sa SARS-om, koji oporavljenima daje dvogodišnji imunitet.[^SARS immunity]
* Virusi koji prouzrokuju tipičnu prehladu daju vam imunitet od 8 meseci.[^cold immunity]
* Postoje neki izveštaji o ljudima koji su se oporavili od COVID-19, ali su ipak naknadno detektovani kao pozitivni testiranjem, ali je nejasno da li su ovo greške testiranja.[^unclear]
* Jedna *još-uvek-nerecenzirana* studija na majmunima je pokazala da COVID-19 imunitet traje barem 28 dana.[^monkeys]

Ali u slučaju COVID-19 i *ljudi*, prvog maja 2020, "koliko dugo" je još uvek velika nepoznanica.

[^SARS immunity]: “SARS antitela su održana u proseku 2 godine [...] Stoga, SARS pacijenti mogu ponovo postati podložni infekciji ≥3 godine nakon inicijalne infekcije.” [Wu LP, Wang NC, Chang YH, et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2851497/) "Nažalost" nikad nećemo znati koliko dugo bi SARS imunitet trajao, obzirom da je suzbijen tako brzo.

[^cold immunity]: “Nismo pronašli značajnu razliku između verovatnoće pozitivnog testa bar jednom i verovatniće povratka beta-koronavirusa HKU1 i OC43 nakon 34 nedelje posle priključivanja studiji/prve infekcije.” [Marta Galanti & Jeffrey Shaman (PDF)](http://www.columbia.edu/~jls106/galanti_shaman_ms_supp.pdf)

[^unclear]: “Jednom kada osoba pobedi virus, delovi virusa opstaju još neko vreme. Ali oni ne mogu izazvati infekciju, ali mogu izazvati pozitivan ishod na testu.” [from STAT News by Andrew Joseph](https://www.statnews.com/2020/04/20/everything-we-know-about-coronavirus-immunity-and-antibodies-and-plenty-we-still-dont/)

[^monkeys]: Iz [Bao et al.](https://www.biorxiv.org/content/10.1101/2020.03.13.990226v1.abstract) *Napomena: Ovaj članak još uvek nije prošao recenziju.* Takođe, da istaknemo: oni su samo testirali nakon 28 dana. 

Za ove simulacije, pretpostavimo da traje jednu godinu.
**Ova simulacija počinje sa 100% <span class="nowrap"><icon r></icon>,</span>** čiji broj eksponencijalno opada, dok oni prelaze u zdrave/podložne, bez imuniteta <span class="nowrap"><icon s></icon></span> kroz 1 godinu *u proseku*:

<div class="sim">
		<iframe src="sim?stage=yrs-1&format=lines&height=600" width="800" height="600"></iframe>
</div>

Povratak eksponencijalnog opadanja!

Ovo je **SEIRS model**. Drugo "S" u nazivu označava da postoji povratak u <icon s></icon> Susceptible - podložno stanje ponovo.

![](pics/seirssrb.png)

Hajde da simuliramo COVID-19 širenje, tokom 10 godina, bez intervencija... *pretpostavljajući da imunitet traje samo godinu dana:*

<div class="sim">
		<iframe src="sim?stage=yrs-2&format=lines&height=600" width="800" height="600"></iframe>
</div>

U prethodnim simulacijama imali smo samo *jedan* maksimum kada smo premašivali kapacitete intenzivne nege. Sada ih ima više *i* roj <icon i></icon> slučajeva je *permanentno* na granici kapaciteta intenzivne nege. (Koje smo, setite se, procenili na *trostruko* veće za potrebe ovih simulacija)

R = 1, je **endemija.**

Na sreću, zato što leto smanjuje R, poboljšaće simulaciju:

<div class="sim">
		<iframe src="sim?stage=yrs-3&format=lines&height=640" width="800" height="640"></iframe>
</div>

Ups.

Kontraintuitivno, leto čini da se maksimumi pogoršavaju *i* vraćaju! To je zato što leto smanji broj novih <span class="nowrap"><icon i></icon>,</span> ai to takođe smanjuje i broj imunih <span class="nowrap"><icon r></icon>.</span> Što znači da se imunitet smanji tokom leta, *kreirajući* tako intenzivnija ponavljanja porasta zaraženih tokom zima.

Na sreću, rešenje za ovo je prilično zdravorazumsko – vakcinacija svake jeseni/zime, kao što to radimo sa vakcinama protiv gripa:

**(Nakon puštanja snimka, probajte vaše simulacije sa različitim kampanjama vakcinacije! Setite se da možete pauzirati i nastaviti simulaciju u bilo kom trenutku)**

<div class="sim">
		<iframe src="sim?stage=yrs-4&format=lines" width="800" height="540"></iframe>
</div>

Ali imamo i jedno strašnije pitanje:

Šta ako budemo čekali na vakcinu *godinama*? Ili *zauvek?*

**Da budemo jasni: ovo je neverovatno.** Većina epidemiologa očekuje vakcinu za godinu do dve. Tačno je da ne postoji vakcina ni za jedan od koronavirusa, ali to je zato što je SARS bio suzbijen brzo, a vakcina protiv tipične prehlade nije smatrana isplativnom investicijom. 

Međutim, istraživači zaraznih bolesti su izrazili sledeća strahovanja: Šta ako ne možemo da napravimo dovoljno vakcina?[^vax_enough] Šta ako ubrzamo proces po cenu bezbednosti?[^vax_safe]

[^vax_enough]: “Ako stigne vakcina protiv koronavirusa, da li svet može da napravi dovoljno?” [autorka Roxanne Khamsi, u časopisu Nature](https://www.nature.com/articles/d41586-020-01063-8)

[^vax_safe]: “Ne žurite s produkcijom COVID-19 vakcina i lekova bez dovoljno čvrstih garancija o njihovoj bezbednosti” [autor Shibo Jiang, u časopisu Nature](https://www.nature.com/articles/d41586-020-00751-9)

Čak i u scenariju iz noćne more u kome nema vakcine, i dalje postoje tri izlaza. Slede od najviše do najmanje strašnih:

1) Ponavljanje ciklusa intervencija za dostizanje R < 1, do postizanja "prirodnog imuniteta krda". (Upozorenje: ovo će za rezultat imati puno smrti i oštećenih pluća. *I* neće raditi ako imunitet ne traje.)

2) Ponavljanje R < 1 intervencija zauvek. Praćenje kontakata i nošenje maski samo postane nova normalnost u post-COVID-19 svetu, kao što su testovi na seksualno prenosive infekcije i korišćenje kondoma postali nova norma u post-HIV svetu.

3) Ponavljanje R < 1 intervencija dok ne razvijemo tretmane koji čine da COVID-19 zahteva intenzivnu negu mnogo mnogo ređe. (Što bi *svakako* trebalo da radimo!) Smanjivanje potreba za intenizvnom negom faktorom 10x je isto što i povećanje naših kapaciteta u intenzivnoj nezi za faktor od 10x:

**Evo simulacije *bez* trajnog imuniteta, *bez* vakcine, pa čak i bez bilo kakvih intervencija - samo sa sporim povećavanjem spremnosti da preživimo nove talase:**

<div class="sim">
		<iframe src="sim?stage=yrs-5&format=lines" width="800" height="540"></iframe>
</div>

Čak i u ovom *najgorem* od najgorih slučajeva... život opstaje.

. . .

Možda želite da preispitate naše pretpostavke i probate drugačije vrednsoti R<sub>0</sub> i ostalih parametara. Ili želite da simulirate *svoju* kombinaciju intervencija!

**Ovde je simulacija, u kojoj je menjanje *svega* dostupno. (skrolovanjem ćete videti sve kontrole) Simulirajte i igrajte se dok ne zadovoljite znatiželju:**

<div class="sim">
		<iframe src="sim?stage=SB&format=sb" width="800" height="540"></iframe>
</div>

Ovaj osnovni "epidemiološki simulator letenja" nas je naučio dosta toga. Dozvolio nam je da odgovorimo na mnoga pitanja o prethodnim mesecima, budućim mesecima i budućim godinama.

Konačno, hajde da se vratimo na...

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Sada</div>
    </div>
</div>

Avion je potonuo. Uhvatili smo se za splavove za spašavanje. Vreme je da pronađemo kopno.[^dry_land]

[^dry_land]: Metafora kopna [iz članka autora Marc Lipsitch i Yonatan Grad, u STAT News](https://www.statnews.com/2020/04/01/navigating-covid-19-pandemic/)

Timovi epidemiologa i donosioca odluka ([levo](https://www.americanprogress.org/issues/healthcare/news/2020/04/03/482613/national-state-plan-end-coronavirus-crisis/), [desno](https://www.aei.org/research-products/report/national-coronavirus-response-a-road-map-to-reopening/ ), i [multi-partisan](https://ethics.harvard.edu/covid-roadmap)) došli su do koncenzusa o tome kako pobediti COVID-19, čuvajući naše živote *i* slobode.

U nastavku je obris ideje, sa nekim (manje-usaglašenim) rezervnim planovima:

![](pics/plansrb.png)

Šta ovo znači za TEBE, sada?

**Za sve:** Poštuj mere policijskog časa tako da svi možemo izaći iz Faze I što pre moguće. Nastavi da pereš te ruke. Pravi svoje maske. Preuzmi aplikaciju za praćenje kontakata koja *poštuje privatnost* kada postane dostupna sledećeg meseca. Ostani zdravo, fizički i mentalno! I piši lokalnim donosiocima odluka da se uozbilje i...

**Za donosioce odluka:** Donesite zakone da podržite osobe koje moraju da se samoizoluju/koji su u karantinu. Uposlite više osoba da se bave praćenjem kontakata, *podržite* ih adekvatnim aplikacijama koje prate kontakte i poštuju privatnost. Usmerite više finansija u stvari koje bi treblo da pravimo, kao što su...

**Za stvaraoce:** Stvarajte testove. Stvarajte respiratore. Stvarajte opremu za ličnu zaštitu za bolnice. Stvarajte testove. Stvarajte maske. Stvarajte aplikacije. Stvarajte antivirotike, profilaktike, i ostale lekove i tretmane koji nisu vakcine. Stvarajte vakcine. Stvarajte testove. Stvarajte testove. Stvarajte testove. Stvarajte nadu. 

Ne umanjujte strah da pobudite nadu. Naš strah treba da se *udruži* sa nadom, kao što su stvaraoci aviona i padobrana. Pripremanje za strašne budućnosti je i način na koji *stvaramo* budućnost kojoj se nadamo.

Jedina stvar za strah je ideja da je jedina stvar za strah sam strah.
