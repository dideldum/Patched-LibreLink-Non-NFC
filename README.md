# Kontinuierliche Glukose-Anzeige des Libre 2 auf Smartphone ohne NFC

## 1. Einleitung 
Mit dem Libre 2 Sensor werden minütlich die Glukosewerte
zu einem Empfangsgerät übertragen.

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

## 2. Warum nicht ein normales Smartphone verwenden?
Unsere Tochter ist 6 Jahre alt und soll vom Diabetes so wenig wie möglich merken.

Da wir loopen (also die Sensor-Werte mit Hilfe eines Programms zur automatischen Steuerung der Insulinpumpe verwenden), brauchen wir entsprechende Hardware. Und die muss so klein und unmerkbar wie möglich sein.

Idealerweise würde unsere Tochter eine Full Android Uhr im Bauchband haben, aber noch ist das Miniphone die am besten handhabbare Lösung.

Ein normales Smartphone würde immer irgendwo liegen bleiben. Ein Miniphone wie das Melrose 2019, das Ulcool U2 oder einige andere (Soyes, Anica, Melrose und Ulcool sind die vier mir bekannten Miniphone-Marken) lässt sich gut in eine Tasche im Bauchband zur Pumpe stecken und ist dann immer dabei.

## 3. Gibt es keine Miniphones mit NFC?
Mir bekannt ist nur ein aktuelles: Das Unihertz Atom. Das ist mit 250€ aber sehr teuer. Und es ist dicker und schwerer als das Melrose 2019.

Die chinesischen Miniphones wie die von uns verwendeten liegen im 70€-100€ Bereich. Und das von uns für unsere Tochter präferierte Melrose 2019 ist nur halb so dick wie das Atom und 40g leichter.

