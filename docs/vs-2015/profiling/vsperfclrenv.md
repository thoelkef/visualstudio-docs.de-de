---
title: VSPerfCLREnv | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af5301baffc7ba55a48eb62562f1aa6eabf5b90e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178541"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das VSPerfCLREnv-Tool wird verwendet, um Umgebungsvariablen festzulegen, die für die Profilerstellung einer .NET Framework-Anwendung erforderlich sind. Es verwendet die folgende Syntax:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 Die Option, die Sie auswählen, hängt davon ab, welche der drei Typen der Profilerstellung Sie verwenden: Sampling, Instrumentierung oder die globale Profilerstellung. Eine separate Option ist erforderlich, um Ebeneninteraktionsdaten in die Profilerstellungsdaten einzuschließen. Die Syntax für jede Option wird in den folgenden Tabellen beschrieben.  
  
> [!NOTE]
>  Wenn Sie mit der Profilerstellung fertig sind, führen Sie **VSPerfCLREnv** mit der Option **/off** oder **/globaloff** aus, um die für die Profilerstellung erforderlichen Umgebungsvariablen zu löschen. Weitere Informationen finden Sie in den hier dargestellten VSPerfCLREnv-Optionen zum Löschen von Umgebungseinstellungen.  
  
 **VSPerfCLREnv-Optionen zum Einschließen von Ebeneninteraktionsdaten**  
  
> [!WARNING]
>  Profilerstellungsdaten für die Ebeneninteraktion können mit [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] oder [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] erfasst werden. Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] und [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] angezeigt werden.  
  
 Die Profilerstellung für die Ebeneninteraktion bietet zusätzliche Informationen zu ADO.NET-Abfragen in mehrstufigen Anwendungen. Es werden nur Daten für synchrone Funktionsaufrufe gesammelt. Interaktionsdaten können zu jeder Profilerstellung hinzugefügt werden, unabhängig von der Profilerstellungsmethode.  
  
 Die Optionen **InteractionOn** und **GlobalInteractionOn** aktivieren die Sammlung von Ebeneninteraktionsdaten. Die Interaktionsoption muss festgelegt werden, nachdem die Umgebungsvariable VSPerfCLREnv festgelegt wurde, die für die Profilerstellung einer Anwendung benötigt wird.  
  
 Das folgende Beispiel schließt Ebeneninteraktionsdaten in eine Profilerstellung ein, die die Samplingmethode verwendet:  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 Das folgende Beispiel schließt Ebeneninteraktionsdaten in eine Profilerstellung für einen Windows-Dienst ein:  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **VSPerfCLREnv-Optionen zum Verarbeiten der Instrumentierungsprofilerstellung**  
  
 Die folgende Tabelle beschreibt VSPerfCLREnv-Optionen für die Instrumentierungsprofilerstellung:  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**TraceOn**|Aktiviert die Profilerstellung mithilfe der Instrumentierungsmethode. Aktiviert nicht die Profilerstellung für die Speicherreservierung oder die Sammlung von Objektlebensdauerdaten.|  
|**TraceGC**|Aktiviert die Profilerstellung für die Speicherreservierung mithilfe der Instrumentierungsmethode. Aktiviert nicht die Sammlung von Objektlebensdauerdaten.|  
|**TraceGCLife**|Aktiviert die Profilerstellung für die Speicherreservierung und die Sammlung von Objektlebensdauerdaten mithilfe der Instrumentierungsmethode.|  
  
 **VSPerfCLREnv-Optionen zum Verarbeiten der Sampling-Profilerstellung**  
  
 Die folgende Tabelle beschreibt VSPerfCLREnv-Optionen für die Sampling-Profilerstellung:  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**SampleOn**|Aktiviert die Profilerstellung mithilfe der Samplingmethode. Aktiviert nicht die Profilerstellung für die Speicherreservierung oder die Sammlung von Objektlebensdauerdaten.|  
