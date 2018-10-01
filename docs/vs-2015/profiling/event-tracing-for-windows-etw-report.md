---
title: Bericht der Ereignisablaufverfolgung für Windows (ETW) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49ea37f6830c7e4fdf8c8d94b0f323c6337329c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524078"
---
# <a name="event-tracing-for-windows-etw-report"></a>Bericht der Ereignisablaufverfolgung für Windows (ETW)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Bericht der Ereignisablaufverfolgung für Windows (ETW)](https://docs.microsoft.com/visualstudio/profiling/event-tracing-for-windows-etw-report).  
  
In dem Bericht „Ereignisablaufverfolgung für Windows (ETW)“ werden die ETW-Ereignisse aufgeführt, die in einer Leistungssitzung für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools aufgezeichnet wurden. ETW-Daten werden in einer Binärdatei (.etl) erfasst.  
  
> [!NOTE]
>  ETW-Berichte werden in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Schnittstellen nicht angezeigt.  
  
-   Weitere Informationen zum Erfassen der ETW über die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Schnittstelle mithilfe von Profilerstellungstools finden Sie unter [Vorgehensweise: Erfassen von Daten der Ereignisablaufverfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Weitere Informationen zum Erfassen von ETW-Daten über die Befehlszeilentools [VSPerfCmd](../profiling/vsperfcmd.md) finden Sie unter [Events (Ereignisse)](../profiling/events-vsperfcmd.md).  
  
-   Der ETW-Bericht wird über den Befehl **VSReport/Summary:ETW** erstellt. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Zeitstempel**|Gibt an, wann das Ereignis aufgetreten ist|  
|**Prozess-ID**|Gibt den Prozess an, der das Ereignis generiert hat|  
|**Thread-ID**|Gibt den Thread an, der das Ereignis generiert hat|  
|**Beschreibung**|Gibt den Ereignisanbieter an|  
|**Type**|Gibt den Ereignistyp an|  
|**Eigenschaften**|Eigenschaften des Ereignisses Jedes Ereignis besteht aus einem durch Kommas abgetrennten Name/Wert-Paar in Klammern.|



