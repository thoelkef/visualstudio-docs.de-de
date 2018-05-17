---
title: Ausgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e5b588100666f54d4345c15bc3278cf4bf2b3054
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
---
# <a name="output"></a>Ausgabe
Die Option **Ausgabe** gibt den Namen der Profilerstellungsdaten für die Leistungssitzung an. **Ausgabe** muss zusammen mit der Option **Start** verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)