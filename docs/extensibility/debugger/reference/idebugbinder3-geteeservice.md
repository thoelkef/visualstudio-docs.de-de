---
title: "IDebugBinder3::GetEEService | Microsoft Docs"
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
  - "IDebugBinder3::GetEEService"
helpviewer_keywords: 
  - "IDebugBinder3::GetEEService-Methode"
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetEEService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt einen angeforderten Dienst zurück.  
  
## Syntax  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```c#  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### Parameter  
 `vendor`  
 \[in\]  `GUID` eines Anbieters \(ein NULL\-Wert ist zulässig\).  
  
 `language`  
 \[in\]  `GUID` einer Sprache \(ein NULL\-Wert ist zulässig\).  
  
 `iid`  
 \[in\]  `IID` des Diensts abzurufen.  
  
 `ppService`  
 \[out\]  Eine Schnittstelle des angeforderten Diensts.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Führen Sie `IID` für die [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)\-Schnittstelle \(`IID_IEEVisualizerServiceProvider`\), um festzustellen, ob der Typ\-Schnellansichts für verfügbar ist.  In diesem Fall kann die Ausdrucksauswertung Abrufen der [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)\-Schnittstelle, um Typ schnellansichten zu unterstützen.  Ausführliche Informationen finden Sie unter [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md).  
  
## Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)