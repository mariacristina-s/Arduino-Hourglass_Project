# Arduino-Hourglass_Project
Sima Maria-Cristina, grupa 331AB - 
Proiect la Sisteme cu Microprocesoare

# Introducere
Proiectul are rolul de a simula funcționarea unei clepsidre. 

Ansamblul de componente este format din: 
- plăcuță Arduino UNO,
- senzor giroscopic și accelerometru ADXL335 cu 3 axe,
- 2 matrici LED MAX7219 de 8x8,
- cablurile folosite pentru legarea componentelor.

Pentru rularea și încărcarea codului pe plăcuță, este necesară crearea unui fișier numit ”hourglass”, care să conțină: hourglass.ino, Delay.h, Delay.cpp, LedControl.h, LedControl.cpp.

# Modulul cu accelerometrul ADXL335
Accelerometrul este un echipament/o piesă/un senzor, care oferă 
posibilitatea măsurării și analizării accelerației liniare și
unghiulare, fiind necesar în multe sisteme de bază din diverse
domenii. El este utilizat pentru a determina unghiul de înclinare
a obiectului măsurat față de planul vertical și pentru a măsura
accelerația dinamică produsă ca rezultat a mișcării/vibrațiilor.

Accelerometrul ADXL335 este un accelerometru pe 3 axe, cu un 
consum de putere scăzut (320 uA), de dimensiuni mici, potrivit
pentru detectarea basculării obiectelor. El măsoară accelerația
de-a lungul axelor X, Y și Z, și oferă output analog proporțional cu accelerația de-a lungul celor 3 axe.


![image](https://user-images.githubusercontent.com/100774960/168488721-0dcf66a2-9175-48f1-9443-6d5b90566b37.png)

# Modulul cu cele 2 matrici LED MAX7219 8x8
![image](https://user-images.githubusercontent.com/100774960/168489053-2056076c-4646-40c8-a429-c98aa730d13e.png)

# Schema circuitului
![image](https://user-images.githubusercontent.com/100774960/168489196-13d4d977-99e6-4134-ab10-f30e747bb60b.png)

# Descriere
Circuitul funcționează pentru a simula funcționarea unei clepsidre. ”Particulele” (elementele matricelor de 8x8),
care țin locul nisipului unei clepsidre obișnuite, vor cădea una câte una, pe rând, dintr-o matrice în alta, în 
funcție de înclinația și de direcția în care se află ansamblul. Particulele din matrici cad cu un delay (destul de) 
mic, pentru a ”imita” funcționarea realistă a unei clepsidre (dar viteza de cădere a particulelor poate fi schimbată cu ușurință din cod). Particulele trebuie să se mute pe display-ul 
matricii în funcție de direcția în care trebuie să meargă:
- în jos, linia va scădea, iar coloana va crește (x = x-1, y = y+1)
- în stânga, linia va scădea, iar coloana va rămâne la fel (x = x-1)
- în dreapta, coloana va crește, iar linia va rămâne la fel (y = y+1).
Înainte ca fiecare particulă să ”cadă”, se va verifica poziția care nu este deja ocupată de altă particulă, cu 
ajutorul a 3 funcții (canGoLeft, canGoRight și canGoDown). Dacă locația respectivă este liberă, particula se ”va
muta” acolo. Citirea de la senzorul accelerometru este dată de funcția getGravity(), care citește coordonatele
x și y pentru a determina înclinarea. Luminozitatea matricilor LED este minimă (dar și aceasta se poate modifica din cod).

# Direcții de dezvoltare
Pentru un proiect mai amplu, s-ar putea adăuga și o alarmă, care să anunțe utilizatorul când timpul s-a scurs, sau un display, pe care să se afișeze câte secunde mai sunt până timpul se scurge.
