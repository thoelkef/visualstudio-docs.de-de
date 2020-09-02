---
title: LineOff | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbe8a715c5bb179c5293dd666f1879c07068d8b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62583170"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standardmäßig erfasst der Profiler die Zeilennummer des Quellcodes sowie die Offsetdaten der Zeilennummer, wenn Sie die Sampling-Profilerstellungsmethode verwenden. Die **LineOff**-Option für VSPerfCmd deaktiviert die Datensammlung der Zeilennummern, wenn VSPerfCmd zum Starten der Anwendung verwendet wird. Wenn **LineOff** angegeben ist, werden Profilerstellungsdaten für die Funktionsebene gesammelt.  
  
 Sie können **LineOff** nur mit der Option **Launch** (Starten) verwenden und auch nur, wenn der Profiler für das Sampling mithilfe der Option **Start**:**Sample** initialisiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die **LineOff**-Option kann nur auf einer Befehlszeile verwendet werden, die die Option **Launch** (Starten) enthält.  
  
 **Starten** Sie Folgendes: `AppName`  
 Startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel werden die Anwendung und der Profiler gestartet, und das Sampling auf Zeilenebene wird deaktiviert.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung ASP.NET Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)
