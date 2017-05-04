---
title: "IEnumDebugExpressionContexts::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExpressionContexts.Clone
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugExpressionContexts::Clone"
ms.assetid: c8070ae1-120c-4b5d-bd3d-ae8fca6f9277
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExpressionContexts::Clone
Erstellt einen Enumerator, der den gleichen Zustand wie der aktuelle Enumerator enthält.  
  
## Syntax  
  
```  
HRESULT Clone(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### Parameter  
 `ppedec`  
 \[out\] Gibt die `IEnumDebugExpressionContexts`\-Schnittstelle des Klons des Enumerators zurück.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode erstellt einen Enumerator, der denselben Zustand wie der aktuelle Enumerator enthält.  
  
## Siehe auch  
 [IEnumDebugExpressionContexts\-Schnittstelle](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)