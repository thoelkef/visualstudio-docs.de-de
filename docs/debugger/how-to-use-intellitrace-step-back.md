---
title: Anzeigen eine Momentaufnahme mit Schritt-Back - Visual Studio IntelliTrace | Microsoft Docs
ms.custom: 
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c05905e8ffeec3aa699aac9dfa46c4b017b86be5
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2017
---
# <a name="view-snapshots-using-intellitrace-step-back"></a>Anzeigen von Momentaufnahmen mithilfe von IntelliTrace-Schritt-zurück
IntelliTrace-Schritt-Back erstellt eine Momentaufnahme Ihrer Anwendung bei jeder Haltepunkt und der Debugger automatisch bei Schritt-Ereignis. Die erfassten Momentaufnahmen können Sie zurückkehren zum vorherigen Haltepunkte oder Schritte und den Status der Anwendung anzeigen, wie dies in der Vergangenheit war. IntelliTrace Schritt Back kann sparen Sie Zeit, wenn Sie möchten, finden in den vorherigen Anwendungszustand aber nicht angezeigt werden sollen, Debuggen neu starten, oder erstellen Sie die gewünschte app-Status erneut.

IntelliTrace-Schritt-wieder wird ab Visual Studio Enterprise 2017 Version 15.5 und höher verfügbar und erfordert Anniversary-Update für Windows 10 oder höher. Das Feature ist derzeit für das Debuggen von ASP.NET, WinForms, WPF, verwaltete Konsolen-apps und verwalteten Klassenbibliotheken unterstützt. Debuggen von ASP.NET Core, .NET Core oder uwp-Anwendungen ist derzeit nicht unterstützt. 
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>IntelliTrace-Ereignisse und Momentaufnahmen Modus aktivieren 
Um das Feature zu aktivieren, wechseln Sie zu **Extras > Optionen > IntelliTrace** Einstellungen, und wählen Sie die Option **IntelliTrace-Ereignisse und Momentaufnahmen**. 

![Aktivieren Sie den IntelliTrace-Ereignisse und Momentaufnahmen Modus](../debugger/media/intellitrace-enable-snapshots.png "Modus aktivieren von IntelliTrace-Ereignisse und Momentaufnahmen")

IntelliTrace nimmt eine Momentaufnahme des Prozesses für die Anwendung auf jeder Debugger Schritt und Haltepunkt-Ereignisses. Diese Ereignisse werden aufgezeichnet, der **Ereignisse** Registerkarte der **Diagnosetools** Fenster zusammen mit weiteren IntelliTrace-Ereignissen. Um dieses Fenster zu öffnen, wählen Sie **Debuggen / Windows / Diagnosetools anzeigen**.

Neben den Ereignissen, die für die Momentaufnahmen verfügbar sind, wird ein Kamerasymbol angezeigt. 

![Ereignisse mit Momentaufnahmen Registerkarte](../debugger/media/intellitrace-events-tab-with-snapshots.png "Registerkarte "Ereignisse" mit Momentaufnahmen Haltepunkte und Schritte")

Aus Gründen der Leistung werden Momentaufnahmen nicht implementiert, wenn Sie sich sehr schnell. Wenn kein Kamerasymbol neben dem Schritt angezeigt wird, versuchen Sie es ausführen in Einzelschritten langsamer.

## <a name="navigate-and-view-snapshots"></a>Navigieren und Anzeigen von Momentaufnahmen

Sie können Navigieren zwischen Ereignissen bei der Verwendung der **Schritt zurück (Alt + [)** und **Schritt vorwärts (Alt +])** Schaltflächen in der Debug-Symbolleiste. Diese Schaltflächen navigieren, die Ereignisse, die in der **Ereignisse** Registerkarte der **Fenster "Diagnosetools"**. Verlaufsbezogenes debugging für das ausgewählte Ereignis ausführen in Einzelschritten vorwärts oder rückwärts auf ein Ereignis automatisch aktiviert werden.

![Schritt rückwärts und Vorwärts-Schaltflächen](../debugger/media/intellitrace-step-back-icons-description.png "Schritt rückwärts und Schritt vorwärts-Schaltflächen")

