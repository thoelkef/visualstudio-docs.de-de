---
title: WinCounter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9a8e381ed058c30dcbf1760f380cf065c1443cd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520696"
---
# <a name="wincounter"></a>WinCounter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [WinCounter](https://docs.microsoft.com/visualstudio/profiling/wincounter).  
  
Über die Option **WinCounter** wird ein Leistungsindikator für Windows oder die Anwendung angegeben, um bei der Profilerstellung festgelegte Intervalle zu erfassen. Leistungsindikatoren für Windows und die Anwendung werden als Markierungen in den Profilerstellungs-Datendateien aufgeführt. Sie können mehrere Leistungsindikatoren angeben, die in separaten Optionen erfasst werden sollen.  
  
 Standardmäßig werden Leistungsindikatoren alle 500 ms erfasst. Verwenden Sie die Option **AutoMark**, um ein anderes Intervall für die Erfassung festzulegen.  
  
 Es wird nur die Option **AutoMark** verwendet. Wenn mehrere Optionen **AutoMark** angegeben sind, wird nur die letzte verwendet.  
  
 Die Option **WinCounter** kann nur mit der Option **Start** verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Path`  
 Der Windows-Leistungsindikator im PDH-Indikatorpfadformat.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die Option **WinCounter** kann nur mit der Option **Start** verwendet werden.  
  
 **Start:** `Method`  
 Die Option **Start** initialisiert den Profiler mit der angegebenen Profilerstellungsmethode.  
  
## <a name="exclusive-options"></a>Ausschließliche Optionen  
 Die Option **AutoMark** kann nur mit der Option **WinCounter** verwendet werden.  
  
 **AutoMark:** `Milliseconds`  
 Gibt die Zeit in Millisekunden zwischen Datenerfassungen mit einem Windows-Leistungsindikator an.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden zwei Windows-Leistungsindikatoren angeben, die in einem Intervall von 1000 ms erfasst werden.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)



