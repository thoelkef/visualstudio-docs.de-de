---
title: User (VSPerfCmd) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b96005f0935f0d1a50233196aa01bf157b6e0cd
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
Die **User**-Option gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.  
  
 Die **User**-Option kann nur in einer Befehlszeile angegeben werden, die auch die **Start**-Option enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Domain`  
 Der Name der Domäne des Benutzers.  
  
 `UserName`  
 Der Name des Benutzers.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die Option **User** kann nur mit der Option **Start** verwendet werden.  
  
 **Start:** `Method`  
 Initialisiert den Profiler mit der angegebenen Profilerstellungsmethode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der **User**-Option gezeigt.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)