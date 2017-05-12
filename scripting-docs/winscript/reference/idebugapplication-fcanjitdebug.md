---
title: "IDebugApplication::FCanJitDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FCanJitDebug
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FCanJitDebug"
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FCanJitDebug
Bestimmt, ob ein Just\-in\-Time\-Debugger \(JIT\) registriert ist.  
  
## Syntax  
  
```  
BOOL FCanJitDebug();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Wenn die Methode erfolgreich ist und ein JIT\-Debugger registriert wird, gibt die Methode `TRUE` zurück.  Andernfalls wird `FALSE` zurückgegeben.  
  
## Hinweise  
 Diese Methode bestimmt, wenn ein JIT\-Debugger registriert wird.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)