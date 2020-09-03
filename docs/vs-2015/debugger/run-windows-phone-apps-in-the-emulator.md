---
title: Ausführen von Windows Phone-apps im Emulator | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5673ebf28cc652e3bcd973808db87b5bb058659c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683526"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Ausführen von Windows Phone-Apps im Emulator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Windows Phone-Emulator stellt eine virtualisierte Umgebung bereit, in der Sie Windows Phone-Apps auf Ihrem Computer ohne ein physisches Gerät debuggen und testen können. Sie können typische Touch- und Rotationsereignisse simulieren und die physische Bildschirmgröße und -auflösung auswählen, die Sie emulieren möchten. Sie können außerdem viele häufig verwendete Features wie Standort, Netzwerk, Benachrichtigungen, Sensoren, den Beschleunigungsmesser und die optionale SD-Karte testen.  
  
 Weitere Informationen zu den Funktionen, die Sie im Emulator testen können, finden Sie unter [Testen von App-Features in Windows Phone Emulator](https://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 In Kombination mit Visual Studio stellt der Emulator eine vollständige Umgebung bereit, in der Sie Windows Phone-Apps entwerfen, entwickeln, debuggen und testen können.  
  
## <a name="run-a-windows-phone-app-in-the-emulator"></a><a name="BKMK_run"></a> Ausführen einer Windows Phone-App im Emulator  
 Während der Entwicklung einer Windows Phone-App können Sie den Windows Phone-Emulator verwenden, um die App schnell bereitzustellen und zu testen. Wir empfehlen jedoch, die App auf einem tatsächlichen Windows Phone-Gerät zu testen, bevor Sie die App im Windows Phone Store veröffentlichen. Damit können Sie Ihre App verwenden, wie Benutzer es tun würden.  
  
 Wenn Sie eine Windows Phone-App zum ersten Mal im Windows Phone-Emulator ausführen, finden die folgenden Ereignisse statt:  
  
1. Der Emulator wird gestartet.  
  
2. Der Emulator lädt das Windows Phone-Betriebssystem.  
  
3. Der Emulator zeigt den Windows Phone-Startbildschirm an.  
  
4. Ihre App wird im Emulator bereitgestellt.  
  
5. Ihre App wird im Emulator ausgeführt.  
  
   Wenn der ausgewählte Emulator bereits ausgeführt wird, wird Ihre App im ausgeführten Emulator bereitgestellt und gestartet. Es kann jeweils nur eine Instanz jedes Emulators ausgeführt werden.  
  
> [!TIP]
> Wenn Sie Ihre App im Emulator testen, lassen Sie den Emulator zwischen Debugsitzungen geöffnet, damit Sie die App schnell erneut ausführen können.  
  
### <a name="run-an-app-from-visual-studio"></a><a name="BKMK_vs"></a> Ausführen einer APP in Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>So funktioniert das Bereitstellen und Ausführen einer App über Visual Studio  
  
1. Öffnen Sie in Visual Studio ein Windows Phone-Projekt.  
  
2. Wählen Sie auf der Symbolleiste **Standard** eine der Emulatoroptionen aus.  
  
     ![Liste der Bilder des Windows Phone-Emulators](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3. Klicken Sie zum Bereitstellen und Ausführen der APP mit Debuggen im Menü **Debuggen** auf **Debugging starten**, oder drücken Sie F5.  
  
     Klicken Sie im Menü **Debuggen** auf **Starten ohne Debugging**, oder drücken Sie STRG + F5, um die APP ohne Debuggen bereitzustellen und auszuführen.  
  
     Ihre App wird bereitgestellt und gestartet.  
  
     Klicken Sie im Menü **Erstellen** **auf Projekt**Mappe bereitstellen, um Ihre APP ohne Ausführung bereitzustellen.  
  
##### <a name="to-stop-a-running-app"></a>So beenden Sie eine ausgeführte App  
  
- Gehen Sie wie folgt vor, um eine ausgeführte App zu beenden:  
  
  - Klicken Sie in Visual Studio im Menü **Debuggen** auf **Debuggen Debuggen**, oder drücken Sie UMSCHALT + F5.  
  
  - Klicken Sie im Emulator auf die Schaltfläche **zurück** , um die APP zu beenden. Wenn die aktive Seite der APP nicht die Startseite der APP war, müssen Sie möglicherweise mehrmals auf die Schaltfläche " **zurück** " klicken.  
  
    Die App wird beendet, und der Startbildschirm wird geöffnet. Damit wird die aktuelle Debugsitzung beendet.  
  
##### <a name="to-restart-an-app-without-debugging"></a>So starten Sie eine App neu ohne Debugging neu  
  
1. Streifen Sie im Emulator auf dem Startbildschirm nach links, um die Liste der Apps anzuzeigen.  
  
2. Tippen Sie in der Liste der Apps auf das App-Symbol. Die App wird ohne Debugging neu gestartet.  
  
##### <a name="to-deactivate-a-running-app"></a>So deaktivieren Sie eine ausgeführte App  
  
1. Klicken Sie vor dem Ausführen der app in Visual Studio mit der rechten Maustaste auf das Projekt in Projektmappen-Explorer, und wählen Sie dann **Eigenschaften** aus, um den **Projekt-Designer**zu öffnen.  
  
2. Lassen Sie im **Projekt-Designer**auf der Seite **Debuggen** das Kontrollkästchen **Tombstone bei Deaktivierung während des Debuggens** deaktiviert, wenn die APP bei Deaktivierung in einen Ruhezustand versetzt werden soll. Aktivieren Sie das Kontrollkästchen, wenn die App bei Deaktivierung in einen Tombstone-Zustand wechseln soll.  
  
3. Klicken Sie im Menü **Debuggen** auf **Debugging starten**, oder drücken Sie F5, um die APP auszuführen.  
  
4. Klicken Sie im Emulator auf die Schaltfläche **Start** . Der Startbildschirm wird angezeigt, und die App wird deaktiviert. Die APP wechselt entweder in den Ruhezustand oder ist abhängig von der Einstellung des Kontrollkästchens **Tombstone bei Deaktivierung während des Debuggens** ein tombstoning.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>So reaktivieren Sie eine App im Ruhe- oder Tombstone-Zustand  
  
- Klicken Sie im Emulator auf die Schaltfläche **zurück** , um zur APP zurückzukehren. Wenn Sie zu anderen Seiten navigiert sind oder eine andere APP geöffnet haben, müssen Sie möglicherweise mehrmals auf die Schaltfläche " **zurück** " klicken, um die APP erneut zu aktivieren.  
  
     Die Debugsitzung wird fortgesetzt. Wenn der Debugger von der App getrennt wurde, müssen Sie möglicherweise F5 drücken, um die Debugsitzung fortzusetzen.  
  
### <a name="run-an-app-with-the-application-deployment-tool"></a><a name="BKMK_depltool"></a> Ausführen einer APP mit dem Anwendungs Bereitstellungs Tool  
 Sie können auch das Windows Phone Anwendungs Bereitstellungs Tool (**AppDeploy.exe**) verwenden, um die APP im Emulator auszuführen. Dieses Tool ist eine eigenständige App, die bei der Installation der Windows Phone-Entwicklungstools installiert wird.  
  
 Weitere Informationen finden Sie unter Bereitstellen von [Windows Phone 8,1-apps mit dem Anwendungs Bereitstellungs Tool](https://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
## <a name="configure-the-windows-phone-emulator-with-the-emulator-toolbar"></a><a name="BKMK_toolbar"></a> Konfigurieren des Windows Phone Emulators mit der Emulator-Symbolleiste  
 In dieser Tabelle sind die auf der Symbolleiste des Emulators verfügbaren Konfigurationsschaltflächen sichtbar.  
  
|Schaltflächen auf der Symbolleiste|Konfigurationsoptionen|  
|---------------------|---------------------------|  
|![Eingabeoptionen auf Emulator-Symbolleiste Windows Phone](../debugger/media/wp-emulator.png "WP_Emulator_")|**Konfigurieren einer Einzel- oder Multipunkteingabe**<br /><br /> Wenn Sie die Multipunkteingabe aktivieren, können Sie mit der rechten Maustaste klicken, um die Berührungspunkte zu verschieben, ohne den Bildschirm zu berühren. Dann können Sie mit der linken Maustaste klicken, um beide Berührungspunkte gleichzeitig zu verschieben.|  
|![Orientierung auf der Emulator-Symbolleiste Windows Phone](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Konfigurieren der Ausrichtung des Emulators**<br /><br /> Sie können die Ausrichtung im Windows Phone-Emulator in eine der drei folgenden Ausrichtungen ändern: Hochformat, Querformat links oder Querformat rechts. Die Größe des Emulators wird bei einer Änderung der Ausrichtung nicht geändert.<br /><br /> Klicken Sie zum Ändern der Ausrichtung auf die Schaltfläche nach **links drehen** oder nach **rechts drehen** .|  
|![Größenoptionen auf Emulator-Symbolleiste Windows Phone](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Konfigurieren der Größe des Emulators**<br /><br /> Sie können die Größe des Emulators auf dem Hostcomputerbildschirm ändern. Die Punkte pro Zoll (DPI) für den Emulator basieren auf dem DPI-Wert des Hostbildschirms, unabhängig vom Zoomwert.<br /><br /> -Klicken Sie zum Anpassen des Emulators an den Bildschirm auf die Schaltfläche **an Bildschirm anpassen** .<br />-Um die Zoomeinstellung zu ändern, klicken Sie auf die Schaltfläche **Zoom** . Das Dialogfeld **Zoom** wird geöffnet. Geben Sie im Dialogfeld **Zoom** einen Zoomwert zwischen 33 und 100 ein.|  
  
## <a name="use-the-simulated-hardware-buttons-on-the-emulator"></a><a name="BKMK_buttons"></a> Verwenden der simulierten Hardware Schaltflächen im Emulator  
 Über die simulierten Hardwaretasten auf der rechten Seite des Emulator-Bildschirms können Sie die Hardwaretasten eines Telefons simulieren.  
  
- Klicken Sie auf den Schaltflächen **Strom** , um das Deaktivieren und Aktivieren der Anzeige zu simulieren. Klicken und halten Sie die Taste, um das Ausschalten des Telefons zu simulieren.  
  
- Klicken Sie auf die Schaltfläche **Lautstärke** oder **Lautstärke** , um das Ändern des Lautsprechers des Telefons für Telefonanrufe und Benachrichtigungen zu simulieren.  
  
- Mit der Schaltfläche **Kamera** wird die Kamera-APP gestartet. Sie können die Aufnahme eines Fotos oder Videos mit den Steuerelementen in der Kamera-App simulieren.  
  
  Der folgende Screenshot zeigt die simulierten Hardwaretasten.  
  
1. Im linken Bild ist der Startbildschirm im Emulator gezeigt.  
  
2. Das mittlere Bild zeigt den Emulator an, nachdem er auf den **Netz** Schalter geklickt hat, um die Anzeige zu deaktivieren.  
  
3. Das rechte Bild zeigt den Emulator-Bildschirm nach dem Tippen auf die Schaltfläche **Lautstärke** , um das Volume zu vergrößern.  
  
   ![Schaltfläche auf Windows Phone-Emulator](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
## <a name="use-the-computer-keyboard-with-the-emulator"></a><a name="BKMK_tasks_kbd"></a> Verwenden der Computertastatur mit dem Emulator  
 Der Emulator unterstützt die Zuordnung der Hardwaretastatur an Ihrem Entwicklungscomputer zur Tastatur auf einem Windows Phone. Das Verhalten der Tasten entspricht dem Verhalten auf einem Windows Phone-Gerät.  
  
 Standardmäßig ist die Hardwaretastatur nicht aktiviert. Diese Implementierung entspricht einer gleitenden Tastatur, die bereitgestellt werden muss, bevor Sie sie verwenden können. Bevor Sie die Hardwaretastatur aktivieren, akzeptiert der Emulator nur Tasteneingaben von den Steuerelementtasten.  
  
 Sonderzeichen auf der Tastatur einer lokalisierten Version eines Windows-Entwicklungscomputers werden vom Emulator nicht unterstützt. Verwenden Sie zum Eingeben von Sonderzeichen, die auf einer lokalisierten Tastatur vorhanden sind, stattdessen das Software Input Panel (SIP).  
  
 Um Ihre Computertastatur im Emulator zu verwenden, drücken Sie die BILD-AUF-TASTE oder die PAUSE-TASTE (Windows 8/8.1-Emulator) oder F4 (Windows 10-Emulator).  
  
 Um die Verwendung Ihrer Computertastatur im Emulator zu beenden, drücken Sie die BILD-AB-TASTE oder die PAUSE-TASTE (Windows 8/8.1-Emulator) oder F4 (Windows 10-Emulator).  
  
 In der folgenden Tabelle sind die Tasten auf einer Hardwaretastatur aufgeführt, die Sie zum Emulieren der Tasten und anderer Steuerelemente auf einem Windows Phone verwenden können.  
  
|Computerhardwaretaste|Windows Phone-Taste|Notizen|  
|---------------------------|-----------------------------------|-----------|  
|F1|ZURÜCK|Langes Drücken funktioniert erwartungsgemäß.|  
|F2|START|Langes Drücken funktioniert erwartungsgemäß.|  
|F3|SEARCH||  
|F4|Im Windows 10-Emulator wird zwischen der Verwendung der Tastatur des lokalen Computers und der Nicht-Verwendung der Tastatur des lokalen Computers umgeschaltet.|Gilt nicht für den Windows 8/8.1-Emulator.|  
|F5|Nicht zutreffend||  
|F6|KAMERA HALB|Eine dedizierte Kamerataste, die halb heruntergedrückt wird.|  
|F7|KAMERA GANZ|Eine dedizierte Kamerataste.|  
|F8|Nicht zutreffend||  
|F9|LAUTER||  
|F10|LEISER||  
|F11|Nicht zutreffend||  
|F12|POWER|Drücken Sie F12 zweimal, um den Sperrbildschirm zu aktivieren.<br /><br /> Langes Drücken funktioniert erwartungsgemäß.|  
|ESC|ZURÜCK|Langes Drücken funktioniert erwartungsgemäß.|  
|PAUSE|Tastaturwechsel (gilt nur für den Windows 8/8.1-Emulator).|Gilt nicht für den Windows 10-Emulator.|  
|BILD-AUF|Aktiviert die Hardwaretastatur (gilt nur für den Windows 8/8.1-Emulator).|Gilt nicht für den Windows 10-Emulator.|  
|BILD-AB|Deaktiviert die Hardwaretastatur (gilt nur für den Windows 8/8.1-Emulator).|Gilt nicht für den Windows 10-Emulator.|  
  
## <a name="save-and-load-custom-checkpoints"></a><a name="BKMK_checkpoints"></a> Speichern und Laden von benutzerdefinierten Prüfpunkten  
 Speichern Sie eine Momentaufnahme des emulatorzustands auf der Registerkarte **Prüfpunkte** der **zusätzlichen Tools**des Emulators. Dieses Feature ist nützlich, wenn Sie Ihre App häufig mit denselben Daten und Einstellungen testen.  
  
 Wenn für die App beispielsweise mehrere Kontakte erforderlich sind, können Sie den Kontaktdatensatz einmal erstellen und dann eine Momentaufnahme des Emulators speichern. Andernfalls müssten Sie den Kontaktdatensatz bei jedem Starten des Emulators erneut erstellen.  
  
- Klicken Sie auf **neuer** Prüfpunkt, um eine neue Momentaufnahme des Status des Emulators mit den Daten und Einstellungen zu erfassen, die zum erneuten Testen der APP erforderlich sind. Der neue Prüfpunkt wird zur Liste **Prüfpunkte** hinzugefügt.  
  
   Sie können einen Prüfpunkt erfassen, während der Debugger mit dem Emulator verbunden ist.  
  
- Wählen Sie einen Prüfpunkt in der Liste Prüfpunkte aus, um Informationen zum **Prüfpunkt** anzuzeigen.  
  
- Aktivieren Sie das Optionsfeld in der Spalte **Standard** , um einen gespeicherten Prüfpunkt zum Standard Prüf Punkt für den aktiven Emulator zu machen.  
  
- Klicken Sie auf **Wiederherstellen** , um das Windows Phone Betriebssystem im Emulator neu zu starten und die ausgewählte Momentaufnahme zu laden.  
  
- Klicken Sie auf **Löschen** , um eine Momentaufnahme zu löschen, die Sie nicht mehr benötigen.  
  
  Das ursprüngliche emulatorimage wird immer als erstes Element in der Liste der **Prüfpunkte** angezeigt und kann weder geändert noch gelöscht werden. Sie können jedoch eine andere Momentaufnahme als Standard-Emulator-Image auswählen.  
  
  ![Registerkarte Prüfpunkt auf Windows Phone-Emulator](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
## <a name="capture-screenshots-in-the-emulator"></a><a name="BKMK_tasks_shot"></a> Aufzeichnen von Screenshots im Emulator  
 Sie können Screenshots Ihrer Windows Phone-Apps über das Screenshottool bei den zusätzlichen Tools erstellen. Das Tool erstellt PNG-Dateien, die der Auflösung des ausgeführten Emulators entsprechen.  
  
 ![Bildschirmfotos des Windows Phone-Emulators](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>So erstellen Sie einen App-Screenshot über das in den Emulator integrierte Screenshottool  
  
1. Zum Optimieren der Qualität Ihrer Screenshots legen Sie die Zoomstufe des Emulators auf 100 Prozent fest. Je höher Sie die Zoomstufe setzen, umso besser ist die Qualität des Screenshots.  
  
2. Starten Sie Ihre App im Emulator.  
  
3. Klicken Sie auf der Emulator-Symbolleiste auf die Schaltfläche erweitern, um das Fenster **zusätzliche Tools** zu öffnen.  
  
4. Klicken Sie auf die Registerkarte **Screenshot** .  
  
5. Wenn Ihre APP bereit ist, klicken Sie auf die Schaltfläche **erfassen** .  
  
    Der Screenshot wird im Arbeitsbereich angezeigt.  
  
6. Klicken Sie auf die Schaltfläche **Speichern** , um das Dialogfeld **Speichern** unter zu öffnen.  
  
7. Wählen Sie den gewünschten Speicherort und **Dateinamen** aus, und klicken Sie dann auf **Speichern**.  
  
8. Navigieren Sie optional zu anderen Seiten in der App, und nehmen Sie weitere Screenshots auf.  
  
9. Starten Sie einen Emulator mit einer anderen Bildschirmauflösung, um dieselben Screenshots mit einer anderen Auflösung aufzunehmen. Wenn Sie die App mit Debugging ausgeführt haben, müssen Sie das Debugging beenden, bevor Sie die App erneut in einem anderen Emulator ausführen können.  
  
   Deaktivieren Sie die Frameratenzähler auf dem Emulator-Bildschirm, bevor Sie Screenshots aufnehmen, die in den Windows Phone Store übermittelt werden.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>So deaktivieren Sie Frameratencounter im Emulator, bevor Sie Screenshots aufnehmen  
  
- Geben Sie einen Releasebuild in Visual Studio an. Nachdem Sie einen Releasebuild angegeben haben, starten Sie Ihre APP, indem Sie im Menü **Erstellen** den Link ** _[App-Name]_ ** bereitstellen auswählen.  
  
- Alternativ können Sie die Codezeile in der Datei app.xaml.cs oder app.xaml.vb auskommentieren, die den Wert von `EnableFrameRateCounter` auf `true` festlegt.
