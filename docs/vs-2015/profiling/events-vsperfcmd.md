---
title: Events (VSPerfCmd) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9d14397da6eae0c85b2549bb2f7e6d48af03c17
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512095"
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Events (VSPerfCmd)](https://docs.microsoft.com/visualstudio/profiling/events-vsperfcmd).  
  
Die VSPerfCmd.exe-Option **Events** steuert die Protokollierung der Ereignisablaufverfolgung für Windows (ETW). ETW-Daten werden in einer ETL-Datei gespeichert, die von der Profiler-Datendatei getrennt ist. Die Daten können in einem Bericht mithilfe des Befehls „[VSPerfReport ](../profiling/vsperfreport.md) /summary: etw“ angezeigt werden.  
  
 Die Option **Events** kann jederzeit aufgerufen werden, bevor der VSPerfCmd-Befehl **Shutdown** zum Beenden der Profilerstellung aufgerufen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Wenn Sie Startereignisse nicht ausschließen, werden sie als GUIDs im Bericht angezeigt, weil sie nicht in der MOF-Datei (Managed Object Format) aufgeführt werden. Weitere Informationen finden Sie auf dieser Microsoft-Website: [Sample Managed Object Format (MOF) File (Managed Object Format-Beispieldatei (MOF))](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)



