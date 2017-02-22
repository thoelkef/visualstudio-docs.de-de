---
title: "IDebugCustomAttribute::GetParentField | Microsoft Docs"
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
  - "IDebugCustomAttribute::GetParentField"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetParentField"
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttribute::GetParentField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Rechteck ab, mit dem das benutzerdefinierte Attribut angefügt wird.  
  
## Syntax  
  
```cpp#  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```c#  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### Parameter  
 `ppField`  
 \[out\]  Gibt das [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt zurück, das das Feld darstellt, auf den das benutzerdefinierte Attribut angefügt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Rufen Sie die Methode [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) für den zurückgegebenen [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt auf, um zu bestimmen, welche Art von Kästchen der übergeordnete Inhalt ist.  
  
## Siehe auch  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)