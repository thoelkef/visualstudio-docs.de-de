---
title: 'Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Instrumentierung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a37350cf274fbb551326ac96387330b0f3956e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841153"
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>Exemplarische Vorgehensweise: Profilerstellung über die Befehlszeile mit Instrumentierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise führt Sie durch die Profilerstellung einer eigenständigen [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Anwendung zum Sammeln ausführlicher Daten zur Zeitsteuerung und Aufrufanzahl mithilfe der Instrumentierungsmethode der Profilerstellungstools. Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Aufgaben aus:  
  
- Verwenden des Befehlszeilentools [VSInstr](../profiling/vsinstr.md) zum Erstellen instrumentierter Binärdateien  
  
- Verwenden des Tools [VSPerfCLREnv](../profiling/vsperfclrenv.md) zum Festlegen der Umgebungsvariablen zum Sammeln von .NET-Profilerstellungsdaten  
  
- Verwenden des Tools [VSPerfCmd](../profiling/vsperfcmd.md) zum Sammeln von Profilerstellungsdaten  
  
- Verwenden des Tools [VSPerfReport](../profiling/vsperfreport.md) zum Erstellen dateibasierter Berichte der Profilerstellungsdaten  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
- [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]  
  
- Fortgeschrittene C#-Kenntnisse  
  
- Grundlegende Kenntnisse der Arbeit mit Befehlszeilentools  
  
- Eine Kopie von [PeopleTrax-Beispiel](../profiling/peopletrax-sample-profiling-tools.md)  
  
- Um mit den durch die Profilerstellung bereitgestellten Informationen arbeiten zu können, sollten Symbolinformationen für das Debuggen verfügbar sein. Weitere Informationen finden Sie unter Gewusst [wie: verweisen auf Windows-Symbol Informationen](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Profilerstellung über die Befehlszeile mithilfe der Instrumentierungsmethode  
 Bei der Instrumentierung handelt es sich um eine Profilerstellungsmethode, bei der speziell erstellte Versionen der Binärdateien, für die das Profil erstellt wird, Testfunktionen erhalten, die Zeitsteuerungsdaten zum Funktionseinstieg und -ende in einem instrumentierten Modul sammeln. Da diese Profilerstellungsmethode invasiver als das Sampling ist, fällt der Mehraufwand höher aus. Instrumentierte Binärdateien sind zudem größer als Binärdateien für eine Debug- oder Releaseversion und nicht für die Bereitstellung vorgesehen.  
  
> [!NOTE]
> Senden Sie keine instrumentierten Binärdateien an Ihre Kunden. Instrumentierte Binärdateien können verschiedene Risiken bergen. Die Binärdateien enthalten Informationen, die das Reverse Engineering sowie Sicherheitsrisiken für Ihre Anwendung erleichtern.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>So führen Sie eine Profilerstellung einer PeopleTrax-Anwendung mithilfe der Instrumentierungsmethode durch  
  
1. Installieren Sie die Beispielanwendung „PeopleTrax“, und erstellen Sie die Releaseversion.  
  
2. Öffnen Sie ein Eingabeaufforderungsfenster, und fügen Sie der lokalen PATH-Umgebungsvariablen das Verzeichnis **Profilerstellungstools** hinzu.  
  
3. Legen Sie das Arbeitsverzeichnis auf das Verzeichnis fest, das die Binärdateien für „PeopleTrax“ enthält.  
  
4. Erstellen Sie ein Verzeichnis, das die dateibasierten Berichte enthält. Geben Sie folgenden Befehl ein:  
  
    ```  
    md Reports  
    ```  
  
5. Verwenden Sie die VSInstr-Befehlszeilentools zum Instrumentieren der Binärdateien in der Anwendung. Geben Sie folgende Befehle in getrennte Befehlszeilen ein:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Hinweis** VSInstr speichert standardmäßig eine nicht instrumentierte Sicherung der ursprünglichen Datei. Der Dateiname der Sicherung hat die Erweiterung „.orig“. Die ursprüngliche Version von „MyApp.exe“ würde beispielsweise als „MyApp.exe.orig“ gespeichert werden.  
  
6. Geben Sie den folgenden Befehl ein, um die entsprechenden Umgebungsvariablen festzulegen:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7. Starten Sie den Profiler, indem Sie den folgenden Befehl eingeben:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8. Nachdem der Profiler im Nachverfolgungsmodus gestartet wurde, führen Sie die instrumentierte Version des PeopleTrax.exe-Prozesses zum Sammeln von Daten aus.  
  
     Das Anwendungsfenster für **PeopleTrax** wird angezeigt.  
  
9. Klicken Sie auf **Get People** (Personen abrufen).  
  
     Im Datenblatt PeopleTrax werden Daten angezeigt.  
  
10. Klicken Sie auf **Daten exportieren**.  
  
     In Editor wird eine neue Datei angezeigt, die eine Liste von Personen aus **PeopleTrax** enthält.  
  
11. Schließen Sie Editor, und schließen Sie dann die Anwendung **PeopleTrax**.  
  
12. Schließen Sie den Profiler. Geben Sie folgenden Befehl ein:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Geben Sie den folgenden Befehl ein, um die Umgebungsvariablen zurückzusetzen:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Verwenden Sie das Tool VSPerfReport, um durch Trennzeichen getrennte (.csv) Berichtsdateien zu erstellen. Typ:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Sie können die erstellten Berichte in einem Tabellenkalkulationsprogramm analysieren, oder Sie können die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-IDE verwenden, um die Profilerstellungsdaten in der Datei „Report.vsp“ zu analysieren. Weitere Informationen finden Sie unter [Analysieren der durch Profilerstellungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über Leistungs Sitzungen](../profiling/performance-session-overview.md)   
 [Profilerstellung über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Grundlegendes zu Stichprobendaten Werten](../profiling/understanding-sampling-data-values.md)   
 [Leistungs Berichts Ansichten](../profiling/performance-report-views.md)
