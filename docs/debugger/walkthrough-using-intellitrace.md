---
title: Anzeigen von Ereignissen mit IntelliTrace | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ffbe0b8365948dc5a69edca390f308cb55ba5a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929396"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Anzeigen von Ereignissen mit IntelliTrace in Visual Studio Enterprise (C#, Visual Basic)

Sie können IntelliTrace zum Sammeln von Informationen über bestimmte Ereignisse oder Ereigniskategorien oder zum Erfassen von einzelnen Funktionsaufrufen zusätzlich zu den Ereignissen verwenden. In der folgenden Vorgehensweisen wird gezeigt, wie dies umzusetzen ist.

Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden, jedoch nicht in der Professional oder Community Edition.

## <a name="GettingStarted"></a> Konfigurieren von IntelliTrace

Sie können ein Debugging nur mit IntelliTrace-Ereignissen durchführen. IntelliTrace-Ereignisse sind Debuggerereignisse, Ausnahmen, .NET Framework-Ereignisse und andere Systemereignisse. Bevor Sie mit dem Debuggen beginnen, sollten Sie bestimmte Ereignisse aktivieren oder deaktivieren, um die von IntelliTrace aufgezeichneten Ereignisse zu steuern. Weitere Informationen finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md).

- Aktivieren Sie das IntelliTrace-Ereignis für den Dateizugriff. Wechseln Sie zur Seite **Extras > Optionen > IntelliTrace > IntelliTrace-Ereignisse**, und erweitern Sie die Kategorie **Datei**. Aktivieren Sie die Ereigniskategorie **Datei** . Dadurch werden alle Dateiereignisse (Zugriff, Schließen, Löschen) überprüft.

## <a name="create-your-app"></a>Erstellen der App

1. Erstellen Sie eine C#- Konsolenanwendung. Fügen Sie in der Datei "Program.cs" die folgende `using` -Anweisung hinzu:

    ```csharp
    using System.IO;
    ```

2. Erstellen Sie ein <xref:System.IO.FileStream> -Element in der Main-Methode, lesen Sie es aus, schließen Sie es, und löschen Sie die Datei. Fügen Sie eine weitere Zeile hinzu, um einen Haltepunkt festlegen zu können:

    ```csharp
    static void Main(string[] args)
    {
        FileStream fs = File.Create("WordSearchInputs.txt");
        fs.ReadByte();
        fs.Close();
        File.Delete("WordSearchInputs.txt");

        Console.WriteLine("done");
    }
    ```

3. Legen Sie einen Haltepunkt auf `Console.WriteLine("done");`fest.

## <a name="start-debugging-and-view-intellitrace-events"></a>Starten Sie das Debuggen und Anzeigen von IntelliTrace-Ereignisse

1. Starten Sie das Debuggen wie gewohnt. (Drücken Sie **F5**, oder klicken Sie auf **Debuggen > Debuggen starten**.)

    > [!TIP]
    > Halten Sie während des Debuggens die Fenster **Lokal** und **Auto** geöffnet, um die Werte darin anzuzeigen und aufzuzeichnen.

2. Die Ausführung hält am Haltepunkt an. Wenn das Fenster **Diagnosetools** nicht angezeigt wird, klicken Sie auf **Debuggen > Fenster > IntelliTrace-Ereignisse**.

    Wechseln Sie im Fenster **Diagnosetools** zur Registerkarte **Ereignisse** (es sollten drei Registerkarten vorhanden sein: **Ereignisse**, **Speicherauslastung**und **CPU-Auslastung**). Die Registerkarte **Ereignisse** zeigt eine chronologische Liste aller Ereignisse, die mit dem letzten Ereignis endet, bevor die Ausführung vom Debugger unterbrochen wurde. Es sollte ein Ereignis namens **Access WordSearchInputs.txt**angezeigt werden.

    Der folgende Screenshot stammt aus Visual Studio 2015 Update 1.

    ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")

3. Wählen Sie das Ereignis aus, um die Details zu erweitern.

    Der folgende Screenshot stammt aus Visual Studio 2015 Update 1.

    ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")

    Sie können den Link des Pfadnamens auswählen, um die Datei zu öffnen. Wenn der vollständige Pfadname nicht verfügbar ist, wird das Dialogfeld **Datei öffnen** angezeigt.

    Klicken Sie auf **Verlaufsbezogenes Debugging aktivieren**, um den Kontext des Debuggers auf den Zeitpunkt festzulegen, zu dem das ausgewählte Ereignis gesammelt wurde. So werden Verlaufsdaten in den Fenstern **Aufrufliste**, **Lokal** sowie in den anderen zugehörigen Debuggerfenstern angezeigt. Wenn Quellcode verfügbar ist, bewegt Visual Studio den Zeiger auf den entsprechenden Code im Quellcodefenster, damit Sie ihn überprüfen können.

    Der folgende Screenshot stammt aus Visual Studio 2015 Update 1.

    ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")

4. Wenn Sie den Fehler nicht finden, überprüfen Sie andere Ereignisse, die zu dem Fehler geführt haben. Sie können auch veranlassen, dass IntelliTrace Aufrufinformationen aufzeichnet, damit Sie die Funktionsaufrufe schrittweise durchlaufen können.

## <a name="next-steps"></a>Nächste Schritte

Sie können einige der erweiterten Funktionen von IntelliTrace mit verlaufsbezogenem debugging verwenden:

- Zum Anzeigen von Momentaufnahmen finden Sie unter [überprüfen Sie die vorherigen app-Status, die mit IntelliTrace](../debugger/view-historical-application-state.md)
- So untersuchen Sie Variablen, und Navigieren im Code finden Sie unter [untersuchen Ihrer app mit verlaufsbezogenem debugging](../debugger/historical-debugging-inspect-app.md)
