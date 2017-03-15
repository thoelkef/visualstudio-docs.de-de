---
title: "Ausf&#252;hren von Windows Store-Apps im Simulator | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 42
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 42
---
# Ausf&#252;hren von Windows Store-Apps im Simulator
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Visual Studio\-Simulator für Windows Store\-Apps ist eine Desktopanwendung, die eine Windows Store\-App simuliert. So können auf Ihrem Entwicklungscomputer Anwendungen ausführen und allgemeine Berührungs\- und Drehungsereignisse simulieren. Sie können die Größe und die Auflösung des physischen Bildschirms auswählen, der emuliert werden soll, und Netzwerkverbindungseigenschaften simulieren.  
  
 Der Simulator stellt eine Umgebung bereit, in der Sie Windows Store\-Apps entwerfen, entwickeln, debuggen und testen können. Bevor Sie Ihre App im Windows Store veröffentlichen, sollten Sie sie jedoch auf einem echten Gerät testen.  
  
 Der Visual Studio\-Simulator für Windows Store\-Apps wird nicht in einer isolierten Umgebung auf dem lokalen Computer ausgeführt. Daher können im Simulator auftretende Fehler, z. B. nicht behebbare systemweite Fehler, auch Auswirkungen auf den restlichen Computer haben.  
  
 Für Informationen zu Windows Phone gehen Sie zu [Ausführen von Windows Phone\-Apps im Emulator](../debugger/run-windows-phone-apps-in-the-emulator.md).  
  
