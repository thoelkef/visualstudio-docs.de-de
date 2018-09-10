---
title: Ausführen von UWP-apps im Simulator | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: fd0aa403e702a591a0b09d0891116063a3ed9ff2
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281051"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Ausführen von UWP-Apps im Simulator
Visual Studio-Simulator für UWP-apps ist eine Desktopanwendung, die eine UWP-app simuliert. In der Regel sollten Sie auf dem lokalen Computer, einem verbundenen Gerät oder einem Remotecomputer zu debuggen. In einigen Szenarien möchten jedoch möglicherweise Visual Studio-Simulator zu verwenden, um eine andere physische Bildschirmgröße und Auflösung zu emulieren. Sie können auch allgemeine berührungs- und drehungsereignisse simulieren und Netzwerkverbindungseigenschaften simulieren.
  
 Der Simulator stellt eine Umgebung, in der Sie können zu entwerfen, entwickeln, Debuggen und Testen von UWP-Apps, bereit. Bevor Sie Ihre app in Microsoft Store veröffentlichen, sollten Sie jedoch Ihre app auf einem echten Gerät testen.  
  
 Visual Studio-Simulator für UWP-apps wird nicht in einer isolierten Umgebung auf dem lokalen Computer ausgeführt werden. Daher können im Simulator auftretende Fehler, z. B. nicht behebbare systemweite Fehler, auch Auswirkungen auf den restlichen Computer haben.  
  
