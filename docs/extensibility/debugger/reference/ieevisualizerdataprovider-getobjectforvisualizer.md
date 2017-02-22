---
title: "IEEVisualizerDataProvider::GetObjectForVisualizer | Microsoft Docs"
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
  - "IEEVisualizerDataProvider::GetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::GetObjectForVisualizer-Methode"
ms.assetid: bd5376fc-13b4-40b7-9a5d-7ba8289f1b24
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider::GetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft das Objekt ab, das diese Schnellansicht darstellt.  
  
## Syntax  
  
```cpp  
HRESULT GetObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int GetObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### Parameter  
 `ppObject`  
 \[out\]  Das Objekt, auf das diese Schnellansicht dargestellte  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 `GetObjectForVisualizer` wird eine zwischengespeicherte Version des Objekts zurückzugeben.  Wenn der Aufrufer überprüft werden soll, ob das Objekt auf dem neuesten Stand ist, ruft es [GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)an.  
  
## Siehe auch  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)