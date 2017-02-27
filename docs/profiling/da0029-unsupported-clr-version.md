---
title: "DA0029: Nicht unterst&#252;tzte CLR-Version | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.29"
  - "vs.performance.rules.DA0029"
helpviewer_keywords: 
  - "vs.performance.29"
  - "vs.performance.DA0029"
  - "vs.performance.rules.DA0029"
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# DA0029: Nicht unterst&#252;tzte CLR-Version
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0029|  
|Kategorie \(Category\)|Verwendung der Profilerstellungstools|  
|Profilerstellungsmethode|Profilerstellung mithilfe der Befehlszeile|  
|Meldung|Während der Auflistung wurde eine nicht unterstützte CLR\-Version erkannt.  Verwaltete Symbole werden möglicherweise nicht korrekt aufgelöst.|  
|Regeltyp|Information|  
  
## Ursache  
 Sie versuchen, ein Profil für eine Anwendung zu erstellen, von der [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] verwendet wird. Diese Version wird jedoch von den Profilerstellungstools nicht unterstützt.  
  
## Regelbeschreibung  
 Diese Warnung wird ausgegeben, da von den Profilerstellungstools keine Symbole für den verwalteten Code aufgelöst werden können, der in der Anwendung ausgeführt wird.  Von den Profilerstellungstools können für Anwendungen, von denen [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] ausgeführt wird, keine Symbole für verwalteten Code aufgelöst werden.  
  
## Behandeln von Verstößen  
 Keine.