---
title: "Exemplarische Vorgehensweise: Profilerstellung &#252;ber die Befehlszeile mit Instrumentation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, exemplarische Vorgehensweisen"
  - "Leistungstools, exemplarische Vorgehensweisen"
  - "Leistungstools, Befehlszeilentools"
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Exemplarische Vorgehensweise: Profilerstellung &#252;ber die Befehlszeile mit Instrumentation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird das Erstellen eines Profils für eine eigenständige [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Anwendung beschrieben, um mithilfe der Instrumentationsmethode der Profilerstellungstools ausführliche Daten zur Zeitsteuerung sowie zur Aufrufanzahl zu sammeln.  Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Aufgaben aus:  
  
-   Erstellen instrumentierter Binärdateien mithilfe des Befehlszeilentools [VSInstr](../profiling/vsinstr.md)  
  
-   Festlegen der Umgebungsvariablen zum Sammeln von .NET\-Profilerstellungsdaten mithilfe des Tools [VSPerfCLREnv](../profiling/vsperfclrenv.md)  
  
-   Sammeln von Profilerstellungsdaten mithilfe des Tools [VSPerfCmd](../profiling/vsperfcmd.md)  
  
-   Generieren dateibasierter Berichte der Profilerstellungsdaten mithilfe des Tools [VSPerfReport](../profiling/vsperfreport.md)  
  
## Vorbereitungsmaßnahmen  
  
-   [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]  
  
-   Grundlegende Kenntnisse über C\#  
  
-   Grundlegende Kenntnisse über die Arbeit mit Befehlszeilentools  
  
-   Eine Kopie von [PeopleTrax\-Beispiel](../profiling/peopletrax-sample-profiling-tools.md)  
  
-   Um mit den durch die Profilerstellung bereitgestellten Informationen arbeiten zu können, sollten Symbolinformationen für das Debuggen verfügbar sein.  Weitere Informationen finden Sie unter [Gewusst wie: Verweisen auf Windows\-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md).  
  
## Profilerstellung über die Befehlszeile mit der Instrumentationsmethode  
 Die Instrumentation ist eine Methode der Profilerstellung, bei der speziell erstellte Versionen der Binärdateien, für die eine Profilerstellung durchgeführt wurde, Testfunktionen enthalten, die beim Aufrufen und beim Verlassen von Funktionen in einem instrumentierten Modul Zeitinformationen erfassen.  Da diese Methode der Profilerstellung stärker als das Sampling eingreift, verursacht sie einen größeren Verwaltungsaufwand.  Instrumentierte Binärdateien sind zudem größer als Binärdateien für eine Debug\- oder Releaseversion und nicht für die Bereitstellung vorgesehen.  
  
> [!NOTE]
>  Senden Sie keine instrumentierten Binärdateien an die Kunden.  Instrumentierte Binärdateien können verschiedene Risiken bergen.  Die Binärdateien enthalten Informationen, mit denen die Anwendung leichter zurückentwickelt werden kann, sowie Sicherheitsrisiken.  
  
#### So erstellen Sie mithilfe der Instrumentationsmethode ein Profil für die Anwendung "PeopleTrax"  
  
1.  Installieren Sie die Beispielanwendung "PeopleTrax", und erstellen Sie die Releaseversion.  
  
2.  Öffnen Sie ein Eingabeaufforderungsfenster, und fügen Sie der lokalen Path\-Umgebungsvariablen das Verzeichnis **Profilerstellungstools** hinzu.  
  
3.  Legen Sie das Arbeitsverzeichnis auf das Verzeichnis fest, das die Binärdateien für "PeopleTrax" enthält.  
  
4.  Erstellen Sie ein Verzeichnis für die dateibasierten Berichte.  Geben Sie folgenden Befehl ein:  
  
    ```  
    md Reports  
    ```  
  
5.  Verwenden Sie das Befehlszeilentool "VSInstr", um die Binärdateien in der Anwendung zu instrumentieren.  Geben Sie die folgenden Befehle in separate Befehlszeilen ein:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Hinweis** VSInstr speichert standardmäßig eine nicht instrumentierte Sicherungskopie der ursprünglichen Datei.  Der Name der Sicherungsdatei hat die Erweiterung .orig.  Die ursprüngliche Version von "MyApp.exe" wird beispielsweise als "MyApp.exe.orig" gespeichert.  
  
6.  Geben Sie den folgenden Befehl ein, um die entsprechenden Umgebungsvariablen festzulegen:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  Starten Sie den Profiler, indem Sie den folgenden Befehl eingeben:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  Führen Sie zum Erfassen von Daten die instrumentierte Version von "PeopleTrax.exe" aus, nachdem Sie den Profiler im Ablaufverfolgungsmodus gestartet haben.  
  
     Das Anwendungsfenster für **PeopleTrax** wird angezeigt.  
  
9. Klicken Sie auf **Personen abrufen**.  
  
     Im Datenblatt PeopleTrax werden Daten angezeigt.  
  
10. Klicken Sie auf **Daten exportieren**.  
  
     In Editor wird eine neue Datei angezeigt, die eine Liste der Personen aus der Anwendung **PeopleTrax** enthält.  
  
11. Schließen Sie Editor, und schließen Sie dann die Anwendung **PeopleTrax**.  
  
12. Schließen Sie den Profiler.  Geben Sie folgenden Befehl ein:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Geben Sie den folgenden Befehl ein, um die Umgebungsvariablen zurückzusetzen:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Generieren Sie mithilfe des Tools "VSPerfReport" Berichtsdateien mit durch Trennzeichen getrennten Werten \(CSV\-Datei\).  Geben Sie Folgendes ein:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Sie können die generierten Berichte in einem Tabellenkalkulationsprogramm oder die Profilerstellungsdaten mithilfe der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE in der Datei "Report.vsp" analysieren.  Weitere Informationen finden Sie unter [Analysieren der durch Profilerstellungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md).  
  
## Siehe auch  
 [Übersicht über Leistungssitzungen](../profiling/performance-session-overview.md)   
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)   
 [Berichtsansichten für Profilerstellungstools](../profiling/performance-report-views.md)