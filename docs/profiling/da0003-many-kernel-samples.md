---
title: "DA0003: Zahlreiche Kernelbeispiele | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0003"
  - "vs.performance.DA0003"
  - "vs.performance.3"
  - "vs.performance.rules.DAManyKernelSamples"
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0003: Zahlreiche Kernelbeispiele
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0003|  
|Kategorie \(Category\)|Verwendung der Profilerstellungstools|  
|Profilerstellungsmethoden|Sampling|  
|Meldung|Im Kernelmodus ist ein hoher Anteil von Beispielen vorhanden.  Dies deutet auf ein hohes Maß an E\/A\-Aktivitäten oder auf häufige Kontextwechsel hin.  Erstellen Sie nach Möglichkeit ein neues Profil für die Anwendung, und verwenden Sie dabei den Instrumentationsmodus.|  
|Regeltyp|Information|  
  
## Ursache  
 Ein großer Teil der für die Anwendung gesammelten Aufruflistensamples wurde im Kernelmodus ausgeführt.  Führen Sie die Profilerstellung für die Anwendung ggf. mit einer anderen Profilerstellungsmethode aus.  
  
## Regelbeschreibung  
 In Windows kann Code entweder im Kernelmodus oder im Benutzermodus ausgeführt werden. \(Der Kernelmodus wird auch als privilegierter Modus bezeichnet.\) Nur Systemcode niedriger Ebene, z. B. Gerätetreiber, wird im Kernelmodus ausgeführt.  Von einer Benutzermodusanwendung kann in den Kernelmodus gewechselt werden, um E\/A\-Vorgänge auszuführen, auf Thread\- oder Prozesssynchronisierungsprimitive zu warten oder Systemaufrufe auszuführen.  
  
 Sampling ist am effektivsten, wenn Sie Anwendungen profilieren, die hauptsächlich im Benutzermodus arbeiten.  In die Anzahl von Samplings, die erfasst wurden, als die Anwendung im Kernelmodus ausgeführt wurde, können auf häufige E\/A\-Vorgänge hinweisen oder darauf hinweisen, dass Kontextwechsel auftreten.  Keine dieser Operationen kann mit der Samplingmethode untersucht werden.  Wenn zu viele Kernelmodusbeispiele akzeptiert werden, enthalten die Samplingdaten möglicherweise nicht genug Benutzermodusbeispiele, um statistisch bedeutend zu sein.  
  
## Behandeln von Verstößen  
 Führen Sie ggf. eine neue Profilerstellung für die Anwendung mit einer der folgenden Optionen durch:  
  
-   Profilerstellung mit der Instrumentationsmethode.  
  
-   Erhöhen der Samplingrate, um zu versuchen, mehr Samplings im Benutzermodus zu sammeln