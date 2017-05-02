---
title: "IDebugApplication::FIsAutoJitDebugEnabled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FIsAutoJitDebugEnabled
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FIsAutoJitDebugEnabled"
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FIsAutoJitDebugEnabled
Bestimmt, ob ein Just\-in\-Time Debugger \(JIT\) stummen Hosts AUTODEBUGs registriert wird.  
  
## Syntax  
  
```  
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Wenn die Methode erfolgreich ist und ein JIT\-Debugger zu stummen Hosts AUTODEBUGs registriert wird, gibt die Methode `TRUE` zurück.  Andernfalls wird `FALSE` zurückgegeben.  
  
## Hinweise  
 Diese Methode bestimmt, wenn ein JIT\-Debugger zu stummen Hosts AUTODEBUGs registriert wird.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)