> [!IMPORTANT]
>  Der Visual Studio 2015\-Simulator umfasst nicht die Geolocation\-Schaltfläche. Dies ist darin begründet, dass der Windows 10\-Simulator keine Geolocation\-Simulation umfasst. Wenn Sie diese Art der Simulation durchführen müssen, können Sie den Visual Studio 2013\-Simulator unter Windows 8.1 oder einem älteren Betriebssystem verwenden.  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Festlegen des Simulators als Ziel  
 Um Ihre Windows Store\-App im Simulator auszuführen, wählen Sie auf der Debugger\-Symbolleiste **Standard** neben der Schaltfläche **Debuggen starten** aus der Dropdownliste die Option **Simulator** aus.  
  
 ![Ausführung im Simulator](../debugger/media/vsrun_f5_simulator.png "VSRUN\_F5\_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Auswählen eines Interaktionsmodus  
 Sie können zwischen folgenden Interaktionsmodi wählen:  
  
-   ![Schaltfläche für Mausmodus](../debugger/media/simulator_mousemodebtn.png "SIMULATOR\_MouseModeBtn") Mausmodus: Legt den Interaktionsmodus auf Mausgesten fest. Zu Mausgesten zählen Klicks, Doppelklicks und Ziehen.  
  
-   ![Schaltfläche zur Aktivierung der Fingereingabeemulation](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR\_StartTouchEmulationBtn") Fingereingabe\-Emulation starten: Legt den Interaktionsmodus auf Fingereingabegesten mit einem einzelnen Finger fest. Zu Einfingerereignissen zählen Tippen, Ziehen und Streifen.  
  
     ![Simulator one finger target](../debugger/media/simulator_onefinger.png "SIMULATOR\_OneFinger") Das einzelne Zielsymbol gibt die Position von Ereignissen im Simulator an. Verwenden Sie die Maus, um den Zeiger zu positionieren.  
  
     ![One finger touch target](../debugger/media/simulator_onefingerengaged.png "SIMULATOR\_OneFingerEngaged") Drücken Sie die linke Maustaste, um den Fingereingabemodus zu aktivieren. Klicken Sie beispielsweise auf die Schaltfläche, um ein Tippen zu simulieren oder drücken und halten Sie die Schaltfläche beim Ziehen oder Streifen.  
  
## Verkleinern und vergrößern  
 Legt den Interaktionsmodus auf Verkleinerungs\- und Vergrößerungsgesten fest.  
  
-   ![Siimulator two finger target](../debugger/media/simulator_twofinger.png "SIMULATOR\_TwoFinger")  
  
     Das doppelte Zielsymbol gibt die Position von zwei Fingern auf dem Gerätebildschirm an.  
  
    -   Bewegen Sie den Mauszeiger, um die Symbole über dem Objekt auf dem Gerätebildschirm zu positionieren.  
  
    -   Drehen Sie das Mausrad nach oben oder unten , um den simulierten Abstand der zwei Finger vor dem Zusammendrücken oder Zoomen zu simulieren.  
  
-   -   ![Pinch, zoom, and rotate targets](../debugger/media/simulator_twofingerengaged.png "SIMULATOR\_TwoFingerEngaged")  
  
         Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach unten \(zu Ihnen hin\), um zu vergrößern.  
  
    -   Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach oben \(von Ihnen weg\), um zu verkleinern .  
  
## Objektdrehung  
 Die Schaltfläche **Fingereingabe\-Emulation – Drehen** legt den Interaktionsmodus auf Drehbewegungen mit zwei Fingern fest.  
  
-   -   Bewegen Sie den Mauszeiger, um die Symbole über dem Objekt auf dem Gerätebildschirm zu positionieren.  
  
    -   Drehen Sie das Mausrad nach oben oder unten, um die simulierte Ausrichtung der zwei Finger vor dem Drehen des Objekts zu simulieren.  
  
-   -   Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach unten \(zu Ihnen hin\), um das Objekt gegen den Uhrzeigersinn zu drehen. Beim Drehen des Mausrads rotiert eines der beiden Zielsymbole um das andere, um die relative Größe der Drehung anzugeben.  
  
    -   Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach oben \(von Ihnen weg\), um das Objekt im Uhrzeigersinn zu drehen.  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Aktivieren oder deaktivieren des "Immer im Vordergrund"\-Modus  
 Sie können festlegen, dass das Simulatorfenster immer an der obersten Position aller Fenster angezeigt wird. Die Schaltfläche **Umschalten des obersten Fensters** aktiviert oder deaktiviert den Modus **Immer im Vordergrund** des Simulatorfensters.  
  
##  <a name="BKMK_Change_the_device_orientation"></a> Ändern der Geräteausrichtung  
 Sie können Hochformat\- und Querformatausrichtung des Geräts wechseln, indem Sie den Simulator in beliebiger Richtung um 90 Grad drehen.  
  
> [!NOTE]
>  Der Simulator berücksichtigt nicht die Eigenschaft [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) eines Projekts. Wenn Ihr Projekt beispielsweise auf die Ausrichtung `Landscape` festgelegt ist und Sie den Simulator in die Ausrichtung "Hochformat" drehen, wird die Anzeige des Simulators ebenfalls gedreht und die Größe angepasst. Testen Sie diese Einstellungen auf einem echten Gerät.  
  
> [!NOTE]
>  Wenn Sie den Simulator so drehen, dass der Simulator größer als der Bildschirm ist, auf dem er angezeigt wird, erfolgt eine automatische Größenanpassung auf die Bildschirmgröße. Die ursprüngliche Größe des Simulators wird nicht wiederhergestellt, wenn Sie diesen erneut drehen.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Ändern der simulierten Bildschirmgröße und \-auflösung  
 Verwenden Sie die Schaltfläche **Auflösung ändern** auf der Palette, und wählen Sie anschließend eine neue Größe und Auflösung aus der Liste aus, um die simulierte Bildschirmgröße und \-auflösung zu ändern.  
  
 Die Bildschirmgröße und \-auflösung werden als *Bildschirmbreite Zoll, Pixel Breite X Pixel Höhe* aufgeführt. Beachten Sie, dass sowohl Bildschirmgröße als auch \-auflösung simuliert werden. Die Positionskoordinaten im Simulator werden in die Koordinaten der ausgewählten Gerätegröße und \-auflösung übersetzt.  
  
> [!NOTE]
>  Sie können skalierte Versionen von Bitmapbildern in Ihrer App speichern, und Windows lädt das richtige Bild für die aktuelle Skalierung. Weitere Informationen finden Sie unter [Reaktionsfähiger Entwurf 101](https://msdn.microsoft.com/en-us/library/windows/apps/dn958435.aspx). Wenn Sie die Simulatorauflösung ändern, sodass Windows ein anderes Bild für die Auflösung auswählt, müssen Sie die Debugsitzung beenden und erneut starten, damit das neue Bild angezeigt wird.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Erfassen eines Screenshots ihrer App für die Übermittlung zum Windows Store  
 Wenn Sie eine App an den Windows\-App\-Store übermitteln, müssen Sie auch Screenshots der App einbeziehen.  
  
> [!NOTE]
>  Der Screenshot wird in der aktuellen Auflösung des Simulators gespeichert. Verwenden Sie die Schaltfläche **Auflösung ändern**, um die Auflösung zu ändern.  
  
-   Verwenden Sie die Schaltfläche **Screenshot in Zwischenablage ablegen**, um Screenshots Ihrer App im Simulator zu erstellen.  
  
-   Verwenden Sie die Schaltfläche **Screenshoteinstellungen**, und wählen Sie im Kontextmenü den Speicherort aus, um den Speicherort der Screenshots festzulegen.  
  
     ![Kontextmenü für Screenshoteinstellungen](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR\_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Simulieren der Netzwerkverbindungseigenschaften  
 Sie können die Benutzer der App dabei unterstützen, die Kosten gemessener Netzwerkverbindungen zu verwalten, indem Sie die Statusänderungen von Netzwerkverbindungskosten oder Datentarifplänen präsent halten und die App so aktivieren, dass zusätzliche Kosten für das Roaming oder das Überschreiten angegebener Datenübertragungsgrenzen anhand dieser Informationen vermieden werden. Mithilfe der [Windows.Networking.Connectivity](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.aspx)\-APIs können Sie auf [NetworkStatusChanged](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx)\- und [TriggerType](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx)\-Ereignisse antworten, die signieren. Weitere Informationen finden Sie unter [Schnellstart: Verwalten von gemessenen Netzwerkkosteneinschränkungen](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Um den Code für die kostenbewusste Nutzung des Netzwerks zu debuggen oder zu testen, kann der Simulator Eigenschaften eines Netzwerks imitieren, die vom [ConnectionProfile](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx)\-Objekt verfügbar gemacht werden, das von [GetInternetConnectionProfile](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx) zurückgegeben wird.  
  
 So simulieren Sie Netzwerkeigenschaften:  
  
1.  Wählen Sie auf der Simulatorsymbolleiste die Schaltfläche **Netzwerkeigenschaften ändern** aus.  
  
2.  Klicken Sie im Dialogfeld **Netzwerkeigenschaften festlegen**, und wählen Sie **Simulierte Netzwerkeigenschaften verwenden** aus.  
  
     Deaktivieren Sie das Kontrollkästchen, um die Simulation zu entfernen und zu den Netzwerkeigenschaften der aktuell verbundenen Schnittstelle zurückzukehren.  
  
3.  Geben Sie **Profilname** für das simulierte Netzwerk ein. Es empfiehlt sich, einen eindeutigen Namen zu verwenden, den Sie verwenden können, um die Simulation in der [ProfileName](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx)\-Eigenschaft des [ConnectionProfile](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx)\-Objekts zu identifizieren.  
  
4.  Wählen Sie den [NetworkCostType](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx)\-Wert für das Profil aus der Liste **Netzwerkkostentyp** aus.  
  
5.  Aus der Liste **Datenlimit\-Statusflag** können Sie die [ApproachingDataLimit](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx)\- oder die [OverDataLimit](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)\-Eigenschaft auf „true“ festlegen. Sie können auch **Unter Datenlimit** auswählen, um beide Werte auf „false“ festzulegen.  
  
6.  Legen Sie aus der Liste **Roamingzustand** die [Roaming](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx)\-Eigenschaft fest.  
  
7.  Wählen Sie **Eigenschaften festlegen**, um die Netzwerkeigenschaften zu simulieren, indem Sie ein [NetworkStatusChanged](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx)\-Vordergrundereignis und einen Hintergrund\-[SystemTrigger](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) vom Typ **NetworkStateChange** starten.  
  
 **Weitere Informationen zum Verwalten von Netzwerkverbindungen**  
  
 [Schnellstart: Verwalten von gemessenen Netzwerkkosteneinschränkungen.](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
 [Beispiel für Netzwerkinformationen](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
 [Analysieren des Energieverbrauchs](../profiling/analyze-energy-use-in-store-apps.md)  
  
 [Windows.Networking.Connectivity](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.aspx)  
  
 [Reagieren auf Systemereignisse mit Hintergrundaufgaben](http://msdn.microsoft.com/de-de/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
 [So können Sie Ereignisse in Windows Store\-Apps auslösen, anhalten, fortsetzen und im Hintergrund ausführen](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Navigieren des Simulators mit der Tastatur  
 Sie können die Simulatorsymbolleiste navigieren, indem Sie **STRG\+ALT\+NACH\-OBEN\-TASTE** drücken, um den Fokus vom Simulatorfenster auf die Simulatorsymbolleiste zu verschieben. Verwenden Sie die **NACH\-OBEN\-TASTE** und die **NACH\-UNTEN\-TASTE**, um zwischen den Schaltflächen auf der Symbolleiste zu wechseln.  
  
 Sie können den Simulator durch Drücken von **STRG\+ALT\+F4** herunterfahren.  
  
## Siehe auch  
 [Ausführen von Apps aus Visual Studio](../debugger/run-store-apps-from-visual-studio.md)