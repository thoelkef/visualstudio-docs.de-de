---
title: "IDebugField::GetContainer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetContainer"
helpviewer_keywords: 
  - "IDebugField::GetContainer-Methode"
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetContainer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft den Container eines Felds ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetContainer(   
   IDebugContainerField** ppContainerField  
);  
```  
  
```c#  
int GetContainer(  
   out IDebugContainerField ppContainerField  
);  
```  
  
#### Parameter  
 `ppContainerField`  
 \[out\]  Gibt den Container zurück, der durch die [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)\-Schnittstelle dargestellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn dieses Feld keinen Container verfügt, ist das zurückgegebene `ppContainerField` ein NULL\-Wert.  
  
## Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)