---
title: Bericht der Ereignisablaufverfolgung für Windows (ETW) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 627caa20d53bbb93c6c4477c3323dda57a37d9f0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194779"
---
# <a name="event-tracing-for-windows-etw-report"></a>Bericht der Ereignisablaufverfolgung für Windows (ETW)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



