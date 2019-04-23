---
title: Bericht der Ereignisablaufverfolgung für Windows (ETW) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bfcb10bdbbfcb8e4b98f8d90d6652832059107d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108216"
---
# <a name="event-tracing-for-windows-etw-report"></a>Bericht der Ereignisablaufverfolgung für Windows (ETW)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dem Bericht „Ereignisablaufverfolgung für Windows (ETW)“ werden die ETW-Ereignisse aufgeführt, die in einer Leistungssitzung für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools aufgezeichnet wurden. ETW-Daten werden in einer Binärdatei (.etl) erfasst.  
  
> [!NOTE]
>  ETW-Berichte werden in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Schnittstellen nicht angezeigt.  
  
- Weitere Informationen zum Erfassen der ETW über die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Schnittstelle mithilfe von Profilerstellungstools finden Sie unter [Vorgehensweise: Sammeln der Ereignisablaufverfolgung für Windows (ETW) Daten](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Weitere Informationen zum Erfassen von ETW-Daten über die Befehlszeilentools [VSPerfCmd](../profiling/vsperfcmd.md) finden Sie unter [Events (Ereignisse)](../profiling/events-vsperfcmd.md).  
  
- Der ETW-Bericht wird über den Befehl **VSReport/Summary:ETW** erstellt. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Zeitstempel**|Gibt an, wann das Ereignis aufgetreten ist|  
|**Prozess-ID**|Gibt den Prozess an, der das Ereignis generiert hat|  
|**Thread-ID**|Gibt den Thread an, der das Ereignis generiert hat|  
|**Beschreibung**|Gibt den Ereignisanbieter an|  
|**Type**|Gibt den Ereignistyp an|  
|**Eigenschaften**|Eigenschaften des Ereignisses Jedes Ereignis besteht aus einem durch Kommas abgetrennten Name/Wert-Paar in Klammern.|
