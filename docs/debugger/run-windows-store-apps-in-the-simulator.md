---
title: Ausführen von UWP-apps im Simulator | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 263759cc463bf21afa20877db320b4c83f1dc761
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187523"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Ausführen von UWP-Apps im Simulator

Der Visual Studio-Simulator für UWP-Apps ist eine Desktop Anwendung, die eine UWP-App simuliert. In der Regel empfiehlt es sich, auf dem lokalen Computer, einem verbundenen Gerät oder einem Remote Computer zu debuggen. In einigen Szenarien möchten Sie jedoch möglicherweise den Visual Studio-Simulator verwenden, um eine andere physische Bildschirmgröße und-Auflösung zu emulieren. Sie können auch allgemeine Berührungs-und Drehungs Ereignisse simulieren und Netzwerkverbindungseigenschaften simulieren.

Der Simulator stellt eine Umgebung bereit, in der Sie UWP-apps entwerfen, entwickeln, Debuggen und testen können. Bevor Sie Ihre APP jedoch in Microsoft Store veröffentlichen, sollten Sie Ihre APP auf einem tatsächlichen Gerät testen.

Der Visual Studio-Simulator für UWP-apps wird nicht in einer isolierten Umgebung auf dem lokalen Computer ausgeführt. Daher können im Simulator auftretende Fehler, z. B. nicht behebbare systemweite Fehler, auch Auswirkungen auf den restlichen Computer haben.

> [!IMPORTANT]
> Der Visual Studio 2015-Simulator umfasst nicht die Geolocation-Schaltfläche. Dies ist darin begründet, dass der Windows 10-Simulator keine Geolocation-Simulation umfasst.

## <a name="BKMK_Set_the_simulator_as_the_target"></a> Festlegen des Simulators als Ziel

Um die UWP-App im Simulator auszuführen, wählen Sie in der Dropdown Liste neben der Schaltfläche **Debuggen starten** auf der Debugger- **Standard** Symbolleiste die Option **Simulator** aus. Diese Option ist nur verfügbar, wenn die **Zielplattform min. Version** Ihrer APP kleiner als oder gleich dem Betriebssystem auf dem Entwicklungs Computer ist.

