World of USO - Manual extins
============================

I. Informații de bază
---------------------

Un jucător poate avea la un moment dat: puncte, bani, vrăji și artefacte.

Punctele reprezintă singurul criteriu care determină ordinea în clasament. Acestea pot fi acumulate din:

* Question of the Day
* Challenge
* Weekly Quest
* Final Quest

Vrăjile sunt abilități speciale care îl ajută pe jucător pe o perioadă determinată de timp (în general câteva zile). Un jucător poate vrăji un alt jucător, inclusiv pe el însuși; vrăjile pot fi pozitive, negative sau neutre.

Artefactele sunt abilităţi speciale care îl ajută pe jucător în mod permanent.

Banii sunt folosiți pentru a cumpăra vrăji. Banii pot fi obținuți din:

* Special Quest
* Bonusuri din partea asistenţilor
* Propuneri de întrebări
* Raportare de buguri

II. Întrebarea zilei (Question of the Day)
------------------------------------------

Este o întrebare unică în fiecare zi. Jucătorul poate răspunde la aceasta în orice moment al zilei. Întrebarea are multiple variante de răspuns, dintre care una singură este cea corectă.

Răspunsul corect în intervalul orar 00:00-11:59 este echivalent cu obținerea a 50 puncte, iar în intervalul 12:00-23:59 cu 30 puncte.

III. Provocări (Challenges)
---------------------------

Provocarea este modul în care doi jucători pot concura pentru obținerea de puncte prin răspunsul la un număr de întrebări comune.

O provocare constă din 5 întrebări cu variante multiple și cu mai multe variante de răspuns corecte.

Un jucător poate lansa o singură provocare în fiecare zi însă poate să accepte oricâte.

Costul lansării sau acceptării unei provocări este de 30 de puncte. Practic, fiecare concurent pune în joc 30 de puncte. În momentul lansării provocării sunt extrase 30 de puncte din contul fiecărui participant.

Pentru a fi rulată, o provocare trebuie să fie acceptată. Rularea provocării trebuie realizată pe parcursul aceleiași zile. Dacă la finalul zilei, cel puțin unul dintre jucători nu a rulat provocarea, atunci aceasta este anulată, iar cele 30 de puncte puse în joc sunt returnate fiecărui jucător.

O provocare poate fi rulată asincron și fiecare dintre cei doi jucători are un timp maxim propriu de rulare a provocării, dependent de level-ul său în momentul respectiv. La level 1, timpul este de 5 minute, urmând ca acesta să scadă cu 5 secunde per level.

Cele 5 întrebări ale unei provocări au pondere egală - valoarea 100. Se poate obține, astfel, maxim valoarea 500 pentru un challenge. Se compară valorile obținute de cei doi concurenți și cel cu valoarea mai mare câștigă. Timpul în care se răspunde la cele 5 întrebări nu are impact în matematica punctelor; nu are relevanță dacă termini în 30 de secunde sau în 4 minute și 59 de secunde.

Pentru o întrebare dată se calculează punctajul ponderat la răspunsurile corecte și incorecte, după formula:

	Punctaj_intrebare = (NRCU / NRC - NRGU/NRG) * 100

unde:

* NRCU - numărul de răspunsuri corecte furnizate (checked) de utilizator/concurent
* NRC - numărul total de răspunsuri corecte ale întrebării
* NRGU - numărul de răspunsuri greșite furnizate (checked) de utilizator/concurent
* NRG - numărul total de răspunsuri greșite ale întrebării

Înmulțirea cu 100 se realizează din rațiuni de rotunjire pentru numerele fracționare.

Astfel, pentru o întrebare cu 7 variante de răspuns, dintre care 4 corecte și 3 greșite:

* dacă un utilizator selectează 2 variante corecte (și dor atât), va obține

	Punctaj_intrebare = (2/4 - 0/3) * 100 = 50

