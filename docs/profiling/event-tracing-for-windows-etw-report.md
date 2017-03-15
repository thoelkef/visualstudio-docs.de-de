---
title: "Bericht der Ereignisablaufverfolgung f&#252;r Windows (ETW) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW-Profilerstellungsbericht"
  - "Ereignisablaufverfolgung für Windows-Profilerstellungsbericht"
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Bericht der Ereignisablaufverfolgung f&#252;r Windows (ETW)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Bericht der Ereignisablaufverfolgung für Windows \(ETW\) werden die ETW\-Ereignisse aufgeführt, die in einer Leistungssitzung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \- Profilerstellungstools aufgezeichnet wurden.  ETW\-Daten werden in einer Binärdatei \(.etl\) erfasst.  
  
> [!NOTE]
>  Sie können keine ETW\-Berichte in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Oberfläche anzeigen.  
  
-   Informationen zum Sammeln von ETW\-Daten mit der Profilerstellungstools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Oberfläche finden Sie unter [Gewusst wie: Sammeln von Daten der Ereignisablaufverfolgung für Windows \(ETW\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Informationen zum Sammeln von ETW\-Daten mit den [VSPerfCmd](../profiling/vsperfcmd.md)\-Befehlszeilentools finden Sie unter [Ereignisse](../profiling/events-vsperfcmd.md).  
  
-   Der ETW\-Bericht wird mit dem **VSReport \/Summary:ETW**\-Befehl generiert.  Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Timestamp**|Identifiziert den Zeitpunkt, an dem das Ereignis aufgetreten ist.|  
|**Prozess\-ID**|Identifiziert den Prozess, der das Ereignis generiert hat.|  
|**Thread\-ID**|Identifiziert den Thread, der das Ereignis generiert hat.|  
|****Beschreibung****|Identifiziert den Ereignisanbieter.|  
|**Typ**|Identifiziert den Ereignistyp.|  
|**Eigenschaften**|Die Eigenschaften des Ereignisses.  Jedes Ereignis ist ein durch Trennzeichen getrenntes Name\-Wert\-Paar, das in Klammern eingeschlossen wird.|