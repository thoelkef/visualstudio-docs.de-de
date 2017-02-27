---
title: "marker_series-Klasse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series-Klasse"
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series-Klasse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Stellt einen seriellen Kanal von Ereignissen dar, die durch einen einzelnen Anbieter generiert werden.  
  
## Syntax  
  
```  
class marker_series;  
```  
  
## Member  
  
### Öffentliche Konstruktoren  
  
|Name|**Beschreibung**|  
|----------|----------------------|  
|[marker\_series::marker\_series\-Konstruktor](../profiling/marker-series-marker-series-constructor.md)|Initialisiert eine neue Instanz der `marker_series`\-Klasse.|  
|[marker\_series::~marker\_series\-Destruktor](../profiling/marker-series-tilde-marker-series-destructor.md)|Zerstört marker\_series\-Objekt und alle Versionen zugeordnete Ressourcen.|  
  
### Öffentliche Methoden  
  
|Name|**Beschreibung**|  
|----------|----------------------|  
|[marker\_series::is\_enabled\-Methode](../profiling/marker-series-is-enabled-method.md)|Bestimmt wenn eine Sitzung ist aktiviert den Anbieter.|  
|[marker\_series::write\_alert\-Methode](../profiling/marker-series-write-alert-method.md)|Schreibt eine Warnung in die Parallelitätsschnellansichts\-Ablaufverfolgungsdatei.|  
|[marker\_series::write\_flag\-Methode](../profiling/marker-series-write-flag-method.md)|Schreibt ein Flag in die Parallelitätsschnellansichts\-Ablaufverfolgungsdatei.|  
|[marker\_series::write\_message\-Methode](../profiling/marker-series-write-message-method.md)|Schreibt eine Meldung in die Parallelitätsschnellansichts\-Ablaufverfolgungsdatei.|  
  
## Vererbungshierarchie  
 `marker_series`  
  
## Anforderungen  
 **Header:**  cvmarkersobj.h  
  
 **Namespace:**  Concurrency::diagnostic  
  
## Siehe auch  
 [diagnostic\-Namespace](../profiling/diagnostic-namespace.md)