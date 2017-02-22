---
title: "IDebugObject2::GetField | Microsoft Docs"
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
  - "IDebugObject2::GetField"
helpviewer_keywords: 
  - "IDebugObject2::GetField-Methode"
ms.assetid: add6a6b5-e752-47dd-9613-29206ea809b0
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::GetField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Typ dieses Objekts ab.  
  
## Syntax  
  
```cpp  
HRESULT GetField(  
 IDebugField** ppField  
);  
```  
  
```c#  
int GetField(  
   out IDebugField ppField  
);  
```  
  
#### Parameter  
 `ppField`  
 \[out\]  Gibt ein Objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) wenn kein NULL\-Wert zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Feld beschreibt den Typ des Objekts.  
  
## Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)