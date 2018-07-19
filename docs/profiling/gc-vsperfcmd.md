---
title: GC (VSPerfCmd) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45b93d3184a825c11e0a4742ad752c6a2c1c031e
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237564"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
Die Option **GC** aktiviert das Erfassen von Daten zur Speicherbelegung durch .NET-Framework und zur Objektlebensdauer. Die Option **GC** kann nur gemeinsam mit der Sampling-Profilerstellungsmethode und der Option **Launch** (Start) verwendet werden.  
  
 Wenn Sie die Option **GC** verwenden, ist der VSPerfClrEnv-Befehl **/sampleon** nicht erforderlich.  
  
 Wenn keine Parameter angegeben sind, oder wenn der Parameter **Speicherbelegung** angegeben ist, werden nur Daten zur Speicherbelegung durch .NET-Framework erfasst. Wenn der Parameter **Lebensdauer** angegeben ist, werden sowohl Daten zur Speicherbelegung durch .NET-Framework als auch zur Objektlebensdauer erfasst.  
  
## <a name="syntax"></a>Syntax  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 **Speicherbelegung**  
 Standard. Erfasst Daten zur Speicherbelegung durch .NET-Framework.  
  
 **Lebensdauer**  
 Erfasst sowohl Daten zur Speicherbelegung durch .NET-Framework als auch zur Lebensdauer von .NET Framework-Objekten.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die Option **GC** kann nur mit der Option **Launch** (Start) verwendet werden.  
  
 **Starten:** `AppName`  
 Startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.  
  
## <a name="example"></a>Beispiel  
 Mithilfe des folgenden Beispiels wird eine Anwendung gestartet und Daten zur Speicherbelegung durch .NET-Framework erfasst.  
  
```cmd  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)