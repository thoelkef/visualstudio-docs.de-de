---
title: Events (VSPerfCmd) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48957b7078f8348f4ac1489267b603992e04a56a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965761"
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
Die *VSPerfCmd.exe*-Option **Events** steuert die Protokollierung der Ereignisablaufverfolgung für Windows (ETW). ETW-Daten werden in einer ETL-Datei gespeichert, die von der Profiler-Datendatei getrennt ist. Die Daten können in einem Bericht mithilfe des Befehls „[VSPerfReport ](../profiling/vsperfreport.md) /summary: etw“ angezeigt werden.  
  
 Die Option **Events** kann jederzeit aufgerufen werden, bevor der VSPerfCmd-Befehl **Shutdown** zum Beenden der Profilerstellung aufgerufen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cmd  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parameter  
 **On**|**Off**  
 Startet oder beendet die Sammlung von Ereignisdaten  
  
 `Guid`  
 Die GUID des Anbietersteuerelements  
  
 `ProviderName`  
 Der Name des Anbieters, der bei der Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) registriert ist  
  
 `Flags`  
 Ein mit „0x“ präfigierter Wert eines hexadezimal Flags, der vom Ereignisanbieter definiert wird  
  
 `Level`  
 Gibt die Menge der gesammelten Daten an. `Level` wird vom Ereignisanbieter definiert.  
  
 Die Option **Events** versteht die folgenden Kernelschlüsselwörter als Anbieternamen:  
  
 **Process**  
 Prozessereignisse  
  
 **Thread**  
 Threadereignisse  
  
 **Image**  
 Lade- und Entladeereignisse für Bilder  
  
 **Disk**  
 E/A-Datenträgerereignisse  
  
 **Datei**  
 E/A-Dateiereignisse  
  
 **Hardfault**  
 Harte Seitenfehler  
  
 **Pagefault**  
 Weiche Seitenfehler  
  
 **Network**  
 Netzwerkereignisse  
  
 **Registry**  
 Ereignisse beim Zugriff auf die Registrierung  
  
 Beachten Sie, dass der Kernelanbieter nur aktiviert werden kann. Er kann weder deaktiviert werden, noch können Flags geändert werden, bis der Monitor heruntergefahren wurde.  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
>  Wenn CLR-ETW-Ereignisse aktiviert sind, werden im Bericht in der Ablaufverfolgungsansicht auch zusätzliche Startdaten gesammelt. Mit dem folgenden Befehl vermeiden Sie, dass Startereignisse im Bericht angezeigt werden:  
  
```cmd  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Wenn Sie Startereignisse nicht ausschließen, werden sie als GUIDs im Bericht angezeigt, weil sie nicht in der MOF-Datei (Managed Object Format) aufgeführt werden. Weitere Informationen finden Sie auf der Microsoft-Website auf der Seite zum Thema: [Sample Managed Object Format (MOF) file (MOF-Beispieldatei (Managed Object Format))](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)