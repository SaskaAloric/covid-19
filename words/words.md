<div class="section">
    <div>
    	<iframe id="splash" width="960" height="480" src="banners/splash.html"></iframe>
        <div style="top: 70px;font-size: 75px;font-weight: bold;">
        	Šta dalje? 
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
			(epidemiologija)
			&
			<a href="https://ncase.me/">Nicky Case</a>
			(dizajn/programiranje)
		</div>
	</div>
</div>

„Jedino čega se treba plašiti je sâm strah“ je bio glup savet.

Naravno, ne morate nagomilavati rolne toalet papira – ali ako se oni zaduženi za donošenje odluka plaše straha, oni će podceniti realnost situacije sa ciljem da izbegnu „masovnu paniku“. Strah nije problem, već šta *radimo* sa njim. Strah nam daje snagu da se nosimo sa sadašnjim opasnostima i priprema nas za one kasnije.

Mi (Marcel, epidemiologija + Nicky, dizajn/programiranje) smo iskreno zabrinuti. Kladimo se da ste i vi! Zato smo mi kanalisali naš strah u pripremanje ovih **interaktivnih simulacija**, tako da *vi* možete kanalisati strah u razumevanje:

* **Prethodnih nekoliko meseci** (uvodni kurs epidemiologije, SEIR model, R i R<sub>0</sub>)
* **Narednih nekoliko meseci** (ograničenja kretanja, praćenje kontakata, maske)
* **Narednih nekoliko godina** (imunitet, vakcinacija)

Ovaj vodič (objavljen prvog maja 2020. godine, vidi ovu fusnotu!→[^timestamp]) za cilj ima da u vama pobudi nadu *i* strah. Da bismo pobedili COVID-19 **na način koji čuva našu mentalnu i finansijsku stabilnost**, potreban nam je optimizam za smišljanje planova, ali i pesimizam za smišljanje rezervnih planova. *“Optimista izmisli avion, a pesimista padobran.”*, Gladis Brovnin Stern. 

[^timestamp]: Fusnote će sadržati izvore informacija, linkove i bonus komentare, kao ovaj komentar!
    
    **Ovaj vodič je objavljen prvog maja 2020.** Mnogi detalji će se menjati ali smo mi uvereni da će ovaj vodič pokriti 95% mogućih budućnosti i da će početni kurs epidemiologije biti zauvek od koristi.

Vežite se, polećemo!

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Prethodnih nekoliko meseci</div>
    </div>
</div>

Piloti koriste simulatore letenja da nauče kako da ne sruše avione.

**Epidemiolozi koriste simulatore epidemija da nauče kako da ne uruše čovečanstvo.**

Počećemo od veoma, *veoma* jednostavnog „epidemiološkog simulatora letenja“! U ovoj simulaciji, zarazni ljudi <icon i></icon> (eng. **I**nfected) mogu preneti zarazu na podložne/zdrave ljude <icon s></icon> (eng. **S**usceptible) uvećavajući tako broj zaraznih <icon i></icon>:

![](pics/spreadsrb.png)

Procenjeno je da *se na početku* izbijanja COVID-19, virus prenosio sa <icon i></icon> na <icon s></icon> *u proseku* na svaka 4 dana.[^serial_interval] (Zapamtite, ovaj vremenski period puno varira.)

[^serial_interval]: „Prosečno vreme prenošenja zaraze (eng. serial interval) je 3.96 dana (interval poverenja od 95% je 3.53–4.39 dana).“ [Du Z, Xu X, Wu Y, Wang L, Cowling BJ, Ancel Meyers L](https://wwwnc.cdc.gov/eid/article/26/6/20-0357_article) (Napomena: Preliminarne verzije radova ne treba posmatrati na isti način kao finalne verzije.)

Ako simuliramo *samo efekat* „dupliranja broja slučajeva na svaka 4 dana“, u populaciji koja počinje sa samo 0.001% <span class="nowrap"><icon i></icon>,</span> šta se događa? 

**Pritiskom na „Pokreni“ pokreće se simulacija! Možete je puštati ponovo kasnije sa drugačijim parametrima** (napomena o simulacijama [^caveats]): 

[^caveats]: **Zapamtite: sve ove simulacije su vrlo pojednostavljene u svrhu obrazovanja.**
    
    Jedno pojednostavljenje: Kada kažete simulaciji „Inficiraj 1 novu osobu svakih X dana“, ona zapravo povećava broj zaraznih za 1/X svakog dana. Slično za buduća podešavanja u ovim simulacijama – „Oporavak svakih X dana“ zapravo umanjuje broj zaraznih za 1/X svakog dana.
    
    Ove dve interpretacije *nisu* u potpunosti iste, ali su dovoljno blizu, i za potrebe obrazovanja učinkovitije su od direktnog uspostavljanja stopa transmisije i oporavka.

<div class="sim">
		<iframe src="sim?stage=epi-1" width="800" height="540"></iframe>
</div>

Ovo je **kriva eksponencijalnog rasta.** Počinje malim brojevima, a zatim naglo poraste. Od „a ma to je samo grip“ do „zapravo, grip ne uzrokuje *masovne grobnice u razvijenim gradovima*“. 

![](pics/exponentialsrb.png)

Međutim, ova simulacija je pogrešna.  Na svu sreću, eksponencijalni rast ne dešava se u nedogled. Jedna od stvari koje zaustavljaju širenje virusa su ljudi koji *već* imaju virus:

![](pics/susceptiblessrb.png)

Što ima više zaraznih <span class="nowrap"><icon i></icon></span>, zdravi <span class="nowrap"><icon s></icon></span> češće postaju zarazni <span class="nowrap"><icon i></icon>,</span> **ali tada je manje zdravih <span class="nowrap"><icon s></icon>,</span> pa zdravi <span class="nowrap"><icon s></icon></span> *ređe* postaju zarazni <span class="nowrap"><icon i></icon>.</span>**

Kako ovo menja porast broja zaraznih tokom epidemije? Otkrijmo:

<div class="sim">
		<iframe src="sim?stage=epi-2" width="800" height="540"></iframe>
</div>

Ovo je „S-kriva“ ili **kriva logističkog rasta.** Počinje malim brojevima, zatim eksplodira, a onda usporava.

Ali, ova simulacija je *i dalje* pogrešna. Nismo iskoristili činjenicu da zarazni <icon i></icon> u nekom trenutku prestaju da budu zarazni, ili 1) oporavkom, 2) „oporavkom“ sa oštećenim plućima, ili 3) umiranjem.

Zarad pojednostavljenja, hajde da pretpostavimo da svi zarazni <icon i></icon> postaju oporavljeni <icon r></icon> (eng. **R**ecovered). (Samo zapamtite da u realnosti, neki umiru. [^sirkoment]) Oporavljeni <span class="nowrap"><icon r></icon></span> ne mogu ponovo biti zaraženi, i pretpostavimo – *za sada!* – da oni ostaju doživotno imuni.
[^sirkoment]: Na engleskom se u okviru **SIR** modela - **R**ecovered često nazivaju i **R**emoved, tj. uklonjeni iz daljeg epidemiološkog razmatranja ili smrću ili trajnim imunitetom, prim. prev.
U slučaju COVID-19, procenjeno je da su <icon i></icon> zarazni  *u proseku* 10 dana.[^infectiousness] To znači da će se neki oporaviti za manje od 10 dana, a nekima će biti potrebno više. **To ovako izgleda sa simulacijom koja *počinje* sa 100% <span class="nowrap"><icon i></icon>:</span>**

