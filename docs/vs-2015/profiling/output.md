---
title: Ausgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26a9532bcf0e641d9ad27522f207493b905dc471
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54776956"
---
# <a name="output"></a>Output
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Option **Ausgabe** gibt den Namen der Profilerstellungsdaten für die Leistungssitzung an. **Ausgabe** muss zusammen mit der Option **Start** verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `FileName`  
 Der Name der Datendatei. Es werden vollständige und partielle Pfade angenommen. Wenn kein Pfad angegeben ist, wird die Datei im aktuellen Verzeichnis erstellt.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die Option **Ausgabe** muss zusammen mit der Option **Start** verwendet werden.  
  
 **Start:** `Method`  
 Gibt den Ausgabedateinamen an.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Profilerstellungs-Datendatei im aktuellen Verzeichnis erstellt.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)
