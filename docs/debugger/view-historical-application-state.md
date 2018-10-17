---
title: Anzeigen der vorherigen Zustand der Anwendung mit IntelliTrace
ms.description: Learn how to take snapshots, and view snapshots with IntelliTrace step-back
ms.custom: mvc
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85b34fd85e8449949bb1e96efc1dd79aacbc1bd9
ms.sourcegitcommit: 1c675dae7c348defb32d9f7ccf7079a1062a1c4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "48243951"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio"></a>Überprüfen Sie die vorherigen app-Status, die mithilfe von IntelliTrace Rückschritt in Visual Studio

IntelliTrace Rückschritt Momentaufnahme automatisch eine Ihrer Anwendung in jedem Breakpoint und Debuggerschritt Schrittereignis. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

IntelliTrace-Schritt-Feature ist ab Visual Studio Enterprise 2017 Version 15.5 und höher verfügbar und erfordert Windows 10 Anniversary Update oder höher. Das Feature wird derzeit für das Debuggen von ASP.NET, WinForms, WPF, verwalteten Konsolen-apps und verwalteten Klassenbibliotheken unterstützt. Ab Visual Studio 2017 Enterprise-Version 15.7 wird wird das Feature auch für ASP.NET Core und .NET Core unterstützt. Beginnend mit Visual Studio 2017 Enterprise-Version 15.9 wird Preview 2, das Feature auch für native apps, die für Windows unterstützt. Debuggen von UWP-Anwendungen wird derzeit nicht unterstützt.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Aktivieren von Intellitrace-Ereignisse und Momentaufnahmen
> * Navigieren Sie Ereignisse mithilfe der Schritt zurück und Schritt-Forward-Befehle
> * Ereignis-Momentaufnahmen anzeigen
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>IntelliTrace-Ereignisse und-Momentaufnahmen-Modus aktivieren 

1. Öffnen Sie Ihr Projekt in Visual Studio Enterprise.

1. Open **Tools** > **Optionen** > **IntelliTrace** Einstellungen, und wählen Sie die Option **IntelliTrace-Ereignisse und Momentaufnahmen** . 

    Ab Visual Studio 2017 Enterprise-Version 15.9 Preview 2, diese Option ist die **IntelliTrace-Momentaufnahmen (verwaltet und systemeigen)**. 

    ![Aktivieren des Modus für IntelliTrace-Ereignisse und-Momentaufnahmen](../debugger/media/intellitrace-enable-snapshots.png "Aktivieren von IntelliTrace-Ereignisse und Momentaufnahmen-Modus")

