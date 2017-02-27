---
title: "VSPerfCLREnv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehlszeilentools, VSPerfCLREnv"
  - "Befehlszeile, Tools"
  - "Leistungstools, VSPerfCLREnv"
  - "Profilerstellungstools, VSPerfCLREnv"
  - "VSPerfCLREnv-Tool"
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# VSPerfCLREnv
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das VSPerfCLREnv\-Tool wird verwendet, um Umgebungsvariablen festzulegen, die erforderlich sind, um eine .NET Framework\-Anwendung ein Profil zu erstellen.  Es verwendet die folgende Syntax:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 Die Auswahl der Option hängt davon ab, welchen der drei Profilerstellungstypen Sie verwenden: Sampling, Instrumentation oder Global.  Eine separate Option ist erforderlich, um Ebeneninteraktionsdaten in die Profilerstellungsdaten einzuschließen.  Die Syntax für die einzelnen Optionen wird in den folgenden Tabellen beschrieben.  
  
> [!NOTE]
>  Wenn Sie die Profilerstellung abgeschlossen haben, führen Sie **VSPerfCLREnv** mit der **\/off**\-Option oder der **\/globaloff**\-Option aus, um die für die Profilerstellung erforderlichen Umgebungsvariablen zu löschen.  Weitere Informationen finden Sie unter "VSPerfCLREnv\-Optionen zum Löschen von Umgebungseinstellungen".  
  
 **VSPerfCLREnv\-Optionen zum Einschließen von Daten zur Ebeneninteraktion**  
  
> [!WARNING]
>  Profilerstellungsdaten für die Ebeneninteraktion können mit [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] oder [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)] erfasst werden.  Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] und [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] angezeigt werden.  
  
 Ebeneninteraktionsprofilerstellung stellt weitere Informationen zu ADO.NET\-Abfragen in Anwendungen mit mehreren Ebenen bereit.  Es werden nur Daten für synchrone Funktionsaufrufe gesammelt.  Jeder Profilerstellungsausführung können mit einer beliebigen Profilerstellungsmethode Interaktionsdaten hinzugefügt werden.  
  
 Die **InteractionOn**\-Option und die **GlobalInteractionOn**\-Option ermöglichen das Sammeln von Ebeneninteraktionsdaten.  Die Interaktionsoption muss nach der Umgebungsvariable VSPerfCLREnv festgelegt werden, die zum Erstellen eines Profils für eine Anwendung erforderlich ist.  
  
 Im folgenden Beispiel werden Daten zur Ebeneninteraktion in eine Profilerstellungsausführung aufgenommen, die die Samplingmethode verwendet:  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 Im folgenden Beispiel werden Daten zur Ebeneninteraktion in eine Profilerstellungsausführung für einen Windows\-Dienst aufgenommen:  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **VSPerfCLREnv\-Optionen für die instrumentierte Profilerstellung**  
  
 In der folgenden Tabelle werden VSPerfCLREnv\-Optionen für die instrumentierte Profilerstellung beschrieben:  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|**TraceOn**|Aktiviert die Profilerstellung mit der Instrumentationsmethode  Aktiviert die Speicherbelegungsprofilerstellung oder das Auflisten von Objektlebensdauerdaten nicht.|  
|**TraceGC**|Aktiviert die Speicherbelegungsprofilerstellung mit der Instrumentationsmethode.  Aktiviert das Auflisten von Objektlebensdauerdaten nicht.|  
|**TraceGCLife**|Aktiviert die Speicherbelegungsprofilerstellung und das Sammeln von Daten zur Objektlebensdauer mithilfe der Instrumentationsmethode.|  
  
 **VSPerfCLREnv\-Optionen für die Sampling\-Profilerstellung**  
  
 In der folgenden Tabelle werden VSPerfCLREnv\-Optionen für die Sampling\-Profilerstellung beschrieben:  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|**SampleOn**|Aktiviert die Profilerstellung mit der Samplingmethode.  Aktiviert die Speicherbelegungsprofilerstellung oder das Auflisten von Objektlebensdauerdaten nicht.|  