[^infectiousness]: „Medijalna vrednost perioda tokom koga je COVID-19 pozitivna osoba zarazna \[...\] je 9.5 dana.“ [Hu, Z., Song, C., Xu, C. et al](https://link.springer.com/article/10.1007/s11427-020-1661-4) Da, znamo da „medijalna“ vrednost nije isto što i „prosečna vrednost“. U cilju ovog pojednostavljenog edukativnog modela mislimo da su ove dve vrednosti dovoljno bliske.

<div class="sim">
		<iframe src="sim?stage=epi-3" width="800" height="540"></iframe>
</div>

Ovo je suprotno od eksponencijalnog rasta, ovo je **kriva eksponencijalnog pada.**

Kako se menja S-kriva logističkog rasta ako se u simulaciju *doda* efekat oporavljanja?

![](pics/graphs_q.png)

Hajde da otkrijemo.

<b style='color:#ff4040'>Crvena kriva</b> predstavlja broj *aktuelnih* slučajeva <span class="nowrap"><icon i></icon>,</span>    
<b style='color:#999999'>Siva kriva</b> je *ukupan* broj slučajeva (aktuelni + oporavljeni <span class="nowrap"><icon r></icon>),</span>
počinjemo sa samo 0.001% <span class="nowrap"><icon i></icon>:</span>

<div class="sim">
		<iframe src="sim?stage=epi-4" width="800" height="540"></iframe>
</div>

I *otuda* famozna kriva! Ovo nije zvonasta kriva (poznata i kao normalna ili Gausova raspodela, prim. prev.), nije čak ni „log-normalna“ kriva. Ona nema ime. Ali videli ste je zilion puta, i preklinjani ste da je ispeglate.

Ovo je takozvani **SIR model** (<icon s></icon> **S**usceptible - zdravi/podložni <icon i></icon> **I**nfectious - zarazni <icon r></icon> **R**ecovered - oporavljeni) [^sir], *druga* najvažnija ideja u početnom kursu epidemiologije:

[^sir]: Za više tehničkih objašnjenja o SIR modelu, vidite [Institut za modelovanje bolesti](https://www.idmod.org/docs/hiv/model-sir.html#) i [Vikipediju](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SIR_model).

![](pics/sirsrb.png)

**Komentar: Simulacije na osnovu kojih se donose odluke su *mnogo* sofisticiranije od ovih!** Ali SIR model i dalje može da objasni neke generalne trendove, iako mu nedostaju finese.

U stvari, hajde da dodamo jednu finesu: pre nego što <icon s></icon> postanu <span class="nowrap"><icon i></icon>, </span> oni prvo postanu <icon e></icon> *inficirani* (eng. **E**xposed). U ovom stanju, ljudi imaju virus ali ga ne mogu još prenositi, oni su zara*ženi* ali ne još zara*zni*.

![](pics/seirsrb.png)

(Ova varijanta modela zove se **SEIR model**, gde „E“ potiče od <icon e></icon> „**E**xposed“ - inficiranih.[^seir] Na engleskom „Exposed“ , što znaci „izložen“, ne potvrđuje da je virus u organizmu, već samo da je postojala šansa da se osoba zarazi. Međutim, u ovom modelu „Exposed“ znači da osoba ima virus. Naučna terminologija je loša. [^inficirani])

[^seir]: Za više tehničkih objašnjenja o SEIR modelu, pogledajte [Institute za modelovanje bolesti](https://www.idmod.org/docs/hiv/model-seir.html) i [Vikipediju](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SEIR_model).

[^inficirani]: Da bi se izbegla ista dilema u ovom prevodu odabrano korišćenje reči „inficirani“ umesto „izloženi“, prim. prev.

U slučaju COVID-19, procenjeno je da se u stanju <icon e></icon> inficiran-ali-ne-još-zarazan provede 3 dana, *u proseku*.[^latent] Šta se dešava ako i to dodamo u simulaciju?

[^latent]: „Pretpostavljajući distribuciju perioda inkubacije sa prosečnom vrednošću od 5.2 dana iz druge studije na ranim COVID-19 slučajevima, mi smo zaključili da zaraznost počinje od 2.3 dana (interval sa 95% poverenja je 0.8–3.0 dana) pre nego što počnu simptomi.“ (u prevodu: Pretpostavljajući da simptomi počinju petog dana, zaraznost počinje dva dana pre = zaraznost počinje tri dana nakon što je osoba inficirana) [He, X., Lau, E.H.Y., Wu, P. et al.](https://www.nature.com/articles/s41591-020-0869-5)

<b style='color:#ff4040'>Crvena <b style='color:#FF9393'>+ Roze</b> kriva</b> su *aktuelni* slučajevi (zarazni <icon i></icon> + inficirani <span class="nowrap"><icon e></icon>),</span>[^izvestavanje]    
<b style='color:#888'>Siva kriva</b> su *ukupni* slučajevi (aktuelni + oporavljeni <span class="nowrap"><icon r></icon>):</span>

[^izvestavanje]: U dnevnim izveštajima i medijima govori se samo o zaraznima koji su *testirani*, kojih je svakako manje od *aktuelnih* slučajeva prikazanih na graficima, prim. prev.

<div class="sim">
		<iframe src="sim?stage=epi-5" width="800" height="540"></iframe>
</div>

Nije se mnogo toga promenilo! Vreme tokom kojeg osoba ostaje <icon e></icon> inficirana (ali ne i zarazna) menja odnos <span class="nowrap"><icon e></icon> : <icon i></icon>,</span> kao i *kada* broj aktuelnih slučajeva dostiže maksimum... ali *visina* maksimuma, i ukupan broj slučajeva na kraju, ostaje isti.

Zašto je to tako? To je zbog *prve* najvažnije ideje u početnom kursu epidemiologije:

![](pics/r.png)

Ovo je skraćeno od „Reproduktivni broj“ (eng. Reproduction number). To je *prosečan* broj ljudi koje <icon i></icon> zarazi *pre* nego što ozdravi (ili umre).

![](pics/r2srb.png)

**R** se menja tokom trajanja epidemije, jer se menjaju broj imunih i intervencija.

**R<sub>0</sub>** je vrednost R *na početku epidemije, pre imuniteta ili intervencija*. R<sub>0</sub> bliže prikazuje snagu samog virusa, ali se ipak menja u zavisnosti od lokacije. Na primer, R<sub>0</sub> je veće u gušće naseljenim gradovima nego u retko naseljenim ruralnim sredinama.

(Većina članaka u novinama – čak i neki istraživački radovi! – mešaju R i R<sub>0</sub>. Opet, naučna terminologija je loša.)

R<sub>0</sub> „tipičnog“ sezonskog gripa je oko 1.28.[^r0_flu] Ovo znači da na *početku* epidemije gripa, svaki <icon i></icon> zarazi 1.28 drugih *u proseku.* (Ako zvuči čudno što ovo nije ceo broj, setite se da „prosečno“ majke imaju 2.4 deteta. To ne znači da polu-deca trče okolo.)

[^r0_flu]: „Medijalna vrednost R za sezonski grip je 1.28 (interkvartalni interval: 1.19–1.37)“ [Biggerstaff, M., Cauchemez, S., Reed, C. et al.](https://bmcinfectdis.biomedcentral.com/articles/10.1186/1471-2334-14-480)

Procenjena vrednost R<sub>0</sub> za COVID-19 je oko 2.2[^r0_covid], mada jedna *još-uvek-nedovršena* studija procenjuje da je u Vuhanu vrednost R<sub>0</sub> bila 5.7(!).[^r0_wuhan]

[^r0_covid]: „Procenili smo bazični reproduktivni broj R<sub>0</sub> virusa 2019-nCoV na oko 2.2 (interval velike gustine od 90%: 1.4–3.8).“ [Riou J, Althaus CL.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7001239/)

[^r0_wuhan]: „Izračunali smo da medijalna vrednost R<sub>0</sub> iznosi 5.7 (interval sa 95% poverenja: 3.8–8.9).“ [Sanche S, Lin YT, Xu C, Romero-Severson E, Hengartner N, Ke R.](https://wwwnc.cdc.gov/eid/article/26/7/20-0282_article)

U našim simulacijama – *na početku i u proseku* – u toku 10 dana, svaki <icon i></icon> zarazi nekoga na svaka 4 dana. „4 dana“ je dva i po puta kraće od „10 dana“. Ovo znači da – *na početku i u proseku* – <icon i></icon> zarazi 2.5 drugih. Stoga je R<sub>0</sub> = 2.5.[^r0_caveats_sim]

[^r0_caveats_sim]: Ovde smo pretpostavili da je osoba jednako zarazna tokom celog „zaraznog perioda“. Opet, pojednostavljenje u službi obrazovanja.

**Igrajte se sa računanjem R<sub>0</sub> da vidite kako R<sub>0</sub> zavisi od vremena potrebnog za oporavak i vremena proteklog do novo-zaraženih:**

<div class="sim">
		<iframe src="sim?stage=epi-6a&format=calc" width="285" height="255"></iframe>
</div>

Ali zapamtite, što je manje <span class="nowrap"><icon s></icon></span>, *ređe* <span class="nowrap"><icon s></icon></span> postaju <span class="nowrap"><icon i></icon>.</span> *Aktuelni* reproduktivni broj (R) zavisi ne samo od *bazičnog* reproduktivnog broja (R<sub>0</sub>), *nego i od* brojnosti ljudi koji nisu više <icon s></icon> tj. podložni/zdravi (time što su, na primer, ozdravili i stekli prirodni imunitet).

<div class="sim">
		<iframe src="sim?stage=epi-6b&format=calc" width="285" height="390"></iframe>
</div>

Kada je dovoljan broj ljudi imun tada je R < 1 i virus je zauzdan! Ovo se naziva **imunitet krda**. Za viruse gripa, imunitet krda se dostiže *vakcinisanjem*. Pokušaj da se dostigne „prirodan imunitet krda“ izlažući ljude zarazi je *užasna* ideja. (Ali ne zbog razloga koji vam možda padaju na pamet! Objasnićemo kasnije.)

Poigrajmo se sa SEIR modelom ponovo, ali prikazujući kako se vrednosti R<sub>0</sub> i R menjaju tokom vremena, kao i granični broj zaraženih kada je imunitet krda dostignut:

<div class="sim">
		<iframe src="sim?stage=epi-7" width="800" height="540"></iframe>
</div>

**Obratite pažnju: Ukupan broj slučajeva *ne staje sa rastom* kada se dostigne broj zaraženih potrebnih za imuniteta krda, već ga premašuje!** I taj broj je premašen *tačno u trenutku* kada broj aktuelnih slučajeva dostiže svoj maksimum. (Ovo se dešava nezavisno od toga kako promenite parametre – probajte!)

Ovo se dešava zato što u trenutku kada broj <span class="nowrap">ne-<icon s></icon></span> nadmaši broj potreban za imunitet krda, tada se dostiže R < 1. A kada je R < 1, tada i broj aktuelnih slučajeva prestaje da raste: dostignut je maksimalni broj zaraženih.

**Ako ćete iz ovog čitanja usvojiti samo jednu pouku, neka to bude poruka na sledećem dijagramu** – u pitanju je izuzetno kompleksan dijagram, temeljno ga analizirajte:

![](pics/r3srb.png)

**Ovo znači: NE moramo da zauzdamo sva prenošenja virusa, čak ni skoro sva, da bismo zaustavili COVID-19!**

Ovo je paradoks. COVID-19 je ekstremno zarazan, ali da ga zauzdamo, potrebno je zaustaviti „samo“ 60% prenosa virusa. 60%?! Da je to školska ocena, bila bi neka dvojčica. Ali ako je R<sub>0</sub> = 2.5, smanjenjem od 61% dostižemo R = 0.975, koje je manje od 1 i virus je zauzdan! (tačna formula:[^exact_formula])

[^exact_formula]: Setite se da je R = R<sub>0</sub> × udeo zaraza koje se i dalje mogu odvijati. I još se setite da je ovaj udeo zaraza koje i dalje mogu da se odvijaju = 1 - udeo zaraza koje su *zaustavljene*.
    
    Stoga, da bismo dostigli R < 1, potrebno je da R<sub>0</sub> × MogućeZaraze < 1. 
    
    Stoga, MogućeZaraze < 1/R<sub>0</sub>
    
    Stoga, 1 - ZaustavljeneZaraze < 1/R<sub>0</sub>
    
    Stoga, ZaustavljeneZaraze > 1 - 1/R<sub>0</sub>
    
    Stoga, potreno je zastaviti više od **1 - 1/R<sub>0</sub>** prenosa zaraze da bi R < 1 i zauzdali virus!

![](pics/r4srb.png)

(Ako mislite da je R<sub>0</sub> ili bilo koji drugi broj u našim simulacijama premali/prevelik, super je što preispitujete naše pretpostavke! Na kraju ovog vodiča biće još fleksibilnija verzija simulacije u kojoj možete uneti *vaše* brojeve, i simulirati šta se dešava.)

*Sve* interevencije protiv COVID-19 o kojima ste čuli – pranje ruku, socijalno/fizičko distanciranje, policijski čas, samoizolacija, praćenje kontakata i karantin, maske, pa čak i „imunitet krda“ –  *sve* one rade istu stvar:

Spuštaju vrednost do R < 1.

U nastavku, hajde da iskoristimo naš „epidemiološki simulator letenja“ da istražimo: Kako postići R < 1 tako da **sačuvamo našu mentalnu *i* finansijsku stabilnost?**

Pripremite se, prinudno sletanje...

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Narednih nekoliko meseci</div>
    </div>
</div>

...moglo je da bude gore. Evo paralelnog univerzuma koji smo zaobišli:

###Scenario 0: Ne učiniti apsolutno ništa


Otprilike jednoj od 20 osoba inficiranih koronavirusom potrebna je intenzivna nega.[^icu_covid] U razvijenim zemljama kao što su SAD, postoji jedno mesto na intenzivnoj nezi na 3400 stanovnika.[^icu_us] Stoga, bolnički sistem u SAD može da podnese da 20 ljudi na svakih 3400 bude *istovremeno* zaraženo – ili 0.6% populacije.

[^icu_covid]: [„Procenat COVID-19 slučajeva u Sjedinjenim Američkim Državama od 12. februara do 16. marta 2020. godine kojima je bila potrebna intenzivna nega, grupisano po starosti“](https://www.statista.com/statistics/1105420/covid-icu-admission-rates-us-by-age-group/). Između 4.9% i 11.5% od *svih* COVID-19 slučajeva zahtevalo je intenzivnu negu. Velikodušno smo odabrali minimalnu vrednost, tj. 5%, odnosno 1 od 20. Obratite pažnju da je ova vrednost specifična u odnosu na starosnu strukturu Sjedinjenih Američkih Država, i može biti veća za države sa starijom populacijom, ili manja za države sa mlađom populacijom.

[^icu_us]: „Broj mesta na intenzivnoj nezi = 96,596“. Izvor [the Society of Critical Care Medicine](https://sccm.org/Blog/March-2020/United-States-Resource-Availability-for-COVID-19) Broj stanovnika u SAD bio je 328,200,000 u 2019. godini, stoga 96,596 naspram 328,200,000 = približno je 1 na 3400. 

Čak i kada bi se *utrostručio* kapacitet intenzivne nege na 2% u SAD, ovako bi izgledao slučaj kada se *ništa ne preduzme:* 

<div class="sim">
		<iframe src="sim?stage=int-1&format=lines" width="800" height="540"></iframe>
</div>

Daleko od dobrog.

Ovo je ono što je [Izveštaj Imperial Koledža od 16. marta](http://www.imperial.ac.uk/mrc-global-infectious-disease-analysis/covid-19/report-9-impact-of-npis-on-covid-19/) takođe zaključio: ako se ništa ne uradi, popuniće se svi kapaciteti intenzivne nege, dok je preko 80% stanovništva zaraženo. (Setite se: ukupan broj slučajeva je *premašio* imunitet krda.)

Čak i kad bi samo 0.5% zaraženih slučajeva preminulo (vrlo optimistična pretpostavka ako nema uslova za lečenje na intenzivnoj nezi) u velikim državama kao što su SAD, sa populacijom od 300 miliona, 0.5% od tih 80% inficiranih predstavlja u stvari 1.2 miliona mrtvih... *AKO se ne uradi ništa.*

(Dosta vesti i medija na društvenim mrežama izveštava da će „80% biti inficirano“ *bez* informacije da je to pod pretpostavkom „DA SE NE URADI NIŠTA“. Strah je pretočen u klikove, a ne u razumevanje.)

###Scenario 1: Peglanje krive / Imunitet krda

Plan „Peglanje krive“ je bio reklamiran od strane svake zvanične javne zdravstvene organizacije, dok je inicijalno pominjani plan u Velikoj Britaniji pod nazivom „imunitet krda“ bio sveopšte kritikovan. To su u stvari *isti planovi*. Samo su u VB plan dosta loše predstavili javnosti.[^yong]

[^yong]: „On kaže da je cilj isti kao u drugim zemljama: peglanje krive time što se poljulja početak infekcije. Posledično, narod će postići imunitet krda; to je sporedni efekat, a ne cilj. [...] Zvaničan plan akcije vlasti u vezi sa koronavirusom, dostupan na njihovom sajtu, uopšte nije pominjao imunitet krda.“
    
    Iz [The Atlantic članka autora Ed Yong](https://www.theatlantic.com/health/archive/2020/03/coronavirus-pandemic-herd-immunity-uk-boris-johnson/608065/)

Oba plana, s' druge strane, imaju jednu bukvalno fatalnu manu.

Prvo, pogledajmo dva osnovna načina kako se „pegla kriva“: pranje ruku i fizičko distanciranje/udaljavanje.

Češće pranje ruku smanjuje prehlade i grip u razvijenim zemljama za ~25%[^handwashing], dok je zatvaranje celog Londona smanjilo kontakte za ~70%[^london]. Stoga, hajde da pretpostavimo da pranje ruku smanjuje R za *do* 25%, a distanciranje *do* 70%:

[^handwashing]: „U svih osam dostupnih istraživanja su zaključili da pranje ruku smanjuje rizik od infekcija respiratornog sistema, sa smanjenjem rizika u intervalu od 6% do 44% [zbirna srednja vrednost je 24%, interval od 95% poverenja je 6–40%].“ Mi smo zaokružili srednju vrednost na 25% u ovim simulacijama radi jednostavnosti. [Rabie, T. and Curtis, V.](https://onlinelibrary.wiley.com/doi/full/10.1111/j.1365-3156.2006.01568.x) Napomena: kako ova meta-analiza pokazuje, kvalitet istraživanja na temu pranja ruku (bar u razvijenijim zemljama) su grozna.

[^london]: „Primećeno je da postoji 73% smanjenja u prosečnom broju kontakata po učesniku. Ovo bi bilo dovoljno da smanji R<sub>0</sub> sa 2.6, vrednosti koju je imalo pre zatvaranja grada/policijskog časa), na 0.62 (0.37 - 0.89) tokom zatvaranja grada.“ Mi smo ovo zaokružili na 70% u ovim simulacijima radi jednostavnosti. [Jarvis i Zandvoort et al](https://cmmid.github.io/topics/covid19/comix-impact-of-physical-distance-measures-on-transmission-in-the-UK.html)

**Igrajte se sa ovim kalkulatorom da vidite kako  % <span class="nowrap">ne-<icon s></icon>,</span> pranje ruku i distanciranje smanjuju R:** 

(Ovaj kalkulator vizualizuje njihov *relativni* uticaj, i zbog toga *izgleda* kao da povećanje jednog smanjuje efekat drugog.[^log_caveat])

[^log_caveat]: Ova naizgled nelogičnost ne bi postojala kad bismo predstavili R na logaritamskoj skali... ali onda bismo morali da objasnimo šta je *logaritamska skala.*

<div class="sim">
		<iframe src="sim?stage=int-2a&format=calc" width="285" height="260"></iframe>
</div>

Hajdemo sad da simuliramo šta bi se dogodilo sa COVID-19 epidemijom, da smo od marta 2020. godine češće prali ruke, ali samo sa *blagim* fizičkim distanciranjem - tako da se R smanji, ali da je i dalje veće od 1:

<div class="sim">
		<iframe src="sim?stage=int-2&format=lines" width="800" height="540"></iframe>
</div>

Tri napomene:

1. Ovo *smanjuje* ukupan broj slučajeva! **Čak i da nemamo R < 1, smanjivanje R i dalje spasava živote, jer se time smanjuje i premašivanje broja zaraženih preko broja potrebnog za imunitet krda.** Dosta ljudi misli da se „peglanjem krive“ samo vremenski raširi broj slučajeva bez uticaja na ukupan broj. To je nemoguće u *svakom* osnovnom epidemiološkom modelu. Ali, zbog toga što su na vestima predstavili „80%+ biće inficirano“ kao neizbežnu stvar, ljudi su mislili da će svejedno ukupan broj slučajeva prosto ostati isti. *Netačno.*

2. Zbog dodatnih intervencija, aktuelni slučajevi su dostigli maksimum *pre* nego što je došlo do imuniteta krda. Zapravo, u ovoj simulaciji, ukupan broj slučajeva tek *malo* premašuje imunitet krda - što je bio i plan Velike Britanije! U tom trenutku je R < 1, što znači da se može odustati od svih ostalih intervencija, i COVID-19 ostaje zauzdan! Da, ako zanemarimo jedan problem:...

3. I dalje dolazi do zauzimanja svih kapaciteta na intenzivnoj nezi. Na nekoliko meseci. (I setimo se, *već* smo uzeli trostruko veći broj realnih kapaciteta u ovim simulacijama.)

To je bio još jedan zaključak Izveštaja Imperial Koledza od 16. marta, koji je ubedio Engleze da odustanu od njihovog početnog plana. Svaki pokušaj u *ublažavanju* (što je smanjenje R, ali i dalje R > 1) će propasti. Jedini način da se izađe iz ove situacije je **suzbijanje** (smanjenje R tako da bude R < 1).


![](pics/mitigation_vs_suppressionsrb.png)

To znači nemoj samo da *peglaš* krivu - *uništi* krivu. Na primer, probajmo...

###Scenario 2: Višemesečno zatvaranje (gradova, policijski čas i slično)

Hajde da vidimo šta se dešava ako *suzbijemo* krivu sa petomesečnim zatvaranjem u kuće, tako smanjimo broj <icon i></icon> praktično potpuno, a onda se *napokon* vratimo normalnom životu:

<div class="sim">
		<iframe src="sim?stage=int-3&format=lines" width="800" height="540"></iframe>
</div>

Ups.

Ovo je taj „drugi talas“ o kojem svi pričaju. Čim prestanemo sa zatvaranjem, opet dolazi do R > 1. Onda, jedan preostali <icon i></icon> (ili neki <span class="nowrap"><icon i></icon> koji je došao)</span> može da prouzrokuje ponovni skok u broju slučajeva, što je skoro pa podjednako loše kao da smo samo uradili Scenario 0: Apsolutno ništa.


**Zatvaranje nije rešenje, već samo restart situacije.**

Dobro, šta to znači, mi sad samo treba da se zatvaramo (ili da uvodimo policijski čas) iznova i iznova?

###Scenario 3: Naizmenično Zatvaranje-Otvaranje

Ovo rešenje je bilo predloženo prvo u Izveštaju Imperial Koledža 16. marta, a potom i u jednom radu naučnika sa Harvarda.[^lockdown_harvard]

[^lockdown_harvard]: „Ako ne uzmemo u obzir ostale intervencije, glavni parametar uspešnosti sprovođenja mera fizičkog distanciranja je da li su popunjeni svi kapaciteti intenzivnih nega. Da bi se ovo izbeglo, produžena ili pak naizmenična fizička distanciranja su potencijalno neophodna i do 2022 godine.“ [Kissler i Tedijanto et al](https://science.sciencemag.org/content/early/2020/04/14/science.abb5793)

**Evo i simulacije:** 
(Pošto se izigrate sa „već nameštenim scenariom“, možete da probate i *vaše* rasporede zatvaranja gradova/policijskog časa, menjajući vrednosti klizača *dok* traje simulacija! Setite se da možete da pauzirate i nastavite simulaciju, kao i da promenite njenu brzinu izvršavanja.)

<div class="sim">
		<iframe src="sim?stage=int-4&format=lines" width="800" height="540"></iframe>
</div>

Ovo *bi* zadržalo ukupan broj slučajeva ispod kapaciteta invenzivne nege! I *mnogo* je bolje od zatvaranja gradova na 18 meseci, dok vakcina ne postane dostupna. Jedino što mi treba da radimo jeste.. da se zatvorimo na par meseci, otvorimo na par meseci, i ponavljamo ovo u krug dok ne dođemo do vakcine. (Ili u slučaju da nema vakcine, ponavljamo dok ne dostignemo imunitet krda... u 2022. godini.)

Lepo je što smo nacrtali liniju koja predstavlja „kapacitet intenzivne nege“, ali postoji tu još vrlo bitnih stvari koje mi *ne možemo* da simuliramo. Na primer:

**Mentalno zdravlje:** Usamljenost je jedan od najbitnijih faktora rizika za depresiju, anksioznost i samoubistvo. I povezuje se sa preuranjenom smrtnošću u sličnoj meri kao i pušenje 15 cigareta dnevno.[^loneliness]

[^loneliness]: Pogledajte [Sliku 6 iz Holt-Lunstad i Smith 2010](https://journals.sagepub.com/doi/abs/10.1177/1745691614568352). Naravno, obratimo pažnju da su uočili *korelaciju*. Ali, sem ako ne želimo da nasumično ljude stavljamo u izolaciju da bismo istraživali usamljenost, jedino što imamo su podaci sa posmatranja kao što je ovo. 

**Finansijsko stanje:** „Šta ćemo sa ekonomijom?!“ zvuči kao da neko više brine o parama nego o životima, ali „ekonomija“ nije samo berza i zarada poslodavaca: to je mogućnost da ljudi zarade za hranu i krov nad glavom za njih i njihove bližnje, da ulažu u budućnost njihove dece, i uživaju u umetnosti, hrani, video igrama - u svim onim stvarima koje čine život lepim i vrednim. I pored toga, siromaštvo *samo po sebi* ima katastrofalne posledice po mentalno i fizičko zdravlje.


Ali ne kažemo da smo *protiv* ponovnog zatvaranja! Vratićemo se kasnije na to "ciklično" otvaranje i zatvaranje. I dalje je daleko od idealne situacije.

Ali, čekajte. Zar nisu Tajvan i Južna Koreja *već* zauzdali COVID-19? Na čitava četiri meseca, *bez* dugoročnog zatvaranja?!

Kako?

###Scenario 4: Testiranje, praćenje, izolovanje

*"Da, sigurno, mi smo \*mogli\* da uradimo to što su i Tajvan i Južna Koreja uradili na početku, ali sada je previše kasno za to. Omašili smo početak."*


Upravo to! „Zatvaranje nije rešenje, ali jeste restart“... **i novi početak je ono što nam treba.**

Da bismo razumeli kako su Tajvan i Južna Koreja zaustavili COVID-19, potrebno je da razumemo tačne vremenske okvire tipične COVID-19 infekcije [^timeline]:

[^timeline]: **3 dana u proseku za infektivnost:** „Pretpostavljajući da je inkubacioni period normalna distribucija oko srednje vrednosti 5.2 dana (iz drugog istraživanja COVID-19 slučajeva), zaključujemo da infektivnost počinje vec od 2.3 dana (interval 95% poverenja je 0.8–3.0 dana) pre nego što se manifestuju simptomi.“ (u prevodu: Ako pretpostavimo da se simptomi vide od petog dana, zaraznost je počela dva dana pre, tj. počinje od treceg dana) [He, X., Lau, E.H.Y., Wu, P. et al.](https://www.nature.com/articles/s41591-020-0869-5)  
    
    **4 dana u proseku da se zarazi druga osoba:** „Usrednjen [serijski] interval je bio 3.96 dana (interval 95% poverenja je 3.53–4.39 dana).“ [Du Z, Xu X, Wu Y, Wang L, Cowling BJ, Ancel Meyers L](https://wwwnc.cdc.gov/eid/article/26/6/20-0357_article)
    
    **5 dana u proseku da se ispolje simptomi:** „Medijana distribucije inkubacionog perioda je procenjena da je 5.1 dan (interval 95% poverenja je 4.5 do 5.8 dana).“ [Lauer SA, Grantz KH, Bi Q, et al](https://annals.org/AIM/FULLARTICLE/2762808/INCUBATION-PERIOD-CORONAVIRUS-DISEASE-2019-COVID-19-FROM-PUBLICLY-REPORTED)

![](pics/timeline1srb.png)

Ako se slučajevi samoizoluju kad shvate da su se razboleli (tj. osete simptome), virus i dalje može da se širi:

![](pics/timeline2srb.png)

I zapravo, 44% svih prenošenja su: *pred*-simptomatska! [^pre_symp]

[^pre_symp]: „Mi smo procenili da su 44% (interval 95% poverenja je 25–69%) sekundarnih slučajeva bili zaraženi tokom predsimptomatskog perioda za dati slučaj.“ [He, X., Lau, E.H.Y., Wu, P. et al](https://www.nature.com/articles/s41591-020-0869-5)

Ali, ako pronađemo *i stavimo u karantin* skorašnje kontakte tog jednog analiziranog slučaja koji ispoljava simptome zaraze... mi zaustavljamo širenje, time što smo jedan korak ispred!

![](pics/timeline3srb.png)

Ovo se zove **praćenje kontakata**. Ideja je stara, i bila je korišćena u velikoj meri da se zauzda širenje Ebole[^ebola], i sada je suština plana kojim su Tajvan i Južna Koreja zauzdali COVID-19!


[^ebola]: „Praćenje kontakata je bilo od suštinske važnosti u Liberiji i predstavlja jednu od najvećih napora i akcija za praćenje kontakata tokom svih epidemija u istoriji.“ [Swanson KC, Altare C, Wesseh CS, et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6152989/)

(Ovim se takođe omogućava i efikasnije korišćenje ograničeno dostupnih testova, za lociranje predsimptomatskih <span class="nowrap"><icon i></icon></span> bez potrebe da se testira cela populacija.)

Tradicionalno, kontakti se prikupljaju prilikom intervjuisanja zaražene osobe, ali to je samo po sebi vrlo sporo za vremenski prozor COVID-19, koji je ~48 sati. Zato ljudima koji sprovode intervjue treba pomoć, kao i podrška, u vidu aplikacija za praćenje kontakata.


(Ova ideja nije potekla od inženjera: korišćenje aplikacije da se suzbije COVID-19 je prvobitno bilo predloženo od strane [tima epidemiologa sa Oksforda](https://science.sciencemag.org/content/early/2020/04/09/science.abb6936).)

Čekajte, aplikacije koje prate kontakte?... Da li to znači da se odričemo naše privatnosti, dajući pristup Velikom bratu?

Ni pod razno! **[DP-3T](https://github.com/DP-3T/documents#decentralized-privacy-preserving-proximity-tracing)**, tim epidemiologa i kriptografa (u koji je uključen i jedan od nas, Marcel Salathé) *već* rade na pravljenju takve aplikacije - sa javno dostupnim kodom - koja ne otkriva **podatke o identitetu, lokaciji, kontaktima, pa čak ni *koliko kontakata* je osoba imala.**

Ovako ona radi:

![](pics/dp3tsrb.png)

([Ovde je ceo strip.](https://ncase.me/contact-tracing/) Detalji oko "varanja"/lažno pozitivnih/i ostalo u fusnoti:[^dp3t_details])

[^dp3t_details]: Da bi se onemogućilo „varanje“ (ljudi koji lažno tvrde da su zaraženi), DP-3T Protokol zahteva da bolnica prvo dodeli jednokratnu šifru potencijalno zaraženoj osobi, što omogućava slanje bolnici svih njihovih poruka.

    Lažno pozitivni su problem u oba slučaja - i u ručnom i u automatskom praćenju kontakata. Mada, i dalje možemo smanjiti broj lažno pozitivnih na dva načina: 1) time što bismo obavestili sve Bojane tek ako su čule, recimo, više od 30 min poruka, a ne samo jednu poruku u prolazu; 2) Ako aplikacija misli da Bojana *jeste* bila izložena virusu, može da savetuje Bojani da ode na intervju u bolnicu.
    
    Za ostala pitanja kao što je potrošnja internet protoka, integritet izvora, i ostala pitanja u vezi sa bezbednošću podataka, pogledajte [open-source DP-3T predloge!](https://github.com/DP-3T/documents#decentralized-privacy-preserving-proximity-tracing)

Pored timova poput TCN Protocol[^tcn] i MIT PACT[^pact], i Apple i Google rade na razvijanju rešenja za praćenje kontakata sa zaštitom privatnosti kroz adaptiranje sistema iOS i Android.[^gapple] (Ne veruješ Google/Apple? Ako! Lepota ovog sistema jeste što mu *ne treba* tvoje poverenje!) Možda će uskoro tvoj zdravstveni sistem od tebe tražiti da instaliraš neku aplikaciju. Ako je obezbeđena zaštita privatnosti i aplikacija ima javno dostupan kod (open-source), molimo te instaliraj je!

[^tcn]: [Temporary Contact Numbers, a decentralized, privacy-first contact tracing protocol](https://github.com/TCNCoalition/TCN#tcn-protocol)

[^pact]: [PACT: Private Automated Contact Tracing](https://pact.mit.edu/)

[^gapple]: [Apple i Google partneri za tehnologiju praćenja kontakata COVID-19](https://www.apple.com/ca/newsroom/2020/04/apple-and-google-partner-on-covid-19-contact-tracing-technology/). Primetite da ih oni ne prave *sami*, već da samo prave sistem koji će moći da *podrži* ovakve aplikacije.

Ali šta je sa ljudima koji nemaju pametne telefone? Ili sa infekcijama koje se dešavaju preko kvaka na vratima? Ili sa „stvarnim“ asimptomatskim slučajevima? Aplikacije za praćenje kontakata ne mogu da uhvate baš sva prenošenja... *i to je okej!* Mi ni ne moramo da ih *sve* uhvatimo, već samo 60+% da bismo došli do R<1.

(Fusnota o nerviranju oko mešanja termina - predsimptomatskih i "stvarnih" asimptomatskih slučajeva - "stvarni" asimptomatski su vrlo retki:[^rant])

[^rant]: Veliki broj novih izveštaja - i iskreni da budemo, dosta istraživačkih radova - ne razlikuje „slučajeve koji ne pokazuju simptome kad ih testiraju“ (predsimptomastki slučajevi) i „slučajeve koji ne pokazuju simptome *nikada*“ (stvarni asimptomatski). Jedini način na koji oni mogu da se razdvoje je da se radi ponovno testiranje posle nekog vremena.

    Šta je šta - [ovo istraživanje](https://wwwnc.cdc.gov/eid/article/26/8/20-1274_article) je analiziralo. (Obratite pažnju: „Rano objavljivanje radova se ne smatra finalnim verzijama.“) U kol-centru u Južnoj Koreji koja je imala izbijanje COVID-19 bolesti, „samo 4 slučaja  (1.9%) su ostali asimptomatski u toku 14 dana karantina, i niko od njihovih ukućana nije imao sekundarnu infekciju.“
    
    
    To znači da su  „stvarni asimptomatski“ slučajevi stvarno retki, a da vas zaraze takvi je još ređe.
    

Izolacija *simptomatskih* slučajeva bi smanjila R za do 40%, a odlazak u karantin njihovih *pred/a-simptomatskih* kontakata bi smanjilo R za do 50%[^oxford]:

[^oxford]: Iz istog istraživanja sa Oksforda koje je prvo predložilo aplikacije za suzbijanje COVID-19 bolesti: [Luca Ferretti i Chris Wymant et al](https://science.sciencemag.org/content/early/2020/04/09/science.abb6936/tab-figures-data) Pogledajte Sliku 2. Pretpostavljajući R<sub>0</sub> = 2.0, oni su zaključili da:    
    
    * Simptomatični doprinose R = 0.8 (40%)
    * Predsimptomatični doprinose  R = 0.9 (45%)
    * Asimptomatični doprinose R = 0.1 (5%, iako njihov model ima neke nesigurnosti i moglo bi da bude i dosta manji broj u pitanju)
    * Stvari u okolini kao što su kvake na vratima doprinose R = 0.2 (10%)

    I ako saberemo pred- i a-simptomatične kontakte (45% + 5%) dobijamo 50% od R!

<div class="sim">
		<iframe src="sim?stage=int-4a&format=calc" width="285" height="340"></iframe>
</div>

Čak i bez stavljanja 100% kontakata u karantin, možemo da dođemo do R < 1 *bez zatvaranja*! Ovo je mnogo bolje za mentalnu i finansijsku stabilnost. (Mislimo da bi *vlade trebalo da potpomognu* troškove ljudi koji moraju da se samoizoluju/odu u karantin - obezbede testove, osiguraju njihove poslove, subvencionišu odsustvo, i slično. To je i dalje jeftinije od periodičnog zatvaranja čitavih gradova.)


Time bismo održavali R < 1 dok ne dođemo do vakcine, koja će podložne <span class="nowrap"><icon s></icon></span> pretvarati u imune <span class="nowrap"><icon r></icon>.</span> Izvolite imunitet *krda*, ali na pravi način:

<div class="sim">
		<iframe src="sim?stage=int-4b&format=calc" width="285" height="230"></iframe>
</div>

(Komentar: ovaj kalkulator pretpostavlja da je hipotetička vakcina 100% efikasna. Zapamtimo da u realnosti to moramo da kompenzujemo vakcinacijom *većeg* broja ljudi od onog potrebnog za „imunitet krda“, da bismo *zapravo* dostigli imunitet krda.)

Dobro, dosta priče. Ovo je simulacija:

1. Zatvaranja na nekoliko meseci, dok nismo u stanju da...
2. Pređemo na „Testiranje, praćenje, izolovanje“, dok ne omogućimo da...
3. Vakcinišemo dovoljan broj ljudi, što bi značilo...
4. Da smo pobedili.


<div class="sim">
		<iframe src="sim?stage=int-5&format=lines" width="800" height="540"></iframe>
</div>

I to je to! To je način da uspešno izvedemo prinudno sletanje ovog aviona. 

I to je način na koji pobeđujemo COVID-19.

...

Ali šta ako stvari *i dalje* idu po zlu? Stvari su već otišle u vrlo pogrešnu stranu. To je strah, i to je dobro! Strah nam daje snagu da smišljamo *rezervne planove*.

Pesimista pravi padobran.

###Scenario 4+: Maske za sve, leto, ciklično otvaranje i zatvaranje

Šta ako je R<sub>0</sub> mnogo veće nego što smo mi mislili, i pored svih intervencija, i blagog distanciranja, mi *i dalje* ne uspevamo da dobijemo R < 1?

Setimo se, iako ne možemo da dođemo do R < 1, smanjenjem R smanjujemo ukupan broj slučajeva, što znači da spasavamo živote. Ali i dalje, R < 1 je idealno, tako da evo na koje još dodatne načine možemo da utičemo na smanjenje R:


**Maske Za Sve:**

*„Čekaj,“* možda ćete pitati, *„Zar se nije pokazalo da maske ne mogu potpuno da zaštite od zaraze?“*

I bili biste u pravu. Maske ne mogu da nas zaštite od infekcije[^incoming]... one štite *druge* od nas.

[^incoming]: „Nijedna od ovih hirurških maski nema adekvatan učinak filtera, kao što ni ne prijanjaju licu u dovoljnoj meri, da bi se mogle klasifikovati kao respiratorna zaštita.“ [Tara Oberg i Lisa M. Brosseau](https://www.sciencedirect.com/science/article/pii/S0196655307007742)

[^outgoing]: „Ukupno smanjenje od 3.4 puta [70% smanjenja] u broju čestica aerosoli koje je primećeno, zajedno sa skoro potpunom eliminacijom velikih kapljica koje je demonstrirano od strane by Johnson et al., sugeriše da bi nošenje hirurške maske od strane zaraženog lica imalo klinički značajan uticaj na prenošenje zaraze.“ [Milton DK, Fabian MP, Cowling BJ, Grantham ML, McDevitt JJ](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3591312/)

[^homemade]: [Davies, A., Thompson, K., Giri, K., Kafatos, G., Walker, J., i Bennett, A](https://www.cambridge.org/core/journals/disaster-medicine-and-public-health-preparedness/article/testing-the-efficacy-of-homemade-masks-would-they-protect-in-an-influenza-pandemic/0921A05A69A9419C862FA2F35F819D55) Pogledajte Tabelu 1: 100% pamučna majica ima oko 2/3 efikasnost filtriranja u poređenju sa hirurškom maskom, za dve vrste testiranih bakterijskih aerosoli.

![](pics/maskssrb.png)

Ako hoćemo da pričamo u brojevima: kada *inficirana osoba* nosi hiruršku masku ona smanjuju izbacivanje kapljica za do 70% (a one mogu sadržati viruse gripa i prehlade).[^outgoing] Smanjivanje prenošenja za 70% ima *sličan* efekat kao što ima i zatvaranje gradova!

No svejedno, mi i dalje ne znamo zasigurno koji je uticaj maski na *konkretno* COVID-19 zarazu. U nauci se objavljuju jedino rezultati ako ste bar 95% sigurni u njih. (...ok, barem bi trebalo da je tako.[^replication]) Maske, bar 1. maja 2020, su manje od „95% sigurne“.

[^replication]: Svi pravi naučnici koji su pročitali poslednju rečenicu su se upravo sarkastično nasmejali. Pogledajte: [p-hacking](https://en.wikipedia.org/wiki/Data_dredging), [kriza repreducibilnosti](https://en.wikipedia.org/wiki/Replication_crisis))


U svakom slučaju, pandemija je kao poker. **Ako se kladite samo kad se 95% sigurni, izgubićete sve što imate.** Kao što je skorašnji članak na temu maski u Britanskom medicinskom časopisu primetio[^precautionary], mi *moramo* da pravimo analizu potencijalnih uloga i dobitaka i u nesigurnim vremenima.

[^precautionary]: „Vreme je da primenimo princip predostrožnosti.“ [Trisha Greenhalgh et al \[PDF\]](https://www.bmj.com/content/bmj/369/bmj.m1435.full.pdf)

Ulog: Ako koristimo ručno pravljene platnene maske (koje su ~2/3 efektivne u odnosu na hirurške maske[^homemade]), to je super jeftino. Ako koristimo hirurške maske, to je skuplje, ali i dalje prilično jeftino.

Dobitak: Čak i ako je šansa 50% da hirurške maske smanje prenošenje sa 0% na 70%, „očekivana vrednost“ je i dalje 35%, što je kao da smo uveli polu-policijski čas! Stoga, hajde da probamo da procenimo da hirurške maske smanjuju R za 35%, umanjeno da odrazi nesigurnost. (Kao i u prethodnom slučaju, možete da se igrate i vidite kako se menjaju ishodi ako menjate parametre pomeranjem klizača.)

<div class="sim">
		<iframe src="sim?stage=int-6a&format=calc" width="285" height="380"></iframe>
</div>

(Ostali razlozi za i protiv maski:[^mask_args])

[^mask_args]: **„Mi moramo da čuvamo zalihe za bolnice.“** *Apsolutno se slažem.* Ali to je u stvari argument za povećanje proizvodnje maski, a ne čuvanja za rezerve. U međuvremenu, možemo da pravimo tekstilne maske.

	**„Teško je da se pravilno nose.“** Takođe je teško da se peru ruke u skladu sa preporukama Svetske Zdravstvene Organizacije - ozbiljno, "Korak 3) desni dlan preko levog dorsuma"?!?!?! – ali mi i dalje preporučujemo pranje ruku, jer *nesavršeno* je i dalje bolje nego ništa.
	
	**„Ljudi će postati opušteniji sa pranjem ruku i fizičkim distanciranjem.“**  Naravno, i pojasevi za vezivanje čine da ljudi počnu da ignorišu stop znak, i konac za zube čini da ljudi jedu kamenje. Za ozbiljno, mi bismo zapravo to koristili kao kontra-argument - maske su ljudima *konstantni* podsetnik da treba da budu pažljivi - a uzgred, u Istočnoj Aziji maske su i simbol solidarnosti!

*Samo* maskama nećemo dostići R < 1. Ali ako pranje ruku i „Testiranje, praćenje, izolovanje“ spuste vrednost do R = 1.10, i na to dodamo da samo trećina ljudi nosi maske,  dostići ćemo R < 1 i virus je zauzdan!

**Leto:**

OK, ovo nije „intervencija“ koju možemo kontrolisati, ali će pomoći! Neki mediji su izveštavali da leto neće učiniti ništa koronavirusu. Oni su samo delimično u pravu: sâmo leto neće pomoći da se dostigne R < 1, ali *hoće* umanjiti R.

U slučaju COVID-19, svaki dodatni 1°C snižava R za 1.2%.[^heat] Razlika u stepenima između leta i zime u Njujorku je 26°C[^nyc_heat], tako da će kao posledica letnjih vrelina vrednost R opasti za ~31%. Što se tiče situacije u Srbiji, razlika između zimskog i letnjeg perioda u protekloj godini iznosi 19.1°C, čime dolazimo do procene da će R opasti za ~23%. Ako pogledamo razliku temperatura između januara 2020. godine i jula 2019. godine, u Beogradu je ona iznosila 22.3°C (R se smanjuje za ~27%), dok je na Zlatiboru 19.2°C (R je manje za ~23%). Prim. prev. [^rhzm]

[^heat]: „Povećanje temperature za jedan stepen Celzijusove skale [...] smanjuje R za 0.0225“ i „Prosečna vrednost R za ovih 100 gradova je 1.83“. 0.0225 ÷ 1.83 = ~1.2%. [Wang, Jingyuan i Tang, Ke and Feng, Kai and Lv, Weifeng](https://papers.ssrn.com/sol3/Papers.cfm?abstract_id=3551767)

[^nyc_heat]: Tokom 2019. godine u Centralnom parku, tokom najtoplijeg meseca (jul) bilo je 79.6°F, a tokom najhladnijeg meseca (januar) bilo je 32.5°F. Razlika je 47.1°F, odnosno ~26°C. [PDF sa Weather.gov](https://www.weather.gov/media/okx/Climate/CentralPark/monthlyannualtemp.pdf)

[^rhzm]: Po podacima Republičkog hidrometeorološkog zavoda Srbije za [zimu 2019/20. godine](http://www.hidmet.gov.rs/podaci/meteorologija/ciril/zima.pdf), [leto 2019. godine](http://www.hidmet.gov.rs/podaci/meteorologija/ciril/leto.pdf), [januar 2020. godine](http://www.hidmet.gov.rs/podaci/meteorologija/ciril/Januar.pdf) i [jul 2019. godine](http://www.hidmet.gov.rs/podaci/meteorologija/ciril/Jul.pdf).

<div class="sim">
		<iframe src="sim?stage=int-6b&format=calc" width="285" height="220"></iframe>
</div>

Leto sâmo po sebi neće učiniti da je R < 1, ali kako imamo ograničene resurse, možemo umanjiti neke od intervencija tokom leta – tako da bismo mogli da ih *povećamo* tokom zime.

**"Ciklično" zatvaranje:**

I ako sve to *i dalje* nije dovoljno da dođemo do R < 1... možemo se ponovo zatvoriti.

Ali nećemo morati da prolazimo kroz ciklus 2 meseca u zatvorenom / 1 mesec na otvorenom, iznova i iznova! Kako se R smanjuje, biće nam potreban jedan ili dva "ciklična" zatvaranja pre nego što se pojavi vakcina. (U Singapuru je moralo nedavno da dođe do ovoga, "iako" su uspevali da kontrolišu COVID-19 tokom prethodna 4 meseca. Ovo nije neuspeh: ovo *je* potrebno za uspeh.)

Evo simulacije „osnovnog“ scenarija:

1. Zatvaranje, praćeno
2. Umerenom količinom politika povećane higijene i „Testiranje, Praćenje, Izolovanje“, sa blagom količinom „Maske za sve“, a zatim...
3. Još jedan „ciklus“ zatvaranja pre nego što vakcina postane dostupna.

<div class="sim">
		<iframe src="sim?stage=int-7&format=lines&height=620" width="800" height="620"></iframe>
</div>

Da ne pominjemo sve *ostale* intervencije koje možemmo primeniti da dodatno snizimo R:

* Restrikcije putovanja uz karantin putnika
* Kontrola temperature u tržnim centrima i školama
* Detaljno čišćenje javnih prostora
* [Prelazak na nogovanje umesto rukovanja](https://twitter.com/V_actually/status/1233785527788285953)
* I sve ostalo što će ljudska genijalnost iznedriti

. . .

Nadamo se da vam ovi planovi daju nadu. 

**Čak i u pesimističnom scenariju, *moguće* je pobediti COVID-19, štiteći našu psihičku i finansijsku stabilnost.** Koristeći zatvaranja kao „dugme za reset“, čuvajući R < 1 sa izolacijom slučajeva + prateći kontakte uz zaštitu privatnosti + *barem* platnenim maskama za sve... i život se može vratiti u nešto skoro-normalno!

Sigurno, suve su vam ruke od čestog pranja. Ali, imaćete šansu da pozovete simpatiju u prodavnicu stripova! Imaćete šansu da odete sa prijateljima u bioskop i gledate poslednji holivudski blokbaster. Imaćete šansu da posmatrate ljude u biblioteci, uživajući u činjenici da ljudi nastavljaju sa sitnicama koje *život znače*.

Čak i u najgorem slučaju... život opstaje.

A sada, hajde da isplaniramo neke od *gorih* najgorih scenarija. Sletanje na vodu, pripremite svoje prsluke za spasavanje, i molimo pratite svetla do izlaza u slučaju opasnosti:

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Narednih nekoliko godina</div>
    </div>
</div>

Dobili ste COVID-19 i oporavili ste se. Ili, primili ste vakcinu protiv COVID-19. U svakom slučaju, sada ste imuni...

...*koliko dugo?*

* COVID-19 je najsličniji SARS-u, koji oporavljenima daje dvogodišnji imunitet.[^SARSimmunity]
* Koronavirusi koji prouzrokuju tipičnu prehladu daju vam imunitet od 8 meseci.[^coldimmunity]
* Postoje neki izveštaji o ljudima koji su se oporavili od COVID-19, pa su posle bili ponovo pozitivni na COVID-19 testu, ali je nejasno da li su ovo u stvari greške u testiranju.[^unclear]
* Jedna *još-uvek-nerecenzirana* studija na majmunima je pokazala da COVID-19 imunitet traje barem 28 dana.[^monkeys]

Ali u slučaju COVID-19 *i ljudi*, prvog maja 2020., „koliko dugo traje imunitet“ je još uvek velika nepoznanica.

[^SARSimmunity]: „SARS antitela su održana u proseku 2 godine [...] Stoga, SARS pacijenti mogu ponovo postati podložni infekciji ≥3 godine nakon inicijalne infekcije.“ [Wu LP, Wang NC, Chang YH, et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2851497/) „Nažalost“ nikad nećemo saznati koliko dugo bi SARS imunitet trajao, s obzirom da je suzbijen tako brzo.

[^coldimmunity]: „Nismo pronašli značajnu razliku između verovatnoće pozitivnog testa bar jednom i verovatnoće povratka beta-koronavirusa HKU1 i OC43 nakon 34 nedelje posle priključivanja studiji/prve infekcije.“ [Marta Galanti i Jeffrey Shaman (PDF)](http://www.columbia.edu/~jls106/galanti_shaman_ms_supp.pdf)

[^unclear]: „Jednom kada osoba pobedi virus, delovi virusa opstaju još neko vreme. Oni ne mogu izazvati infekciju, ali mogu izazvati pozitivan ishod na testu.“ [iz STAT News od Andrew Joseph](https://www.statnews.com/2020/04/20/everything-we-know-about-coronavirus-immunity-and-antibodies-and-plenty-we-still-dont/)

[^monkeys]: Iz [Bao et al.](https://www.biorxiv.org/content/10.1101/2020.03.13.990226v1.abstract) *Napomena: Ovaj članak još uvek nije prošao recenziju.* Takođe, da istaknemo: oni su jedino re-testirali nakon 28 dana. 

Za ove simulacije, pretpostavimo da imunitet traje jednu godinu.
**Ova simulacija počinje sa 100% <span class="nowrap"><icon r></icon>,</span>** čiji broj eksponencijalno opada, jer oni prelaze u zdrave  bez imuniteta <span class="nowrap"><icon s></icon></span>, kroz *u proseku* 1 godinu :

<div class="sim">
		<iframe src="sim?stage=yrs-1&format=lines&height=600" width="800" height="600"></iframe>
</div>

Povratak eksponencijalnog pada!

Ovo je **SEIRS model**. Drugo „S“ u nazivu označava da postoji povratak u <icon s></icon> (eng. **S**usceptible) - podložno stanje ponovo.

![](pics/seirssrb.png)

Hajde da simuliramo COVID-19 širenje, tokom 10 godina, bez intervencija... *pretpostavljajući da imunitet traje samo godinu dana:*

<div class="sim">
		<iframe src="sim?stage=yrs-2&format=lines&height=600" width="800" height="600"></iframe>
</div>

U prethodnim simulacijama imali smo samo *jedan* maksimum kada smo premašivali kapacitete intenzivne nege. Sada ih ima više, *i* broj <icon i></icon> slučajeva je *konstantno* na granici kapaciteta intenzivne nege. (...koje smo, setite se, uzeli da su *trostruko* veće nego u realnosti.)

R = 1, je **endemija.**

Na sreću, leto smanjuje R, što će poboljšati situaciju:

<div class="sim">
		<iframe src="sim?stage=yrs-3&format=lines&height=640" width="800" height="640"></iframe>
</div>

Ups.

Kontraintuitivno, leto čini da se skokovi u broju slučajeva pogoršavaju *i* vraćaju! To je zato što leto smanji broj novih <span class="nowrap"><icon i></icon>,</span> ali to takođe smanji i broj imunih <span class="nowrap"><icon r></icon>.</span> To znači da se imunitet umanji tokom leta, *stvarajući* tako intenzivnija ponavljanja porasta zaraženih tokom zimskih perioda.

Na sreću, rešenje za ovo je prilično zdravorazumsko – vakcinacija svake jeseni/zime, kao što to radimo sa vakcinama protiv gripa:

**(Nakon puštanja snimka, probajte vaše simulacije sa različitim kampanjama vakcinacije! Setite se da možete pauzirati i nastaviti simulaciju u bilo kom trenutku.)**

<div class="sim">
		<iframe src="sim?stage=yrs-4&format=lines" width="800" height="540"></iframe>
</div>

Ali imamo i jedno strašnije pitanje:

Šta ako budemo čekali na vakcinu *godinama*? Ili *zauvek?*

**Da budemo jasni: ovo je skoro neverovatno.** Većina epidemiologa očekuje vakcinu za godinu do dve. Tačno je da ne postoji vakcina ni za jedan od koronavirusa, ali to je zato što je SARS suzbijen brzo, a vakcina protiv tipične prehlade nije smatrana isplativom investicijom. 

Međutim, istraživači zaraznih bolesti su izrazili sledeća strahovanja: Šta ako ne možemo da napravimo dovoljno vakcina?[^vax_enough] Šta ako ubrzamo proces po cenu bezbednosti?[^vax_safe]

[^vax_enough]: „Ako stigne vakcina protiv koronavirusa, da li svet može da ih napravi dovoljno?“ [autorka Roxanne Khamsi, u časopisu Nature](https://www.nature.com/articles/d41586-020-01063-8)

[^vax_safe]: „Ne žurite sa upotrebom COVID-19 vakcina i lekova bez dovoljnog broja bezbednosnih provera.“ [autor Shibo Jiang, u časopisu Nature](https://www.nature.com/articles/d41586-020-00751-9)

Čak i u scenariju iz noćne more u kojem nema vakcine, i dalje postoje tri izlaza. Slede od najviše do najmanje strašnih:

1) Ponavljanje ciklusa intervencija za dostizanje R < 1, do postizanja „prirodnog imuniteta krda“. (Upozorenje: ovo će rezultirati u velikom broju smrtnih slučajeva i oštećenih pluća. *Plus* neće raditi ako imunitet ne potraje.)

2) Ponavljanje R < 1 intervencija zauvek. Praćenje kontakata i nošenje maski nam prosto postane nova svakodnevnica u post-COVID-19 svetu, kao što su testovi na seksualno prenosive infekcije i korišćenje kondoma postali nova norma u post-HIV svetu.

3) Ponavljanje R < 1 intervencija dok ne razvijemo tretmane koji čine da COVID-19 mnogo ređe zahteva intenzivnu negu. (Što bi *svakako* trebalo da radimo!) Smanjivanje potreba za intenzivnom negom sa faktorom 10x je isto što i povećanje kapaciteta u intenzivnoj nezi za faktor od 10x:

**Evo simulacije *bez* trajnog imuniteta, *bez* vakcine, pa čak i bez bilo kakvih intervencija - samo sa sporim povećavanjem spremnosti da preživimo nove talase:**

<div class="sim">
		<iframe src="sim?stage=yrs-5&format=lines" width="800" height="540"></iframe>
</div>

Čak i u ovom *najgorem* od najgorih slučajeva... život opstaje.

. . .

Možda želite da preispitate naše pretpostavke i probate drugačije vrednosti R<sub>0</sub> i ostalih parametara? Ili želite da simulirate *svoju* kombinaciju intervencija?

**Ovde je simulacija, u kojoj je menjanje *svega* dostupno (skrolovanjem ćete videti sve kontrole). Simulirajte i igrajte se dok ne zadovoljite znatiželju:**

<div class="sim">
		<iframe src="sim?stage=SB&format=sb" width="800" height="540"></iframe>
</div>

Ovaj osnovni „epidemiološki simulator letenja“ nas je naučio dosta toga. Dozvolio nam je da odgovorimo na mnoga pitanja o prethodnim mesecima, budućim mesecima i budućim godinama.

Konačno, hajde da se vratimo na...

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Sada</div>
    </div>
</div>

Avion je potonuo. Uhvatili smo se za čamce za spasavanje. Vreme je da pronađemo kopno.[^dry_land]

[^dry_land]: Metafora kopna [iz članka autora Marc Lipsitch i Yonatan Grad, u STAT News](https://www.statnews.com/2020/04/01/navigating-covid-19-pandemic/)

Timovi epidemiologa i donosioca odluka ([levih uverenja](https://www.americanprogress.org/issues/healthcare/news/2020/04/03/482613/national-state-plan-end-coronavirus-crisis/), [desnih uverenja](https://www.aei.org/research-products/report/national-coronavirus-response-a-road-map-to-reopening/ ), i [zajedničkim snagama](https://ethics.harvard.edu/covid-roadmap)) došli su do koncenzusa o tome kako pobediti COVID-19, čuvajući naše živote *i* slobode.

U nastavku je skica ideje, sa nekim (manje-usaglašenim) rezervnim planovima:

![](pics/plansrb.png)

Šta ovo znači za TEBE, sada?

**Za sve:** Poštuj mere lokalnih i nacionalnih vlasti tako da svi možemo izaći iz Faze I što je pre moguće. Nastavi da pereš ruke. Pravi svoje maske. Preuzmi aplikaciju za praćenje kontakata koja *poštuje privatnost* kada postane dostupna sledećeg meseca. Ostani zdravo, fizički i mentalno! I piši lokalnim donosiocima odluka da se uozbilje i deluju.

**Za donosioce odluka:** Donesite zakone da podržite osobe koje moraju da se samoizoluju/koji su u karantinu. Zaposlite više osoba da se bave praćenjem kontakata, *podržite* ih adekvatnim aplikacijama koje prate kontakte i poštuju privatnost. Usmerite više finansija u stvari koje bi trebalo da pravimo.

**Za stvaraoce:** Pravite testove. Pravite respiratore. Pravite opremu za ličnu zaštitu za bolnice. Pravite testove. Pravite maske. Pravite aplikacije. Pravite antivirotike, profilaktike, i ostale lekove i tretmane koji nisu vakcine. Pravite vakcine. Pravite testove. Pravite testove. Pravite testove. Stvarajte nadu. 

Ne umanjujte strah da biste probudili nadu. Naš strah treba da se *udruži* sa nadom, kao što su izumitelji aviona i padobrana. Pripremanje za strašne budućnosti je takođe i način na koji *stvaramo* budućnost kojoj se nadamo.

Jedino čega se treba plašiti je ideja da se jedino treba plašiti sâmog straha.