1. Wenn Sie Optionen zum Anzeigen von Momentaufnahmen zu Ausnahmen konfigurieren möchten, wählen Sie **IntelliTrace** > **erweitert** aus der **Optionen** Dialogfeld.

    Diese Optionen sind verfügbar in Visual Studio 2017 Enterprise-Version 15.7 ab.

    ![Konfigurieren von Verhalten für Momentaufnahmen für Ausnahmen](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Wenn Sie Ereignisse und-Momentaufnahmen aktivieren, wird auch Momentaufnahmen bei Ausnahmen standardmäßig aktiviert. Sie können Momentaufnahmen für Ausnahmen deaktivieren, wählen Sie hierzu von **Sammeln von Momentaufnahmen zu Ausnahmeereignissen**. Wenn dieses Feature aktiviert ist, werden Momentaufnahmen für nicht behandelte Ausnahmen erstellt. Behandelt Ausnahmen werden Momentaufnahmen erstellt, und nur dann, wenn die Ausnahme ausgelöst wird, ist dies nicht erneut Auslösen einer Ausnahme zuvor ausgelöst. Sie können eine maximale Anzahl von Momentaufnahmen bei Ausnahmen festlegen, indem Sie einen Wert aus der Dropdown-Liste auswählen. Die maximale gilt für jedes Mal, wenn Ihre app in den Unterbrechungsmodus wechselt (z. B., wenn Ihre app einen Haltepunkt erreicht).

    > [!NOTE]
    > Momentaufnahmen sind nur für Ausnahmeereignisse von IntelliTrace aufgezeichneten erstellt. Für verwalteten Code können Sie welche Ereignisse IntelliTrace aufzeichnet angeben, indem Sie die Auswahl **Tools** > **Optionen** > **IntelliTrace-Ereignisse**.

1. In Ihrem Projekt eine oder mehrere Haltepunkte festlegen, und starten Sie das Debuggen (drücken Sie die **F5**), oder starten Sie das Debuggen durch den Code schrittweise durchlaufen (**F10** oder **F11**).

    IntelliTrace erstellt eine Momentaufnahme der Anwendungsprozess auf jeden Debuggerschritt, Haltepunktereignis und nicht behandelten Ausnahmeereignisses. Diese Ereignisse werden aufgezeichnet, der **Ereignisse** Registerkarte die **Diagnosetools** Fenster zusammen mit anderen IntelliTrace-Ereignisse. Wählen Sie zum Öffnen dieses Fensters **Debuggen** > **Windows** > **Diagnosetools anzeigen**.

    Eine Kamerasymbol wird neben den Ereignissen, die für die Momentaufnahmen verfügbar sind. 

    ![Ereignisse mit Momentaufnahmen Registerkarte](../debugger/media/intellitrace-events-tab-with-snapshots.png "Registerkarte \"Ereignisse\" mit Momentaufnahmen zu Haltepunkten und Schritten")

    Aus Leistungsgründen werden die Momentaufnahmen nicht erstellt, wenn Sie sehr schnell ausführen. Wenn keine Kamerasymbol neben dem Schritt angezeigt wird, versuchen Sie es schrittweise Ausführung langsamer.

## <a name="navigate-and-view-snapshots"></a>Navigieren Sie aus, und Anzeigen von Momentaufnahmen

1. Navigieren Sie zwischen Ereignissen mithilfe der **Schritt zurück (Alt + [)** und **Schritt vorwärts (Alt +])** Schaltflächen in der Debug-Symbolleiste.

    Diese Schaltflächen zu navigieren, die Ereignisse, die in angezeigt werden. die **Ereignisse** Registerkarte die **Fenster "Diagnosetools"**. Schrittweises durchlaufen vorwärts oder rückwärts für ein Ereignis automatisch aktiviert [verlaufsbezogenes debugging](../debugger/historical-debugging.md) für das ausgewählte Ereignis.

    ![Schrittweise rückwärts und Vorwärts-Schaltflächen](../debugger/media/intellitrace-step-back-icons-description.png "Schritt zurück und Schritt vorwärts-Schaltflächen")

    Wenn Sie zurück, oder ein vorwärts Schritt, wechselt Visual Studio Modus "verlaufsbezogenes debugging" an. In diesem Modus wechselt den datenschnellansichten des Debuggers mit der Zeit, wenn das ausgewählte Ereignis aufgezeichnet wurde. Visual Studio verschiebt außerdem den Zeiger auf die entsprechende Zeile des Codes im Quellcodefenster. 

    In dieser Ansicht können Sie überprüfen, die Werte in der **Aufrufliste**, **"lokal"**, **"Auto"**, und **Watch** Windows. Sie können auch über Variablen, um DataTips anzuzeigen, und führen Sie die Auswertung von Ausdrücken in zeigen die **direkt** Fenster. Die angezeigten Daten werden aus der der Anwendungsprozess ausgeführt wird, zu diesem Zeitpunkt-Momentaufnahme ist.

    Ja, z. B. Wenn Sie einen Haltepunkt und einen Schritt erstellt haben (**F10**), wird die **Schritt zurück** Schaltfläche wird Visual Studio im Modus "verlaufsbezogenes" in der Codezeile, die für den Haltepunkt. 

    ![Aktiviert Modus "verlaufsbezogenes" auf ein Ereignis mit einer Momentaufnahme](../debugger/media/intellitrace-historical-mode-with-snapshot.png "aktiviert Modus \"verlaufsbezogenes\" auf ein Ereignis mit einer Momentaufnahme")

2. Um zum live-Ausführung zurückzukehren, wählen Sie **fortsetzen (F5)** oder klicken Sie auf die **zurück zum Livedebugging** -Link in der Infoleiste. 

3. Sie können auch anzeigen, eine Momentaufnahme aus der **Ereignisse** Registerkarte. Zu diesem Zweck wählen Sie ein Ereignis mit einer Momentaufnahme aus, und klicken Sie auf **verlaufsbezogenes Debugging aktivieren**.

    ![Verlaufsbezogenes Debugging aktivieren, auf ein Ereignis](../debugger/media/intellitrace-activate-historical-debugging.png "verlaufsbezogenes Debugging für ein Ereignis aktivieren")

    Im Gegensatz zu den **Festlegen der nächsten Anweisung** Befehl Anzeigen einer Momentaufnahme nicht erneut Ihr Code ausgeführt; sie erhalten Sie eine statische Ansicht des Zustands der Anwendung zu einem Zeitpunkt in der Zeit, die in der Vergangenheit aufgetreten ist.

    ![Übersicht über IntelliTrace Rückschritt](../debugger/media/intellitrace-step-back-overview.png "Übersicht über die von IntelliTrace ein Schritt zurück")

    Weitere Informationen zum Untersuchen von Variablen in Visual Studio finden Sie unter [Debugger – Featuretour](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen (FAQs)

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Wie unterscheidet sich IntelliTrace Rückschritt von IntelliTrace-Ereignisse Modus?

IntelliTrace im Ereignisse Modus lässt Sie in Einzelschritten des Debuggers und Haltepunkten verlaufsbezogenes debugging aktivieren. IntelliTrace zeichnet jedoch nur Daten in die **"lokal"** und **"Auto"** Windows, wenn die Fenster geöffnet sind, und es erfasst nur Daten, die erweitert wird und in der Ansicht. Im Modus nur Ereignisse müssen häufig Sie keinen vollständigen Überblick über die Variablen und komplexe Objekte. Darüber hinaus Ausdruck Auswertung und Anzeigen von Daten in die **Watch** Fenster wird nicht unterstützt. 

Im Modus für Ereignisse und-Momentaufnahmen erfasst IntelliTrace den gesamte Momentaufnahme der der Anwendungsprozess, z. B. komplexe Objekte. In einer Zeile des Codes sehen Sie die gleiche Informationen, als ob Sie an einem Haltepunkt beendet wurden (und es keine Rolle spielt, ob Sie zuvor die Informationen erweitert). Auswertung des Ausdrucks wird ebenfalls unterstützt, wenn Sie eine Momentaufnahme anzeigen.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Was ist die Auswirkungen auf die Leistung dieses Feature? 

Die Auswirkungen auf die gesamtleistung der schrittweisen Ausführung hängt von Ihrer Anwendung ab. Der Mehraufwand für das Erstellen einer Momentaufnahme ist ca. 30 ms. Wenn eine Momentaufnahme erstellt wird, den Prozess der app verzweigt ist und die verzweigte Kopie wird angehalten. Wenn Sie eine Momentaufnahme anzeigen, ist das Visual Studio auf die verzweigten Kopie an den Prozess anfügen. Für jede Momentaufnahme Visual Studio kopiert nur die Seitentabelle und Seiten auf Kopie-bei-Schreibvorgang. Wenn Objekte auf dem Heap zwischen Einzelschritten des Debuggers mit zugeordneten Momentaufnahmen ändern, wird die jeweiligen Seitentabelle dann kopiert, minimale Speicherkosten führt. Wenn Visual Studio erkennt, dass nicht genügend Arbeitsspeicher zum Erstellen einer Momentaufnahme, dauert nicht eine.
 
## <a name="known-issues"></a>Bekannte Probleme  
* Wenn Sie IntelliTrace-Ereignisse und-Momentaufnahmen-Modus auf Versionen von Windows, die älter als Windows 10 Fall Creators Update (RS3) verwenden und wenn das Debugziel für die Plattform der Anwendung auf X86 festgelegt ist, nimmt IntelliTrace keine Momentaufnahmen an.

    Problemumgehungen:
    * Wenn Sie auf das Windows 10 Anniversary Update (RS1) und aktuellere 10.0.14393.2273, [installieren KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720). 
    * Wenn Sie auf dem Windows 10 Creators Update (RS2) und aktuellere 10.0.15063.1112, [installieren KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
    * Installieren oder ein upgrade auf Windows 10 Fall Creators Update (RS3). 
    * Alternativ: 
        1. Installieren Sie das Toolset VC++ 2015.3 v140 für Desktop (x86, x64) aus dem Visual Studio-Installer.
        2. Erstellen Sie die Zielanwendung.
        3. Verwenden Sie das Editbin-Tool über die Befehlszeile, Festlegen der `Largeaddressaware` Flag für die ausführbare Zieldatei. Beispielsweise können Sie diesen Befehl verwenden, (nach der Aktualisierung des Pfads): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" / LARGEADDRESSAWARE "C:\Path\To\Application\app.exe".
        4. Drücken Sie **F5**, um mit dem Debuggen zu beginnen. Jetzt werden Momentaufnahmen in Einzelschritten des Debuggers und Haltepunkten erstellt.

        > [!Note]
        > Die `Largeaddressaware` Flag muss festgelegt werden jedes Mal, die die ausführbare Datei mit Änderungen neu erstellt wird.

* Wenn eine Momentaufnahme der Prozess der Anwendung für eine Anwendung, die eine permanente Speicher abgebildete Datei verwendet erstellt wird, hält der Prozess mit der Momentaufnahme eine exklusive Sperre auf die Datei mit zugewiesenem Speicher, (auch nach der übergeordnete Prozess die Sperre aufgehoben hat). Andere Prozesse können immer noch gelesen, aber nicht in der Datei mit zugewiesenem Speicher schreiben.

    Problemumgehung:
    * Deaktivieren Sie alle Momentaufnahmen, indem Sie die Debugsitzung beenden. 

* Beim Debuggen einer Anwendung, deren Prozess eine hohe Anzahl von eindeutigen Speicherbereiche, z. B. eine Anwendung verfügt, die eine große Anzahl von DLLs lädt, möglicherweise stepping Leistung mit Momentaufnahmen aktiviert beeinträchtigt. Dieses Problem wird in einer zukünftigen Version von Windows behoben werden. Wenn Sie dieses Problem auftreten, wenden Sie sich an uns stepback@microsoft.com. 

* Beim Speichern einer Datei mit **Debuggen > IntelliTrace > Speichern Sie die IntelliTrace-Sitzung** Ereignisse und-Momentaufnahmen im Modus für die zusätzlichen Daten erfasst, die aus Momentaufnahmen ist nicht verfügbar in der ITRACE-Datei. Auf Haltepunkt und Schritt-Ereignisse sehen Sie die gleiche Informationen, als ob Sie die Datei im IntelliTrace-Ereignisse Modus gespeichert haben. 

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie IntelliTrace Rückschritt verwendet wird. Sie möchten möglicherweise weitere Informationen zu anderen IntelliTrace-Funktionen.

> [!div class="nextstepaction"]
> [IntelliTrace-Funktionen](../debugger/intellitrace-features.md)
