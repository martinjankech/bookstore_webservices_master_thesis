# bookstore_webservices_master_thesis
# Ciele práce 
Cieľom tejto práce je prispieť k rozvoju online kníhkupectiev, skúmaním  možností využívania XML webových služieb v ich informačnom systéme. 
Hlavným cieľom tejto práce je navrhnúť a vyvinúť webovú ASP .NET XML službu, ktorú možno integrovať do online kníhkupectva. 
Táto webová služba by mala poskytovať rôzne usporiadané informácie o knihách a transakciách v danom online kníhkupectve, 
ako aj zabezpečiť základnú manipuláciu s týmito informáciami. Cieľ práce súvisí aj s tvorbou ukážkového dynamického webového klienta, 
ktorý môže dané vystavené metódy webovej služby použiť a výsledky vo vhodnej forme zobraziť používateľovi. 
Služba má rozšíriť funkčnosť internetového kníhkupectva a svojou funkcionalitou poskytnúť  svojím používateľom lepší zážitok.
# Požiadavky na metódy webovej služby
Vystavené metódy webovej služby, by mali byť schopné zvládať  nasledujúce úlohy:
* Vystavené metódy webovej služby majú byť schopné načítať  údaje z XML súboru. 
*	Pri metódach s komplexnejším výstupom  tento výstup   zapísať  do jedného samostatného  novo-vytvoreného XML súboru. Názov XML súboru bude pozostávať z časovej pečiatky, názvu volanej metódy a z aktuálnych hodnôt parametrov volanej metódy.
*	Pri metódach s menším a opakujúcim sa výstupom zapísať tento výstup s časovou pečiatkou do jedného toho istého XML súboru s tým, že výsledok aktuálneho volania služby sa  zapíše na koniec za posledné dieťa koreňového elementu XML dokumentu. 
*	Vystavené metódy webovej služby majú byť schopné ten istý výstup, ktorý          bol zapísaný do XML súboru serializovať  do JSON formátu a v tejto štruktúre            ho poslať klientovi na ďalšie spracovanie. 
*	V prípade chyby metóda odošle klientovi status-kód chyby, ako aj popis chyby.
*	Vystavené metódy webovej služby by mali byť schopné vrátiť údaj o jednej knihe alebo transakcii na základe identifikátora, zoznam kníh a transakcií.
*	Vystavené metódy webovej služby majú byť schopné vrátiť zoznam všetkých kníh a transakcií.
*	Vystavené metódy webovej služby majú byť schopné pridať, aktualizovať alebo vymazať údaj o jednej knihe alebo transakcii. 
*	Vystavené metódy majú byť schopné vrátiť začiatočný a konečný počet kníh            na sklade kníhkupectva v zadanom období. Používateľ si môže zvoliť, či  chce vrátiť údaje  len pre  knihy patriace  do hodnoty zadaného atribútu (napríklad autor, kategória, vydavateľstvo) alebo údaje o všetkých knihách. Výsledky s počtami a názvami kníh  služba poskytne zoradené vzostupne alebo zostupne  podľa hodnôt rôznych atribútov knihy (počet strán, rok vydania, cena, priemerné hodnotenie, názov). Metódy majú byť taktiež schopné vrátiť celkový, maximálny, minimálny a priemerný počet kníh na začiatku a na konci  sledovaného obdobia.
*	Vystavené metódy majú byť schopné poskytnúť agregované a zoskupené údaje o počte kusov predaných kníh, ako aj peňažného príjmu z predaja kníh v  zadanom období. Počty a príjmy z predaja  kníh môžu byť agregované podľa rôzneho atribútu (kategória, jazyk, autor, väzba, rok vydania),   ale aj podľa samotných titulov kníh. Cieľom je klientovi poskytnúť výstup v takom formáte, aby bol schopný vytvoriť drill down graf (teda graf, v ktorom sú dáta agregované a zoskupené podľa rôznej úrovne detailu a granularity), kde na najvyššej  hierarchii budú údaje agregované a zoskupené podľa zvoleného atribútu  a na nižšej hierarchii budú údaje o počtoch a príjmoch agregované a zoskupené podľa jednotlivých kníh. 
Tieto údaje budú zoradené vzostupne alebo zostupne, a to buď podľa hodnoty (číselná hodnota/počty, príjmy) alebo názvu (abecedné zoradenie podľa názvu atribútu/knihy).
Vystavené metódy, by mali taktiež vrátiť celkový počet kusov a celkový príjem z predaných kníh v danom období, priemerný denný príjem a priemerný  počet predaných kusov v zadanom období, maximálny a minimálny príjem a počet predaných kusov pre podkategóriu atribútu, podľa ktorého sa zoskupovalo        (Napr. pri zvolenom atribúte kategória je podkategória beletria, klasika. a                 pri zvolenom atribúte väzba je to napr. pevná väzba, brožovaná väzba ), a taktiež maximálny a minimálny príjem a počet predaných kusov pre tituly jednotlivých kníh. 
*	Vystavené metódy, by mali byť schopné urobiť podobnú funkcionalitu spomínanú v predošlom bode aj pre počty naskladnených kníh od dodávateľa                          ako aj  pre náklady ktoré z toho vyplývajú.
*	Vystavené metódy, by mali taktiež na základe údajov o predajoch a nákupoch v danom období poskytnúť pre manažment zaujímavé metriky, ktoré im prezradia niečo viacej o výkonnosti podniku v danom období.
# Požiadavky na klienta webovej služby
*	Na domovskej stránke klienta, by sa mal nachádzať zoznam, ktorý bude obsahovať linky na stránky, kde sa bude demonštrovať funkcionalita vystavených metód webovej služby.
*	Klient má byť single page dynamická webová aplikácia, ktorá dokáže s používateľom interagovať dynamicky bez nutnosti znovu načítania stránky.
*	O každom úspechu alebo chybe, by mal byť používateľ klienta informovaný vhodným farebne označeným oznámením alebo upozornením.
*	Vstupy do formulárov by mali obsahovať funkcionalitu auto dopĺňania textu, ktorá bude fungovať na princípe pred-načítaných údajov z XML dátovej základne. To poslúži jednak na urýchlenie zadávania vstupov,         ale aj zníži počet chybových vstupov, keďže používateľ tak bude vedieť v akom formáte má vstup zadať.
*	Klient by mal byť vytvorený ako responzívny, tak aby bol vhodný              na použitie na rôznych zariadeniach. 
*	Výstupy webových služieb by mal klient prekonvertovať z JSON formátu do používateľsky prívetivého výstupu, akým je tabuľka alebo graf.  
*	Použitím vhodného nástroja, by malo byť možné výstup z klienta stiahnuť napríklad ako obrázok alebo vo formáte  pdf, xsl, csv.
# 	Použité technológie pri tvorbe webovej služby
Pri tvorbe webových služieb sme použili framework ASP .NET, ktorý poskytuje vývojárom širokú škálu nástrojov a knižníc, ktorá im umožňuje vytvárať dynamické webové aplikácie, webové stránky alebo  webové služby pomocou rôznych programovacích jazykov, ako sú C#, Visual Basic alebo F#. Zo širokej ponuky programovacích jazykov  sme si zvolili  objektovo orientovaný jazyk C#, s ktorým máme najväčšie skúsenosti. 
Celá naša webová služba sa bude nachádzať v ASMX súbore. Skratka ASMX (Active Server Method Extension)  je to typ súboru, ktorý sa používa na definovanie           a implementáciu webových  SOAP služieb v ASP .NET frameworku.  Ako integrované vývojové prostredie pri tvorbe webovej služby budeme používať produkt od firmy Microsoft a to Visual Studio. Webová služba bude nasadená na IIS server.  Službu budeme testovať pomocou testovacieho klienta bežiaceho na ľahšej verzii IIS Express a ukážeme      si aj testy v nástroji SOAP UI.  Na dopytovanie z XML dokumentov sme využili jazyky XPath a LINQ. XPath sme využili hlavne pri jednoduchších dopytoch, kde nám stačilo prechádzať štruktúrou XML dokumentu a vybrať požadované údaje.  Na druhej strane LINQ sme využili pri zložitejších dopytoch, kde sme potrebovali technológie,  ktoré nám umožnia funkcionalitu, ako je projekcia údajov do novej podoby, agregácia údajov, filtrovanie údajov, triedenie  a pod.
# 	Technológie použité pri tvorbe webového klienta 
Na tvorbu základnej štruktúry webovej stránky a jej štýlov sme využili Hypertextový značkovací jazyk (HTML) a kaskádové štýly (CSS). Na zabezpečenie dynamiky sme použili štandardne  jazyk Javascript. Pri tvorbe klienta sme využili viacero frameworkov, ktoré jeho tvorbu uľahčili. Medzi tieto patria:
Bootstrap- populárny frontendový framework, ktorý umožňuje vývojárom rýchlo    a jednoducho vytvárať responzívne webové stránky a webové aplikácie pre mobilné zariadenia. Medzi kľúčové vlastnosti Bootstrapu patrí grid systém (systém mriežky), ktorý umožňuje flexibilné a responzívne rozvrhnutie stránky, rozsiahly súbor tried CSS              na štylizáciu bežných komponentov používateľského rozhrania, ako sú tlačidlá, formuláre        tabuľky a rôzne pomocné moduly JavaScriptu, ktoré poskytujú ďalšie funkcie, napríklad modálne okná.
*	jQuery- javascriptová knižnica, ktorá zjednodušuje skriptovanie na strane klienta    a poskytuje funkcie AJAX, ktoré boli použité na tzv. „konzumáciu“ webových metód tak, aby sa výsledky na stránke zobrazili bez nutnosti znovu načítania stránky. 
*	jQuery UI- túto knižnicu založenú na klasickom Jquery sme využili hlavne                pre zabezpečenia automatického dopĺňania vstupov formulára. 
*	DataTables- Doplnok pre jQuery sa používa na pridávanie pokročilých ovládacích prvkov interakcie do tabuliek HTML.
*	Highcharts a Chart.js-  tieto javascritové knižnice sme  používali na vytváranie interaktívnych a responzívnych grafov.
*	Ako verzionovací systém sme použili Git a  cloudovú platformu Github. 
*	Visual Studio Code- editor zdrojového kódu, ktorý vďaka mnohým doplnkom           uľahčuje písanie HTML, CSS a Javascriptoveho kódu.
# Ukážky obrazoviek	
![image](https://github.com/martinjankech/distribuovane_spracovanie_udajov_projekt/assets/63880926/2666c63d-c61a-4a29-a3db-2d4c0f6b8f7d)
![image](https://github.com/martinjankech/distribuovane_spracovanie_udajov_projekt/assets/63880926/9eace4d6-94ae-4964-887d-dfd67a97cd82)
![image](https://github.com/martinjankech/distribuovane_spracovanie_udajov_projekt/assets/63880926/63fc26c6-ed57-4e20-b794-630de4f9cf79)
![image](https://github.com/martinjankech/distribuovane_spracovanie_udajov_projekt/assets/63880926/037bc486-0ec9-457c-b62c-5d8bead52cf5)
![image](https://github.com/martinjankech/distribuovane_spracovanie_udajov_projekt/assets/63880926/fc0c753e-e506-43d5-b4b9-52b13bcfa373)
![image](https://github.com/martinjankech/distribuovane_spracovanie_udajov_projekt/assets/63880926/1048cedb-325e-463a-8c2a-0da0e1583b23)
![image](https://github.com/martinjankech/distribuovane_spracovanie_udajov_projekt/assets/63880926/27c50f07-e048-443d-9b34-141c3eec61a8)
![image](https://github.com/martinjankech/distribuovane_spracovanie_udajov_projekt/assets/63880926/11973f29-1f8c-4b9c-93bd-afcef5c8f162)
![image](https://github.com/martinjankech/distribuovane_spracovanie_udajov_projekt/assets/63880926/4671ed60-8987-417c-8e3c-2e595a83fa20)
![image](https://github.com/martinjankech/distribuovane_spracovanie_udajov_projekt/assets/63880926/fc9781e8-472e-4428-becf-d2c8e9fc5c87)


