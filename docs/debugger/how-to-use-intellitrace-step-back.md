---
title: Anzeigen eine Momentaufnahme mit Schritt-Back - Visual Studio IntelliTrace | Microsoft Docs
ms.description: Learn how to take snapshots, and view snapshots with IntelliTrace step-back
ms.custom: mvc
ms.date: 12/06/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
caps.latest.revision: ''
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8f9f0c65110ef1003c58c0a4002f90ec7e7e08e3
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="view-snapshots-using-intellitrace-step-back-in-visual-studio"></a>Anzeigen von Momentaufnahmen mithilfe von IntelliTrace-Schritt-wieder in Visual Studio

IntelliTrace-Schritt-Back erstellt eine Momentaufnahme Ihrer Anwendung bei jeder Haltepunkt und der Debugger automatisch bei Schritt-Ereignis. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

IntelliTrace-Schritt-wieder wird ab Visual Studio Enterprise 2017 Version 15.5 und höher verfügbar und erfordert Anniversary-Update für Windows 10 oder höher. Das Feature ist derzeit für das Debuggen von ASP.NET, WinForms, WPF, verwaltete Konsolen-apps und verwalteten Klassenbibliotheken unterstützt. Beginnend mit Visual Studio 2017 Enterprise Version 15.7 Preview 1, wird die Funktion auch für ASP.NET Core und .NET Core unterstützt. Debuggen von uwp-Apps wird derzeit nicht unterstützt.

In diesem Lernprogramm führen Sie folgende Aktionen ausführen:

> [!div class="checklist"]
> * Aktivieren von Intellitrace-Ereignisse und Momentaufnahmen
> * Navigieren Sie Ereignisse, die mit Befehlen Schritt zurück und Schritt vorwärts
> * Anzeigen von Momentaufnahmen-Ereignis
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>IntelliTrace-Ereignisse und Momentaufnahmen Modus aktivieren 

1. Öffnen Sie das Projekt in Visual Studio Enterprise.

1. Wechseln Sie zu **Extras > Optionen > IntelliTrace** Einstellungen, und wählen Sie die Option **IntelliTrace-Ereignisse und Momentaufnahmen**. 

    ![Aktivieren Sie den IntelliTrace-Ereignisse und Momentaufnahmen Modus](../debugger/media/intellitrace-enable-snapshots.png "Modus aktivieren von IntelliTrace-Ereignisse und Momentaufnahmen")

1. Legen Sie einen oder mehrere Haltepunkte in Ihrem Projekt, und starten Sie das Debuggen (drücken Sie **F5**), oder starten Sie das Debuggen durch schrittweises Durchlaufen des Codes (**F10** oder **F11**).

    IntelliTrace nimmt eine Momentaufnahme des Prozesses für die Anwendung auf jeder Debugger Schritt und Haltepunkt-Ereignisses. Diese Ereignisse werden aufgezeichnet, der **Ereignisse** Registerkarte der **Diagnosetools** Fenster zusammen mit weiteren IntelliTrace-Ereignissen. Um dieses Fenster zu öffnen, wählen Sie **Debuggen** > **Windows** > **Diagnosetools anzeigen**.

    Neben den Ereignissen, die für die Momentaufnahmen verfügbar sind, wird ein Kamerasymbol angezeigt. 

    ![Ereignisse mit Momentaufnahmen Registerkarte](../debugger/media/intellitrace-events-tab-with-snapshots.png "Registerkarte "Ereignisse" mit Momentaufnahmen Haltepunkte und Schritte")

    Aus Gründen der Leistung werden Momentaufnahmen nicht implementiert, wenn Sie sich sehr schnell. Wenn kein Kamerasymbol neben dem Schritt angezeigt wird, versuchen Sie es ausführen in Einzelschritten langsamer.

## <a name="navigate-and-view-snapshots"></a>Navigieren und Anzeigen von Momentaufnahmen

