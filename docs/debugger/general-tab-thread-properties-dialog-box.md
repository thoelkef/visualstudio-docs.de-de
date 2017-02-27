---
title: "Registerkarte &quot;Allgemein&quot;, Dialogfeld &quot;Threadeigenschaften&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Threading [Visual Studio], Threadeigenschaften"
  - "Threadeigenschaften"
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Registerkarte &quot;Allgemein&quot;, Dialogfeld &quot;Threadeigenschaften&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden Sie dieses Dialogfeld, um weitere Informationen über einen bestimmten Thread zu erhalten.  Verschieben Sie zum Anzeigen dieses Dialogfelds den Fokus auf ein [Threadansichtsfenster](../debugger/threads-view.md), oder öffnen Sie die [Meldungsansicht](../debugger/messages-view.md), und erweitern Sie eine Meldung.  Wählen Sie in der Struktur einen Threadknoten und dann **Eigenschaften** im Menü **Ansicht** aus.  
  
 Das Dialogfeld **Threadeigenschaften** enthält einen einzigen Bereich, die Registerkarte **Allgemein**.  Die folgenden Einstellungen sind verfügbar:  
  
|Eintrag|Beschreibung|  
|-------------|------------------|  
|**Modulname**|Der Name des Moduls.|  
|**Thread\-ID**|Die eindeutige ID des Threads.  Beachten Sie, dass Thread\-IDs wiederverwendet werden. Sie identifizieren einen Thread nur während dessen Lebensdauer.|  
|**Prozess\-ID**|Die eindeutige ID des Prozesses.  Prozess\-IDs werden wiederverwendet, daher identifizieren sie einen Prozess nur für die Lebensdauer dieses Prozesses.  Der Prozessobjekttyp wird erstellt, wenn ein Programm ausgeführt wird.  Alle Threads in einem Prozess verwenden den gleichen Adressbereich und haben Zugriff auf die gleichen Daten.  Wählen Sie diesen Wert aus, um die Eigenschaften der Prozess\-ID anzuzeigen.|  
|**Threadzustand**|Der aktuelle Zustand des Threads.  Ein Thread mit dem Zustand "Wird ausgeführt" verwendet einen Prozessor, und ein Thread mit dem Zustand "Standby" verwendet in Kürze einen Prozessor.  Ein Thread mit dem Zustand "Bereit" wartet auf einen freien Prozessor.  Ein Thread mit dem Zustand "Übergang" wartet auf die Ausführung einer Ressource, z. B. auf das Lesen des Ausführungsstapels vom Datenträger.  Ein Thread mit dem Zustand "Wartend" benötigt keinen Prozessor, da er auf die Beendigung einer Operation in der Peripherie oder auf das Freiwerden einer Ressource wartet.|  
|**Warteursache**|Dies gilt nur für einen Thread, der sich im Wartezustand befindet.  Für die Kommunikation mit geschützten Subsystemen werden Ereignispaare verwendet.|  
|**CPU\-Zeit**|Die gesamte für den Prozess und seine Threads aufgewendete CPU\-Zeit.  Gleich Benutzerzeit \+ privilegierte Zeit.|  
|**Benutzerzeit**|Die gesamte verstrichene Zeit, in der der Thread Code im Benutzermodus ausgeführt hat.  Anwendungen werden im Benutzermodus ausgeführt, ebenso Subsysteme, z. B. der Fenster\-Manager und die Grafikengine.|  
|**Privilegierte Zeit**|Die gesamte verstrichene Zeit, in der der Thread Code im privilegierten Modus ausgeführt.  Wenn ein Windows\-Systemdienst aufgerufen wird, wird der Dienst häufig im privilegierten Modus ausgeführt, um Zugriff auf private Daten des Systems zu erhalten.  Solche Daten werden durch im Benutzermodus ausgeführte Threads vor Zugriff geschützt.  Aufrufe des Systems können explizit oder implizit, z. B. beim Auftreten eines Seitenfehlers oder Interrupts, erfolgen.|  
|**Verstrichene Zeit**|Die gesamte verstrichene Ausführungszeit \(in Sekunden\) des Threads.|  
|**Aktuelle Priorität**|Die aktuelle dynamische Priorität des Threads.  Threads in einem Prozess können die eigene Basispriorität relativ zur Basispriorität des Prozesses erhöhen und verringern.|  
|**Basispriorität**|Die aktuelle Basispriorität des Threads.|  
|**Startadresse**|Die virtuelle Startadresse für den Thread.|  
|**User PC**|Der Benutzerprogrammzähler für den Thread.|  
|**Kontextwechsel**|Die Anzahl der Wechsel zwischen Threads.  Threadwechsel können innerhalb eines einzelnen Prozesses oder prozessübergreifend erfolgen.  Ein Threadwechsel kann durch einen Thread verursacht werden, der Informationen von einem anderen Thread anfordert, oder durch einen Thread, der präemptiv unterbrochen wird, wenn ein Thread mit höherer Priorität zur Ausführung bereit ist.|