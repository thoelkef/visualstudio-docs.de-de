---
title: LineOff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba5d8c3e2644c94a4e15115661341a34c9e6f761
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845427"
---
# <a name="lineoff"></a>LineOff
Standardmäßig erfasst der Profiler die Zeilennummer des Quellcodes sowie die Offsetdaten der Zeilennummer, wenn Sie die Sampling-Profilerstellungsmethode verwenden. Die **LineOff**-Option für VSPerfCmd deaktiviert die Datensammlung der Zeilennummern, wenn VSPerfCmd zum Starten der Anwendung verwendet wird. Wenn **LineOff** angegeben ist, werden Profilerstellungsdaten für die Funktionsebene gesammelt.  
  
 Sie können **LineOff** nur mit der Option **Launch** (Starten) verwenden und auch nur, wenn der Profiler für das Sampling mithilfe der Option **Start**:**Sample** initialisiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 Keiner  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die **LineOff**-Option kann nur auf einer Befehlszeile verwendet werden, die die Option **Launch** (Starten) enthält.  
  
 **Starten:** `AppName`  
 Startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel werden die Anwendung und der Profiler gestartet, und das Sampling auf Zeilenebene wird deaktiviert.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)