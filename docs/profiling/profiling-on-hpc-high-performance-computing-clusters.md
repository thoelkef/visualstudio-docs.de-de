---
title: "Profilerstellung bei HPC-Clustern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.hpc.wizard.exeoptions"
  - "vs.performance.hpc.wizard.summary"
  - "vs.performance.hpc.wizard.startoptions"
  - "vs.performance.hpc.wizard.intro"
  - "vs.performance.hpc.property.basic"
  - "vs.performance.hpc.wizard.application"
  - "vs.performance.hpc.wizard.clusteroptions"
  - "vs.performance.hpc.property.advanced"
helpviewer_keywords: 
  - "Profilerstellungstools, HPC"
  - "HPC-Profilerstellung"
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Profilerstellung bei HPC-Clustern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Profilerstellung für Berechnungsknoten von Microsoft Windows\-HPC\-Clustern kann mithilfe der Samplingmethode der [!INCLUDE[vsPreExt](../profiling/includes/vspreext_md.md)]\- oder [!INCLUDE[vsUltExt](../profiling/includes/vsultext_md.md)]\-Profilerstellungstools vorgenommen werden.  Weitere Informationen zu HPC finden Sie auf [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393) der Microsoft\-Website.  
  
## Voraussetzungen  
 Zur Profilerstellung für einen HPC\-Berechnungsknoten müssen die folgenden Schritte ausgeführt werden:  
  
-   Installieren Sie Microsoft HPC Pack 2008 auf dem gleichen Computer, auf dem auch [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] installiert ist.  Der Computer muss nicht Teil des HPC\-Clusters sein.  Sie können das HPC Pack an installieren [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=177414).  
  
-   Installieren Sie [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] sowie die eigenständige Version der Profilerstellungstools auf dem HPC\-Berechnungsknoten.  Für [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] und den eigenständigen Profiler sind auf den Installationsmedien [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] verfügbar.  **Notiz** Sie müssen die Berechnung neu starten, nachdem Sie installiert haben [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] und vor der Installation der Profilerstellungstools.  
  
 Gehen Sie folgendermaßen vor, um [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] und die eigenständigen Profilerstellungstools auf einem aktiven HPC\-Berechnungsknoten zu installieren und die Profilerstellung auf dem Clustercomputer zu aktivieren:  
  
1.  Öffnen Sie das Eingabeaufforderungsfenster, das zusammen mit dem HPC Pack installiert wurde.  
  
2.  Geben Sie an getrennten Eingabeaufforderungen die folgenden Befehle ein:  
  
    1.  `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`  
  
|||  
|-|-|  
|*%HeadNode%*|Der Name des Hauptknotens für den Cluster.|  
|*%FxPath%*|Der Pfad zum Installationsprogramm von [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)].  Auf dem [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]\-Installationsmedium lautet der Pfad "WCU\\dotNetFramework\\dotNetFx40\_Full\_x86\_x64.exe".|  
|*%ProfilerPath%*|Der Pfad zur eigenständigen Version des Installationsprogramms für die Profilerstellungstools.  Auf dem [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]\-Installationsmedium lautet der Pfad "Standalone Profiler\\x64\\vs\_profiler.exe".|  
  
## Profilerstellung für einen HPC\-Berechnungsknoten  
 Geben Sie zum Konfigurieren einer Profilerstellungssitzung mithilfe des HPC\-Leistungs\-Assistenten den HPC\-Cluster und die Zielinformationen an.  Zusätzliche Optionen können auf den Eigenschaftenseiten der Leistungssitzung festgelegt werden.  Von den Profilerstellungstools werden automatisch die erforderlichen Zielbinärdateien bereitgestellt, und Profiler sowie HPC\-Anwendung werden automatisch gestartet.  
  
#### So führen Sie die Profilerstellung für einen HPC\-Berechnungsknoten aus  
  
1.  Klicken Sie im Menü **Analyse** auf **HPC\-Leistungs\-Assistent starten**.  Sollte der Befehl nicht verfügbar sein, vergewissern Sie sich, dass die weiter oben aufgeführten Voraussetzungen erfüllt sind.  
  
2.  Klicken Sie auf der ersten Seite des Assistenten auf **Weiter**.  
  
