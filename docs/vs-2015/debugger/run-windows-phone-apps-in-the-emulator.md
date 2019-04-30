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
ms.openlocfilehash: c594e3837a4fe2c8b2e5a7b69e5db93377a8dc8d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442324"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Ausführen von Windows Phone-Apps im Emulator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Windows Phone-Emulator stellt eine virtualisierte Umgebung bereit, in der Sie Windows Phone-Apps auf Ihrem Computer ohne ein physisches Gerät debuggen und testen können. Sie können typische Touch- und Rotationsereignisse simulieren und die physische Bildschirmgröße und -auflösung auswählen, die Sie emulieren möchten. Sie können außerdem viele häufig verwendete Features wie Standort, Netzwerk, Benachrichtigungen, Sensoren, den Beschleunigungsmesser und die optionale SD-Karte testen.  
  
 Weitere Informationen über die Funktionen, die Sie im Emulator testen können, finden Sie unter [Testen von app-Features in Windows Phone-Emulator](http://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 In Kombination mit Visual Studio stellt der Emulator eine vollständige Umgebung bereit, in der Sie Windows Phone-Apps entwerfen, entwickeln, debuggen und testen können.  
  
## <a name="BKMK_run"></a> Führen Sie eine Windows Phone-app im emulator  
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
  
### <a name="BKMK_vs"></a> Ausführen einer app über Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>So funktioniert das Bereitstellen und Ausführen einer App über Visual Studio  
  
1. Öffnen Sie in Visual Studio ein Windows Phone-Projekt.  
  
2. Auf der **Standard** wählen Sie eine der Emulatoroptionen-Symbolleiste.  
  
     ![Liste der Windows Phone-Emulator-Images](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3. Bereitstellen und Ausführen Ihrer app mit debugging im der **Debuggen** Menü klicken Sie auf **Debuggen starten**, oder drücken Sie F5.  
  
     Bereitstellen und Ausführen Ihrer app ohne Debuggen, im dem **Debuggen** im Menü klicken Sie auf **Starten ohne Debugging**, oder drücken Sie STRG + F5.  
  
     Ihre App wird bereitgestellt und gestartet.  
  
     Um Ihre app bereitzustellen, ohne Sie auszuführen, auf die **erstellen** Menü klicken Sie auf **Projektmappe bereitstellen**.  
  
##### <a name="to-stop-a-running-app"></a>So beenden Sie eine ausgeführte App  
  
- Gehen Sie wie folgt vor, um eine ausgeführte App zu beenden:  
  
  - In Visual Studio auf die **Debuggen** Menü klicken Sie auf **Debuggen beenden**, oder drücken Sie UMSCHALT + F5.  
  
  - Drücken Sie in der Emulator die **wieder** Schaltfläche, um die app zu beenden. Wenn die aktive Seite der app nicht die Startseite der app war, müssen Sie möglicherweise zum Drücken der **wieder** Schaltfläche mehr als einmal.  
  
    Die App wird beendet, und der Startbildschirm wird geöffnet. Damit wird die aktuelle Debugsitzung beendet.  
  
##### <a name="to-restart-an-app-without-debugging"></a>So starten Sie eine App neu ohne Debugging neu  
  
1. Streifen Sie im Emulator auf dem Startbildschirm nach links, um die Liste der Apps anzuzeigen.  
  
2. Tippen Sie in der Liste der Apps auf das App-Symbol. Die App wird ohne Debugging neu gestartet.  
  
##### <a name="to-deactivate-a-running-app"></a>So deaktivieren Sie eine ausgeführte App  
  
1. Vor dem Ausführen Ihrer app in Visual Studio mit der Maustaste des Projekts im Projektmappen-Explorer, und wählen Sie dann **Eigenschaften** öffnen **Projekt-Designer**.  
  
2. In **Projekt-Designer**auf die **Debuggen** Seite, lassen Sie die **Tombstone bei Deaktivierung während des Debuggens** aktivieren Sie Kontrollkästchen deaktiviert, wenn die app in einen Ruhezustand wechseln soll Zustand über, wenn deaktiviert. Aktivieren Sie das Kontrollkästchen, wenn die App bei Deaktivierung in einen Tombstone-Zustand wechseln soll.  
  
3. Auf der **Debuggen** Menü klicken Sie auf **Debuggen starten**, oder drücken Sie F5, um die app auszuführen.  
  
4. Drücken Sie in der Emulator die **starten** Schaltfläche. Der Startbildschirm wird angezeigt, und die App wird deaktiviert. Die app wechselt entweder in den Ruhe- oder Tombstone-Zustand, abhängig von der Einstellung von der **Tombstone bei Deaktivierung während des Debuggens** Kontrollkästchen.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>So reaktivieren Sie eine App im Ruhe- oder Tombstone-Zustand  
  
- Drücken Sie in der Emulator die **wieder** Schaltfläche, um zur app zurückzukehren. Wenn Sie zu anderen Seiten navigiert sind oder eine andere app geöffnet haben, müssen Sie möglicherweise zum Drücken der **wieder** mehr als einmal Schaltfläche, um die app erneut zu aktivieren.  
  
     Die Debugsitzung wird fortgesetzt. Wenn der Debugger von der App getrennt wurde, müssen Sie möglicherweise F5 drücken, um die Debugsitzung fortzusetzen.  
  
### <a name="BKMK_depltool"></a> Ausführen einer app mit dem anwendungsbereitstellungstool  
 Sie können auch das Windows Phone-anwendungsbereitstellungstool (**AppDeploy.exe**) um Ihre app im Emulator auszuführen. Dieses Tool ist eine eigenständige App, die bei der Installation der Windows Phone-Entwicklungstools installiert wird.  
  
 Weitere Informationen finden Sie unter [Bereitstellen von Windows Phone 8.1-apps mit dem anwendungsbereitstellungstool](http://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
## <a name="BKMK_toolbar"></a> Konfigurieren Sie den Windows Phone-Emulator über die Symbolleiste des Emulators  
 In dieser Tabelle sind die auf der Symbolleiste des Emulators verfügbaren Konfigurationsschaltflächen sichtbar.  
  
|Schaltflächen auf der Symbolleiste|Konfigurationsoptionen|  
|---------------------|---------------------------|  
|![Eingabeoptionen auf Windows Phone-Emulator-Symbolleiste](../debugger/media/wp-emulator.png "WP_Emulator_")|**Konfigurieren einer Einzel- oder multipunkteingabe**<br /><br /> Wenn Sie die Multipunkteingabe aktivieren, können Sie mit der rechten Maustaste klicken, um die Berührungspunkte zu verschieben, ohne den Bildschirm zu berühren. Dann können Sie mit der linken Maustaste klicken, um beide Berührungspunkte gleichzeitig zu verschieben.|  
|![Ausrichtung auf Windows Phone-Emulator-Symbolleiste](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Konfigurieren der Ausrichtung des Emulators**<br /><br /> Sie können die Ausrichtung im Windows Phone-Emulator in eine der drei folgenden Ausrichtungen ändern: Hochformat, Querformat links oder Querformat rechts. Die Größe des Emulators wird bei einer Änderung der Ausrichtung nicht geändert.<br /><br /> Klicken Sie zum Ändern der Ausrichtung auf die **nach links drehen** Schaltfläche oder die **nach rechts drehen** Schaltfläche.|  
|![Größe der Optionen auf Windows Phone-Emulator-Symbolleiste](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Konfigurieren Sie die Größe des Emulators**<br /><br /> Sie können die Größe des Emulators auf dem Hostcomputerbildschirm ändern. Die Punkte pro Zoll (DPI) für den Emulator basieren auf dem DPI-Wert des Hostbildschirms, unabhängig vom Zoomwert.<br /><br /> – Zum Anpassen des Emulators auf dem Bildschirm klicken Sie auf die **an Bildschirmgröße anpassen** Schaltfläche.<br />– Zum Ändern der zoomeinstellungen klicken Sie auf die **Zoom** Schaltfläche. Die **Zoom** Dialogfeld wird geöffnet. In der **Zoom** Dialogfeld Geben Sie einen Wert zwischen 33 und 100.|  
  
## <a name="BKMK_buttons"></a> Verwenden der simulierten Hardwaretasten im emulator  
 Über die simulierten Hardwaretasten auf der rechten Seite des Emulator-Bildschirms können Sie die Hardwaretasten eines Telefons simulieren.  
  
- Klicken Sie auf die **Power** Schaltfläche, um zu simulieren, und das Ausschalten des Displays. Klicken und halten Sie die Taste, um das Ausschalten des Telefons zu simulieren.  
  
- Klicken Sie auf die **lauter** oder **leiser** Schaltfläche, um die Lautstärke der Telefonlautsprecher für Anrufe und Benachrichtigungen zu ändern.  
  
- Die **Kamera** die Kamera-app wird gestartet. Sie können die Aufnahme eines Fotos oder Videos mit den Steuerelementen in der Kamera-App simulieren.  
  
  Der folgende Screenshot zeigt die simulierten Hardwaretasten.  
  
1. Im linken Bild ist der Startbildschirm im Emulator gezeigt.  
  
2. Das mittlere Bild zeigt den Emulator nach Tippen auf die **Power** Schaltfläche, um das Ausschalten des Displays.  
  
3. Das rechte Bild zeigt den Emulator-Bildschirm nach Tippen auf die **lauter** Schaltfläche zum Erhöhen der Lautstärke.  
  
   ![Schaltflächen auf dem Windows Phone-Emulator](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
## <a name="BKMK_tasks_kbd"></a> Verwenden der Computertastatur mit dem emulator  
 Der Emulator unterstützt die Zuordnung der Hardwaretastatur an Ihrem Entwicklungscomputer zur Tastatur auf einem Windows Phone. Das Verhalten der Tasten entspricht dem Verhalten auf einem Windows Phone-Gerät.  
  
 Standardmäßig ist die Hardwaretastatur nicht aktiviert. Diese Implementierung entspricht einer gleitenden Tastatur, die bereitgestellt werden muss, bevor Sie sie verwenden können. Bevor Sie die Hardwaretastatur aktivieren, akzeptiert der Emulator nur Tasteneingaben von den Steuerelementtasten.  
  
 Sonderzeichen auf der Tastatur einer lokalisierten Version eines Windows-Entwicklungscomputers werden vom Emulator nicht unterstützt. Verwenden Sie zum Eingeben von Sonderzeichen, die auf einer lokalisierten Tastatur vorhanden sind, stattdessen das Software Input Panel (SIP).  
  
 Um Ihre Computertastatur im Emulator zu verwenden, drücken Sie die BILD-AUF-TASTE oder die PAUSE-TASTE (Windows 8/8.1-Emulator) oder F4 (Windows 10-Emulator).  
  
 Um die Verwendung Ihrer Computertastatur im Emulator zu beenden, drücken Sie die BILD-AB-TASTE oder die PAUSE-TASTE (Windows 8/8.1-Emulator) oder F4 (Windows 10-Emulator).  
  
 In der folgenden Tabelle sind die Tasten auf einer Hardwaretastatur aufgeführt, die Sie zum Emulieren der Tasten und anderer Steuerelemente auf einem Windows Phone verwenden können.  
  
|Computerhardwaretaste|Windows Phone-Taste|Hinweise|  
|---------------------------|-----------------------------------|-----------|  
|F1|ZURÜCK|Langes Drücken funktioniert erwartungsgemäß.|  
|F2|START|Langes Drücken funktioniert erwartungsgemäß.|  
|F3|SUCHE||  
|F4|Im Windows 10-Emulator wird zwischen der Verwendung der Tastatur des lokalen Computers und der Nicht-Verwendung der Tastatur des lokalen Computers umgeschaltet.|Gilt nicht für den Windows 8/8.1-Emulator.|  
|F5|Nicht zutreffend.||  
|F6|KAMERA HALB|Eine dedizierte Kamerataste, die halb heruntergedrückt wird.|  
|F7|KAMERA GANZ|Eine dedizierte Kamerataste.|  
|F8|Nicht zutreffend.||  
|F9|LAUTER||  
|F10|LEISER||  
|F11|Nicht zutreffend.||  
|F12|EIN/AUS|Drücken Sie F12 zweimal, um den Sperrbildschirm zu aktivieren.<br /><br /> Langes Drücken funktioniert erwartungsgemäß.|  
|ESC|ZURÜCK|Langes Drücken funktioniert erwartungsgemäß.|  
|PAUSE|Tastaturwechsel (gilt nur für den Windows 8/8.1-Emulator).|Gilt nicht für den Windows 10-Emulator.|  
|BILD-AUF|Aktiviert die Hardwaretastatur (gilt nur für den Windows 8/8.1-Emulator).|Gilt nicht für den Windows 10-Emulator.|  
|BILD-AB|Deaktiviert die Hardwaretastatur (gilt nur für den Windows 8/8.1-Emulator).|Gilt nicht für den Windows 10-Emulator.|  
  
## <a name="BKMK_checkpoints"></a> Speichern und Laden von benutzerdefinierten Prüfpunkten  
 Speichern Sie eine Momentaufnahme des Emulator-Zustands mit den **Prüfpunkte** des Emulators auf der Registerkarte **zusätzliche Tools**. Dieses Feature ist nützlich, wenn Sie Ihre App häufig mit denselben Daten und Einstellungen testen.  
  
 Wenn für die App beispielsweise mehrere Kontakte erforderlich sind, können Sie den Kontaktdatensatz einmal erstellen und dann eine Momentaufnahme des Emulators speichern. Andernfalls müssten Sie den Kontaktdatensatz bei jedem Starten des Emulators erneut erstellen.  
  
- Klicken Sie auf **neuer Prüfpunkt** um eine neue Momentaufnahme des Zustands des Emulators mit den Daten und Einstellungen, die Ihre app testen Sie es später noch Mal zu erfassen. Der neue Prüfpunkt wird hinzugefügt, um die **Prüfpunkte** Liste.  
  
   Sie können einen Prüfpunkt erfassen, während der Debugger mit dem Emulator verbunden ist.  
  
- Wählen Sie einen Prüfpunkt in die **Prüfpunkte** Liste, um Informationen zum Prüfpunkt anzuzeigen.  
  
- Wählen Sie das Optionsfeld in der **Standard** Spalte in einem gespeicherten Prüfpunkt zum standardprüfpunkt für den aktiven Emulator machen.  
  
- Klicken Sie auf **wiederherstellen** , starten das Windows Phone-Betriebssystem auf dem Emulator und die ausgewählte Momentaufnahme zu laden.  
  
- Klicken Sie auf **löschen** beim Löschen einer Momentaufnahme, die Sie nicht mehr benötigen.  
  
  Das ursprüngliche Emulatorabbild wird immer als das erste Element in der **Prüfpunkte** auflisten und kann nicht geändert oder gelöscht wird. Sie können jedoch eine andere Momentaufnahme als Standard-Emulator-Image auswählen.  
  
  ![Registerkarte Prüfpunkt auf dem Windows Phone-Emulator](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
## <a name="BKMK_tasks_shot"></a> Aufnehmen von Screenshots im emulator  
 Sie können Screenshots Ihrer Windows Phone-Apps über das Screenshottool bei den zusätzlichen Tools erstellen. Das Tool erstellt PNG-Dateien, die der Auflösung des ausgeführten Emulators entsprechen.  
  
 ![Screenshots aus dem Windows Phone Emulator](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>So erstellen Sie einen App-Screenshot über das in den Emulator integrierte Screenshottool  
  
1. Zum Optimieren der Qualität Ihrer Screenshots legen Sie die Zoomstufe des Emulators auf 100 Prozent fest. Je höher Sie die Zoomstufe setzen, umso besser ist die Qualität des Screenshots.  
  
2. Starten Sie Ihre App im Emulator.  
  
3. Klicken Sie auf der Emulator-Symbolleiste auf die Schaltfläche zum Öffnen der **zusätzliche Tools** Fenster.  
  
4. Klicken Sie auf die **Screenshot** Registerkarte.  
  
5. Wenn Ihre app bereit ist, klicken Sie auf die **erfassen** Schaltfläche.  
  
    Der Screenshot wird im Arbeitsbereich angezeigt.  
  
6. Klicken Sie auf die **speichern** die Schaltfläche, um die **speichern** Dialogfeld.  
  
7. Wählen Sie den Speicherort und **Dateiname** , die Sie möchten, und klicken Sie dann auf **speichern**.  
  
8. Navigieren Sie optional zu anderen Seiten in der App, und nehmen Sie weitere Screenshots auf.  
  
9. Starten Sie einen Emulator mit einer anderen Bildschirmauflösung, um dieselben Screenshots mit einer anderen Auflösung aufzunehmen. Wenn Sie die App mit Debugging ausgeführt haben, müssen Sie das Debugging beenden, bevor Sie die App erneut in einem anderen Emulator ausführen können.  
  
   Deaktivieren Sie die Frameratenzähler auf dem Emulator-Bildschirm, bevor Sie Screenshots aufnehmen, die in den Windows Phone Store übermittelt werden.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>So deaktivieren Sie Frameratencounter im Emulator, bevor Sie Screenshots aufnehmen  
  
- Geben Sie einen Releasebuild in Visual Studio an. Starten Sie nach dem Angeben eines Releasebuilds, die Ihre app durch Auswählen der **bereitstellen _[app-Name]_**  auf einen link auf die **erstellen** Menü.  
  
- Alternativ können Sie die Codezeile in der Datei app.xaml.cs oder app.xaml.vb auskommentieren, die den Wert von `EnableFrameRateCounter` auf `true` festlegt.
