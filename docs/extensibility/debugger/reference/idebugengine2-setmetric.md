---
title: "IDebugEngine2::SetMetric | Microsoft Docs"
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
  - "IDebugEngine2:::SetMetric"
helpviewer_keywords: 
  - "IDebugEngine2:::SetMetric"
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::SetMetric
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode legt diesen fest\), der einen Registrierungswert als eine Metrik bekannt ist.  
  
## Syntax  
  
```cpp#  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```c#  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### Parameter  
 `pszMetric`  
 \[in\]  Der metrische Name.  
  
 `varValue`  
 \[in\]  Gibt den metrischen Wert an.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Eine Metrik ist ein Registrierungswert, die für die Debug\- Moduls ändern Verhalten eines oder unterstützte Funktionalität anzukündigen.  Diese Methode kann den Aufruf an den entsprechenden Format der [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)\-Funktion, `SetMetric`weiterleiten.  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)