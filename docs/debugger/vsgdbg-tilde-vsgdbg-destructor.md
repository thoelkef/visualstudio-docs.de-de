---
title: "VsgDbg::~VsgDbg (Destruktor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::~VsgDbg (Destruktor)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Zerstört eine Instanz der `VsgDbg`\-Klasse.  Wenn Grafikinformationen aktiv aufgezeichnet werden, wird die Grafikprotokolldatei abgeschlossen und geschlossen, und die Ressourcen, die während der aktiven Erfassung der Grafikinformationen verwendet wurden, werden freigegeben.  
  
## Syntax  
  
```cpp  
~VsgDbg();  
```  
  
## Siehe auch  
 [VsgDbg::VsgDbg \(Konstruktor\)](../debugger/vsgdbg-vsgdbg-constructor.md)