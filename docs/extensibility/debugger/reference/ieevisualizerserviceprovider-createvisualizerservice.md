---
title: "IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService"
helpviewer_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService-Methode"
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode erstellt eine für Schnellansicht.  
  
## Syntax  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```c#  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### Parameter  
 `binder`  
 \[in\]  Das [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)\-Objekt übergeben [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 \[in\]  Das [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)\-Objekt übergeben `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 \[in\]  Das [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Objekt übergeben `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 \[in\]  Ein Objekt, das die [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)\-Schnittstelle implementiert \(angezeigt vom Ausdrucksauswertung\).  
  
 `ppService`  
 \[out\]  Der erstellte Dienst.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 `binder`, `pSymProv`und `pAddress` alle Parameter wurden `IDebugParsedExpression::EvaluateSync` die Methode übergeben.  `CreateVisualizerService` soll nur von `IDebugParsedExpression::EvaluateSync` als Teil der Unterstützung eines Ausdrucksauswerters für den Typ schnellansichten aufgerufen werden.  
  
## Siehe auch  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)