---
title: "IDebugStackFrame::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetDebugProperty
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetDebugProperty"
ms.assetid: e03c7504-bce4-4a44-81e4-db8c0216538d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetDebugProperty
Gibt einen Eigenschaftenbrowser für den aktuellen Frame zurück.  
  
## Syntax  
  
```  
HRESULT GetDebugProperty(  
   IDebugProperty**  ppDebugProp  
);  
```  
  
#### Parameter  
 `ppDebugProp`  
 \[out\] Ein Eigenschaftenbrowser für den aktuellen Frame.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt einen Eigenschaftenbrowser für den aktuellen Frame zurück.  
  
## Siehe auch  
 [IDebugStackFrame\-Schnittstelle](../../winscript/reference/idebugstackframe-interface.md)