|**SampleGC**|Aktiviert die Profilerstellung für die Speicherreservierung mithilfe der Samplingmethode. Aktiviert nicht die Sammlung von Objektlebensdauerdaten.|  
|**SampleGCLife**|Aktiviert die Profilerstellung für die Speicherreservierung mithilfe der Samplingmethode. Aktiviert zudem die Sammlung von Objektlebensdauerdaten.|  
|**SampleLineOff**|Deaktiviert die Sammlung von .NET-Profilerstellungsdaten auf Zeilenebene.|  
  
 **VSPerfCLREnv-Optionen für die globale Profilerstellung**  
  
 Um die Profilerstellung für einen verwalteten Dienst wie die ASP.NET-Webanwendung auszuführen, die vom Betriebssystem anstatt vom Benutzer gestartet wird, verwenden Sie Optionen für die globale Profilerstellung der VSPerfCLREnv-Optionen. Die folgende Tabelle beschreibt die globalen Versionen der VSPerfCLREnv-Optionen. Diese Optionen legen die geeigneten Umgebungsvariablen bei der Registrierung fest.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**GlobalTraceOn**|Aktiviert die globale Profilerstellung mithilfe der Instrumentierungsmethode. Sammelt keine Speicherreservierungsereignisse oder Objektlebensdauerdaten.|  
|**GlobalTraceGC**|Aktiviert die globale Profilerstellung für die Speicherreservierung mithilfe der Instrumentierungsmethode. Aktiviert nicht die Sammlung von Objektlebensdauerdaten.|  
|**GlobalTraceGCLife**|Aktiviert die globale Profilerstellung für die Speicherreservierung mithilfe der Instrumentierungsmethode. Aktiviert zudem die Sammlung von Objektlebensdauerdaten.|  
|**GlobalSampleOn**|Aktiviert die globale Profilerstellung mithilfe der Samplingmethode. Aktiviert nicht die Sammlung von Speicherreservierungsereignissen oder Objektlebensdauerdaten.|  
|**GlobalSampleGC**|Aktiviert die globale Profilerstellung für die Speicherreservierung mithilfe der Samplingmethode. Aktiviert nicht die Sammlung von Objektlebensdauerdaten.|  
|**GlobalSampleGCLife**|Aktiviert die globale Profilerstellung für die Speicherreservierung mithilfe der Samplingmethode. Aktiviert zudem die Sammlung von Objektlebensdauerdaten.|  
  
 **VSPerfCLREnv-Optionen zum Löschen von Umgebungseinstellungen**  
  
 Wenn Sie mit der Profilerstellung für die verwaltete Anwendung fertig sind, verwenden Sie eine der folgenden Optionen zum Löschen der Umgebungsvariablen, die von VSPerfCLREnv hinzugefügt wurden. In der folgenden Tabelle wird beschrieben, wie sowohl Standard- als auch globale Umgebungsvariablen gelöscht werden:  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Off**|Löscht Umgebungsvariablen für die Standard-.NET-Profilerstellung. Verwenden Sie diese Option, wenn die nicht globalen VSPerfClrEnv-Optionen zum Festlegen der Profiler-Umgebungsvariablen verwendet wurden.|  
|**GlobalOff**|Löscht Umgebungsvariablen für die globale .NET-Profilerstellung. Verwenden Sie diese Option, wenn die Anwendung vom Betriebssystem anstatt vom Profiler gestartet wurde.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Optionen sind für die Profilerstellung einer verwalteten Anwendung nicht erforderlich, wenn die Anwendung mithilfe des Leistungs-Explorers in der IDE gestartet wurde. Der Leistungs-Explorer legt alle erforderlichen Umgebungseinstellungen für Sie fest.  
  
 Wenn während der Profilerstellung nicht die richtige Umgebung festgelegt wurde, wird während der Analyse eine Warnung ausgegeben und die Namen der verwalteten Funktionen werden nicht ordnungsgemäß aufgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)