3.  Wählen Sie auf der zweiten Seite des Assistenten die Anwendung aus, für die Sie ein Profil erstellen möchten.  
  
    -   Wählen Sie zur Profilerstellung für ein Projekt, das gerade in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] geöffnet ist, die Option **Mindestens ein verfügbares Projekt** aus, und wählen Sie anschließend den Projektnamen in der Liste aus.  
  
    -   Wählen Sie zur Profilerstellung für eine Binärdatei, die sich nicht in einem geöffneten Projekt befindet, die Option **Eine ausführbare Datei \(EXE\-Datei\)** aus.  
  
4.  Klicken Sie auf **Weiter**.  
  
5.  Gehen Sie auf der dritten Seite des Assistenten folgendermaßen vor:  
  
    -   Wenn Sie ein Profil für eine ausführbare Datei erstellen, die sich nicht in einem geöffneten Projekt befindet, geben Sie unter **Wie lautet der vollständige Pfad der ausführbaren Datei?** den Pfad zur Binärdatei an.  
  
    -   Wenn Sie ein Profil für eine ausführbare Datei erstellen, die sich nicht in einem geöffneten Projekt befindet, können Sie unter **Befehlszeilenargumente** alle Befehlszeilenargumente angeben, die an den Prozess übergeben werden sollen.  
  
    -   Geben Sie unter **Remotearbeitsverzeichnis** den Pfad zu dem Ordner an, der von den Prozessinstanzen der einzelnen Berechnungsknoten verwendet wird.  
  
    -   Geben Sie unter **Bereitstellungsort** den Pfad zu dem Verzeichnis an, das vom HPC\-Server zum Bereitstellen von Abbildern für die Bereitstellung verwendet wird.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Gehen Sie auf der vierten Seite des Assistenten folgendermaßen vor:  
  
    -   Klicken Sie in der Liste **Hauptknoten** auf den Computer, der bei der Profilerstellung als HPC\-Hauptknoten fungiert.  Bei dem Hauptknoten kann es sich um "localhost" handeln. Dadurch kann die Profilerstellung auf dem lokalen Computer ausgeführt werden, ohne dass ein Cluster erforderlich ist.  
  
    -   Klicken Sie in der Liste **Anzahl von Prozessen** auf die Anzahl der auszuführenden Anwendungsinstanzen.  
  
    -   Wählen Sie in der Liste **Profilerstellungsoptionen** das Profilerstellungsziel aus.  
  
         Wenn Sie ein Profil für einen bestimmten Prozess in einem Cluster erstellen möchten, aktivieren Sie die Option **Profil für Rang**, und wählen Sie anschließend in der Dropdownliste den Rang des Prozesses aus.  
  
         Wenn Sie ein Profil für Prozesse erstellen möchten, die im HPC\-Cluster auf einem bestimmten Knoten ausgeführt werden, aktivieren Sie die Option **Profil für Knoten**, und wählen Sie anschließend in der Dropdownliste den gewünschten Knoten aus.  
  
8.  Klicken Sie auf **Weiter**.  
  
9. Auf der fünften Seite des Assistenten können Sie auswählen, ob der Profiler und die Profilerstellung umgehend gestartet werden sollen oder ob Sie die Profilerstellung später mithilfe des Leistungs\-Explorers starten möchten.  
  
    -   Aktivieren Sie das Kontrollkästchen **Profilerstellung nach Abschluss des Assistenten starten**, um die Profilerstellung sofort zu starten, oder deaktivieren Sie es, um die Profilerstellung manuell zu starten.  
  
10. Klicken Sie auf **Fertig stellen**.  
  
## Festlegen der HPC\-Profilerstellungseigenschaften mithilfe der Eigenschaftenseiten der Leistungssitzung  
 Die im HPC\-Profilerstellungs\-Assistent festgelegten Leistungssitzungseigenschaften können auf der Seite "HPC\-Starteigenschaften" der Eigenschaftenseite der Leistungssitzung geändert werden.  Zusätzliche Optionen werden auf der Seite "Erweiterte HPC\-Eigenschaften" festgelegt.  
  
#### So öffnen Sie die Eigenschaftenseiten der Leistungssitzung  
  
1.  Öffnen Sie ggf. die Leistungssitzungsdatei \(PSESS\-Datei\) im Leistungs\-Explorer.  Klicken Sie im Menü **Datei** auf **Öffnen**, und suchen Sie die Datei.  
  