Wenn Sie zurückgehen oder vorwärts Schritt, wechselt Visual Studio verlaufsbezogenen Debugmodus vor. In diesem Modus wechselt, den Kontext des Debuggers mit der Zeit, wenn das ausgewählte Ereignis aufgezeichnet wurde. Visual Studio auch Mauszeiger den auf die entsprechende Zeile des Codes im Quellcodefenster. 

In dieser Ansicht können Sie überprüfen, die Werte in der **Aufrufliste**, **"lokal"**, **"Auto"**, und **Überwachen** Windows. Sie können auch den Mauszeiger Variablen so zeigen DataTips und führen die Auswertung von Ausdrücken in der **Direktfenster** Fenster. Daten, die Sie sehen werden aus der Momentaufnahme, der die Anwendung zu diesem Zeitpunkt durchgeführt.

Dies der Fall ist, z. B. Wenn Sie einen Haltepunkt erreicht und einen Schritt ausgeführt haben (**F10**), wird die **Schritt rückwärts** Schaltfläche fügt Visual Studio in historischen-Modus auf die Codezeile, die bis zum Haltepunkt entspricht. 

![Verlaufsdaten Modus aktiviert, auf ein Ereignis mit einer Momentaufnahme](../debugger/media/intellitrace-historical-mode-with-snapshot.png "historische aktiviert-Modus auf ein Ereignis mit einer Momentaufnahme")

Um zum live-Ausführung zurückzukehren, wählen Sie **fortfahren (F5)** oder klicken Sie auf die **zurück zum Live-Debuggen** Link in der Infoleiste. 

Sie können auch anzeigen, eine Momentaufnahme aus der **Ereignisse** Registerkarte. Wählen Sie ein Ereignis mit einer Momentaufnahme, und klicken Sie auf **verlaufsbezogenes Debugging aktivieren**. Sie können auch auf das Kamerasymbol verlaufsbezogenes debugging aktivieren klicken.

![Verlaufsbezogenes Debugging aktivieren, auf ein Ereignis](../debugger/media/intellitrace-activate-historical-debugging.png "verlaufsbezogenes Debugging auf ein Ereignis aktivieren")

Im Gegensatz zu den **nächste Anweisung festlegen** Befehl, Anzeigen von einer Momentaufnahme nicht erneut Codes ausgeführt; es gibt Ihnen eine statische Ansicht des Zustands der Anwendung zu einem Zeitpunkt in der Zeit, die in der Vergangenheit aufgetreten ist.

![Übersicht über die IntelliTrace-Schritt-Back](../debugger/media/intellitrace-step-back-overview.png "Übersicht über die von IntelliTrace Schritt hinten")

## <a name="next-steps"></a>Nächste Schritte  
 Gewusst wie: Untersuchen von Variablen in Visual Studio finden Sie unter [Debugger-Funktion Tour](../debugger/debugger-feature-tour.md)  
 Einen Überblick über das verlaufsbezogene debugging finden Sie unter [verlaufsbezogenes debugging](../debugger/historical-debugging.md).  

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
        4. Drücken Sie zum Starten des Debugvorgangs **F5**. Jetzt sind Momentaufnahmen Debuggersprung und Haltepunkte generiert.

        > [!Note]
        > Die `Largeaddressaware` Flag muss festgelegt werden jedes Mal, die die ausführbare Datei mit Änderungen neu erstellt wird.

* Wenn eine Momentaufnahme des Prozesses für die Anwendung auf eine Anwendung, der eine permanente Speicher abgebildete Datei verwendet erstellt wird, enthält der Prozess mit der Momentaufnahme eine exklusive Sperre für die Speicherabbilddatei (selbst wenn der übergeordnete Prozess die Sperre aufgehoben hat). Andere Prozesse werden weiterhin kann gelesen, aber nicht in den im Speicher abgebildeten Datei geschrieben.

    Problemumgehung:
    * Deaktivieren Sie alle Momentaufnahmen, indem Sie die Debugsitzung beenden. 

* Beim Speichern einer Datei mit **Debuggen > IntelliTrace > Speichern der IntelliTrace-Sitzung** im Modus für Ereignisse und Momentaufnahmen, die zusätzlichen Daten, die von Momentaufnahmen aufgezeichneten ist nicht verfügbar in der ITRACE-Datei. Auf den Haltepunkt und Schritt-Ereignisse wird die gleichen Informationen angezeigt, als ob Sie die Datei befindet sich im Modus IntelliTrace-Ereignisse gespeichert wurde. 
