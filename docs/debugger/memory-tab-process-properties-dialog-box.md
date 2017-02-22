---
title: "Registerkarte &quot;Arbeitsspeicher&quot;, Dialogfeld &quot;Prozesseigenschaften&quot; | Microsoft Docs"
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
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Registerkarte &quot;Arbeitsspeicher&quot;, Dialogfeld &quot;Prozesseigenschaften&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Registerkarte **Arbeitsspeicher**, um die Speichernutzung eines Prozesses anzuzeigen.  Um das Dialogfeld [Prozesseigenschaften](../debugger/process-properties-dialog-box.md) anzuzeigen, verschieben Sie den Fokus auf ein [Prozessansichtsfenster](../debugger/processes-view.md).  Wählen Sie in der Struktur einen Prozessknoten und dann **Eigenschaften** im Menü **Ansicht** aus.  
  
 Auf der Registerkarte **Arbeitsspeicher** sind die folgenden Einstellungen verfügbar:  
  
|Eintrag|Beschreibung|  
|-------------|------------------|  
|**Virtuelle Bytes**|Die aktuelle Größe \(in Bytes\) des vom Prozess verwendeten virtuellen Adressbereichs.  Wenn der virtuelle Adressbereich verwendet wird, bedeutet dies nicht notwendigerweise, dass eine entsprechende Verwendung von Datenträger\- oder Hauptspeicherseiten erfolgt.  Der virtuelle Adressbereich ist jedoch begrenzt, und durch die Verwendung eines zu hohen Anteils wird möglicherweise die Fähigkeit zum Laden von Bibliotheken durch den Prozess beschränkt.|  
|**Virtuelle Bytes max.**|Die maximale Anzahl von Bytes des virtuellen Adressbereichs, die vom Prozess zu einem beliebigen einzelnen Zeitpunkt verwendet wurde.|  
|**Workingset**|Der Satz von Speicherseiten, auf die vor kurzem von den Threads im Prozess zugegriffen wurde.  Wenn der freie Arbeitsspeicher im Computer einen Schwellenwert überschritten hat, werden Seiten im Workingset eines Prozesses belassen, auch wenn sie nicht verwendet werden.  Wenn der freie Arbeitsspeicher einen Schwellenwert unterschreitet, werden Seiten aus dem Workingset entfernt.  Wenn sie benötigt werden, werden sie per Softfault wieder in das Workingset eingeschlossen, bevor sie den Hauptspeicher verlassen.|  
|**Workingset max.**|Die maximale Anzahl von Seiten im Workingset des Prozesses zu einem beliebigen Zeitpunkt.|  
|**Auslagerbare Poolbytes**|Die aktuelle Menge an auslagerbarem Pool, der vom Prozess belegt wurde.  Der auslagerbare Pool ist ein Systemspeicherbereich, aus dem Betriebssystemkomponenten Speicher abrufen, wenn sie zugewiesene Aufgaben ausführen.  Auslagerbare Poolseiten können in die Auslagerungsdatei ausgelagert werden, wenn das System für einen längeren Zeitraum nicht auf sie zugreift.|  
|**Nicht auslagerbare Poolbytes**|Die aktuelle Anzahl von Bytes im nicht auslagerbaren Pool, der vom Prozess belegt wurde.  Der nicht auslagerbare Pool ist ein Systemspeicherbereich, aus dem Betriebssystemkomponenten Speicher abrufen, wenn sie zugewiesene Aufgaben ausführen.  Nicht auslagerbare Poolseiten können in die Auslagerungsdatei ausgelagert werden. Sie bleiben im Hauptspeicher, solange sie belegt sind.|  
|**Private Bytes**|Die aktuelle Anzahl von Bytes, die der Prozess belegt hat und die nicht mit anderen Prozessen gemeinsam genutzt werden können.|  
|**Freie Bytes**|Der gesamte nicht verwendete virtuelle Adressbereich des Prozesses.|  
|**Reservierte Bytes**|Die Gesamtmenge an virtuellem Arbeitsspeicher, der von dem Prozess für die zukünftige Verwendung reserviert wurde.|  
|**Freie Bytes des Images**|Die Menge des virtuellen Adressbereichs, der nicht von Images im Prozess verwendet oder reserviert ist.|  
|**Reservierte Bytes des Images**|Die Summe des virtuellen Arbeitsspeichers, die von im Prozess ausgeführten Images reserviert ist.|