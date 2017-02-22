---
title: "IEEVisualizerDataProvider::GetNewObjectForVisualizer | Microsoft Docs"
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
  - "IEEVisualizerDataProvider::GetNewObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::GetNewObjectForVisualizer-Methode"
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider::GetNewObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft ein neues Objekt für die Schnellansicht ab.  Diese Methode erstellt ein neues Objekt aus vorhandenen Objekt.  
  
## Syntax  
  
```cpp  
HRESULT GetNewObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int GetNewObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### Parameter  
 `ppObject`  
 \[out\]  Das neue Objekt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 `This method` gilt für das Objekt darstellt, das er gerade neu und gibt das Ergebnis als neues Objekt zurück.  Das vorhandene Objekt wird als Ergebnis der Auswertung aktualisiert.  
  
## Siehe auch  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)