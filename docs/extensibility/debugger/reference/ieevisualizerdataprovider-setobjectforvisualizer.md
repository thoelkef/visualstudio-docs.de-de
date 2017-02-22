---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer-Methode"
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ändert das Objekt, das die Schnellansicht darstellt.  
  
## Syntax  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```c#  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### Parameter  
 `pNewObject`  
 \[in\]  Das festzulegende Objekt.  
  
 `error`  
 \[out\]  Wenn ein Fehler, der das angegebene Objekt festgelegt wird, verhindert diese Zeichenfolge der Fehlermeldung.  
  
 `pException`  
 \[out\]  Wenn es einen Fehler enthält, ist dieses Objekt die Ausnahmeinformationen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Es ist von der Implementierung, um zu bestimmen, wie Fehlerinformationen zurückgegeben werden.  Es ist jedoch möglich, dass einige Aufrufer nur überprüfen, um zu ermitteln, ob ein Ausnahmeobjekt zurückgegeben wurde, um zu wissen, dass ein Fehler gegeben hat, sollte daher immer ein Ausnahmeobjekt diese Methode zurückgeben, wenn ein Fehler aufgetreten ist.  Die Fehlerzeichenfolge muss auch angegeben werden, wenn der Aufrufer sie verwenden möchte.  
  
## Siehe auch  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)