# Kontinuierliche Glukose-Anzeige des Libre 2 auf Smartphone ohne NFC

## Einleitung
Mit dem Libre 2 Sensor werden minütlich die Glukosewerte zu einem Empfangsgerät übertragen.

Die Standardlösung von Abbott mit der originalen LibreLink App erlaubt dabei, dass auf dem Smartphone Alarme ausgelöst werden können.
Der Benutzer sieht aber keine Werte - dafür muss er mit dem NFC-fähigen Smartphone oder dem Lesegerät scannen.
Findige IT-Spezialisten haben die LibreLink App so verändert, dass man die Werte, die ja sowieso minütlich auf dem Smartphone von der LibreLink App empfangen werden, an xDrip+ weitergeleitet wrden können.
Dort werden sie (regulär im 5-Minuten-Takt, in einer zusätzlichen Detailansicht aber auch mit den minütlichen Werten) kontinuierlich angezeigt.
 
Damit das funkioniert, muss dieses Smartphone NFC haben. Denn der Libre 2 sendet die minütlichen Werte per Bluetooth nur an das Smartphone (oder Abbott-Lesegerät), mit dem er gestartet wird.
Deshalb darf man den Libre 2 auch nicht mit dem Lesegerät starten, wenn man die Werte kontinuierlich auf dem Smartphone haben will. Nur das Startgerät erhält die kontinuierlichen Werte.

Nun haben wir bei uns seit 2 Jahren speziell bei unserer Tochter, aber auch bei mir selbst, möglichst Mini-Lösungen in Betrieb.

Im Grunde soll (und kann auch!) eine Full Android Smartwatch (wie sie von Herstellern wie Kospet, Finow, Lemfo, Microwear, Zeblaze und anderen angeboten wird) den Empfang der Glukosewerte vom Sensor erledigen.

Zusätzlich soll dann unsere Pumpe im Closed Loop gesteuert werden. Leider ist das von uns verwendete AndroidAPS nicht auf einer Full Android Uhr bedienbar, weshalb wir im Moment Miniphones einsetzen.

Wir haben also jetzt das Melrose 2019 bei meiner Tochter und das Ulcool U2 bei mir in Betrieb.

Diese Miniphones sind wunderbar für das Diabetes-Management. Sie haben für den Libre 2 nur einen Fehler: Sie haben kein NFC. Also können sie den Libre 2 nicht starten.

Mit etwas technischem Aufwand ist es jedoch möglich, den Libre mit einem NFC-fähigen Smartphone zu starten und die damit erstellte Bluetooth-Verbindung vom Starter-Handy auf das Miniphone ohne NFC zu übertragen.

## Warum nicht ein normales Smartphone verwenden?
Unsere Tochter ist 6 Jahre alt und soll vom Diabetes so wenig wie möglich merken.

Da wir loopen (also die Sensor-Werte mit Hilfe eines Programms zur automatischen Steuerung der Insulinpumpe verwenden), brauchen wir entsprechende Hardware. Und die muss so klein und unmerkbar wie möglich sein.

Idealerweise würde unsere Tochter eine Full Android Uhr im Bauchband haben, aber noch ist das Miniphone die am besten handhabbare Lösung.

Ein normales Smartphone würde immer irgendwo liegen bleiben. Ein Miniphone wie das Melrose 2019, das Ulcool U2 oder einige andere (Soyes, Anica, Melrose und Ulcool sind die vier mir bekannten Miniphone-Marken) lässt sich gut in eine Tasche im Bauchband zur Pumpe stecken und ist dann immer dabei.

## Gibt es keine Miniphones mit NFC?
Mir bekannt ist nur eines: Das Unihertz Atom. Das ist mit 250€ aber sehr teuer.

Die chinesischen Miniphones wie die von uns verwendeten liegen im 70€-100€ Bereich. Und das von uns für unsere Tochter präferierte Melrose 2019 ist nur halb so dick wie das Atom und 40g leichter.

## Was brauche ich?
- Ein Smartphone mit Mediatek (MTK) Prozessor mit NFC, das zum Starten des Libre 2 verwendet wird. Es geht sicherlich auch mit einem Qualcomm Prozessor, das benötigt aber andere Software und wurde von mir nicht getestet.
- Das Miniphone (ohne NFC) mit Mediatek (MTK) Prozessor, mit dem ich die Werte dann kontinuierlich bekomme. Zum Prozessor gilt das vorher gesagte. 
- Einen PC
- Die PC-Programme [WwR MTK](./WWR_MTK_2.51.zip) und [SP Flash Tool](./SP_Flash_Tool_v5.1924_Win.zip) sowie die [MTK Preloader Treiber](./MTK_USB_All_v1.0.8.zip) 

## Vorbereitung
