---
title: "Init | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Init
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bereitet die In\-App\-Komponente der Grafikdiagnose vor, um Grafikinformationen aktiv in einer Grafikprotokolldatei zu erfassen und aufzuzeichnen.  
  
## Syntax  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### Parameter  
 `vsgLogGetter`  
 Eine aufrufbare Entität, wie etwa eine Funktion, ein Funktionszeiger, Lambda oder ein Funktionsobjekt, die als Parameter die Länge eines Puffers verwendet, der aus `wchar_t` und einem Zeiger auf diesen Puffer besteht, und `void` zurückgibt.  Wenn sie aufgerufen wird, bestimmt die aufrufbare Entität den Dateinamen, der verwendet wird, um Grafikinformationen aufzuzeichnen, und schreibt in den angegebenen Puffer, bevor eine Rückgabe erfolgt.  
  
## Hinweise  
 Die `Init`\-Funktion wird automatisch aufgerufen, wenn eine Instanz der `VsgDbg`\-Klasse erstellt wird, indem der `bDefaultInit`\-Parameter des Konstruktors auf `true` festgelegt wird. Andernfalls muss `Init` explizit aufgerufen werden, bevor Sie Grafikinformationen aktiv erfassen und aufzeichnen können.  
  
 Sie können die aktive Grafikprotokolldatei durch Aufrufen von `UnInit` abschließen und schließen und anschließend weitere Grafikinformationen in einer neuen Grafikprotokolldatei erfassen und aufzeichnen, indem Sie `Init` erneut aufrufen.  Sie können dies so oft wiederholen, wie Sie möchten, um mehrere unabhängige Grafikprotokolldateien mithilfe derselben `VsgDbg`\-Instanz zu erstellen.  
  
## Siehe auch  
 [UnInit](../debugger/init.md)