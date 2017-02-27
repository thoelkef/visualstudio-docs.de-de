---
title: "Schnelle Website-Profilerstellung mit VSPerfASPNETCmd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, VSPerfASPNETCmd"
  - "VSPerfASPNETCmd"
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Schnelle Website-Profilerstellung mit VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe des Befehlszeilentools **VSPerfASPNETCmd** lassen sich auf einfache Weise Profile für [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendungen erstellen.  Verglichen mit dem Befehlszeilentool [VSPerfCmd](../profiling/vsperfcmd.md) stehen weniger Optionen zur Verfügung, es müssen keine Umgebungsvariablen festgelegt werden, und der Computer muss nicht neu gestartet werden.  Die Verwendung von **VSPerfASPNETCmd** ist die bevorzugte Methode für die Profilerstellung mit dem eigenständigen Profiler.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren des eigenständigen Profilers](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 In einigen Szenarien, beispielsweise beim Sammeln von Parallelitätsdaten oder beim Anhalten und anschließenden Fortsetzen der Profilerstellung ist die Verwendung von **VSPerfCmd** bevorzugte Profilerstellungsmethode.  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Verwenden Sie auf 64\-Bit\-Computern das Tool "VSPerfASPNETCmd", das sich im 32\-Bit\-Verzeichnis "\\Team Tools\\Performance Tools" befindet.  Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Profilerstellung für eine ASP.NET\-Anwendung  
 Geben Sie zur Profilerstellung für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung einen der Befehle ein, die in den folgenden Abschnitten beschrieben werden.  Die Website wird gestartet, und der Profiler beginnt mit dem Sammeln von Daten.  Verwenden Sie die Anwendung, und schließen Sie anschließend den Browser.  Drücken Sie zum Beenden der Profilerstellung im Eingabeaufforderungsfenster die EINGABETASTE.  
  
> [!NOTE]
>  Standardmäßig wird die Eingabeaufforderung nach einem **vsperfaspnetcmd**\-Befehl nicht erneut angezeigt.  Mit der Option **\/nowait** können Sie das erneute Anzeigen der Eingabeaufforderung erzwingen.  Siehe [Verwenden der Option "/NoWait"](#UsingNoWait).  
  
## So sammeln Sie Anwendungsstatistikdaten mithilfe der Samplingmethode  
 Sampling ist die Standardprofilerstellungsmethode des Tools **VSPerfASPNETCmd** und muss nicht in der Befehlszeile angegeben werden.  Mit der folgenden Befehlszeile werden Anwendungsstatistikdaten aus der angegebenen Webanwendung gesammelt:  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## So sammeln Sie ausführliche Zeitsteuerungsdaten mithilfe der Instrumentationsmethode  
 Verwenden Sie die folgende Befehlszeile, um ausführliche Zeitsteuerungsdaten aus einer dynamisch kompilierten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung zu sammeln:  
  
 **vsperfaspnetcmd \/trace**  *websiteUrl*  
  
 Wenn Sie ein Profil für statisch kompilierte DLL\-Dateien in der Webanwendung erstellen möchten, müssen die Dateien mit dem Befehlszeilentool [VSInstr](../profiling/vsinstr.md) instrumentiert werden.  Durch den Befehl "vsperfaspnetcmd \/trace" werden Daten aus den instrumentierten Dateien einbezogen.  
  
## So sammeln Sie .NET\-Speicherdaten  
 Mit der Option **\/Memory** werden Daten zur Speicherbelegung von Objekten im .NET\-Speicher gesammelt. Darüber hinaus können Daten zur Lebensdauer dieser Objekte gesammelt werden.  Das Sammeln von Speicherbelegungsdaten ist der Standardmodus der Datenoption **\/Memory** und muss nicht in der Befehlszeile angegeben werden.  
  
 **vsperfaspnetcmd \/memory** *websiteUrl*  
  
 Verwenden Sie den Parameter **Lifetime**, um neben den Speicherbelegungsdaten auch Daten zur Objektlebensdauer zu sammeln:  
  
 **vsperfaspnetcmd \/memory:lifetime** *websiteUrl*  
  
 Sie können auch die Option **\/Trace** verwenden, um ausführliche Zeitsteuerungsinformationen in die .NET\-Speicherdaten einzuschließen:  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/trace** `websiteUrl`  
  
## So sammeln Sie Ebeneninteraktionsdaten  
  
> [!WARNING]
>  Die Ebeneninteraktionsdaten \(TIP\)\-, die Daten ein Profil erstellt, können mit [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] oder [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)] erfasst werden.  Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] und [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] angezeigt werden.  
>   
>  Um TIPPdaten auf Windows 8 oder Windows Server 2012 zu erfassen, müssen Sie die Option der Instrumentation \(**\/trace**\) verwenden.  
  
 So sammeln Sie Ebeneninteraktionsdaten mit Samplingdaten:  
  
 **vsperfaspnetcmd \/tip** `websiteUrl`  
  
 So sammeln Sie Ebeneninteraktionsdaten mit Instrumentationsdaten:  
  
 **vsperfaspnetcmd \/trace \/tip** *websiteUrl*  
  
 So sammeln Sie Ebeneninteraktionsdaten mit .NET\-Speicherdaten:  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/tip** *websiteUrl*  
  
##  <a name="UsingNoWait"></a> Verwenden der Option "\/NoWait"  
 Standardmäßig wird die Eingabeaufforderung nach einem **vsperfaspnetcmd**\-Befehl nicht erneut angezeigt.  Mit der folgenden Syntaxoption können Sie jedoch das erneute Anzeigen der Eingabeaufforderung erzwingen.  Anschließend können Sie weitere Vorgänge im Eingabeaufforderungsfenster ausführen.  Verwenden Sie zum Beenden der Profilerstellung in einem separaten Befehl vom Typ **vsperfaspnetcmd** die Option **\/shutdown**.  
  
 So starten Sie die Profilerstellung:  
  
 **vsperfaspnetcmd** \[*\/Options*\] **\/nowait** *websiteUrl*  
  
 So beenden Sie die Profilerstellung:  
  
 **vsperfaspnetcmd \/shutdown** *websiteUrl*  
  
## Zusätzliche Optionen  
 Mit Ausnahme des Befehls **vsperfaspnetcmd \/shutdown** können alle weiter oben in diesem Abschnitt aufgeführten Befehle mit jeder der folgenden Optionen ergänzt werden:  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|**\/Output:** `VspFile`|Standardmäßig wird die Profilerstellungs\-Datendatei \(VSP\-Datei\) im aktuellen Verzeichnis mit dem Dateinamen **PerformanceReport.vsp** erstellt.  Mithilfe der Option "\/output" können Sie einen anderen Speicherort und\/oder einen anderen Dateinamen angeben.|  
|**\/PackSymbols:Off**|Standardmäßig werden von "VsPerfASPNETCmd" Symbole \(Funktions\- und Parameternamen usw.\) in der VSP\-Datei eingebettet.  Durch die Einbettung der Symbole kann die Profilerstellungs\-Datendatei sehr groß ausfallen.  Wenn Sie beim Analysieren der Daten auf die PDB\-Dateien mit den Symbolen zugreifen können, verwenden Sie die Option "\/packsymbols:off", um die Einbettung der Symbole zu deaktivieren.|