![Ausführung im Simulator](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")

## <a name="BKMK_Choose_an_interaction_mode"></a> Auswählen eines Interaktionsmodus

Sie können die folgenden Interaktions Modi auswählen:

- ![Schaltfläche für Mausmodus](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") Mausmodus: legt den Interaktionsmodus auf Mausgesten fest. Zu Mausgesten zählen Klicks, Doppelklicks und Ziehen.

- ![Schaltfläche](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") "Fingereingabe starten" Touch-Emulation starten: legt den Interaktionsmodus auf Touch-Gesten mit einem einzelnen Finger fest. Zu Einfingerereignissen zählen Tippen, Ziehen und Streifen.

   ![Simulator mit einem fingerziel](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")
   
   Das einzelne Zielsymbol gibt die Position von Ereignissen im Simulator an. Verwenden Sie die Maus, um den Zeiger zu positionieren.

   ![Ein Finger Touch-Ziel](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")
   
   Drücken Sie die linke Maustaste, um den Fingereingabemodus zu aktivieren. Klicken Sie beispielsweise auf die Schaltfläche, um ein Tippen zu simulieren oder drücken und halten Sie die Schaltfläche beim Ziehen oder Streifen.

## <a name="pinch-and-zoom"></a>Verkleinern und vergrößern

Legt den Interaktionsmodus auf Verkleinerungs- und Vergrößerungsgesten fest.

![Simulator mit zwei Fingern](../debugger/media/simulator_twofinger.png)

Das doppelte Zielsymbol gibt die Position von zwei Fingern auf dem Gerätebildschirm an.

- Bewegen Sie den Mauszeiger, um die Symbole über dem Objekt auf dem Gerätebildschirm zu positionieren.

- Drehen Sie das Mausrad nach oben oder unten , um den simulierten Abstand der zwei Finger vor dem Zusammendrücken oder Zoomen zu simulieren.

![Verkleinern, Vergrößern und Drehen von Zielen](../debugger/media/simulator_twofingerengaged.png)

- Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach unten (zu Ihnen hin), um zu vergrößern.

- Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach oben (von Ihnen weg), um zu verkleinern .

## <a name="object-rotation"></a>Objektdrehung

Die Schaltfläche **Fingereingabe-Emulation – Drehen** legt den Interaktionsmodus auf Drehbewegungen mit zwei Fingern fest.

- Bewegen Sie den Mauszeiger, um die Symbole über dem Objekt auf dem Gerätebildschirm zu positionieren. Drehen Sie das Mausrad nach oben oder unten, um die simulierte Ausrichtung der zwei Finger vor dem Drehen des Objekts zu simulieren.

- Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach unten (zu Ihnen hin), um das Objekt gegen den Uhrzeigersinn zu drehen. Beim Drehen des Mausrads rotiert eines der beiden Zielsymbole um das andere, um die relative Größe der Drehung anzugeben.

- Drücken Sie die linke Maustaste und drehen Sie das Mausrad nach oben (von Ihnen weg), um das Objekt im Uhrzeigersinn zu drehen.

## <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Aktivieren oder deaktivieren des "Immer im Vordergrund"-Modus
 Sie können festlegen, dass das Simulatorfenster immer an der obersten Position aller Fenster angezeigt wird. Die Schaltfläche **Umschalten des obersten Fensters** aktiviert oder deaktiviert den Modus **Immer im Vordergrund** des Simulatorfensters.

## <a name="BKMK_Change_the_device_orientation"></a> Ändern der Geräteausrichtung
 Sie können Hochformat- und Querformatausrichtung des Geräts wechseln, indem Sie den Simulator in beliebiger Richtung um 90 Grad drehen.

> [!NOTE]
> Der Simulator berücksichtigt nicht die Eigenschaft [DisplayProperties.AutoRotationPreferences](/uwp/api/Windows.Graphics.Display.DisplayProperties#Windows_Graphics_Display_DisplayProperties_AutoRotationPreferences) eines Projekts. Wenn Ihr Projekt beispielsweise auf die Ausrichtung `Landscape`festgelegt ist und Sie den Simulator in die Ausrichtung "Hochformat" drehen, wird die Anzeige des Simulators ebenfalls gedreht und die Größe angepasst. Testen Sie diese Einstellungen auf einem echten Gerät.

> [!NOTE]
> Wenn Sie den Simulator so drehen, dass der Simulator größer als der Bildschirm ist, auf dem er angezeigt wird, erfolgt eine automatische Größenanpassung auf die Bildschirmgröße. Die ursprüngliche Größe des Simulators wird nicht wiederhergestellt, wenn Sie diesen erneut drehen.

## <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Ändern der simulierten Bildschirmgröße und -auflösung
 Verwenden Sie die Schaltfläche **Auflösung ändern** auf der Palette, und wählen Sie anschließend eine neue Größe und Auflösung aus der Liste aus, um die simulierte Bildschirmgröße und -auflösung zu ändern.

 Die Bildschirmgröße und -auflösung werden als *Bildschirmbreite Zoll, Pixel Breite X Pixel Höhe*aufgeführt. Beachten Sie, dass sowohl Bildschirmgröße als auch -auflösung simuliert werden. Die Positionskoordinaten im Simulator werden in die ausgewählte Gerätegröße und-Auflösung übersetzt.

> [!NOTE]
> Sie können skalierte Versionen von Bitmapbildern in Ihrer App speichern, und Windows lädt das richtige Bild für die aktuelle Skalierung. Weitere Informationen finden Sie unter [Entwerfen und UI-](/windows/uwp/layout/design-and-ui-intro)Einführung. Wenn Sie die Simulatorauflösung ändern, sodass Windows ein anderes Bild für die Auflösung auswählt, müssen Sie die Debugsitzung beenden und erneut starten, damit das neue Bild angezeigt wird.

## <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Erfassen eines Screenshots Ihrer APP für die Übermittlung an Microsoft Store
 Wenn Sie eine APP an Microsoft Store übermitteln, müssen Sie Screenshots der APP einschließen.

> [!NOTE]
> Der Screenshot wird in der aktuellen Auflösung des Simulators gespeichert. Verwenden Sie die Schaltfläche **Auflösung ändern** , um die Auflösung zu ändern.

- Verwenden Sie die Schaltfläche **Screenshot in Zwischenablage ablegen** , um Screenshots Ihrer App im Simulator zu erstellen.

- Verwenden Sie die Schaltfläche **Screenshoteinstellungen** , und wählen Sie im Kontextmenü den Speicherort aus, um den Speicherort der Screenshots festzulegen.

   ![Kontextmenü für Screenshoteinstellungen](../debugger/media/simulator_screenshotsettingscntxmnu.png)

## <a name="BKMK_Simulate_network_connection_properties"></a> Simulieren der Netzwerkverbindungseigenschaften

Sie können die Benutzer der App dabei unterstützen, die Kosten gemessener Netzwerkverbindungen zu verwalten, indem Sie die Statusänderungen von Netzwerkverbindungskosten oder Datentarifplänen präsent halten und die App so aktivieren, dass zusätzliche Kosten für das Roaming oder das Überschreiten angegebener Datenübertragungsgrenzen anhand dieser Informationen vermieden werden. Mithilfe der [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) -APIs können Sie auf [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) - und [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) -Ereignisse antworten, die signieren. Weitere Informationen finden Sie unter [Schnellstart: Verwalten von gemessenen Netzwerkkosteneinschränkungen](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).

Um den Code für die kostenbewusste Nutzung des Netzwerks zu debuggen oder zu testen, kann der Simulator Eigenschaften eines Netzwerks imitieren, die vom [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) -Objekt verfügbar gemacht werden, das von [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation)zurückgegeben wird.

So simulieren Sie Netzwerkeigenschaften:

1. Wählen Sie auf der Simulatorsymbolleiste die Schaltfläche **Netzwerkeigenschaften ändern** aus.

2. Klicken Sie im Dialogfeld **Netzwerkeigenschaften festlegen** , und wählen Sie **Simulierte Netzwerkeigenschaften verwenden**aus.

    Deaktivieren Sie das Kontrollkästchen, um die Simulation zu entfernen und zu den Netzwerkeigenschaften der aktuell verbundenen Schnittstelle zurückzukehren.

3. Geben Sie **Profilname** für das simulierte Netzwerk ein. Es empfiehlt sich, einen eindeutigen Namen zu verwenden, den Sie verwenden können, um die Simulation in der [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) -Eigenschaft des [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) -Objekts zu identifizieren.

4. Wählen Sie den [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) -Wert für das Profil aus der Liste **Netzwerkkostentyp** aus.

5. Aus der Liste **Datenlimit-Statusflag** können Sie die [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost)- oder die [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost)-Eigenschaft auf „true“ festlegen. Sie können auch **Unter Datenlimit** auswählen, um beide Werte auf „false“ festzulegen.

6. Legen Sie aus der Liste **Roamingzustand** die [Roaming](/uwp/api/windows.networking.connectivity.connectioncost) -Eigenschaft fest.

7. Wählen Sie **Eigenschaften festlegen** , um die Netzwerkeigenschaften zu simulieren, indem Sie ein [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) -Vordergrundereignis und einen Hintergrund- [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) vom Typ **NetworkStateChange**starten.

Weitere Informationen zum Verwalten von Netzwerkverbindungen finden Sie unter:

[Schnellstart: Verwalten von gemessenen Netzwerkkosteneinschränkungen](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)

[Beispiel für Netzwerkinformationen](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)

::: moniker range="vs-2017"
[Analysieren des Energieverbrauchs](../profiling/analyze-energy-use-in-store-apps.md)
::: moniker-end

[Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)

[Reagieren auf Systemereignisse mit Hintergrundaufgaben](/previous-versions/windows/apps/hh977058(v=win.10))

[So können Sie Ereignisse in Windows UWP-Apps auslösen, anhalten, fortsetzen und im Hintergrund ausführen](how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Navigieren des Simulators mit der Tastatur

Sie können durch Drücken von **Strg + Alt +** nach-oben-Taste navigieren, um den Fokus vom simulatorfenster auf die Simulator-Symbolleiste zu wechseln. Verwenden Sie die **NACH-OBEN-TASTE** und die **NACH-UNTEN-TASTE** , um zwischen den Schaltflächen auf der Symbolleiste zu wechseln.

Sie können den Simulator durch Drücken von **STRG + ALT + F4**Herunterfahren.

## <a name="see-also"></a>Siehe auch

- [Ausführen von Apps aus Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
