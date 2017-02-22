---
title: "Registerkarte &quot;Auslagerungsdatei&quot;, Dialogfeld &quot;Prozesseigenschaften&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Prozesseigenschaften für Windows NT"
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Registerkarte &quot;Auslagerungsdatei&quot;, Dialogfeld &quot;Prozesseigenschaften&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Registerkarte **Auslagerungsdatei**, um die Auslagerungsdatei eines Prozesses zu untersuchen.  Um das Dialogfeld [Prozesseigenschaften](../debugger/process-properties-dialog-box.md) anzuzeigen, verschieben Sie den Fokus auf ein [Prozessansichtsfenster](../debugger/processes-view.md).  Wählen Sie in der Struktur einen Prozessknoten und dann **Eigenschaften** im Menü **Ansicht** aus.  
  
 Auf der Registerkarte **Auslagerungsdatei** sind die folgenden Einstellungen verfügbar:  
  
|Eintrag|Beschreibung|  
|-------------|------------------|  
|**Bytes für Auslagerungsdatei**|Die aktuelle Anzahl von Seiten, die von dem Prozess in der Auslagerungsdatei verwendet werden.  In der Auslagerungsdatei werden Seiten von Daten gespeichert, die vom Prozess verwendet werden, jedoch nicht in anderen Dateien enthalten sind.  Die Auslagerungsdatei wird von allen Prozessen verwendet, und mangelnder Speicher in der Auslagerungsdatei kann Fehler während der Ausführung anderer Prozesse verursachen.|  
|**Max. Bytes für Auslagerungsdatei**|Die maximale Anzahl von Seiten in der Auslagerungsdatei, die von dem Prozess verwendet wurden.|  
|**Seitenfehler**|Die Anzahl der Seitenfehler durch die in dem Prozess ausgeführten Threads.  Ein Seitenfehler tritt auf, wenn ein Thread auf eine Seite des virtuellen Speichers verweist, die nicht im zugehörigen Workingset des Hauptspeichers enthalten ist.  Somit wird die Seite nicht vom Datenträger abgerufen, wenn sie in der Standbyliste aufgeführt wird und daher bereits im Hauptspeicher enthalten ist, oder wenn sie von einem anderen Prozess verwendet wird, für den die Seite freigegeben ist.|