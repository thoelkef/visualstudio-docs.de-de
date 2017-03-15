---
title: "UnInit | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UnInit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Schließt die Grafikprotokolldatei ab, schließt sie und gibt Ressourcen frei, die verwendet wurden, während die App aktiv Grafikinformationen aufzeichnete.  
  
## Syntax  
  
```cpp  
void UnInit();  
```  
  
## Hinweise  
 `UnInit` wird automatisch aufgerufen, wenn eine Instanz der `VsgDbg`\-Klasse zerstört wird.  Wenn die `VsgDbg`\-Instanz nicht aktiv Grafikinformationen aufzeichnete, hat dies keine Auswirkungen.  
  
 Nachdem `UnInit` auf einer Instanz der `VsgDbg`\-Klasse aufgerufen wurde, kann eine neue Grafikprotokolldatei erstellt werden, indem `Init` aufgerufen wird. Sie kann abgeschlossen werden, indem `UnInit` aufgerufen wird.  Sie können dies so oft wiederholen, wie Sie möchten, um dieselbe `VsgDbg`\-Instanz zum Erstellen mehrerer unabhängiger Grafikprotokolldateien zu verwenden.  
  
## Siehe auch  
 [Init](../debugger/init.md)