## 4. Was brauche ich?
- Ein Smartphone mit Mediatek (MTK) Prozessor mit NFC, das zum Starten des Libre 2 verwendet wird. Es geht sicherlich auch mit einem Qualcomm Prozessor, das benötigt aber andere Software und wurde von mir nicht getestet.
- Das Miniphone (ohne NFC) mit Mediatek (MTK) Prozessor, mit dem ich die Werte dann kontinuierlich bekomme. Zum Prozessor gilt das vorher gesagte.
- Ein passendes USB-Kabel für jedes der beiden Smartphones, um es mit dem PC zu verbinden. 
- Einen PC
- Die PC-Programme [WwR MTK](./WWR_MTK_2.51.zip) und [SP Flash Tool](./SP_Flash_Tool_v5.1924_Win.zip) sowie die [MTK Preloader Treiber](./MTK_USB_All_v1.0.8.zip). Die hier verlinkten Dateien sind die zum Erstellungszeitpunkt neuesten, die ich gefunden und bei mir installiert habe. Möglicherweise gibt es jetzt neuere. Bitte selbst nach Aktualisierungen suchen.
- Die gepatchte LibreLink. Diese muss allerdings noch zusätzlich mehr
  gepatcht werden, damit sie auch auf einem Smartphone ohne NFC läuft.
  Die Anleitung für den grundsätzlichen Patch findet man im Original
  (englisch) [hier](https://github.com/jcwarrior/Libre2-patched-App). 
  
  Tino Kossmann hat für ein Linux-System daraus einen automatisierten
  Patch-Ablauf gemacht, den man
  [hier](https://github.com/TinoKossmann/LibreLink-xDrip-Patch) findet.
  Allerdings ist hier meine manuelle Änderung nicht eingearbeitet, so
  dass die so erstellte APK nicht auf dem Miniphone ohne NFC läuft.
  Derzeit muss nach der englischen Original-Anleitung vorgegangen
  werden.

## 5. Vorbereitung
### 5.1. Auf dem PC
Die Programme WWR MTK und SP Flash Tool müssen in einen Ordner entpackt werden, die MTK Treiber müssen installiert werden.
### 5.2. Auf den beiden Smartphones
Die Entwickleroptionen müssen angeschaltet werden und "USB Debugging" muss aktiviert werden.
- Um die Entwickleroptionen anzuschalten, geht man in den Android Einstellungen des Smartphones typischerweise in die "System"-Seite, dort "Über das Telefon" und dann tippt man mehrere Male auf "Build-Nummer". Wenn man das oft genug gemacht hat, erscheint eine Meldung, die etwa besagt "Sie sind jetzt Entwickler".
Danach ist in den Einstellungen normalerweise auf der "System"-Seite ein neuer Eintrag "Entwickler-Optionen" sichtbar. Bei einigen Smartphones (wie meinem Xiaomi Mi9SE) sind die "Über das Telefon"-Seite und die "Entwickler-Optionen" an anderer Stelle in den Android Einstellungen aufgeführt. Das mag also bei einigen Smartphones etwas anders gestaltet sein als hier beschrieben.
- Sind die Entwickleroptionen angeschaltet, geht man in diese Seite in den Einstellungen. Dort findet man dein Schalter für "USB-Debugging". Der muss angestellt werden.

## 6. Durchführung 

### 6.1. Erweitertes Patchen der LibreLink
#### Nach der englischen Originalanleitung
Man führt die Patch-Anleitung normal aus. Bevor man aber den Punkt "Rebuild the APK" durchführt, ändert man von Hand noch eine Datei.
Diese befindet sich im Patch-Verzeichnis im Unterverzeichnis "`librelink\smali_classes2\com\librelink\app\util`". Hier die Datei `NfcUtils.smali` mit einem Text-Editor öffnen.

Man sieht hier drei Methoden (die Zeilen beginnen mit `.method`, die Methode endet dann mit `.end method`). Die letzten zwei Methoden `isNfcEnabled` und `ìsNfcSupported` müssen geändert werden, so dass der gesamte Text dieser Methoden so aussieht:

    .method public static isNfcEnabled(Landroid/content/Context;)Z
        .locals 0

	    const/4 p0, 0x1
	    return p0
    .end method
    
    .method public static isNfcSupported(Landroid/content/Context;)Z
        .locals 0
    
    	const/4 p0, 0x1
	    return p0
    .end method `

Wenn diese Textänderung vorgenommen wurde, wird die Datei gespeichert
und man kann mit dem Punkt "Rebuild the APK" fortfahren.

Diese so veränderte LibreLink läuft nun auch auf Smartphones ohne NFC.
Natürlich kann sie auf einem Smartphone ohne NFC den Libre nicht
scannen. Für das Smartphone mit NFC macht diese Änderung keinen
merkbaren Unterschied, hier wird die LibreLink ganz normal
funktionieren.

#### Nach der deutschen Anleitung von Tino Kossmann
Noch nicht implementiert.

### 6.2. Backup der Smartphone-ROMs
Das Backup der Smartphones muss natürlich getrennt voneinander
stattfinden. Ich beschreibe hier den grundlegenden Vorgang. Für jedes
Smartphone muss ein eigenes Verzeichnis angelegt werden, in dem das
ROM-Backup gespeichert wird. Diese beiden Verzeichnisse dürfen nicht
vermischt werden und sollten so gesichert werden, dass ein Rückspielen
auf das Smartphone jederzeit möglich ist.

**Insbesondere ist zu beachten, dass die individuellen Parameter des
NFC-Smartphones (IMEI, Wlan-MAC, Bluetooth-MAC, etc.) in Folge mit denen
des Nicht-NFC-Miniphones überschrieben werden! Damit entstehen zwei
Smartphones, die für einen Telefonie-Provider, das Wlan oder andere
Bluetooth-Geräte völlig gleich aussehen. Damit das NFC-Smartphone wieder
in seinen originalen Zustand zurückversetzt werden kann, ist eine
Sicherung seines ROMS, besonders der individualisierenden Teile,
unbedingt notwendig! **

#### 6.2.1. Extrahieren des Preloaders 