2.  Klicken Sie im Leistungs\-Explorer mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Wenden Sie im Dialogfeld "Eigenschaftenseiten" eine der folgenden Methoden an:  
  
    -   Klicken Sie auf **Allgemein**, und aktivieren Sie anschließend das Kontrollkästchen **Sammeln für HPC\-Cluster**, um die HPC\-Profilerstellung zu aktivieren, oder deaktivieren Sie das Kontrollkästchen, um die HPC\-Profilerstellung zu deaktivieren.  
  
    -   Klicken Sie auf **HPC\-Starteigenschaften**, um die Eigenschaften zum Starten der HPC\-Anwendung zu ändern.  
  
    -   Klicken auf **Erweiterte HPC\-Eigenschaften**, um zusätzliche Optionen festzulegen.  
  
### HPC\-Starteigenschaften  
  
|Eigenschaft|**Beschreibung**|  
|-----------------|----------------------|  
|**Hauptknoten**|Gibt den Computer an, der bei der Profilerstellung als HPC\-Hauptknoten fungiert.|  
|**Anzahl von Prozessen**|Gibt an, wie viele Anwendungsinstanzen in der Anwendung ausgeführt werden sollen, für die die Profilerstellung vorgenommen wird.|  
|**Profil für Rang**|Wenn Sie ein Profil für einen bestimmten Prozess in einem Cluster erstellen möchten, aktivieren Sie die Option **Profil für Rang**, und wählen Sie anschließend in der Dropdownliste den Rang des Prozesses aus.|  
|**Profil für Knoten**|Wenn Sie ein Profil für Prozesse erstellen möchten, die im HPC\-Cluster auf einem bestimmten Knoten ausgeführt werden, aktivieren Sie die Option **Profil für Knoten**, und wählen Sie anschließend in der Dropdownliste den gewünschten Knoten aus.|  
|**Remotearbeitsverzeichnis**|Gibt den Pfad zu dem Ordner an, der von den Prozessinstanzen auf den einzelnen Berechnungsknoten verwendet wird.|  
|**Bereitstellungsort**|Gibt den Pfad zu dem Verzeichnis an, das vom HPC\-Server zum Bereitstellen von Abbildern für die Bereitstellung verwendet wird.|  
  
### Erweiterte Eigenschaften  
  
|Eigenschaft|**Beschreibung**|  
|-----------------|----------------------|  
|**Projektname**|Der Name des aktuellen [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Projekts oder der aktuellen Lösung.|  
|**Nach Beenden des Profilers bereinigen**|Bei "true" werden die im Ausführungsverzeichnis bereitgestellten Binärdateien entfernt.  Vom Benutzerprogramm erstellte Dateien und Verzeichnisse werden in diesem Schritt nicht entfernt.  Wenn Ausführungsverzeichnis und Bereitstellungsverzeichnis von der IDE erstellt wurden, wird versucht, sie zu entfernen. Sind allerdings Dateien vorhanden, die nicht von der IDE bereitgestellt wurden, wird dieser Vorgang nicht ausgeführt.|  
|**Zusätzliche bereitzustellende Dateien**|Gibt eine durch Semikolons getrennte Liste mit zusätzlichen Dateien an, die auf dem Berechnungsknoten bereitgestellt werden sollen.  Sie können auf die Schaltfläche mit den Auslassungspunkten \(**...**\) klicken, um mehrere Dateien in einem Dialogfeld auszuwählen.|  
|**Mpiexec\-Befehl**|Gibt die Anwendung an, von der die MPI\-Anwendung gestartet wird.  Standardwert: **mpiexec.exe**|  
|**Mpiexec\-Argumente**|Gibt die Argumente an, die an den mpiexec.exe\-Befehl übergeben werden sollen.|  
|**Angeforderte Knoten für den Cluster**|Gibt die Anzahl der Knoten für den Cluster an, auf denen die Anwendung ausgeführt werden soll.|  
|**CRT\-Dateien bereitstellen**|Bei "true" wird die C\/C\+\+\-Laufzeit für den Cluster bereitgestellt.|  
|**Pre\-Profilskript**|Gibt Pfad und Dateiname eines Skripts an, das auf dem lokalen Entwicklungscomputer ausgeführt werden soll, bevor die Profilerstellungssitzung startet.|  
|**Pre\-Pofilskriptargumente**|Gibt die Argumente an, die an das Pre\-Profilskript übergeben werden sollen.|  
|**Post\-Profilskript**|Gibt Pfad und Dateiname eines Skripts an, das auf dem lokalen Entwicklungscomputer ausgeführt werden soll, nachdem die Profilerstellungssitzung beendet wurde.|  
|**Post\-Profilskriptargumente**|Gibt die Argumente an, die an das Post\-Profilskript übergeben werden sollen.|