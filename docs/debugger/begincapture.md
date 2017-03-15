---
title: "BeginCapture | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# BeginCapture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Startet ein Erfassungsintervall, das mit `EndCapture` endet.  
  
## Syntax  
  
```cpp  
void BeginCapture();  
```  
  
## Hinweise  
 Ein Erfassungsintervall umfasst in der Regel eine Teilmenge eines Frames, etwa wenn Sie Grafikinformationen nur über eine bestimmte Art von Zeichnen\-Befehl erfassen möchten.  Wenn das Erfassungsintervall einen Aufruf von "Present" umfasst, dann werden zwei Frames von Grafikinformationen erfasst.  Der erste Frame umfasst das Intervall zwischen dem Aufruf von `BeginCapture` und dem Aufruf von "Present". Das zweite Intervall umfasst das Intervall zwischen dem ersten Direct3D\-Ereignis nach dem Aufruf von "Present" und dem Aufruf von `EndCapture`.  
  
 Um ein Intervall zu erfassen, müssen Sie die App entsprechend vorbereiten, damit Grafikinformationen erfasst und aufgezeichnet werden – d. h. Sie müssen [Init](../debugger/init.md) durch eine Instanz der `VsgDbg`\-Klasse aufgerufen haben, bevor Sie `BeginCapture` oder `EndCapture` aufrufen.  
  
## Siehe auch  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)