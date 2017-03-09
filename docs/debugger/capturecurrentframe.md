---
title: "CaptureCurrentFrame | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CaptureCurrentFrame
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erfasst den Rest des aktuellen Frames in der Grafikprotokolldatei.  
  
## Syntax  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## Hinweise  
 Wenn derzeit eine andere Erfassung durchgeführt wird – wie etwa eine Erfassung, die durch die `BeginCapture`\-Funktion gestartet wurde – dann wird diese Erfassung abgeschlossen und im Grafikprotokoll als gesonderter Frame aufgezeichnet.  Direkt im Anschluss beginnt die Grafikdiagnose, den Rest des aktuellen Frames zu erfassen, der ebenfalls als gesonderter Frame aufgezeichnet wird.  Das Ende des aktuellen Frames ist durch einen Aufruf von "Present" gekennzeichnet.  
  
 Um Frames zu erfassen, müssen Sie die App entsprechend vorbereiten, damit Grafikinformationen erfasst und aufgezeichnet werden – d. h. Sie müssen [Init](../debugger/init.md) durch eine Instanz der `VsgDbg`\-Klasse aufgerufen haben, bevor Sie `CaptureCurrentFrame` aufrufen.  
  
## Siehe auch  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)