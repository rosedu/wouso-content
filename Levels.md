Niveluri punctaj
================

Sunt 10 niveluri pe rasă pentru cazul în care se acumulează foarte multe puncte.

Punctaj de start
----------------

Propunerea de punctaj de start se bazează pe ideea de a oferi suficiente puncte cât să le permită participanților să facă față pentru două săptămâni, chiar dacă pierd multe provocări. Altfel spus, răspunzând corect la toate întrebările zilei și pierzând toate provocările lansate și o posibilă provocare primită, să ajungă pe zero. Se presupune notația:

* S: punctaj de start
* Q: punctaj pe întrebarea zilei
* P: punctaj pe provocare (pierdută sau câștigată)

Rezultă ecuația:

	S + 14 * Q - 2 * 14 * P = 0

(14 zile = 2 săptămâni)

Fie punctajele: Q = 30 și P = 30; rezultă:

	S + 14 * 30 - 2 * 14 * 30 = 0 -> S = 420

Praguri
-------

Sunt necesare 500 de puncte pentru atingerea celui de-al doilea nivel. Pentru ajunge la nivelul următor (trei), este nevoie de 500 * 1.5 = 750 de puncte. Pentru a ajunge la nivelul patru sunt necesare 750 * 1.5 puncte, etc. Generalizat, pentru a ajunge la nivelul N (de la nivelul N-1) este nevoie de acumularea a 500 * 1.5^(N-2) puncte.

Rezultă următoarele praguri:

* Nivel 2: 920
* Nivel 3: 1670
* Nivel 4: 2770
* Nivel 5: 4420
* Nivel 6: 6920
* Nivel 7: 10670
* Nivel 8: 16320
* Nivel 9: 24820
* Nivel 10: 37620

Program bc pentru realizarea task-ului:

	for (i = 2; i <= 10; i++) {s=s+500*((1.5)^(i-2)); s}

Denumire niveluri
-----------------

**Oxynia**

1. Învățăcel/Student
2. Ucenic/Apprentice
3. Discipol/Disciple
4. Cărturar/Scholar
5. Cercetător/Researcher
6. Maestru/Master
7. Eminent
8. Omniscient
9. Mentalist
10. Transcend

h3. Zota

1. Matelot/Sailor
2. Navigator
3. Cârmaci/Helmsman
4. Corsar/Corsair
5. Căpitan/Captain
6. Explorator/Explorer
7. Amiral/Admiral
8. Cinetic/Kinetic
9. Mach
10. Teleportor/Teleporter

h3. Nifes

1. Calfă/Journeyman
2. Tâmplar/Carpenter
3. Sticlar/Glazier
4. Armurier/Armorer
5. Bijutier/Jeweler
6. Proiectant/Desigenr
7. Arhitect/Architect
8. Alchimist/Alchemist
9. Elementalist
10. Demiurg/Demiurge
