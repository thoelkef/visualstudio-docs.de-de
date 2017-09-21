---
title: "IDebugExpressionEvaluator2::GetService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::GetService"
  - "GetService"
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft ein angegebenes Dienstobjekt sein eindeutiger Bezeichner ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```c#  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### Parameter  
 `uid`  
 \[in\]  Eindeutiger Bezeichner des abzurufenden Diensts.  
  
 `ppService`  
 \[out\]  Gibt ein Objekt zurück, das den Dienst darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Dies kann ein von Drittanbietern Ausdrucksauswertung verwendet werden, um Dienste von einem anderen Ausdrucksauswertung abzurufen.  Beispielsweise kann diese Methode verwendet werden, um die Schnittstelle für Schnellansicht für den vom standardmäßigen Ausdrucksauswertung abzurufen.  Ausdrucksauswerter von Drittanbietern sind unwahrscheinlich diese Schnittstelle implementieren zu müssen.  
  
## Siehe auch  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)