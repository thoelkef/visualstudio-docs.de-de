---
title: "Gewusst wie: Filtern von Berichten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Filtern von Berichten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch Verwenden von Optionen für den **VSPerfReport** \-Befehl können Sie Berichte nach einem bestimmten Zeitsegment der Profilerstellungs\-Datendatei filtern oder die Daten auf einen oder mehrere Prozessen oder Threads beschränken.  Weitere Informationen zu diesem Befehl finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
|Optionen|**Beschreibung**|  
|--------------|----------------------|  
|**StartTime:**\[*Value*\]|Zeigt nur nach einem Wert \(in Millisekunden\) erfasste Daten an.|  
|**EndTime:**\[*Value*\]|Zeigt nur vor einem Wert \(in Millisekunden\) erfasste Daten an.|  
|**FilterFile:** `VSPFFile`|Gibt den Speicherort einer Filterdatei an, die im Visual Studio\-Fenster **Leistungsbericht** generiert wurde.|  
|**MsFilter:**\[*StartTime,Duration*\]|Nur Daten ab `StartTime` und für die Dauer von `Duration` \(in Millisekunden\) anzeigen.|  
|**Process:**\[*Pid*\]|Zeigt nur Daten zum angegebenen Prozess an.|  
|**Thread:**\[*ThreadID*\]|Zeigt nur Daten zum angegebenen Thread an.|  
|**Thread:**\[*ThreadID,ProcessID*\]|Zeigt nur Daten zum angegebenen Thread an, der mit dem angegebenen Prozess verknüpft ist.|