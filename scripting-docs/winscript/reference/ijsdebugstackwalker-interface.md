---
title: "IJsDebugStackWalker-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugStackWalker-Schnittstelle
Stellt einen Stapeldurchlauf für einen angegebenen Thread dar.  
  
## Syntax  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## Member  
  
### Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|------------------|  
|[IJsDebugStackWalker::GetNext\-Methode](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Ruft den nächsten Frame ab.|  
  
## Hinweise  
 Stapeldurchläufe können nur erstellt werden, während das Ziel angehalten wird. Sie sind ungültig, sobald der Zielprozess erneut fortgesetzt wurde.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [Windows Script\-Schnittstellenverweis](../../winscript/reference/windows-script-interfaces-reference.md)