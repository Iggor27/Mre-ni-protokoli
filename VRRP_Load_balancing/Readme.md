## VRRP (Virtualni Redudantni Protokol) </br>

VRRP protokol u našem labu ima dvostruku ulogu: </br>
***1. Balansiranje opterećenja mreže*** </br>
***2. Redudansa u slučaju prekida rada veze na mreži***

<h3>Balansiranje opterećenja mreže</h3>
Iz slike možemo uočiti da postoje dva rutera R2 i R3 nad kojim su postavljenje virtualne adrese (vip).
Sa računara PC1 paketi se salju ruteru R1, dok PC2 salje pakete ruteru R2.
Nad svakim računarom postavljen je izlaz na mrežu (default gateway).

Virtualni ruteri unutar VRRP grupe imaju jedinstvenu MAC adresu: 00-00-5E-00-01-[VRID].</br>
VRID predstavlja identitet date grupe i može imati vrednosti izmedju 0-255. Sa slike uočavamo dve VRRP grupe, grupu 1 kojoj pripada ruter R1 i grupu 2 kojoj pripada ruter R2.
Svaka grupa ima master i backup ruter. 
Master ruteri koriste virtualne MAC adrese koje su im dodeljene da bi odgovorili na ARP zahteve hostova. ARP zahtev uspostavlja vezu izmedju uredjaja (hostova) i mreže.
Svakom ruteru unutar VRRP grupe se dodeljuje odgovarajući prioriteti. Ruter sa većim prioritetm postaje master ruter dok ruter sa manjim prioritetom postaje backup (rezervni ruter). </br>
U slučaju da imamo iste prioritete u jednoj VRRP grupi posmatra se ip adresa i onaj ruter
koji ima veću adresu postaje virtualni master ruter.

<h3>Redudansa u slučaju prekida rada veze na mreži</h3>
Naš zadatak u labu je da uspešno pošaljemo pakete sa hostova na ruter R3. Ruter R3 ne pripada ni jednoj Vrrp grupi. On predstavlja vezu sa eksternom mrežom. </br>
Podešavanjem odgovarajućih virtualnih grupa možemo obezbediti odredjen nivo redudanse.
U slučaju prekida rada master rutera u vrrp grupi rezervni (backup) ruteri će preuziti primarnu ulogu master rutera koji je u prekidu. Protokolom VRRP omogućavamo da ne postoji način dolaska do (SPOF-a) tj. u slučaju prekida  se ne zaustavlja protok na celoj mreži. 
</br>
</br>
</br>

![Vrrp](https://user-images.githubusercontent.com/24782270/233429730-c448ed4c-885b-43d7-af6f-cd6ff34f5cfd.JPG)



<h4>Simulacija prekida</h4>
Komandom <em>ping 210.37.0.1 -t</em> u terminalu PC1 ili PC2 možemo neprekidno slati pakete preko mreže. U nekom trenutku možemo ugasiti bilo koju vezu izmedju sviča i rutera R2 ili R1 ili prekinuti vezu izmedju rutera R2 i R3 ili R1 i R3. Posmatranjem terminala možemo uočiti da  je potreban kraći period da se uspostavi ponovno slanje i da određeni deo paketa nije stigao na željenu destinaciju.</br>
Istu simulaciju prekida možemo izvršiti i u labu-u OSPF_Compare koji se nalazi u OSPF_Load_B folderu stim što nad datom topologijom je primenjeno samo OSPF rutiranje.


<h5>Link do laba</h5>
[Link](https://www.matec-conferences.org/articles/matecconf/pdf/2018/87/matecconf_cas2018_03012.pdf)

