---
title: "IDebugFunctionObject2::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::Evaluate"
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Funktion auf und gibt den sich ergebenden Wert als Objekt zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### Parameter  
 `ppParams`  
 \[in\]  Ein Array [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekten, das die Eingabeparameter darstellt.  Jeder dieser Parameter erstellt wurde, indem eine der Methoden in dieser Schnittstelle.  
  
 `dwParams`  
 \[in\]  Die Anzahl von Parametern im `ppParams` Array.  
  
 `dwEvalFlags`  
 \[in\]  Eine Kombination von Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)\-Enumeration, die angeben, wie die Evaluierung ausgeführt werden soll.  
  
 `dwTimeout`  
 \[in\]  Bevor der Rückgabe dieser Methode gibt die maximale Zeit in Millisekunden an, zu warten.  **INFINITE** verwenden, um unbegrenzt zu warten.  
  
 `ppResult`  
 \[out\]  Gibt ein **IDebugObject zurück,** das den Wert der Funktion als Objekt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)