> [!IMPORTANT]
>  Der Visual Studio 2015-Simulator umfasst nicht die Geolocation-Schaltfläche. Dies ist darin begründet, dass der Windows 10-Simulator keine Geolocation-Simulation umfasst.
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Festlegen des Simulators als Ziel  
 Wählen Sie zum Ausführen Ihrer UWP-app im Simulator **Simulator** aus der Dropdown-Liste neben der **Debuggen starten** Schaltfläche auf der Debugger **Standard** Symbolleiste. Diese Option ist nur verfügbar wenn Ihrer app **Mindestversion. Version** ist kleiner als oder gleich der für das Betriebssystem auf dem Entwicklungscomputer. 
  
 ![Ausführung im Simulator](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Auswählen eines Interaktionsmodus  
 Sie können zwischen folgenden Interaktionsmodi wählen:  
  
-   ![Schaltfläche für Mausmodus](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") mausmodus: Legt den interaktionsmodus auf Mausgesten fest. Zu Mausgesten zählen Klicks, Doppelklicks und Ziehen.  
  
-   ![Schaltfläche "Start Fingereingabe-Emulation"](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Fingereingabe-Emulation starten: Legt den interaktionsmodus auf fingereingabegesten mit einem einzelnen Finger fest. Zu Einfingerereignissen zählen Tippen, Ziehen und Streifen.  
  
     ![Simulator-Ziel für einen Finger](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger") das einzelne Zielsymbol gibt die Position von Ereignissen im Simulator an. Verwenden Sie die Maus, um den Zeiger zu positionieren.  
  
     ![Ziel für eine fingerberührung](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged") drücken Sie die linke Maustaste gedrückt, um den fingereingabemodus zu aktivieren. Klicken Sie beispielsweise auf die Schaltfläche, um ein Tippen zu simulieren oder drücken und halten Sie die Schaltfläche beim Ziehen oder Streifen.  
  
## <a name="pinch-and-zoom"></a>Verkleinern und vergrößern  
 Legt den Interaktionsmodus auf Verkleinerungs- und Vergrößerungsgesten fest.  
  
-   ![Ziel der Simulator zwei-Finger](../debugger/media/simulator_twofinger.png "SIMULATOR_TwoFinger")  
  
     Das doppelte Zielsymbol gibt die Position von zwei Fingern auf dem Gerätebildschirm an.  
  
    -   Bewegen Sie den Mauszeiger, um die Symbole über dem Objekt auf dem Gerätebildschirm zu positionieren.  
  
    -   Drehen Sie das Mausrad nach oben oder unten , um den simulierten Abstand der zwei Finger vor dem Zusammendrücken oder Zoomen zu simulieren.  
  
-   -   ![Verkleinern, vergrößern und Drehen von Zielen](../debugger/media/simulator_twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
         Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach unten (zu Ihnen hin), um zu vergrößern.  
  
    -   Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach oben (von Ihnen weg), um zu verkleinern .  
  
## <a name="object-rotation"></a>Objektdrehung  
 Die Schaltfläche **Fingereingabe-Emulation – Drehen** legt den Interaktionsmodus auf Drehbewegungen mit zwei Fingern fest.  
  
-   -   Bewegen Sie den Mauszeiger, um die Symbole über dem Objekt auf dem Gerätebildschirm zu positionieren.  
  
    -   Drehen Sie das Mausrad nach oben oder unten, um die simulierte Ausrichtung der zwei Finger vor dem Drehen des Objekts zu simulieren.  
  
-   -   Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach unten (zu Ihnen hin), um das Objekt gegen den Uhrzeigersinn zu drehen. Beim Drehen des Mausrads rotiert eines der beiden Zielsymbole um das andere, um die relative Größe der Drehung anzugeben.  
  
    -   Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach oben (von Ihnen weg), um das Objekt im Uhrzeigersinn zu drehen.  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Aktivieren oder deaktivieren des "Immer im Vordergrund"-Modus  
 Sie können festlegen, dass das Simulatorfenster immer an der obersten Position aller Fenster angezeigt wird. Die Schaltfläche **Umschalten des obersten Fensters** aktiviert oder deaktiviert den Modus **Immer im Vordergrund** des Simulatorfensters.  
  
##  <a name="BKMK_Change_the_device_orientation"></a> Ändern der Geräteausrichtung  
 Sie können Hochformat- und Querformatausrichtung des Geräts wechseln, indem Sie den Simulator in beliebiger Richtung um 90 Grad drehen.  
  
> [!NOTE]
>  Der Simulator berücksichtigt nicht die Eigenschaft [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) eines Projekts. Wenn Ihr Projekt beispielsweise auf die Ausrichtung `Landscape`festgelegt ist und Sie den Simulator in die Ausrichtung "Hochformat" drehen, wird die Anzeige des Simulators ebenfalls gedreht und die Größe angepasst. Testen Sie diese Einstellungen auf einem echten Gerät.  
  
> [!NOTE]
>  Wenn Sie den Simulator so drehen, dass der Simulator größer als der Bildschirm ist, auf dem er angezeigt wird, erfolgt eine automatische Größenanpassung auf die Bildschirmgröße. Die ursprüngliche Größe des Simulators wird nicht wiederhergestellt, wenn Sie diesen erneut drehen.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Ändern der simulierten Bildschirmgröße und -auflösung  
 Verwenden Sie die Schaltfläche **Auflösung ändern** auf der Palette, und wählen Sie anschließend eine neue Größe und Auflösung aus der Liste aus, um die simulierte Bildschirmgröße und -auflösung zu ändern.  
  
 Die Bildschirmgröße und -auflösung werden als *Bildschirmbreite Zoll, Pixel Breite X Pixel Höhe*aufgeführt. Beachten Sie, dass sowohl Bildschirmgröße als auch -auflösung simuliert werden. Die Positionskoordinaten im Simulator werden in die Koordinaten der ausgewählten Gerätegröße und -auflösung übersetzt.  
  
> [!NOTE]
>  Sie können skalierte Versionen von Bitmapbildern in Ihrer App speichern, und Windows lädt das richtige Bild für die aktuelle Skalierung. Weitere Informationen finden Sie unter [Entwurfs- und Benutzeroberfläche-Einführung](/windows/uwp/layout/design-and-ui-intro). Wenn Sie die Simulatorauflösung ändern, sodass Windows ein anderes Bild für die Auflösung auswählt, müssen Sie die Debugsitzung beenden und erneut starten, damit das neue Bild angezeigt wird.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Erstellen eines Screenshots Ihrer App für die Übermittlung zum Microsoft Store  
 Wenn Sie eine app zum Microsoft Store übermitteln, müssen Sie Screenshots der app einschließen.  
  
> [!NOTE]
>  Der Screenshot wird in der aktuellen Auflösung des Simulators gespeichert. Verwenden Sie die Schaltfläche **Auflösung ändern** , um die Auflösung zu ändern.  
  
-   Verwenden Sie die Schaltfläche **Screenshot in Zwischenablage ablegen** , um Screenshots Ihrer App im Simulator zu erstellen.  
  
-   Verwenden Sie die Schaltfläche **Screenshoteinstellungen** , und wählen Sie im Kontextmenü den Speicherort aus, um den Speicherort der Screenshots festzulegen.  
  
     ![Kontextmenü für Screenshoteinstellungen](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Simulieren der Netzwerkverbindungseigenschaften  
 Sie können die Benutzer Ihrer app die Kosten gemessener Netzwerkverbindungen zu verwalten, indem Sie Informationen hinsichtlich der Netzwerk-Verbindung Kosten oder Daten Status planänderungen zu verwalten, und aktivieren Ihre app diese Informationen verwenden, um zu verhindern, dass zusätzliche Kosten für das roaming oder das Überschreiten einer angegebene Datenübertragungsvolumen. Die [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) APIs können Sie auf [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) und [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) Ereignisse, die sich anmelden. Finden Sie unter [Schnellstart: Verwalten von gemessenen netzwerkkosteneinschränkungen](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Zum Debuggen oder testen Sie den Netzwerk-sparsame-Code, kann der Simulator Eigenschaften eines Netzwerks, die über verfügbar gemacht werden imitieren die [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) zurückgegebenes Objekt [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).
  
 So simulieren Sie Netzwerkeigenschaften:  
  
1.  Wählen Sie auf der Simulatorsymbolleiste die Schaltfläche **Netzwerkeigenschaften ändern** aus.  
  
2.  Klicken Sie im Dialogfeld **Netzwerkeigenschaften festlegen** , und wählen Sie **Simulierte Netzwerkeigenschaften verwenden**aus.  
  
     Deaktivieren Sie das Kontrollkästchen, um die Simulation zu entfernen und zu den Netzwerkeigenschaften der aktuell verbundenen Schnittstelle zurückzukehren.  
  
3.  Geben Sie **Profilname** für das simulierte Netzwerk ein. Es wird empfohlen, einen eindeutigen Namen, die Sie verwenden können, sind die Simulation in der [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) Eigenschaft der [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) Objekt.  
  
4.  Wählen Sie die [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) Wert für das Profil aus der **Netzwerkkostentyp** Liste.  
  
5.  Von der **Datenlimit-Statusflag** Liste, Sie können festlegen, die [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) Eigenschaft oder das [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) Eigenschaft auf "true", oder Sie können  **Unter Datenlimit** um beide Werte auf "false" festzulegen.  
  
6.  Von der **Roamingzustand** aufzulisten, legen Sie die [Roaming](/uwp/api/windows.networking.connectivity.connectioncost) Eigenschaft.  
  
7.  Wählen Sie **Eigenschaften** zu die Netzwerkeigenschaften zu simulieren, indem Sie ein [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) -vordergrundereignis und einen Hintergrund- [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) des Typs  **NetworkStateChange**.  
  
 **Weitere Informationen zum Verwalten von Netzwerkverbindungen**  
  
 [Schnellstart: Verwalten von gemessenen netzwerkkosteneinschränkungen](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
 [Beispiel für Netzwerkinformationen](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
 [Analysieren des Energieverbrauchs](../profiling/analyze-energy-use-in-store-apps.md)  
  
 [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)  
  
 [Gewusst wie: Reagieren auf Systemereignisse mit Hintergrundaufgaben](/previous-versions/windows/apps/hh977058(v=win.10))  
  
 [So können Sie Ereignisse in Windows UWP-Apps auslösen, anhalten, fortsetzen und im Hintergrund ausführen](/visualstudio/debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Navigieren des Simulators mit der Tastatur  
 Sie können die simulatorsymbolleiste navigieren, durch Drücken von **STRG + ALT + nach-oben** , den Fokus vom simulatorfenster auf die simulatorsymbolleiste zu verschieben. Verwenden Sie die **NACH-OBEN-TASTE** und die **NACH-UNTEN-TASTE** , um zwischen den Schaltflächen auf der Symbolleiste zu wechseln.  
  
 Sie können den Simulator durch Drücken von Herunterfahren **STRG + ALT + F4**.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Apps aus Visual Studio](../debugger/run-store-apps-from-visual-studio.md)