1. Navigieren Sie zwischen Ereignissen mithilfe der **Schritt zurück (Alt + [)** und **Schritt vorwärts (Alt +])** Schaltflächen in der Debug-Symbolleiste.

    Diese Schaltflächen navigieren, die Ereignisse, die in der **Ereignisse** Registerkarte der **Fenster "Diagnosetools"**. Ausführen in Einzelschritten vorwärts oder rückwärts auf ein Ereignis automatisch aktiviert [verlaufsbezogenes debugging](../debugger/historical-debugging.md) auf das ausgewählte Ereignis.

    ![Schritt rückwärts und Vorwärts-Schaltflächen](../debugger/media/intellitrace-step-back-icons-description.png "Schritt rückwärts und Schritt vorwärts-Schaltflächen")

    Wenn Sie zurückgehen oder vorwärts Schritt, wechselt Visual Studio verlaufsbezogenen Debugmodus vor. In diesem Modus wechselt, den Kontext des Debuggers mit der Zeit, wenn das ausgewählte Ereignis aufgezeichnet wurde. Visual Studio auch Mauszeiger den auf die entsprechende Zeile des Codes im Quellcodefenster. 

    In dieser Ansicht können Sie überprüfen, die Werte in der **Aufrufliste**, **"lokal"**, **"Auto"**, und **Überwachen** Windows. Sie können auch den Mauszeiger Variablen so zeigen DataTips und führen die Auswertung von Ausdrücken in der **Direktfenster** Fenster. Daten, die Sie sehen werden aus der Momentaufnahme, der die Anwendung zu diesem Zeitpunkt durchgeführt.

    Dies der Fall ist, z. B. Wenn Sie einen Haltepunkt erreicht und einen Schritt ausgeführt haben (**F10**), wird die **Schritt rückwärts** Schaltfläche fügt Visual Studio in historischen-Modus auf die Codezeile, die bis zum Haltepunkt entspricht. 

    ![Verlaufsdaten Modus aktiviert, auf ein Ereignis mit einer Momentaufnahme](../debugger/media/intellitrace-historical-mode-with-snapshot.png "historische aktiviert-Modus auf ein Ereignis mit einer Momentaufnahme")

2. Um zum live-Ausführung zurückzukehren, wählen Sie **fortfahren (F5)** oder klicken Sie auf die **zurück zum Live-Debuggen** Link in der Infoleiste. 

