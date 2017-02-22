---
title: "IDebugFunctionObject::Evaluate | Microsoft Docs"
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
  - "IDebugFunctionObject::Evaluate"
helpviewer_keywords: 
  - "IDebugFunctionObject::Evaluate-Methode"
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Funktion auf und gibt den sich ergebenden Wert als Objekt zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### Parameter  
 `ppParams`  
 \[in\]  Ein Array [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekten, die die Eingabeparameter darstellen.  Jeder dieser Parameter wurde mit einer der `Create`\-Methoden in der [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Schnittstelle erstellt.  
  
 `dwParams`  
 \[in\]  Die Anzahl von Parametern im `ppParams` Array.  
  
 `dwTimeout`  
 \[in\]  Bevor der Rückgabe dieser Methode gibt die maximale Zeit in Millisekunden an, zu warten.  `INFINITE` verwenden, um unbegrenzt zu warten.  
  
 `ppResult`  
 \[out\]  Gibt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) zurück, das den Wert der Funktion als Objekt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode installierte und führt einen Aufruf der Funktion aus, die vom [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Objekt dargestellt wird.  
  
## Siehe auch  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)