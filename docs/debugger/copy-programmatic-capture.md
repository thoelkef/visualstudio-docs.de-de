---
title: "Kopieren (Programmgesteuerte Aufzeichnung) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Kopieren (Programmgesteuerte Aufzeichnung)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Kopiert den Inhalt der aktiven Grafikprotokolldatei \(VSGLOG\) in eine neue Datei.  
  
## Syntax  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### Parameter  
 `szNewVSGLog`  
 Der Dateiname der neuen Grafikprotokolldatei.  
  
## Hinweise  
 Um die Grafikinformationen in eine neuen Datei zu kopieren, müssen Sie bereits einige Grafikinformationen erfasst haben, andernfalls geschieht nichts.