* dacă un utilizator selectează toate cele 4 variante corecte, va obține

	Punctaj_intrebare = (4/4 - 0/3) * 100 = 100

* dacă un utilizator selectează 3 variante corecte și 2 greșite, va obține

	Punctaj_intrebare = (3/4 - 2/3) * 100 = 9

* dacă un utilizator selectează 2 variante greșite, va obține

	Punctaj_intrebare = (0/4 - 2/3) * 100 = -66 (punctaj negativ)

* dacă un utilizator selectează toate cele 3 variante greșite, va obține

	Punctaj_intrebare = (0/4 - 3/3) * 100 = -100 (punctaj negativ)

* dacă un utilizator face check pe toate variantele

	Punctaj_intrebare = (4/4 - 3/3) * 100 = 0 (punctaj nul)

Dacă cei doi concurenți obțin același rezultat, cele 30 de  puncte puse în joc sunt returnate fiecăruia.

Numărul de puncte obținut de câștigător se calculează după formula:

	30 + min[30 + N, (30 + N) * Y / X]

unde
* N = punctaj bonus(10 pentru aceeași grupă, 20 pentru aceeași serie, 30 pentru serii diferite)
* X = punctajul câștigătorului
* Y = punctajul celui care pierde

Exemple
* exemplul 1: Gigel are 400 de puncte, iar colegul lui de grupă, Martinel, are 4000 de puncte. Martinel câștigă provocarea împotriva lui Gigel și astfel va câștiga:

	30 + min(30 + 10, (30 + 10) * 400 / 4000) = 30(cele puse în joc) + min(40,  4) = 34

* exemplul 2: Vasilică are 700 de puncte și câștigă provocarea împotriva colegului său dintr-o altă serie care are 7000 de puncte. Astfel, Vasilică o să câștige:

	30 + min(30 + 30, (30 + 30) * 7000 / 700) = 30(cele puse în joc) + min(60, 600) = 90

Pentru a preveni "farming"-ul de puncte, jocul limitează provocările cu jucători aflați la o anumită distanță în clasament. Presupunem că un jucător X provoacă un jucător Y. Fie D diferența de poziție dintre X și Y (în modul). Jocul impune următoarele:
* Dacă D <= 10, atunci X îl poate provoca pe Y și în ziua următoare.
* Dacă 10 < D <= 20, atunci X îl poate provoca pe Y peste două zile (nu îl poate provoca în ziua următoare).
* Dacă 20 < D <= 30, atunci X îl poate provoca pe Y peste trei zile (nu îl poate provoca în următoarele două zile).
* ...
* Dacă 60 < D (fără limită superioară), atunci nu îl poate provoca în următoarele 6 zile (provocarea poate avea loc doar la nivel de săptămână, în acest caz).

Vrăjile se aplică numai pe punctele câștigate dintr-o provocare, nu și pe cele puse la bătaie de fiecare jucător. Astfel, dacă un jucător are o vrajă de tipul "câștigă cu 50% mai mult", pe exemplul 1  descris mai sus, punctajul obținut va fi

	30  + 4 * (1 + 1.5) = 30 + 4*2.5 = 40.

IV. Weekly Quest
----------------

Weekly Quest stimulează gândirea "out of the box", are loc săptămânal și constă în întrebări ce trebuie parcurse succesiv.

Rezolvarea cel puțin a unei întrebări conduce la obținerea de puncte, ce cresc odată cu numarul de întrebări rezolvate.

V. Special Quest
----------------

În Special Quest, jucătorii trebuie să își folosească imaginația, să își arate ambiția și să demonstreze că știu să se descurce.

În fiecare săptămână este propus un set de task-uri, iar finalizarea acestora se face prin prezentarea dovezilor în cadrul cursului de USO de săptămâna viitoare.