3. Sie können auch anzeigen, eine Momentaufnahme aus der **Ereignisse** Registerkarte. Zu diesem Zweck wählen Sie ein Ereignis mit einer Momentaufnahme, und klicken Sie auf **verlaufsbezogenes Debugging aktivieren**.

    ![Verlaufsbezogenes Debugging aktivieren, auf ein Ereignis](../debugger/media/intellitrace-activate-historical-debugging.png "verlaufsbezogenes Debugging auf ein Ereignis aktivieren")

    Im Gegensatz zu den **nächste Anweisung festlegen** Befehl, Anzeigen von einer Momentaufnahme nicht erneut Codes ausgeführt; es gibt Ihnen eine statische Ansicht des Zustands der Anwendung zu einem Zeitpunkt in der Zeit, die in der Vergangenheit aufgetreten ist.

    ![Übersicht über die IntelliTrace-Schritt-Back](../debugger/media/intellitrace-step-back-overview.png "Übersicht über die von IntelliTrace Schritt hinten")

    Weitere Informationen zum Untersuchen von Variablen in Visual Studio finden Sie unter [Debugger-Funktion Tour](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen (FAQs)

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Wie unterscheidet sich IntelliTrace Schritt hinten von IntelliTrace-Ereignisse nur im Modus?

IntelliTrace befindet sich im Modus Ereignisse lässt Sie Debuggersprung und Haltepunkte verlaufsbezogenes debugging aktivieren. Allerdings erfasst IntelliTrace nur Daten in der **"lokal"** und **"Auto"** Windows, wenn die Fenster geöffnet sind, und sie erfasst nur Daten, die erweitert werden und in der Sicht. Im Modus nur Ereignisse müssen Sie oftmals einen vollständigen Überblick über die Variablen und komplexe Objekte keinen. Darüber hinaus Ausdruck Auswertung und Anzeigen von Daten in der **Überwachen** Fenster wird nicht unterstützt. 

Im Modus für Ereignisse und Momentaufnahmen erfasst IntelliTrace die gesamte Momentaufnahme der Anwendungsprozess, z. B. komplexe Objekte. Bei einer Codezeile sehen Sie die gleiche Informationen, als ob Sie an einem Haltepunkt angehalten wurden (und es unerheblich ist, ob Sie die Informationen bereits erweitert). Auswertung von Ausdrücken wird ebenfalls unterstützt, wenn Sie eine Momentaufnahme anzeigen.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Was ist die Auswirkungen auf die Leistung dieser Funktion? 

Die Auswirkung auf die gesamtleistung der schrittweisen Ausführung hängt von der Anwendung ab. Der Aufwand für das Erstellen einer Momentaufnahme ist ca. 30 ms. Wenn eine Momentaufnahme erstellt wird, wird die app-Prozess verzweigt ist, und die verzweigter Kopie wird angehalten. Wenn Sie eine Momentaufnahme anzuzeigen, ist Visual Studio auf die verzweigter Kopie des Prozesses anfügen. Für jede Momentaufnahme Visual Studio kopiert nur die Seitentabelle und Seiten auf Kopie-bei-Schreibvorgang. Wenn Objekte auf dem Heap zwischen Debuggersprung mit zugeordneten Momentaufnahmen ändern, wird der jeweiligen Seitentabelle minimale Speicherkosten führt dann kopiert. Wenn Visual Studio erkennt, dass es nicht genügend Arbeitsspeicher zum Erstellen einer Momentaufnahme ist, dauert nicht eine.
 
## <a name="known-issues"></a>Bekannte Probleme  
* Bei Verwendung von IntelliTrace-Ereignisse und Momentaufnahmen-Modus auf Versionen von Windows, die älter sind als Update für Windows 10 fallen Ersteller (RS3), und wenn das Debugziel für die Plattform der Anwendung auf X86 festgelegt ist, ist IntelliTrace keine Momentaufnahmen erstellen.

    Problemumgehung:
    * Installieren oder Aktualisieren auf Windows 10 fallen Ersteller Update (RS3). 
    * Alternativ: 
        1. Installieren Sie das Toolset VC++ 2015.3 v140 für Desktop (x86, x64) aus dem Visual Studio-Installer.
        2. Erstellen Sie die Zielanwendung.
        3. Über die Befehlszeile verwenden Sie das Tool Editbin Festlegen der `Largeaddressaware` der ausführbaren Zieldatei zu kennzeichnen. Beispielsweise können mit diesem Befehl (nach dem Aktualisieren des Pfads): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" LARGEADDRESSAWARE "C:\Path\To\Application\app.exe".
        4. Drücken Sie **F5**, um mit dem Debuggen zu beginnen. Jetzt sind Momentaufnahmen Debuggersprung und Haltepunkte generiert.

        > [!Note]
        > Die `Largeaddressaware` Flag muss festgelegt werden jedes Mal, die die ausführbare Datei mit Änderungen neu erstellt wird.

* Wenn eine Momentaufnahme des Prozesses für die Anwendung auf eine Anwendung, der eine permanente Speicher abgebildete Datei verwendet erstellt wird, enthält der Prozess mit der Momentaufnahme eine exklusive Sperre für die Speicherabbilddatei (selbst wenn der übergeordnete Prozess die Sperre aufgehoben hat). Andere Prozesse werden weiterhin kann gelesen, aber nicht in den im Speicher abgebildeten Datei geschrieben.

    Problemumgehung:
    * Deaktivieren Sie alle Momentaufnahmen, indem Sie die Debugsitzung beenden. 

* Beim Debuggen einer Anwendung, deren Prozess verfügt über eine große Anzahl von eindeutigen Speicherbereiche, z. B. eine Anwendung, die eine große Anzahl von DLLs, lädt, möglicherweise die Leistung mit Momentaufnahmen aktiviert stepping beeinträchtigt. Dieses Problem wird in einer zukünftigen Version von Windows behandelt werden. Wenn Sie dieses Problem auftreten, Remoteknoten uns stepback@microsoft.com. 

* Beim Speichern einer Datei mit **Debuggen > IntelliTrace > Speichern der IntelliTrace-Sitzung** im Modus für Ereignisse und Momentaufnahmen, die zusätzlichen Daten, die von Momentaufnahmen aufgezeichneten ist nicht verfügbar in der ITRACE-Datei. Auf den Haltepunkt und Schritt-Ereignisse wird die gleichen Informationen angezeigt, als ob Sie die Datei befindet sich im Modus IntelliTrace-Ereignisse gespeichert wurde. 

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm haben Sie gelernt, wie mithilfe von IntelliTrace-Schritt-Back wird. Sie möchten möglicherweise weitere Informationen zu anderen IntelliTrace-Funktionen.

> [!div class="nextstepaction"]
> [IntelliTrace-Funktionen](../debugger/intellitrace-features.md)
