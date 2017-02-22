---
title: "IDebugPort2::GetPortId | Microsoft Docs"
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
  - "IDebugPort2::GetPortId"
helpviewer_keywords: 
  - "IDebugPort2::GetPortId"
ms.assetid: 837cb924-c113-4224-aa86-3e02b33dfa70
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPort2::GetPortId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Bezeichner der Port ab oder legt diese fest.  
  
## Syntax  
  
```cpp#  
HRESULT GetPortId(   
   GUID* pguidPort  
);  
```  
  
```c#  
int GetPortId(   
   out Guid pguidPort  
);  
```  
  
#### Parameter  
 `pguidPort`  
 \[out\]  Gibt die GUID zurück, die den Anschluss angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)