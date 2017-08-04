---
title: "Ausf&#252;hren von Windows Phone-Apps im Emulator | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ausf&#252;hren von Windows Phone-Apps im Emulator
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Gilt nur für Windows Phone](~/debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Der Windows Phone\-Emulator ist eine Desktopanwendung, die ein Windows Phone simuliert. Der Emulator stellt eine virtualisierte Umgebung bereit, in der Sie Windows Phone\-Apps auf Ihrem Computer ohne ein physisches Gerät debuggen und testen können. Sie können typische Touch\- und Rotationsereignisse simulieren und die physische Bildschirmgröße und \-auflösung auswählen, die Sie emulieren möchten. Sie können außerdem viele häufig verwendete Features wie Standort, Netzwerk, Benachrichtigungen, Sensoren, den Beschleunigungsmesser und die optionale SD\-Karte testen.  
  
 Weitere Informationen zu den Features, die Sie im Emulator testen können, finden Sie unter [Testen von App\-Features im Windows Phone\-Emulator](http://msdn.microsoft.com/de-de/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 In Kombination mit Visual Studio stellt der Emulator eine vollständige Umgebung bereit, in der Sie Windows Phone\-Apps entwerfen, entwickeln, debuggen und testen können.  
  
## In diesem Thema  
  
-   [Ausführen einer Windows Phone-App im Emulator](#BKMK_run)  
  
    -   [Ausführen einer App über Visual Studio](#BKMK_vs)  
  
    -   [Ausführen einer App mit dem Anwendungsbereitstellungstool](#BKMK_depltool)  
  
-   [Konfigurieren des Windows Phone-Emulators über die Symbolleiste des Emulators](#BKMK_toolbar)  
  
-   [Verwenden der simulierten Hardwaretasten im Emulator](#BKMK_buttons)  
  
-   [Verwenden der Computertastatur mit dem Emulator](#BKMK_tasks_kbd)  
  
-   [Speichern und Laden von benutzerdefinierten Prüfpunkten](#BKMK_checkpoints)  
  
-   [Aufnehmen von Screenshots im Emulator](#BKMK_tasks_shot)  
  
##  <a name="BKMK_run"></a> Ausführen einer Windows Phone\-App im Emulator  
 Während der Entwicklung einer Windows Phone\-App können Sie den Windows Phone\-Emulator verwenden, um die App schnell bereitzustellen und zu testen. Wir empfehlen jedoch, die App auf einem tatsächlichen Windows Phone\-Gerät zu testen, bevor Sie die App im Windows Phone Store veröffentlichen. Damit können Sie Ihre App verwenden, wie Benutzer es tun würden.  
  
 Wenn Sie eine Windows Phone\-App zum ersten Mal im Windows Phone\-Emulator ausführen, finden die folgenden Ereignisse statt:  
  
1.  Der Emulator wird gestartet.  
  
2.  Der Emulator lädt das Windows Phone\-Betriebssystem.  
  
3.  Der Emulator zeigt den Windows Phone\-Startbildschirm an.  
  
4.  Ihre App wird im Emulator bereitgestellt.  
  
5.  Ihre App wird im Emulator ausgeführt.  
  
 Wenn der ausgewählte Emulator bereits ausgeführt wird, wird Ihre App im ausgeführten Emulator bereitgestellt und gestartet. Es kann jeweils nur eine Instanz jedes Emulators ausgeführt werden.  
  
> [!TIP]
>  Wenn Sie Ihre App im Emulator testen, lassen Sie den Emulator zwischen Debugsitzungen geöffnet, damit Sie die App schnell erneut ausführen können.  
  
###  <a name="BKMK_vs"></a> Ausführen einer App über Visual Studio  
  
##### So funktioniert das Bereitstellen und Ausführen einer App über Visual Studio  
  
1.  Öffnen Sie in Visual Studio ein Windows Phone\-Projekt.  
  
2.  Wählen Sie in der Symbolleiste **Standard** eine der Emulatoroptionen aus.  
  
     ![Liste der Bilder des Windows Phone&#45;Emulators](~/debugger/media/wp_emulator_list.png "WP\_Emulator\_list")  
  
3.  Klicken Sie zum Bereitstellen und Ausführen Ihrer App mit Debugging im Menü **Debuggen** auf **Debuggen starten**, oder drücken Sie F5.  
  
     Klicken Sie zum Bereitstellen und Ausführen Ihrer App ohne Debugging im Menü **Debuggen** auf **Starten ohne Debugging**, oder drücken Sie STRG\+F5.  
  
     Ihre App wird bereitgestellt und gestartet.  
  
     Klicken Sie zum Bereitstellen Ihrer App ohne Ausführung im Menü **Erstellen** auf **Projektmappe bereitstellen**.  
  
##### So beenden Sie eine ausgeführte App  
  
-   Gehen Sie wie folgt vor, um eine ausgeführte App zu beenden:  
  
    -   Klicken Sie in Visual Studio im Menü **Debuggen** auf **Debugging beenden**, oder drücken Sie UMSCHALT\+F5.  
  
    -   Klicken Sie im Emulator auf die Schaltfläche **Zurück**, um die App zu beenden. Wenn die aktive Seite der App nicht die Startseite der App war, müssen Sie möglicherweise mehrmals auf die Schaltfläche **Zurück** klicken.  
  
     Die App wird beendet, und der Startbildschirm wird geöffnet. Damit wird die aktuelle Debugsitzung beendet.  
  
##### So starten Sie eine App neu ohne Debugging neu  
  
1.  Streifen Sie im Emulator auf dem Startbildschirm nach links, um die Liste der Apps anzuzeigen.  
  
2.  Tippen Sie in der Liste der Apps auf das App\-Symbol. Die App wird ohne Debugging neu gestartet.  
  
##### So deaktivieren Sie eine ausgeführte App  
  
1.  Klicken Sie vor der Ausführung der App in Visual Studio im Projektmappen\-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** aus, um den **Projekt\-Designer** zu öffnen.  
  
2.  Lassen Sie im **Projekt\-Designer** auf der Seite **Debuggen** das Kontrollkästchen **Tombstone bei Deaktivierung während des Debuggens** deaktiviert, wenn die App bei Deaktivierung in einen Ruhezustand wechseln soll. Aktivieren Sie das Kontrollkästchen, wenn die App bei Deaktivierung in einen Tombstone\-Zustand wechseln soll.  
  
3.  Klicken Sie im Menü **Debuggen** auf **Debugging starten**, oder drücken Sie F5, um die App auszuführen.  
  
4.  Klicken Sie im Emulator auf die Schaltfläche **Starten**. Der Startbildschirm wird angezeigt, und die App wird deaktiviert. Die App wechselt entweder in den Ruhe\- oder den Tombstone\-Zustand, abhängig von der Einstellung des Kontrollkästchens **Tombstone bei Deaktivierung während des Debuggens**.  
  
##### So reaktivieren Sie eine App im Ruhe\- oder Tombstone\-Zustand  
  
-   Klicken Sie im Emulator auf die Schaltfläche **Zurück**, um zur App zurückzukehren. Wenn Sie zu anderen Seiten navigiert sind oder eine andere App geöffnet haben, müssen Sie möglicherweise mehrmals auf die Schaltfläche **Zurück** klicken, um die App zu reaktivieren.  
  
     Die Debugsitzung wird fortgesetzt. Wenn der Debugger von der App getrennt wurde, müssen Sie möglicherweise F5 drücken, um die Debugsitzung fortzusetzen.  
  
###  <a name="BKMK_depltool"></a> Ausführen einer App mit dem Anwendungsbereitstellungstool  
 Sie können auch das Windows Phone\-Anwendungsbereitstellungstool \(**AppDeploy.exe**\) verwenden, um die App im Emulator auszuführen. Dieses Tool ist eine eigenständige App, die bei der Installation der Windows Phone\-Entwicklungstools installiert wird.  
  
 Weitere Informationen finden Sie unter [Bereitstellen von Windows Phone 8.1\-Apps mit dem Anwendungsbereitstellungstool](../Topic/Deploy%20Windows%20Phone%208.1%20apps%20with%20the%20Application%20Deployment%20tool.md).  
  
##  <a name="BKMK_toolbar"></a> Konfigurieren des Windows Phone\-Emulators über die Symbolleiste des Emulators  
 Auf dem folgenden Screenshot sind die auf der Symbolleiste des Emulators verfügbaren Konfigurationsschaltflächen sichtbar.  
  
 f21574ab-5970-4b7a-9281-c13073bf6767  
  
|Schaltflächen auf der Symbolleiste|Konfigurationsoptionen|  
|----------------------------------------|----------------------------|  
|![Eingabeoptionen auf Emulator&#45;Symbolleiste Windows Phone](~/debugger/media/wp_emulator_.png "WP\_Emulator\_")|**Konfigurieren einer Einzel\- oder Multipunkteingabe**<br /><br /> Wenn Sie die Multipunkteingabe aktivieren, können Sie mit der rechten Maustaste klicken, um die Berührungspunkte zu verschieben, ohne den Bildschirm zu berühren. Dann können Sie mit der linken Maustaste klicken, um beide Berührungspunkte gleichzeitig zu verschieben.|  
|![Orientierung auf der Emulator&#45;Symbolleiste Windows Phone](~/debugger/media/wp_emulator_rotation.png "WP\_Emulator\_rotation")|**Konfigurieren der Ausrichtung des Emulators**<br /><br /> Sie können die Ausrichtung im Windows Phone\-Emulator in eine der drei folgenden Ausrichtungen ändern: Hochformat, Querformat links oder Querformat rechts. Die Größe des Emulators wird bei einer Änderung der Ausrichtung nicht geändert.<br /><br /> Klicken Sie zum Ändern der Ausrichtung auf die Schaltfläche **Nach links drehen** oder **Nach rechts drehen**.|  
|![Größenoptionen auf Emulator&#45;Symbolleiste Windows Phone](~/debugger/media/wp_emulator_size.png "WP\_Emulator\_size")|**Konfigurieren der Größe des Emulators**<br /><br /> Sie können die Größe des Emulators auf dem Hostcomputerbildschirm ändern. Die Punkte pro Zoll \(DPI\) für den Emulator basieren auf dem DPI\-Wert des Hostbildschirms, unabhängig vom Zoomwert.<br /><br /> -   Klicken Sie zum Anpassen des Emulators an den Bildschirm auf die Schaltfläche **An Bildschirmgröße anpassen**.<br />-   Zum Ändern der Zoomeinstellungen klicken Sie auf die Schaltfläche **Zoom**. Das Dialogfeld **Zoom** wird geöffnet. Geben Sie im Dialogfeld **Zoom** einen Wert zwischen 33 und 100 ein.|  
  
##  <a name="BKMK_buttons"></a> Verwenden der simulierten Hardwaretasten im Emulator  
 Über die simulierten Hardwaretasten auf der rechten Seite des Emulator\-Bildschirms können Sie die Hardwaretasten eines Telefons simulieren.  
  
-   Klicken Sie auf die **Ein\/Aus**\-Taste, um das Ein\- und Ausschalten des Displays zu simulieren. Klicken und halten Sie die Taste gedrückt, um das Ausschalten des Telefons zu simulieren.  
  
-   Klicken Sie auf **Lauter** oder **Leiser**, um die Lautstärke der Telefonlautsprecher für Anrufe und Benachrichtigungen zu ändern.  
  
-   Mit **Kamera** wird die Kamera\-App gestartet. Sie können die Aufnahme eines Fotos oder Videos mit den Steuerelementen in der Kamera\-App simulieren.  
  
 Der folgende Screenshot zeigt die simulierten Hardwaretasten.  
  
1.  Das linke Bild zeigt den Startbildschirm im Emulator.  
  
2.  Das mittlere Bild zeigt den Emulator nach Antippen der **Ein\/Aus**\-Taste zum Ausschalten des Displays.  
  
3.  Das rechte Bild zeigt den Emulator\-Bildschirm nach Tippen auf die Taste **Lauter** zum Erhöhen der Lautstärke.  
  
 ![Schaltfläche auf Windows Phone&#45;Emulator](~/debugger/media/wp_emulator_buttons.png "WP\_Emulator\_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a> Verwenden der Computertastatur mit dem Emulator  
 Der Emulator unterstützt die Zuordnung der Hardwaretastatur an Ihrem Entwicklungscomputer zur Tastatur auf einem Windows Phone. Das Verhalten der Tasten entspricht dem Verhalten auf einem Windows Phone\-Gerät.  
  
 Standardmäßig ist die Hardwaretastatur nicht aktiviert. Diese Implementierung entspricht einer gleitenden Tastatur, die bereitgestellt werden muss, bevor Sie sie verwenden können. Bevor Sie die Hardwaretastatur aktivieren, akzeptiert der Emulator nur Tasteneingaben von den Steuerelementtasten.  
  
 Sonderzeichen auf der Tastatur einer lokalisierten Version eines Windows\-Entwicklungscomputers werden vom Emulator nicht unterstützt. Verwenden Sie zum Eingeben von Sonderzeichen, die auf einer lokalisierten Tastatur vorhanden sind, stattdessen das Software Input Panel \(SIP\).  
  
#### So verwenden Sie Ihre Computertastatur im Emulator  
  
-   Drücken Sie die BILD\-AUF\-TASTE.  
  
     \- oder \-  
  
-   Drücken Sie die PAUSE\-TASTE.  
  
#### So beenden Sie die Verwendung der Hardwaretastatur auf dem Computer im Emulator  
  
-   Drücken Sie die BILD\-AB\-TASTE.  
  
     \- oder \-  
  
-   Drücken Sie die PAUSE\-TASTE.  
  
 In der folgenden Tabelle sind die Tasten auf einer Hardwaretastatur aufgeführt, die Sie zum Emulieren der Tasten und anderer Steuerelemente auf einem Windows Phone verwenden können.  
  
|Computerhardwaretaste|Windows Phone\-Taste|Hinweise|  
|---------------------------|--------------------------|--------------|  
|F1|ZURÜCK|Langes Drücken funktioniert erwartungsgemäß.|  
|F2|START|Langes Drücken funktioniert erwartungsgemäß.|  
|F3|SUCHE||  
|F4|Nicht zutreffend.||  
|F5|Nicht zutreffend.||  
|F6|KAMERA HALB|Eine dedizierte Kamerataste, die halb heruntergedrückt wird.|  
|F7|KAMERA GANZ|Eine dedizierte Kamerataste.|  
|F8|Nicht zutreffend.||  
|F9|LAUTER||  
|F10|LEISER||  
|F11|Nicht zutreffend.||  
|F12|EIN\/AUS|Drücken Sie F12 zweimal, um den Sperrbildschirm zu aktivieren.<br /><br /> Langes Drücken funktioniert erwartungsgemäß.|  
|ESC|ZURÜCK|Langes Drücken funktioniert erwartungsgemäß.|  
|PAUSE|Tastaturwechsel|Wechselt die Hardwaretastatur.|  
|BILD\-AUF|Tastatur auf|Aktiviert die Hardwaretastatur.|  
|BILD\-AB|Tastatur ab|Deaktiviert die Hardwaretastatur.|  
  
##  <a name="BKMK_checkpoints"></a> Speichern und Laden von benutzerdefinierten Prüfpunkten  
 Speichern Sie eine Momentaufnahme des Emulator\-Zustands über die Registerkarte **Prüfpunkte** der **Zusätzlichen Tools** im Emulator. Dieses Feature ist nützlich, wenn Sie Ihre App häufig mit denselben Daten und Einstellungen testen.  
  
 Wenn für die App beispielsweise mehrere Kontakte erforderlich sind, können Sie den Kontaktdatensatz einmal erstellen und dann eine Momentaufnahme des Emulators speichern. Andernfalls müssten Sie den Kontaktdatensatz bei jedem Starten des Emulators erneut erstellen.  
  
-   Klicken Sie auf **Neuer Prüfpunkt**, um die neue Momentaufnahme des Emulator\-Zustands mit den für das spätere Testen der App erneut erforderlichen Daten und Einstellungen zu erfassen. Der neue Prüfpunkt wird zur Liste **Prüfpunkte** hinzugefügt.  
  
     Sie können einen Prüfpunkt erfassen, während der Debugger mit dem Emulator verbunden ist.  
  
-   Wählen Sie einen Prüfpunkt aus der Liste **Prüfpunkte** aus, um Informationen zum Prüfpunkt anzuzeigen.  
  
-   Aktivieren Sie das Optionsfeld in der Spalte **Standard**, um einen gespeicherten Prüfpunkt zum Standardprüfpunkt für den aktiven Emulator zu machen.  
  
-   Klicken Sie auf **Wiederherstellen**, um das Windows Phone\-Betriebssystem auf dem Emulator neu zu starten und die ausgewählte Momentaufnahme zu laden.  
  
-   Klicken Sie auf **Löschen**, um eine Momentaufnahme zu löschen, die Sie nicht mehr benötigen.  
  
 Das ursprüngliche Emulatorabbild wird immer als erstes Element in der Liste **Prüfpunkte** angezeigt und kann weder geändert noch gelöscht werden. Sie können jedoch eine andere Momentaufnahme als standardmäßiges Emulatorabbild auswählen.  
  
 ![Registerkarte Prüfpunkt auf Windows Phone&#45;Emulator](~/debugger/media/wp_emulator_checkpoints.png "WP\_Emulator\_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a> Aufnehmen von Screenshots im Emulator  
 Sie können Screenshots Ihrer Windows Phone\-Apps mithilfe des Screenshottools bei den zusätzlichen Tools erstellen. Das Tool erstellt PNG\-Dateien, die der Auflösung des ausgeführten Emulators entsprechen.  
  
 ![Bildschirmfotos des Windows Phone&#45;Emulators](~/debugger/media/wp_emulator_screenshots.png "WP\_Emulator\_screenshots")  
  
#### So erstellen Sie einen App\-Screenshot über das in den Emulator integrierte Screenshottool  
  
1.  Zum Optimieren der Qualität Ihrer Screenshots legen Sie die Zoomstufe des Emulators auf 100 % fest. Je höher Sie die Zoomstufe setzen, umso besser ist die Qualität des Screenshots.  
  
2.  Starten Sie Ihre App im Emulator.  
  
3.  Klicken Sie auf der Emulator\-Symbolleiste auf die Schaltfläche zum Erweitern, um das Fenster **Zusätzliche Tools** zu öffnen.  
  
4.  Klicken Sie auf die Registerkarte **Screenshot**.  
  
5.  Wenn die App bereit ist, klicken Sie auf die Schaltfläche **Aufnehmen**.  
  
     Der Screenshot wird im Arbeitsbereich angezeigt.  
  
6.  Klicken Sie auf die Schaltfläche **Speichern**, um das Dialogfeld **Speichern unter** zu öffnen.  
  
7.  Wählen Sie den gewünschten Speicherort und **Dateinamen** aus, und klicken Sie dann auf **Speichern**.  
  
8.  Navigieren Sie optional zu anderen Seiten in der App, und nehmen Sie weitere Screenshots auf.  
  
9. Starten Sie einen Emulator mit einer anderen Bildschirmauflösung, um dieselben Screenshots mit einer anderen Auflösung aufzunehmen. Wenn Sie die App mit Debugging ausgeführt haben, müssen Sie das Debugging beenden, bevor Sie die App erneut in einem anderen Emulator ausführen können.  
  
 Deaktivieren Sie die Frameratenzähler auf dem Emulator\-Bildschirm, bevor Sie Screenshots aufnehmen, die an den Windows Phone Store übermittelt werden.  
  
#### So deaktivieren Sie Frameratencounter im Emulator, bevor Sie Screenshots aufnehmen  
  
-   Geben Sie einen Releasebuild in Visual Studio an. Starten Sie Ihre App nach dem Angeben eines Releasebuilds, indem Sie den Link **Bereitstellen von *\[App\-Name\]*** im Menü **Erstellen** auswählen.  
  
-   Alternativ können Sie die Codezeile in der Datei "app.xaml.cs" oder "app.xaml.vb" auskommentieren, die den Wert von `EnableFrameRateCounter` auf `true` festlegt.