Rezolvarea task-urilor din fiecare instanță de Special Quest conduce la obținerea de bani. Banii obținuți diferă între task-uri. Pentru obținerea de bani trebuie ca echipa în ansamblu să rezolve task-urile. Unele task-uri necesită o acțiune din partea fiecărui membru a echipei; banii se acordă doar dacă toți membrii echipei realizează acțiunea în cauză.

VI. Final Quest
---------------


Quest-ul final este sublima aventură a cunoașterii constând din mai multe niveluri care trebuie parcurse succesiv.

Spre deosebire de Weekly Quest, aveți la dispoziție o mașină virtuală în care trebuie să vă faceți de cap :)

Quest-ul final cuprinde cele mai dificile task-uri și are o durată mai lungă decât celelalte quest-uri. Punctajul obținut este mai mare pentru nivelurile superioare și depinde de numărul de jucători ce au ajuns la un anumit nivel; altfel spus, un nivel oferă un punctaj care se împarte participanților ce au atins acel nivel.

Punctajul aferent fiecărui nivel din quest este:

	([(x + 1)/3] + 1) * 20, unde x este nivelul din Quest

Fiecare nivel are asociat un pool de puncte după următoarea formulă:

	200 + 50 * (x + 1), unde x este nivelul din Quest

Acest punctaj este împărțit în mod egal (la finalul jocului) tuturor celor care au reușit să treacă de nivelul respectiv din Quest.

Astfel, dacă  doar 10 persoane reușesc să finalizeze nivelul 9, aceștia vor primi câte 70 de puncte (pentru nivelul 9). Se observă faptul că în această situație numărul de persoane care ajung la nivelul N (unde N > 9) este cu siguranță cel mult 10. Punctele se distribuie pentru fiecare nivel terminat, nu doar pentru ultimul nivel la care s-a ajuns.

Numerotarea nivelurilor începe cu 0.

VII. Raportare de bug-uri
-------------------------

Pentru a raporta probleme și buguri ale WoUSO, vă rugăm să folosiți issue tracker-ele din GitHub. Raportarea de bug-uri valide conduce la obținerea de bani. Informații despre cum se pot raporta bug-uri se găsesc [aici] [1].
[1]: https://github.com/rosedu/wouso-content/wiki/Cum-Raportez-un-bug%3F "aici"

VIII. Propuneri de întrebări
----------------------------

Pentru a câștiga bani pentru vrăji și schimburi puteți propune întrebări pentru "Întrebarea zilei" (Question of the Day), "Provocare" (Challenge) sau "Quest". Întrebările trebuie să fie de tipul celor descrise în cadrul secțiunilor aferente: 4 variante, una singură corectă pentru QotD, multiple variante, multiple variante corecte pentru Challenge și întrebări cu răspuns liber pentru Quest.

Pentru a propune o întrebare accesați [pagina dedicată][2]. Propunerile vor fi analizate și, dacă sunt considerate potrivite, vor fi aprobate. Veți primi bani pentru propunerile aprobate, astfel:
* Întrebarea zilei: 10 bani
* Challenge: 20 de bani
* Quest: 30 de bani

[2]: https://wouso.cs.pub.ro/qproposal/ "pagina dedicată"

IX. Mesaje
----------

Platforma pune la dispoziție un modul pentru transmiterea mesajelor private. Astfel, puteți comunica mult mai ușor cu ceilalți jucători.

X. Altele
---------

Punctajele prag pentru nivele sunt:
* Nivel 2: 920p
* Nivel 3: 1670p
* Nivel 4: 2770p
* Nivel 5: 4420p
* Nivel 6: 10670p
* Nivel 7: 16320p
* Nivel 8: 24820p
* Nivel 9: 37620p

Pentru întrebări, discuții, observații legate de joc, vom folosi forumul WoUSO, disponibil pe cs.curs.pub.ro. Pe acest forum veți putea solicita acceptarea echipelor pentru Special Quest.

Urmăriți, de asemenea, știrile afișate în cadrul paginii de știri a portalului WoUSO.
