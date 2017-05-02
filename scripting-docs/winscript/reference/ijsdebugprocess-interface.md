---
title: "IJsDebugProcess-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugProcess-Schnittstelle
Stellt Routinen zum Überprüfen und Steuern des Zielprozesses bereit.  
  
## Syntax  
  
```  
IJsDebugProcess : public IUnknown;  
```  
  
## Member  
  
### Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|------------------|  
|[IJsDebugProcess::CreateBreakPoint\-Methode](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Legt den Haltepunkt an der angegebenen Dokumentposition fest.|  
|[IJsDebugProcess::CreateStackWalker\-Methode](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Factorymethode für Stapeldurchlauf.|  
|[IJsDebugProcess::PerformAsyncBreak\-Methode](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Setzt das Skriptmodul in den Unterbrechungsmodus, der bei der nächsten Skriptanweisung eine Unterbrechung veranlasst.|  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [Windows Script\-Schnittstellenverweis](../../winscript/reference/windows-script-interfaces-reference.md)