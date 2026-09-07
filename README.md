# SPOBO_SURGICAL_INFECTIONS_TRACKER
Spremljanje okužb kirurške rane - sedaj v digitalizirani obliki primarno za maksilofacialno kirurgijo.

Digitalno spremljanje okužb kirurške rane
Opis sistema, poteka spremljanja in tehnične postavitve
1. Namen sistema
Sistem je namenjen strukturiranemu in digitaliziranemu spremljanju kirurške rane po operaciji.
Po navodilih, ki smo jih prejeli od NIJZ, je treba izvajati spremljanje kirurških ran po operativnih posegih. Namen vzpostavljene rešitve je ta proces čim bolj poenostaviti, standardizirati in digitalizirati, tako za paciente kot za zdravstveno osebje.
Namesto ročnega kontaktiranja pacientov in ločenega zbiranja podatkov sistem omogoča avtomatsko pošiljanje vprašalnikov ob vnaprej določenih časovnih točkah po operaciji ter centralizirano zbiranje odgovorov.
S tem želimo:
povečati stopnjo digitalizacije spremljanja kirurških ran,
zmanjšati administrativno delo zdravstvenega osebja,
izboljšati odzivnost pacientov,
standardizirati zbiranje podatkov,
omogočiti longitudinalno spremljanje celjenja kirurške rane,
omogočiti zbiranje fotografij kirurške rane,
olajšati prepoznavanje morebitnih znakov okužbe ali drugih zapletov.
2. Kako poteka spremljanje pacienta
Registracija po operaciji
Pacient po operaciji najprej izpolni registracijski obrazec.
V njem navede osnovne podatke, potrebne za nadaljnje spremljanje:
ime in priimek,
elektronski naslov,
telefonsko številko,
datum operacije,
podatek o trenutnem jemanju antibiotične terapije,
naziv antibiotika, kadar ga jemlje.
Ob registraciji sistem pacientu avtomatsko določi enolično identifikacijsko oznako oziroma PatientID.
Po uspešni registraciji pacient prejme potrditveno elektronsko sporočilo.
Samodejna določitev terminov spremljanja
Na podlagi vpisanega datuma operacije sistem samodejno izračuna termine za nadaljnje spremljanje.
Pacient bo vprašalnike prejel:
7., 14., 30. in 90. dan po operaciji.
Prvotno je bil v pilotni sistem vključen tudi 1. dan po operaciji, vendar spremljanje na prvi dan ni potrebno in bo zato iz končne različice odstranjeno.
Samodejni e-poštni opomniki
Pacientu ni treba spremljati datumov ali si shranjevati povezav do posameznih vprašalnikov.
Na vsak predvideni dan spremljanja sistem avtomatsko pošlje elektronsko sporočilo na naslov, ki ga je pacient navedel ob registraciji.
V sporočilu pacient prejme:
informacijo, kateri dan po operaciji je,
kratko pojasnilo namena spremljanja,
neposredno povezavo do ustreznega vprašalnika.
Povezava je personalizirana in vsebuje pacientov PatientID, zato lahko sistem prejeti odgovor pravilno poveže z registracijo pacienta.
3. Kaj pacient izpolni v vprašalniku
Vprašalniki so za posamezne časovne točke standardizirani, kar omogoča spremljanje sprememb skozi čas.
Pacient poroča o naslednjih parametrih:
Bolečina v področju kirurške rane
Ocena na lestvici od 0 do 10, pri čemer 0 pomeni brez bolečine in 10 najhujšo možno bolečino.
Senzibiliteta oziroma občutek v področju kirurške rane
Ocena na lestvici od 0 do 10. Spremljajo se morebitna omrtvelost, zmanjšan občutek, mravljinčenje, spremenjeno zaznavanje in druge motnje senzibilitete.
Oteklina
Pacient označi, ali otekline ni oziroma ali je blaga, zmerna ali izrazita.
Rdečina
Pacient označi prisotnost in izraženost rdečine v okolici kirurške rane.
Povišana telesna temperatura oziroma vročina
Spremlja se odsotnost vročine oziroma povišana temperatura do ali nad 38 °C.
Izcedek iz kirurške rane
Pacient lahko navede odsotnost izcedka oziroma prozoren, krvavkast, rumenkast/gnojen izcedek ali izcedek neprijetnega vonja.
Dehiscenca
Pacient poroča o morebitnem razprtju kirurške rane oziroma kirurških šivov.
Splošno stanje kirurške rane
Pacient označi, ali je trenutno brez težav oziroma ali ima težave.
Antibiotična terapija
Pacient navede, ali trenutno jemlje antibiotik in katerega.
Dodatna opažanja ali vprašanja
Na voljo je prosto besedilno polje, kamor lahko pacient vpiše dodatne težave, opažanja ali vprašanja.
4. Fotografija kirurške rane
Ob posameznem spremljanju ima pacient možnost naložiti tudi fotografijo kirurške rane.
Fotografija predstavlja dopolnitev podatkov iz vprašalnika in omogoča vizualno dokumentiranje poteka celjenja kirurške rane skozi čas.
Sistem trenutno omogoča nalaganje ene slikovne datoteke do velikosti 10 MB pri posameznem spremljanju.
5. Celoten potek za pacienta
Pot spremljanja je za pacienta čim bolj preprosta:
Operacija
↓
Izpolnitev registracijskega obrazca
↓
Potrditveni e-mail
↓
7. dan – avtomatski e-mail → vprašalnik + fotografija
↓
14. dan – avtomatski e-mail → vprašalnik + fotografija
↓
30. dan – avtomatski e-mail → vprašalnik + fotografija
↓
90. dan – avtomatski e-mail → vprašalnik + fotografija
Pacientu tako po prvi registraciji ni treba narediti ničesar drugega kot spremljati svojo elektronsko pošto in ob prejemu opomnika izpolniti vprašalnik.
6. Tehnična izvedba sistema
Sistem je v celoti postavljen v Google okolju in temelji na štirih osnovnih komponentah:
Google Forms
Uporablja se:
ena registracijska forma,
forma za 7. dan,
forma za 14. dan,
forma za 30. dan,
forma za 90. dan.
Vsak vprašalnik je ločen, pacient pa avtomatsko prejme povezavo do ustreznega vprašalnika.
Google Sheets
Google Sheet predstavlja centralno podatkovno in nadzorno točko sistema.
Vsebuje zavihke:
PACIENTI – registrirani pacienti in osnovni podatki,
OPOMNIKI – vsi načrtovani termini spremljanja in podatki o tem, ali je bil posamezen opomnik poslan in odgovor prejet,
ODGOVORI – zbrani odgovori iz vprašalnikov,
NASTAVITVE – tehnični podatki in povezave do posameznih Google Forms,
LOG – dnevnik delovanja sistema in morebitnih napak.
Google Apps Script
Google Apps Script predstavlja avtomatizacijski del sistema.
Skripta avtomatsko:
obdela novo registracijo,
ustvari unikaten PatientID,
iz datuma operacije izračuna termine spremljanja,
ustvari personalizirane povezave do vprašalnikov,
vsak dan preveri, komu je treba poslati vprašalnik,
avtomatsko pošlje elektronsko sporočilo,
zazna oddajo vprašalnika,
odgovore zapiše v centralno tabelo,
označi, da je pacient za določeni termin odgovoril,
vodi dnevnik delovanja sistema.
S tem ni potrebno uporabljati Microsoft Power Automate ali ročno vzpostavljati posameznih avtomatizacij za vsak časovni interval.
Gmail
Gmail se uporablja za avtomatsko komunikacijo s pacienti.
Po registraciji pacient prejme potrditveno sporočilo.
Nato prejema avtomatske opomnike za posamezne termine spremljanja.
Sporočila se zaključijo s podpisom:
Lep pozdrav,
Ekipa za spremljanje okužb kirurške rane
7. Zakaj sporočila trenutno prihajajo z računa maksm.cuzak@gmail.com
Sistem je trenutno postavljen na računu maksm.cuzak@gmail.com, ker je bil ta račun uporabljen kot tehnični oziroma razvojni račun za izdelavo in testiranje pilotne rešitve.
Google Apps Script avtomatizacije se izvajajo v okviru Google računa, ki je lastnik oziroma izvajalec skripte. Zato se v trenutni testni postavitvi tudi avtomatska elektronska sporočila pošiljajo prek tega Gmail računa.
To je primerno za razvoj in pilotno testiranje sistema, ni pa nujno optimalna dolgoročna produkcijska rešitev.
Pred uvedbo sistema v redno klinično uporabo je priporočljivo razmisliti o prenosu sistema na namenski institucionalni Google Workspace račun.
S tem bi bili:
lastništvo sistema,
lastništvo podatkov,
upravljanje dostopov,
pošiljanje elektronskih sporočil in
administracija sistema
vezani na institucijo in ne na osebni Google račun.
8. Digitalizacija procesa
Pomemben cilj rešitve je povečanje stopnje digitalizacije spremljanja kirurških ran.
Klasičen način bi zahteval ročno spremljanje datumov operacij, ročno kontaktiranje pacientov, pošiljanje posameznih vprašalnikov ter kasnejše združevanje odgovorov.
V razvitem sistemu je po prvi registraciji večina tega procesa avtomatizirana.
Zdravstveno osebje zato predvsem spremlja rezultate, medtem ko sistem skrbi za časovno načrtovanje, pošiljanje vprašalnikov, povezovanje odgovorov s pacienti in osnovno evidenco opravljenega spremljanja.
Tak pristop omogoča, da je spremljanje izvedeno bolj standardizirano in z bistveno manj administrativnega dela.

Po operaciji boste najprej izpolnili kratek registracijski obrazec. Na podlagi datuma operacije bo sistem samodejno določil termine nadaljnjega spremljanja.
7., 14., 30. in 90. dan po operaciji boste na svoj elektronski naslov prejeli opomnik s povezavo do kratkega vprašalnika o stanju kirurške rane.
V vprašalniku boste lahko ocenili bolečino in občutek v področju kirurške rane, navedli morebitno oteklino, rdečino, vročino, izcedek ali druge težave ter dodali fotografijo kirurške rane.
Namen spremljanja je omogočiti sistematično spremljanje celjenja kirurške rane in pravočasno prepoznavanje morebitnih težav. Digitalni način spremljanja omogoča enostavnejše obveščanje pacientov in boljšo preglednost zbranih podatkov.
Po prvi registraciji vam ni treba spremljati datumov. Ob ustreznem času boste na svoj elektronski naslov avtomatsko prejeli povezavo do naslednjega vprašalnika.
