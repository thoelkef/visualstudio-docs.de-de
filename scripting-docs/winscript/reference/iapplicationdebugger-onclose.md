---
title: "IApplicationDebugger::onClose | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onClose
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onClose"
ms.assetid: f3d6ca9f-6697-4d02-9d1a-16e3859bf282
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onClose
Behandelt ein Debug\- Anwendungsabschlussereignis.  
  
## Syntax  
  
```  
HRESULT onClose();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird aufgerufen, wenn `IDebugApplication::Close` aufgerufen wird.  
  
## Siehe auch  
 [IApplicationDebugger\-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)