# SystemEngineeringLab
Hier is een overzicht van de verschillende stappen die genomen werden om een apache2 website online te zetten vanaf een Ubuntu Virtual Machine. Later wordt deze website beveiligd met https.

Eerst werd apache2 geïnstalleerd. Na het installeren werd er gekeken op welke poort deze luistert met het commando "sudo ss -tlnp".
Er werd vastgesteld dat deze meteen luistert naar alle netwerken en niet enkel naar de loopback-interface.
De website was meteen raadpleegbaar zowel binnen als buiten de VM.

De nieuwe website in de Document Root zetten (met behulp van unzip commando). De website files werden via mail vanaf het fysiek systeem doorgestuurd naar de VM
(https://user-images.githubusercontent.com/92029627/160095506-2bd325c8-6f67-4de6-90c0-cde455d73466.png)

Openssh installeren:
file:///home/osboxes/Pictures/Screenshot%20from%202022-03-22%2003-40-04.png![image](https://user-images.githubusercontent.com/92029627/160095850-4586c39a-633c-42d2-9f52-fe1d28ec046b.png)

Kijken of de ssh server active is:
file:///home/osboxes/Pictures/Screenshot%20from%202022-03-22%2003-48-33.png![image](https://user-images.githubusercontent.com/92029627/160095974-d6e4ccdf-5c90-4fa9-89d8-544c9af695f2.png)

Kijken op welke poort de ssh server staat:
file:///home/osboxes/Pictures/Screenshot%20from%202022-03-22%2003-48-42.png![image](https://user-images.githubusercontent.com/92029627/160096111-10eb9b90-f609-479b-be52-2dcffda4725c.png)

config file aanpassen
file:///home/osboxes/Pictures/Screenshot%20from%202022-03-25%2006-21-42.png![image](https://user-images.githubusercontent.com/92029627/160102860-a90b10d1-ae30-45f5-8714-39dcd5711877.png)


Certificate voor https in orde brengen
trash:///Screenshot%20from%202022-03-25%2005-35-13.png![image](https://user-images.githubusercontent.com/92029627/160101941-3297c295-38e7-4f67-96c3-457673d8e5b9.png)


Juiste config file op enable zetten.
trash:///Screenshot%20from%202022-03-25%2005-35-26.png![image](https://user-images.githubusercontent.com/92029627/160102312-c5cafca3-5916-4446-a4c5-d89e029d177e.png)


Probleem met ufw, blijkt dat deze al geïnstalleerd was.
trash:///Screenshot%20from%202022-03-25%2005-35-36.png![image](https://user-images.githubusercontent.com/92029627/160102112-f5c7e3f2-93a2-4789-b104-9e5b87bc14ae.png)

De firewall in orde brengen.
trash:///Screenshot%20from%202022-03-25%2005-35-54.png![image](https://user-images.githubusercontent.com/92029627/160102417-6188fdc7-95eb-457c-babc-3c6c87efc805.png)

