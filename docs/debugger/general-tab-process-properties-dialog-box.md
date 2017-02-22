---
title: "Registerkarte &quot;Allgemein&quot;, Dialogfeld &quot;Prozesseigenschaften&quot; | Microsoft Docs"
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
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Registerkarte &quot;Allgemein&quot;, Dialogfeld &quot;Prozesseigenschaften&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Registerkarte **Allgemein**, um weitere Informationen über einen bestimmten Prozess zu erhalten.  Um das Dialogfeld [Prozesseigenschaften](../debugger/process-properties-dialog-box.md) anzuzeigen, verschieben Sie den Fokus auf ein [Prozessansichtsfenster](../debugger/processes-view.md).  Wählen Sie in der Struktur einen Prozessknoten und dann **Eigenschaften** im Menü **Ansicht** aus.  
  
 Auf der Registerkarte **Allgemein** sind die folgenden Einstellungen verfügbar:  
  
|Eintrag|Beschreibung|  
|-------------|------------------|  
|**Modulname**|Der Name des Moduls.|  
|**Prozess\-ID**|Die eindeutige ID des Prozesses.  Prozess\-IDs werden wiederverwendet, daher identifizieren sie einen Prozess nur für die Lebensdauer dieses Prozesses.  Der Prozessobjekttyp wird erstellt, wenn ein Programm ausgeführt wird.  Alle Threads in einem Prozess verwenden den gleichen Adressbereich und haben Zugriff auf die gleichen Daten.|  
|**Basispriorität**|Die aktuelle Basispriorität des Prozesses.  Threads in einem Prozess können die eigene Basispriorität relativ zur Basispriorität des Prozesses erhöhen und verringern.|  
|**Threads**|Die Anzahl der gegenwärtig in dem Prozess aktiven Threads.|  
|**CPU\-Zeit**|Die gesamte für den Prozess und seine Threads aufgewendete CPU\-Zeit.  Gleich Benutzerzeit plus privilegierte Zeit.|  
|**Benutzerzeit**|Die bisher verstrichene Zeit, in der die Threads des Prozesses, die sich nicht im Leerlauf befanden, Code im Benutzermodus ausgeführt haben.  Anwendungen werden im Benutzermodus ausgeführt, ebenso Subsysteme, z. B. der Fenster\-Manager und die Grafikengine.|  
|**Privilegierte Zeit**|Die gesamte verstrichene Zeit, in der dieser Prozess in Threads, die sich nicht im Leerlauf befanden, im privilegierten Modus ausgeführt wurde.  Die Dienstebene, die Ausführungsroutinen und der Kernel werden im privilegierten Modus ausgeführt.  Die Gerätetreiber für die meisten Geräte, außer Grafikadaptern und Druckern, werden ebenfalls im privilegierten Modus ausgeführt.  Einige von Windows für die Anwendung ausgeführte Vorgänge werden möglicherweise nicht nur unter "Privilegierte Zeit", sondern auch in anderen Subsystemprozessen angezeigt.|  
|**Verstrichene Zeit**|Die gesamte verstrichene Zeit, in der der Prozess ausgeführt wurde.|