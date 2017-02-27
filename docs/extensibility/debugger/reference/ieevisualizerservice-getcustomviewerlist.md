---
title: "IEEVisualizerService::GetCustomViewerList | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService::GetCustomViewerList"
helpviewer_keywords: 
  - "IEEVisualizerService::GetCustomViewerList-Methode"
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt eine Liste der Typ schnellansichten zurück, die dieser Dienst weiß Info.  
  
## Syntax  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### Parameter  
 `celtSkip`  
 \[in\]  Zahl, Schnellansichten nach zu überspringen.  
  
 `celRequested`  
 \[in\]  Zahl abzurufen \(Schnellansichten sind außerdem Größe des Arrays `rgViewers` \).  
  
 `rgViewers`  
 \[in, out\]  Array von Strukturen, [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) ausgefüllt werden soll.  
  
 `pceltFetched`  
 \[out\]  Die Anzahl der tatsächlich abgerufenen Visualizers.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) führt die Anforderung an diese Methode als Teil ihrer Unterstützung für den Typ schnellansichten.  Wenn die vom benutzerdefinierten Viewer Ausdrucksauswerters, auch für denselben Typ, er ausgefüllte\-heraus [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen für diese benutzerdefinierten Viewer zur Liste anfügen können.  Überprüfen Sie, ob [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) diese zusätzlichen Viewer aus.  
  
 Weitere Informationen finden Sie unter [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Einzelheiten über die Unterschiede zwischen Viewern und Visualizers.  
  
## Siehe auch  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)   
 [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)