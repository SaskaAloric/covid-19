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
        <div>The Next Few Months</div>
    </div>
</div>

...moglo je biti gore. Evo paralelnog univerzuma koji smo zaobišli:

###Scenario 0: Ne učiniti apsolutno ništa

Otprilike jednoj od 20 osoba inficiranih koronom potrebna je intenzivna nega.[^icu_covid] U bogatim zemljama kao što su SAD, postoji jedno mesto na intenzivnoj nezi na 3400 stanovnika.[^icu_us] Stoga, SAD može da podnese da 20 ljudi na svakih 3400 bude *istovremeno* zaraženo – ili 0.6% populacije.

[^icu_covid]: ["Procenat COVID-19 slučajeva u Sjedinjenim Američkim Državama od 12. februara do 16. marta 2020. godine kojima je bila potrebna intenzivna nega, grupisano po starosti"](https://www.statista.com/statistics/1105420/covid-icu-admission-rates-us-by-age-group/). Između 4.9% i 11.5% od *svih* COVID-19 slučajeva zahtevalo je intenzivnu negu. Velikodušno smo odabrali minimalnu vrednost, t. 5% odnosno 1 od 20. Obratite pažnju da je ova vrednost specifična u odnosu na starosnu strukturu Sjedinjenih Američkih Država, i može biti veća za države sa starijom populacijom, ili manja za države sa mlađom populacijom.

[^icu_us]: “Broj mesta na intenzivnoj nezi = 96,596”. Izvor [the Society of Critical Care Medicine](https://sccm.org/Blog/March-2020/United-States-Resource-Availability-for-COVID-19) Broj stanovnika u SAD bio je 328,200,000 u 2019. godini, stoga 96,596 naspram 328,200,000 = približno je 1 na 3400. 

Even if we *more than tripled* that capacity to 2%, here's what would've happened *if we did absolutely nothing:*

<div class="sim">
		<iframe src="sim?stage=int-1&format=lines" width="800" height="540"></iframe>
</div>

Not good.

That's what [the March 16 Imperial College report](http://www.imperial.ac.uk/mrc-global-infectious-disease-analysis/covid-19/report-9-impact-of-npis-on-covid-19/) found: do nothing, and we run out of ICUs, with more than 80% of the population getting infected. 
(remember: total cases *overshoots* herd immunity)

Even if only 0.5% of infected die – a generous assumption when there's no more ICUs – in a large country like the US, with 300 million people, 0.5% of 80% of 300 million = still 1.2 million dead... *IF we did nothing.*

(Lots of news & social media reported "80% will be infected" *without* "IF WE DO NOTHING". Fear was channelled into clicks, not understanding. *Sigh.*)

###Scenario 1: Flatten The Curve / Herd Immunity

The "Flatten The Curve" plan was touted by every public health organization, while the United Kingdom's original "herd immunity" plan was universally booed. They were *the same plan.* The UK just communicated theirs poorly.[^yong]

[^yong]: “He says that the actual goal is the same as that of other countries: flatten the curve by staggering the onset of infections. As a consequence, the nation may achieve herd immunity; it’s a side effect, not an aim. [...] The government’s actual coronavirus action plan, available online, doesn’t mention herd immunity at all.”
    
    From a [The Atlantic article by Ed Yong](https://www.theatlantic.com/health/archive/2020/03/coronavirus-pandemic-herd-immunity-uk-boris-johnson/608065/)

Both plans, though, had a literally fatal flaw.

First, let's look at the two main ways to "flatten the curve": handwashing & physical distancing.

Increased handwashing cuts flus & colds in high-income countries by ~25%[^handwashing], while the city-wide lockdown in London cut close contacts by ~70%[^london]. So, let's assume handwashing can reduce R by *up to* 25%, and distancing can reduce R by *up to* 70%:

[^handwashing]: “All eight eligible studies reported that handwashing lowered risks of respiratory infection, with risk reductions ranging from 6% to 44% [pooled value 24% (95% CI 6–40%)].” We rounded up the pooled value to 25% in these simulations for simplicity. [Rabie, T. and Curtis, V.](https://onlinelibrary.wiley.com/doi/full/10.1111/j.1365-3156.2006.01568.x) Note: as this meta-analysis points out, the quality of studies for handwashing (at least in high-income countries) are awful.

[^london]: “We found a 73% reduction in the average daily number of contacts observed per participant. This would be sufficient to reduce R0 from a value from 2.6 before the lockdown to 0.62 (0.37 - 0.89) during the lockdown”. We rounded it down to 70% in these simulations for simplicity. [Jarvis and Zandvoort et al](https://cmmid.github.io/topics/covid19/comix-impact-of-physical-distance-measures-on-transmission-in-the-UK.html)

**Play with this calculator to see how % of <span class="nowrap">non-<icon s></icon>,</span> handwashing, and distancing reduce R:** (this calculator visualizes their *relative* effects, which is why increasing one *looks* like it decreases the effect of the others.[^log_caveat])

[^log_caveat]: This distortion would go away if we plotted R on a logarithmic scale... but then we'd have to explain *logarithmic scales.*

<div class="sim">
		<iframe src="sim?stage=int-2a&format=calc" width="285" height="260"></iframe>
</div>

Now, let's simulate what happens to a COVID-19 epidemic if, starting March 2020, we had increased handwashing but only *mild* physical distancing – so that R is lower, but still above 1:

<div class="sim">
		<iframe src="sim?stage=int-2&format=lines" width="800" height="540"></iframe>
</div>

Three notes:

1. This *reduces* total cases! **Even if you don't get R < 1, reducing R still saves lives, by reducing the 'overshoot' above herd immunity.** Lots of folks think "Flatten The Curve" spreads out cases without reducing the total. This is impossible in *any* Epidemiology 101 model. But because the news reported "80%+ will be infected" as inevitable, folks thought total cases will be the same no matter what. *Sigh.*

2. Due to the extra interventions, current cases peak *before* herd immunity is reached. In fact, in this simulation, total cases only overshoots *a tiny bit* above herd immunity – the UK's plan! At that point, R < 1, you can let go of all other interventions, and COVID-19 stays contained! Well, except for one problem...

3. You still run out of ICUs. For several months. (and remember, we *already* tripled ICUs for these simulations)

That was the other finding of the March 16 Imperial College report, which convinced the UK to abandon its original plan. Any attempt at **mitigation** (reduce R, but R > 1) will fail. The only way out is **suppression** (reduce R so that R < 1).

![](pics/mitigation_vs_suppressionsrb.png)

That is, don't merely "flatten" the curve, *crush* the curve. For example, with a...

###Scenario 2: Months-Long Lockdown

Let's see what happens if we *crush* the curve with a 5-month lockdown, reduce <icon i></icon> to nearly nothing, then finally – *finally* – return to normal life:

<div class="sim">
		<iframe src="sim?stage=int-3&format=lines" width="800" height="540"></iframe>
</div>

Oh.

This is the "second wave" everyone's talking about. As soon as we remove the lockdown, we get R > 1 again. So, a single leftover <icon i></icon> (or imported <span class="nowrap"><icon i></icon>)</span> can cause a spike in cases that's almost as bad as if we'd done Scenario 0: Absolutely Nothing.

**A lockdown isn't a cure, it's just a restart.**

So, what, do we just lockdown again & again?

###Scenario 3: Intermittent Lockdown

This solution was first suggested by the March 16 Imperial College report, and later again by a Harvard paper.[^lockdown_harvard]

[^lockdown_harvard]: “Absent other interventions, a key metric for the success of social distancing is whether critical care capacities are exceeded. To avoid this, prolonged or intermittent social distancing may be necessary into 2022.” [Kissler and Tedijanto et al](https://science.sciencemag.org/content/early/2020/04/14/science.abb5793)

**Here's a simulation:** (After playing the "recorded scenario", you can try simulating your *own* lockdown schedule, by changing the sliders *while* the simulation is running! Remember you can pause & continue the sim, and change the simulation speed)

<div class="sim">
		<iframe src="sim?stage=int-4&format=lines" width="800" height="540"></iframe>
</div>

This *would* keep cases below ICU capacity! And it's *much* better than an 18-month lockdown until a vaccine is available. We just need to... shut down for a few months, open up for a few months, and repeat until a vaccine is available. (And if there's no vaccine, repeat until herd immunity is reached... in 2022.)

Look, it's nice to draw a line saying "ICU capacity", but there's lots of important things we *can't* simulate here. Like:

**Mental Health:** Loneliness is one of the biggest risk factors for depression, anxiety, and suicide. And it's as associated with an early death as smoking 15 cigarettes a day.[^loneliness]

[^loneliness]: See [Figure 6 from Holt-Lunstad & Smith 2010](https://journals.sagepub.com/doi/abs/10.1177/1745691614568352). Of course, big disclaimer that they found a *correlation*. But unless you want to try randomly assigning people to be lonely for life, observational evidence is all you're gonna get.

**Financial Health:** "What about the economy" sounds like you care more about dollars than lives, but "the economy" isn't just stocks: it's people's ability to provide food & shelter for their loved ones, to invest in their kids' futures, and enjoy arts, foods, videogames – the stuff that makes life worth living. And besides, poverty *itself* has horrible impacts on mental and physical health.

Not saying we *shouldn't* lock down again! We'll look at "circuit breaker" lockdowns later. Still, it's not ideal.

But wait... haven't Taiwan and South Korea *already* contained COVID-19? For 4 whole months, *without* long-term lockdowns?

How?

###Scenario 4: Test, Trace, Isolate

*"Sure, we \*could've\* done what Taiwan & South Korea did at the start, but it's too late now. We missed the start."*

But that's exactly it! “A lockdown isn't a cure, it's just a restart”... **and a fresh start is what we need.**

To understand how Taiwan & South Korea contained COVID-19, we need to understand the exact timeline of a typical COVID-19 infection[^timeline]:

[^timeline]: **3 days on average to infectiousness:** “Assuming an incubation period distribution of mean 5.2 days from a separate study of early COVID-19 cases, we inferred that infectiousness started from 2.3 days (95% CI, 0.8–3.0 days) before symptom onset” (translation: Assuming symptoms start at 5 days, infectiousness starts 2 days before = Infectiousness starts at 3 days) [He, X., Lau, E.H.Y., Wu, P. et al.](https://www.nature.com/articles/s41591-020-0869-5)  
    
    **4 days on average to infecting someone else:** “The mean [serial] interval was 3.96 days (95% CI 3.53–4.39 days)” [Du Z, Xu X, Wu Y, Wang L, Cowling BJ, Ancel Meyers L](https://wwwnc.cdc.gov/eid/article/26/6/20-0357_article)
    
    **5 days on average to feeling symptoms:** “The median incubation period was estimated to be 5.1 days (95% CI, 4.5 to 5.8 days)” [Lauer SA, Grantz KH, Bi Q, et al](https://annals.org/AIM/FULLARTICLE/2762808/INCUBATION-PERIOD-CORONAVIRUS-DISEASE-2019-COVID-19-FROM-PUBLICLY-REPORTED)

![](pics/timeline1srb.png)

If cases only self-isolate when they know they're sick (that is, they feel symptoms), the virus can still spread:

![](pics/timeline2srb.png)

And in fact, 44% of all transmissions are like this: *pre*-symptomatic! [^pre_symp]

[^pre_symp]: “We estimated that 44% (95% confidence interval, 25–69%) of secondary cases were infected during the index cases’ presymptomatic stage” [He, X., Lau, E.H.Y., Wu, P. et al](https://www.nature.com/articles/s41591-020-0869-5)

But, if we find *and quarantine* a symptomatic case's recent close contacts... we stop the spread, by staying one step ahead!

![](pics/timeline3srb.png)

This is called **contact tracing**. It's an old idea, was used at an unprecedented scale to contain Ebola[^ebola], and now it's core part of how Taiwan & South Korea are containing COVID-19!

[^ebola]: “Contact tracing was a critical intervention in Liberia and represented one of the largest contact tracing efforts during an epidemic in history.” [Swanson KC, Altare C, Wesseh CS, et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6152989/)

(It also lets us use our limited tests more efficiently, to find pre-symptomatic <span class="nowrap"><icon i></icon>s</span> without needing to test almost everyone.)

Traditionally, contacts are found with in-person interviews, but those *alone* are too slow for COVID-19's ~48 hour window. That's why contact tracers need help, and be supported by – *NOT* replaced by – contact tracing apps.

(This idea didn't come from "techies": using an app to fight COVID-19 was first proposed by [a team of Oxford epidemiologists](https://science.sciencemag.org/content/early/2020/04/09/science.abb6936).)

Wait, apps that trace who you've been in contact with?... Does that mean giving up privacy, giving in to Big Brother?

Heck no! **[DP-3T](https://github.com/DP-3T/documents#decentralized-privacy-preserving-proximity-tracing)**, a team of epidemiologists & cryptographers (including one of us, Marcel Salathé) is *already* making a contact tracing app – with code available to the public – that reveals **no info about your identity, location, who your contacts are, or even *how many contacts* you've had.**

Here's how it works:

![](pics/dp3tsrb.png)

([Here's the full comic](https://ncase.me/contact-tracing/). Details about "pranking"/false positives/etc in footnote:[^dp3t_details])

[^dp3t_details]: To prevent "pranking" (people falsely claiming to be infected), the DP-3T Protocol requires that the hospital first give you a One-Time Passcode that lets you upload your messages.
    
    False positives are a problem in both manual & digital contact tracing. Still, we can reduce false positives in 2 ways: 1) By notifying Bobs only if they heard, say, 30+ min worth of messages, not just one message in passing. And 2) If the app *does* think Bob's been exposed, it can refer Bob to a *manual* contact tracer, for an in-depth follow-up interview.
    
    For other issues like data bandwidth, source integrity, and other security issues, check out [the open-source DP-3T whitepapers!](https://github.com/DP-3T/documents#decentralized-privacy-preserving-proximity-tracing)

Along with similar teams like TCN Protocol[^tcn] and MIT PACT[^pact], they've inspired Apple & Google to bake privacy-first contact tracing directly into Android/iOS.[^gapple] (Don't trust Google/Apple? Good! The beauty of this system is it doesn't *need* trust!) Soon, your local public health agency may ask you to download an app. If it's privacy-first with publicly-available code, please do!

[^tcn]: [Temporary Contact Numbers, a decentralized, privacy-first contact tracing protocol](https://github.com/TCNCoalition/TCN#tcn-protocol)

[^pact]: [PACT: Private Automated Contact Tracing](https://pact.mit.edu/)

[^gapple]: [Apple and Google partner on COVID-19 contact tracing technology ](https://www.apple.com/ca/newsroom/2020/04/apple-and-google-partner-on-covid-19-contact-tracing-technology/). Note they're not making the apps *themselves*, just creating the systems that will *support* those apps.

But what about folks without smartphones? Or infections through doorknobs? Or "true" asymptomatic cases? Contact tracing apps can't catch all transmissions... *and that's okay!* We don't need to catch *all* transmissions, just 60%+ to get R < 1.

(Footnote rant about the confusion between pre-symptomatic vs "true" asymptomatic – "true" asymptomatics are rare:[^rant])

[^rant]: Lots of news reports – and honestly, many research papers – did not distinguish between "cases who showed no symptoms when we tested them" (pre-symptomatic) and "cases who showed no symptoms *ever*" (true asymptomatic). The only way you could tell the difference is by following up with cases later.
   
    Which is what [this study](https://wwwnc.cdc.gov/eid/article/26/8/20-1274_article) did. (Disclaimer: "Early release articles are not considered as final versions.") In a call center in South Korea that had a COVID-19 outbreak, "only 4 (1.9%) remained asymptomatic within 14 days of quarantine, and none of their household contacts acquired secondary infections."
    
    So that means "true asymptomatics" are rare, and catching the disease from a true asymptomatic may be even rarer!

Isolating *symptomatic* cases would reduce R by up to 40%, and quarantining their *pre/a-symptomatic* contacts would reduce R by up to 50%[^oxford]:

[^oxford]: From the same Oxford study that first recommended apps to fight COVID-19: [Luca Ferretti & Chris Wymant et al](https://science.sciencemag.org/content/early/2020/04/09/science.abb6936/tab-figures-data) See Figure 2. Assuming R<sub>0</sub> = 2.0, they found that:    
    
    * Symptomatics contribute R = 0.8 (40%)
    * Pre-symptomatics contribute R = 0.9 (45%)
    * Asymptomatics contribute R = 0.1 (5%, though their model has uncertainty and it could be much lower)
    * Environmental stuff like doorknobs contribute R = 0.2 (10%)

    And add up the pre- & a-symptomatic contacts (45% + 5%) and you get 50% of R!

<div class="sim">
		<iframe src="sim?stage=int-4a&format=calc" width="285" height="340"></iframe>
</div>

Thus, even without 100% contact quarantining, we can get R < 1 *without a lockdown!* Much better for our mental & financial health. (As for the cost to folks who have to self-isolate/quarantine, *governments should support them* – pay for the tests, job protection, subsidized paid leave, etc. Still way cheaper than intermittent lockdown.)

We then keep R < 1 until we have a vaccine, which turns susceptible <span class="nowrap"><icon s></icon>s</span> into immune <span class="nowrap"><icon r></icon>s.</span> Herd immunity, the *right* way:

<div class="sim">
		<iframe src="sim?stage=int-4b&format=calc" width="285" height="230"></iframe>
</div>

(Note: this calculator pretends the vaccines are 100% effective. Just remember that in reality, you'd have to compensate by vaccinating *more* than "herd immunity", to *actually* get herd immunity)

Okay, enough talk. Here's a simulation of:

1. A few-month lockdown, until we can...
2. Switch to "Test, Trace, Isolate" until we can...
3. Vaccinate enough people, which means...
4. We win.

<div class="sim">
		<iframe src="sim?stage=int-5&format=lines" width="800" height="540"></iframe>
</div>

So that's it! That's how we make an emergency landing on this plane.

That's how we beat COVID-19.

...

But what if things *still* go wrong? Things have gone horribly wrong already. That's fear, and that's good! Fear gives us energy to create *backup plans*.

The pessimist invents the parachute.

###Scenario 4+: Masks For All, Summer, Circuit Breakers

What if R<sub>0</sub> is way higher than we thought, and the above interventions, even with mild distancing, *still* aren't enough to get R < 1?

Remember, even if we can't get R < 1, reducing R still reduces the "overshoot" in total cases, thus saving lives. But still, R < 1 is the ideal, so here's a few other ways to reduce R:

**Masks For All:**

*"Wait,"* you might ask, *"I thought face masks don't stop you from getting sick?"*

You're right. Masks don't stop you from getting sick[^incoming]... they stop you from getting *others* sick.

[^incoming]: “None of these surgical masks exhibited adequate filter performance and facial fit characteristics to be considered respiratory protection devices.” [Tara Oberg & Lisa M. Brosseau](https://www.sciencedirect.com/science/article/pii/S0196655307007742)

[^outgoing]: “The overall 3.4 fold reduction [70% reduction] in aerosol copy numbers we observed combined with a nearly complete elimination of large droplet spray demonstrated by Johnson et al. suggests that surgical masks worn by infected persons could have a clinically significant impact on transmission.” [Milton DK, Fabian MP, Cowling BJ, Grantham ML, McDevitt JJ](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3591312/)

[^homemade]: [Davies, A., Thompson, K., Giri, K., Kafatos, G., Walker, J., & Bennett, A](https://www.cambridge.org/core/journals/disaster-medicine-and-public-health-preparedness/article/testing-the-efficacy-of-homemade-masks-would-they-protect-in-an-influenza-pandemic/0921A05A69A9419C862FA2F35F819D55) See Table 1: a 100% cotton T-shirt has around 2/3 the filtration efficiency as a surgical mask, for the two bacterial aerosols they tested.

![](pics/maskssrb.png)

To put a number on it: surgical masks *on the infectious person* reduce cold & flu viruses in aerosols by 70%.[^outgoing] Reducing transmissions by 70% would be as large an impact as a lockdown!

However, we don't know for sure the impact of masks on COVID-19 *specifically*. In science, one should only publish a finding if you're 95% sure of it. (...should.[^replication]) Masks, as of May 1st 2020, are less than "95% sure".

[^replication]: Any actual scientist who read that last sentence is probably laugh-crying right now. See: [p-hacking](https://en.wikipedia.org/wiki/Data_dredging), [the replication crisis](https://en.wikipedia.org/wiki/Replication_crisis))

However, pandemics are like poker. **Make bets only when you're 95% sure, and you'll lose everything at stake.** As a recent article on masks in the British Medical Journal notes,[^precautionary] we *have* to make cost/benefit analyses under uncertainty. Like so:

[^precautionary]: “It is time to apply the precautionary principle” [Trisha Greenhalgh et al \[PDF\]](https://www.bmj.com/content/bmj/369/bmj.m1435.full.pdf)

Cost: If homemade cloth masks (which are ~2/3 as effective as surgical masks[^homemade]), super cheap. If surgical masks, more expensive but still pretty cheap.

Benefit: Even if it's a 50–50 chance of surgical masks reducing transmission by 0% or 70%, the average "expected value" is still 35%, same as a half-lockdown! So let's guess-timate that surgical masks reduce R by up to 35%, discounted for our uncertainty. (Again, you can challenge our assumptions by turning the sliders up/down)

<div class="sim">
		<iframe src="sim?stage=int-6a&format=calc" width="285" height="380"></iframe>
</div>

(other arguments for/against masks:[^mask_args])

[^mask_args]: **"We need to save supplies for hospitals."** *Absolutely agreed.* But that's more of an argument for increasing mask production, not rationing. In the meantime, we can make cloth masks.

   **"They're hard to wear correctly."** It's also hard to wash your hands according to the WHO Guidelines – seriously, "Step 3) right palm over left dorsum"?! – but we still recommend handwashing, because imperfect is still better than nothing.
   
   **"It'll make people more reckless with handwashing & social distancing."** Sure, and safety belts make people ignore stop signs, and flossing makes people eat rocks. But seriously, we'd argue the opposite: masks are a *constant physical reminder* to be careful – and in East Asia, masks are also a symbol of solidarity!
    
    

Masks *alone* won't get R < 1. But if handwashing & "Test, Trace, Isolate" only gets us to R = 1.10, having just 1/3 of people wear masks would tip that over to R < 1, virus contained!

**Summer:**

Okay, this isn't an "intervention" we can control, but it will help! Some news outlets report that summer won't do anything to COVID-19. They're half right: summer won't get R < 1, but it *will* reduce R.

For COVID-19, every extra 1° Celsius (1.8° Fahrenheit) makes R drop by 1.2%.[^heat] The summer-winter difference in New York City is 26°C (47°F),[^nyc_heat] so summer will make R drop by ~31%.

[^heat]: “One-degree Celsius increase in temperature [...] lower[s] R by 0.0225” and “The average R-value of these 100 cities is 1.83”. 0.0225 ÷ 1.83 = ~1.2%. [Wang, Jingyuan and Tang, Ke and Feng, Kai and Lv, Weifeng](https://papers.ssrn.com/sol3/Papers.cfm?abstract_id=3551767)

[^nyc_heat]: In 2019 at Central Park, hottest month (July) was 79.6°F, coldest month (Jan) was 32.5°F. Difference is 47.1°F, or ~26°C. [PDF from Weather.gov](https://www.weather.gov/media/okx/Climate/CentralPark/monthlyannualtemp.pdf)

<div class="sim">
		<iframe src="sim?stage=int-6b&format=calc" width="285" height="220"></iframe>
</div>

Summer alone won't make R < 1, but if we have limited resources, we can scale back some interventions in the summer – so we can scale them *higher* in the winter.

**A "Circuit Breaker" Lockdown:**

And if all that *still* isn't enough to get R < 1... we can do another lockdown.

But we wouldn't have to be 2-months-closed / 1-month-open over & over! Because R is reduced, we'd only need one or two more "circuit breaker" lockdowns before a vaccine is available. (Singapore had to do this recently, "despite" having controlled COVID-19 for 4 months. That's not failure: this *is* what success takes.)

Here's a simulation of a "lazy case" scenario:

1. Lockdown, then
2. A moderate amount of hygiene & "Test, Trace, Isolate", with a mild amount of "Masks For All", then...
3. One more "circuit breaker" lockdown before a vaccine's found.

<div class="sim">
		<iframe src="sim?stage=int-7&format=lines&height=620" width="800" height="620"></iframe>
</div>

Not to mention all the *other* interventions we could do, to further push R down:

* Travel restrictions/quarantines
* Temperature checks at malls & schools
* Deep-cleaning public spaces
* [Replacing hand-shaking with foot-bumping](https://twitter.com/V_actually/status/1233785527788285953)
* And all else human ingenuity shall bring

. . .

We hope these plans give you hope. 

**Even under a pessimistic scenario, it *is* possible to beat COVID-19, while protecting our mental and financial health.** Use the lockdown as a "reset button", keep R < 1 with case isolation + privacy-protecting contract tracing + at *least* cloth masks for all... and life can get back to a normal-ish!

Sure, you may have dried-out hands. But you'll get to invite a date out to a comics bookstore! You'll get to go out with friends to watch the latest Hollywood cash-grab. You'll get to people-watch at a library, taking joy in people going about the simple business of *being alive.*

Even under the worst-case scenario... life perseveres.

So now, let's plan for some *worse* worst-case scenarios. Water landing, get your life jacket, and please follow the lights to the emergency exits:

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>The Next Few Years</div>
    </div>
</div>

You get COVID-19, and recover. Or you get the COVID-19 vaccine. Either way, you're now immune...

...*for how long?*

* COVID-19 is most closely related to SARS, which gave its survivors 2 years of immunity.[^SARS immunity]
* The coronaviruses that cause "the" common cold give you 8 months of immunity.[^cold immunity]
* There's reports of folks recovering from COVID-19, then testing positive again, but it's unclear if these are false positives.[^unclear]
* One *not-yet-peer-reviewed* study on monkeys showed immunity to the COVID-19 coronavirus for at least 28 days.[^monkeys]

But for COVID-19 *in humans*, as of May 1st 2020, "how long" is the big unknown.

[^SARS immunity]: “SARS-specific antibodies were maintained for an average of 2 years [...] Thus, SARS patients might be susceptible to reinfection ≥3 years after initial exposure.” [Wu LP, Wang NC, Chang YH, et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2851497/) "Sadly" we'll never know how long SARS immunity would have really lasted, since we eradicated it so quickly.

[^cold immunity]: “We found no significant difference between the probability of testing positive at least once and the probability of a recurrence for the beta-coronaviruses HKU1 and OC43 at 34 weeks after enrollment/first infection.” [Marta Galanti & Jeffrey Shaman (PDF)](http://www.columbia.edu/~jls106/galanti_shaman_ms_supp.pdf)

[^unclear]: “Once a person fights off a virus, viral particles tend to linger for some time. These cannot cause infections, but they can trigger a positive test.” [from STAT News by Andrew Joseph](https://www.statnews.com/2020/04/20/everything-we-know-about-coronavirus-immunity-and-antibodies-and-plenty-we-still-dont/)

[^monkeys]: From [Bao et al.](https://www.biorxiv.org/content/10.1101/2020.03.13.990226v1.abstract) *Disclaimer: This article is a preprint and has not been certified by peer review (yet).* Also, to emphasize: they only tested re-infection 28 days later. 

For these simulations, let's say it's 1 year.
**Here's a simulation starting with 100% <span class="nowrap"><icon r></icon>**,</span> exponentially decaying into susceptible, no-immunity <span class="nowrap"><icon s></icon>s</span> after 1 year, on *average*, with variation:

<div class="sim">
		<iframe src="sim?stage=yrs-1&format=lines&height=600" width="800" height="600"></iframe>
</div>

Return of the exponential decay!

This is the **SEIRS Model**. The final "S" stands for <icon s></icon> Susceptible, again.

![](pics/seirssrb.png)

Now, let's simulate a COVID-19 outbreak, over 10 years, with no interventions... *if immunity only lasts a year:*

<div class="sim">
		<iframe src="sim?stage=yrs-2&format=lines&height=600" width="800" height="600"></iframe>
</div>

In previous simulations, we only had *one* ICU-overwhelming spike. Now, we have several, *and* <icon i></icon> cases come to a rest *permanently at* ICU capacity. (Which, remember, we *tripled* for these simulations)

R = 1, it's **endemic.**

Thankfully, because summer reduces R, it'll make the situation better:

<div class="sim">
		<iframe src="sim?stage=yrs-3&format=lines&height=640" width="800" height="640"></iframe>
</div>

Oh.

Counterintuitively, summer makes the spikes worse *and* regular! This is because summer reduces new <span class="nowrap"><icon i></icon>s,</span> but that in turn reduces new immune <span class="nowrap"><icon r></icon>s.</span> Which means immunity plummets in the summer, *creating* large regular spikes in the winter.

Thankfully, the solution to this is pretty straightforward – just vaccinate people every fall/winter, like we do with flu shots:

**(After playing the recording, try simulating your own vaccination campaigns! Remember you can pause/continue the sim at any time)**

<div class="sim">
		<iframe src="sim?stage=yrs-4&format=lines" width="800" height="540"></iframe>
</div>

But here's the scarier question:

What if there's no vaccine for *years*? Or *ever?*

**To be clear: this is unlikely.** Most epidemiologists expect a vaccine in 1 to 2 years. Sure, there's never been a vaccine for any of the other coronaviruses before, but that's because SARS was eradicated quickly, and "the" common cold wasn't worth the investment. 

Still, infectious disease researchers have expressed worries: What if we can't make enough?[^vax_enough] What if we rush it, and it's not safe?[^vax_safe]

[^vax_enough]: “If a coronavirus vaccine arrives, can the world make enough?” [by Roxanne Khamsi, on Nature](https://www.nature.com/articles/d41586-020-01063-8)

[^vax_safe]: “Don’t rush to deploy COVID-19 vaccines and drugs without sufficient safety guarantees” [by Shibo Jiang, on Nature](https://www.nature.com/articles/d41586-020-00751-9)

Even in the nightmare "no-vaccine" scenario, we still have 3 ways out. From most to least terrible:

1) Do intermittent or loose R < 1 interventions, to reach "natural herd immunity". (Warning: this will result in many deaths & damaged lungs. *And* won't work if immunity doesn't last.)

2) Do the R < 1 interventions forever. Contact tracing & wearing masks just becomes a new norm in the post-COVID-19 world, like how STI tests & wearing condoms became a new norm in the post-HIV world.

3) Do the R < 1 interventions until we develop treatments that make COVID-19 way, way less likely to need critical care. (Which we should be doing *anyway!*) Reducing ICU use by 10x is the same as increasing our ICU capacity by 10x:

**Here's a simulation of *no* lasting immunity, *no* vaccine, and not even any interventions – just slowly increasing capacity to survive the long-term spikes:**

<div class="sim">
		<iframe src="sim?stage=yrs-5&format=lines" width="800" height="540"></iframe>
</div>

Even under the *worst* worst-case scenario... life perseveres.

. . .

Maybe you'd like to challenge our assumptions, and try different R<sub>0</sub>'s or numbers. Or try simulating your *own* combination of intervention plans!

**Here's an (optional) Sandbox Mode, with *everything* available. (scroll to see all controls) Simulate & play around to your heart's content:**

<div class="sim">
		<iframe src="sim?stage=SB&format=sb" width="800" height="540"></iframe>
</div>

This basic "epidemic flight simulator" has taught us so much. It's let us answer questions about the past few months, next few months, and next few years.

So finally, let's return to...

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>The Now</div>
    </div>
</div>

Plane's sunk. We've scrambled onto the life rafts. It's time to find dry land.[^dry_land]

[^dry_land]: Dry land metaphor [from Marc Lipsitch & Yonatan Grad, on STAT News](https://www.statnews.com/2020/04/01/navigating-covid-19-pandemic/)

Teams of epidemiologists and policymakers ([left](https://www.americanprogress.org/issues/healthcare/news/2020/04/03/482613/national-state-plan-end-coronavirus-crisis/), [right](https://www.aei.org/research-products/report/national-coronavirus-response-a-road-map-to-reopening/ ), and [multi-partisan](https://ethics.harvard.edu/covid-roadmap)) have come to a consensus on how to beat COVID-19, while protecting our lives *and* liberties.

Here's the rough idea, with some (less-consensus) backup plans:

![](pics/plansrb.png)

So what does this mean for YOU, right now?

**For everyone:** Respect the lockdown so we can get out of Phase I asap. Keep washing those hands. Make your own masks. Download a *privacy-protecting* contact tracing app when those are available next month. Stay healthy, physically & mentally! And write your local policymaker to get off their butt and...

**For policymakers:** Make laws to support folks who have to self-isolate/quarantine. Hire more manual contact tracers, *supported* by privacy-protecting contact tracing apps. Direct more funds into the stuff we should be building, like...

**For builders:** Build tests. Build ventilators. Build personal protective equipment for hospitals. Build tests. Build masks. Build apps. Build antivirals, prophylactics, and other treatments that aren't vaccines. Build vaccines. Build tests. Build tests. Build tests. Build hope. 

Don't downplay fear to build up hope. Our fear should *team up* with our hope, like the inventors of airplanes & parachutes. Preparing for horrible futures is how we *create* a hopeful future.

The only thing to fear is the idea that the only thing to fear is fear itself.
