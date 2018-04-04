---
title: Analysieren der CPU-Auslastungsdaten (ASP.NET) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/05/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
ms.openlocfilehash: 16bdbcbc66673f872215a7b3812c4c6f7f1724b3
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="analyze-cpu-usage-data-in-visual-studio-aspnet"></a>Analysieren der CPU-Auslastungsdaten in Visual Studio (ASP.NET)

Visual Studio enthält viele leistungsstarke Features, mit denen Sie Leistungsprobleme in Ihrer Anwendung besser analysieren können. In diesem Thema werden einige der grundlegenden Funktionen erläutert. Außerdem betrachten wir ein Tool, mit dem Leistungsengpässe aufgrund hoher CPU-Auslastung erkannt werden können. Die Diagnosetools werden für die .NET-Entwicklung in Visual Studio, darunter ASP.NET, sowie für die native/C++-Entwicklung unterstützt.

Der Diagnosehub bietet Ihnen viele weitere Optionen zum Ausführen und Verwalten Ihrer Diagnosesitzung. Wenn das hier beschriebene **CPU-Auslastungs-Tool** nicht die benötigten Daten zurückgibt, gibt es andere [Tools zur Profilerstellung](../profiling/Profiling-Tools.md), mit denen sie andere hilfreiche Informationen erhalten. In vielen Fällen kann der Leistungsengpass Ihrer Anwendung durch etwas anderes als die CPU ausgelöst werden, z.B. durch den Speicher, das Rendern der Benutzeroberfläche oder die Anforderungszeit des Netzwerks.

> [!NOTE]
> Das CPU-Auslastungstool bietet derzeit keine exakten Ergebnisse mit portablen PBDs für .NET Core und ASP.NET Core. Verwenden Sie stattdessen vollständige PDBs.

## <a name="create-a-project"></a>Erstellen eines Projekts

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

1. Klicken Sie unter **Visual C#** auf **Web** und dann im mittleren Bereich auf **ASP.NET-Webanwendung (.NET Framework)**.

    > [!NOTE]
    > Das Tool „CPU-Auslastung“ wird derzeit in ASP.NET Core nicht unterstützt.

1. Geben Sie einen Namen wie **MyProfilingApp_MVC** ein, und klicken Sie auf **OK**.

1. Wählen Sie im angezeigten Dialogfeld im mittleren Bereich **MVC** aus, und klicken Sie dann auf **OK**.

    Visual Studio erstellt daraufhin das Projekt. Der Projektmappen-Explorer (rechter Bereich) zeigt Ihre Projektdateien an.

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Ordner „Models“ (Modelle) und anschließend auf **Hinzufügen** > **Klasse**.

1. Nennen Sie die neue Klasse `Data.cs`, und klicken Sie auf **Hinzufügen**.

1. Öffnen Sie im Projektmappen-Explorer `Models/Data.cs`, und fügen Sie am Anfang der Datei die folgende `using`-Anweisung hinzu:

    ```cs
    using System.Threading;
    ```

