---
title: "IEEVisualizerDataProvider::CanSetObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::CanSetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::CanSetObjectForVisualizer-Methode"
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEEVisualizerDataProvider::CanSetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Mit dieser Methode wird bestimmt, ob die Schnellansicht das Datenobjekt aktualisiert haben kann, das sie darstellt.  
  
## Syntax  
  
```cpp  
HRESULT CanSetObjectForVisualizer(  
   BOOL* b  
);  
```  
  
```c#  
int CanSetObjectForVisualizer(  
   out int b  
);  
```  
  
#### Parameter  
 `b`  
 \[out\]  Ein Wert ungleich 0 \(`TRUE`\), wenn das Objekt in der Schnellansicht aktualisiert werden kann,`FALSE`\(null\), wenn keine kann.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Objekt ist möglicherweise nicht, wenn es an den schreibgeschützten Speicher gebunden wird, z. B. nicht geändert werden.  
  
## Siehe auch  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)