|**SampleGC**|Aktiviert die Speicherbelegungsprofilerstellung mit der Samplingmethode.  Aktiviert das Auflisten von Objektlebensdauerdaten nicht.|  
|**SampleGCLife**|Aktiviert die Speicherbelegungsprofilerstellung mit der Samplingmethode.  Aktiviert auch das Auflisten von Objektlebensdauerdaten.|  
|**SampleLineOff**|Deaktiviert der Auflistung von .NET\-Profilerstellungsdaten auf Zeilenebene.|  
  
 **VSPerfCLREnv\-Optionen für die globale Profilerstellung**  
  
 Um ein Profil für einen verwalteten Dienst, wie z. B. eine ASP.NET\-Webanwendung, zu erstellen, der vom Betriebssystem und nicht vom Benutzer gestartet wird, verwenden Sie die VSPerfCLREnv\-Optionen für die globale Profilerstellung.  In der folgenden Tabelle werden die globalen Varianten der VSPerfCLREnv\-Optionen beschrieben.  Durch diese Optionen werden die entsprechenden Umgebungsvariablen in der Registrierung festgelegt.  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|**GlobalTraceOn**|Aktiviert die globale Profilerstellung mit der Instrumentationsmethode  Erfasst keine Speicherbelegungsereignisse oder Objektlebensdauerdaten.|  
|**GlobalTraceGC**|Aktiviert die globale Speicherbelegungsprofilerstellung mit der Instrumentationsmethode.  Aktiviert das Auflisten von Objektlebensdauerdaten nicht.|  
|**GlobalTraceGCLife**|Aktiviert die globale Speicherbelegungsprofilerstellung mit der Instrumentationsmethode.  Aktiviert auch die Auflistung von Objektlebensdauerdaten.|  
|**GlobalSampleOn**|Aktiviert die globale Profilerstellung mit der Samplingmethode.  Aktiviert nicht die Erfassung von Speicherbelegungsereignissen oder Objektlebensdauerdaten.|  
|**GlobalSampleGC**|Aktiviert die globale Speicherbelegungsprofilerstellung mit der Samplingmethode.  Aktiviert das Auflisten von Objektlebensdauerdaten nicht.|  
|**GlobalSampleGCLife**|Aktiviert die globale Speicherbelegungsprofilerstellung mit der Samplingmethode.  Aktiviert auch das Auflisten von Objektlebensdauerdaten.|  
  
 **VSPerfCLREnv\-Optionen zum Löschen von Umgebungseinstellungen**  
  
 Nachdem Sie das Profil der verwalteten Anwendung erstellt haben, verwenden Sie eine der folgenden Optionen, um die Umgebungsvariablen zu löschen, die von VSPerfCLREnv hinzugefügt wurden.  In der folgenden Tabelle wird beschrieben, wie sowohl standardmäßige als auch globale Umgebungsvariablen gelöscht werden:  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|**Off**|Löscht die Umgebungsvariablen für die standardmäßige .NET\-Profilerstellung.  Verwenden Sie diese Option, wenn die nicht globalen VSPerfClrEnv\-Optionen verwendet wurden, um die Profilerumgebungsvariablen festzulegen.|  
|**GlobalOff**|Löscht Umgebungsvariablen für die globale .NET\-Profilerstellung.  Verwenden Sie diese Option, wenn die Anwendung vom Betriebssystem und nicht vom Profiler gestartet wurde.|  
  
## Hinweise  
 Diese Optionen sind nicht erforderlich, um ein Profil einer verwalteten Anwendung zu erstellen, wenn die Anwendung über den Leistungs\-Explorer in der IDE gestartet wurde.  Der Leistungs\-Explorer legt alle erforderlichen Umgebungseinstellungen für Sie fest.  
  
 Wenn während der Profilerstellung nicht die richtige Umgebung festgelegt wurde, wird bei der Analyse eine Warnung ausgegeben, und die Namen der verwalteten Funktionen können nicht korrekt aufgelöst werden.  
  
## Siehe auch  
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)