1. Ersetzen Sie in „Data.cs“ den folgenden Code:

    ```cs
    public class Data
    {
    }
    ```

    durch den folgenden:

    ```cs
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. Öffnen Sie im Projektmappen-Explorer „Controller/HomeControllers.cs“, und ersetzen Sie den folgenden Code:

    ```cs
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    durch den folgenden:

    ```cs
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Schritt 1: Sammeln von Profilerstellungsdaten 
  
1.  Legen Sie in Ihrer App zuerst einen Haltepunkt auf diese Codezeile im `Simple`-Konstruktor fest:

    `for (int i = 0; i < 200; i++)`

    Legen Sie einen Haltepunkt fest, indem Sie in den Bundsteg links neben der Codezeile klicken.

1.  Legen Sie als Nächstes einen weiteren Haltepunkt auf die schließende Klammer am Ende des `Simple`-Konstruktors fest:

     ![Haltepunkte für die Profilerstellung festlegen](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    > [!TIP]
    > Durch das Festlegen von zwei Haltepunkten können Sie die Datensammlung auf die Teile des Code begrenzen, die Sie analysieren möchten.
  
1.  Das Fenster **Diagnosetools** wird bereits angezeigt, es sei denn, Sie haben es deaktiviert. Klicken Sie auf **Debuggen / Windows / Diagnosetools anzeigen**, um das Fenster erneut aufzurufen.

1.  Klicken Sie auf **Debuggen / Debugging starten** (oder auf **Start** auf der Symbolleiste oder auf **F5**).

1.  Wenn die Anwendung geladen wurde, klicken Sie auf den Link **About** (Info) oben auf der Webseite, um den neuen Code auszuführen.

1.  Sehen Sie sich die Ansicht **Zusammenfassung** der Diagnosetools an.

1.  Aktivieren Sie, während der Debugger angehalten ist, die Sammlung von CPU-Auslastungsdaten, indem Sie auf **CPU-Profilerstellung aufzeichnen** klicken. Öffnen Sie anschließend die Registerkarte **CPU-Auslastung**.

     ![Diagnosetools ermöglichen die CPU-Profilerstellung](../profiling/media/quickstart-cpu-usage-summary.png)

     Wenn die Datensammlung aktiviert ist, zeigt die Schaltfläche für das Aufzeichnen einen roten Kreis an.

     Wenn Sie auf **CPU-Profilerstellung aufzeichnen** klicken, zeichnet Visual Studio auf, welche Funktionen ausgeführt werden und wie lange dies dauert. Außerdem stellt das Programm ein Zeitachsendiagramm bereit, mit dem Sie bestimmte Segmente der Samplingsitzung genauer betrachten können. Diese gesammelten Daten können jedoch nur angezeigt werden, wenn die Anwendung an einem Haltepunkt angehalten wird.

6.  Drücken Sie F5, um die App bis zum zweiten Haltepunkt auszuführen.

     Jetzt verfügen Sie über Leistungsdaten für Ihre Anwendung, die speziell für den Codebereich gelten, der zwischen den beiden Haltepunkten liegt.

     Der Profiler beginnt, Threaddaten vorzubereiten. Warten Sie, bis dieser Vorgang abgeschlossen ist.
  
     Das CPU-Auslastungstool zeigt den Bericht unter der Registerkarte **CPU-Auslastung** an.

     An diesem Punkt können Sie beginnen, die Daten zu analysieren.

## <a name="Step2"></a> Schritt 2: Analysieren der CPU-Auslastungsdaten

Beginnen Sie bei der Datenanalyse am besten mit der Liste der Funktionen unter „CPU-Auslastung“, stellen Sie fest welche Funktionen die meisten Aufgaben ausführen, und betrachten Sie die einzelnen Funktionen näher.

1. Untersuchen Sie in der Liste der Funktionen die Funktionen, die am meisten Aufgaben ausführen.

     ![Registerkarte „CPU-Auslastung“ der Diagnosetools](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Die Auflistung der Funktionen beginnt mit der Funktion, die die meisten Aufgaben ausführt (sie sind nicht in der Reihenfolge der Aufrufe gelistet). Dadurch können Sie schnell feststellen, welche Funktionen am längsten ausgeführt werden.

2. Doppelklicken Sie in der Funktionsliste auf die `MyProfilingApp_MVC.Models.ServerClass::GetNumber`-Funktion.

    Dabei wird die Ansicht **Aufrufer/Aufgerufener** im linken Bereich geöffnet. 

    ![Ansicht „Aufrufer/Aufgerufener“ der Diagnosetools](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    In dieser Ansicht wird die ausgewählte Funktion in der Überschrift und im Feld **Aktuelle Funktion** angezeigt (in diesem Beispiel `ServerClass::GetNumber`). Die Funktion, die die aktuelle Funktion aufgerufen hat, wird links unter **Calling Function** (Aufrufende Funktion) angezeigt, und alle Funktionen, die von der aktuellen Funktion aufgerufen wurden werden im Feld **Called Functions** (Aufgerufene Funktionen) auf der rechten Seite angezeigt. (Sie können beide Felder auswählen, um die aktuelle Funktion zu ändern.)

    In dieser Ansicht wird Ihnen die Gesamtzeit (ms) und der Prozentsatz der gesamten Ausführungszeit der App angezeigt, den die Funktion bis zum Abschluss eingenommen hat.

    Unter **Funktionsrumpf** wird ebenso die Gesamtzeit (und der Prozentsatz der Zeit) angezeigt, die im Funktionsrumpf aufgewendet wurde. Die Zeit, die in aufrufenden und aufgerufenen Funktionen aufgewendet wurde, ist nicht enthalten. (In dieser Abbildung wurden 2220 von 2235 ms im Funktionsrumpf aufgewendet, und die verbleibende Zeit (<20 ms) wurde im von dieser Funktion aufgerufenen externen Code aufgewendet). Die aktuellen Werte unterscheiden sich je nach Umgebung.

    > [!TIP]
    > Hohe Werte unter **Funktionsrumpf** deuten auf einen Leistungsengpass in der Funktion selbst hin.

## <a name="next-steps"></a>Nächste Schritte

- [Analysieren der Speicherauslastung](../profiling/memory-usage.md), um Leistungsengpässe zu erkennen
- [Analysieren der CPU-Auslastung](../profiling/cpu-usage.md) für weitere Informationen zum CPU-Auslastungs-Tool
- Analysieren der CPU-Auslastung, auch ohne Debugger oder dass eine ausgeführte App als Ziel gesetzt wird: Weitere Informationen finden Sie unter [Sammeln von Profilerstellungsdaten ohne das Debuggen](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) in [Ausführen von Profilerstellungstools mit oder ohne den Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Siehe auch  

 [Profilerstellung in Visual Studio](../profiling/index.md)  
 [Tour zur Profilerstellungsfunktion](../profiling/profiling-feature-tour.md)
