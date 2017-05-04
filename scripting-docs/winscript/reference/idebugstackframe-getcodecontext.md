---
title: "IDebugStackFrame::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetCodeContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetCodeContext"
ms.assetid: 3dd378f3-e4b7-413e-8812-0f6c72952544
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetCodeContext
Gibt den aktuellen Codekontext zurück, der mit dem Stapelrahmen zugeordnet ist.  
  
## Syntax  
  
```  
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### Parameter  
 `ppcc`  
 \[out\] Der Codekontext zugeordnet mit dem Stapelrahmen.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt den aktuellen Codekontext zurück, der mit dem Stapelrahmen zugeordnet ist.  
  
## Siehe auch  
 [IDebugStackFrame\-Schnittstelle](../../winscript/reference/idebugstackframe-interface.md)