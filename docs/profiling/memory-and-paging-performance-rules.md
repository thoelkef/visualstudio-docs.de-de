---
title: "Leistungsregeln f&#252;r Speicher und Auslagerung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Leistungsregeln f&#252;r Speicher und Auslagerung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Leistungsregeln in den Kategorien für Arbeitsspeicher und Paging beziehen sich auf Pagingaktivitäten in einer Profilerstellungsausführung, die die Anwendungsleistung und die Reaktionsfähigkeit beeinträchtigen können.  
  
|||  
|-|-|  
|[DA0014: Äußerst hohes Maß an Paging von aktivem Speicher auf den Datenträger](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Während der gesamten Profilerstellungsausführung ist eine äußerst hohe Pagingrate für aktiven Arbeitsspeicher auf die und von der Festplatte aufgetreten.  Pagingraten dieses Ausmaßes beeinträchtigen meist die Anwendungsleistung und die Reaktionsfähigkeit.  Verringern Sie ggf. die Speicherbelegungen, indem Sie die Algorithmen überarbeiten.  Zudem müssen möglicherweise auch die Speicheranforderungen der Anwendung berücksichtigt werden.  Führen Sie die Profilerstellung ggf. auf einem Computer mit mehr Arbeitsspeicher aus.  Diese Regel wird ausgelöst, wenn die Pagingaktivitäten den oberen Schwellenwert der Regel D0017 überschreiten.|  
|[DA0017: Hohes Maß an Paging von aktivem Speicher auf den Datenträger](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Während der gesamten Profilerstellungsausführung ist eine relativ hohe Pagingrate für aktiven Arbeitsspeicher auf die und von der Festplatte aufgetreten.  Pagingraten dieses Ausmaßes beeinträchtigen meist die Anwendungsleistung und die Reaktionsfähigkeit.  Verringern Sie ggf. die Speicherbelegungen, indem Sie die Algorithmen überarbeiten.  Zudem müssen möglicherweise auch die Speicheranforderungen der Anwendung berücksichtigt werden.  Führen Sie die Profilerstellung ggf. auf einem Computer mit mehr Arbeitsspeicher aus.|