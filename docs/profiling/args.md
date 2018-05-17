---
title: Args | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0452d590395198528788cb433f6ccf9b4a4396b7
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2018
---
# <a name="args"></a>Args
Die VSPerfCmd.exe-Option **Args** bestimmt eine Liste von Argumenten, die an die Zielanwendung des Unterbefehls **Starten** übergeben werden.  
  
 **Args** kann nur dann verwendet werden, wenn **Starten** auch in der Befehlszeile angegeben ist. **Args** ist optional, wenn **Starten** angegeben ist.  
  
## <a name="syntax"></a>Syntax  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Arguments`  
 Eine Liste von Argumenten für die Zielanwendung des Befehls **Starten**.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 **Starten:** `AppName`  
 Startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.  
  
## <a name="example"></a>Beispiel  
 Folgendes Beispiel verwendet die Option **Args**, um Argumente an TestApp.exe zu übergeben.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)