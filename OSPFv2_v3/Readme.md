## OSPFV2_v3 </br>
U labu OSPV3_v2 prikazani su ruteri kojima su dodeljene IPv6 i IPv4 adrese. </br>
</br>
![ospfv2_v3](https://user-images.githubusercontent.com/24782270/233171497-8391d1a5-19b4-43e1-8482-84a992a20d30.JPG)

Ruteri R1 i R2 su deo oblasti 50, dok su R2 i R3 deo oblasti 0. </br>
Ruter R4 ne pripada ni jednoj oblasti, i nad njim ne konfigurišemo OSPF protokol.
Jedna od stvari koje možemo primetite je i da ruter R2 pripada oblastima 50 i 0. </br>
Pošto sam ruter pripada dvema oblastima on je ABR (granicni) ruter.
Rutiranje izmedju područja se odvija preko ABR rutera u nasem slučaju rutera R2
Oblast 0 je (backbone area) centralno cvorište same OSPF topologije.
Jedan od zadatake oblasti 0 je i da distribuira sve ruting informacije oblastima koje nisu
deo nje.

U samom labu oblast 50 je konfigurisana i kao stub oblast. </br>
Osnovni zadatak stub oblasti je da spreči oglašavanje (advertisemnts) ekternih ruta, samim
tim se smanjuje ospf baza podataka i ubrzava OSPF mreža. U našem slučaju eksterni ruter je R4. </br>
Svi interfejsi koji su usmereni prema svičevima su pasivni interfejsi time je isključeno slanje HELLO paketa.


<h5>Link do laba</h5>
[Link](https://itexamanswers.net/ccnp-route-chapter-3-lab-3-2-multi-area-ospfv2-and-ospfv3-with-stub-area-version-7.html)
